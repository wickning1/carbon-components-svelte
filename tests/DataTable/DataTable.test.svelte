<script lang="ts">
  import { DataTable } from "carbon-components-svelte";

  type BaseRow = {
    id: string;
    [key: string]: any;
  };

  type DataTableHeader = {
    key: string;
    value: string;
    width?: string;
    minWidth?: string;
    display?: (value: any) => string;
    sort?: false | ((a: any, b: any) => number);
  };

  export let headers: readonly DataTableHeader[] = [
    { key: "name", value: "Name" },
    { key: "protocol", value: "Protocol" },
    { key: "port", value: "Port" },
    { key: "rule", value: "Rule" },
  ] as const;

  export let rows: readonly BaseRow[] = [
    {
      id: "a",
      name: "Load Balancer 3",
      protocol: "HTTP",
      port: 3000,
      rule: "Round robin",
    },
    {
      id: "b",
      name: "Load Balancer 1",
      protocol: "HTTP",
      port: 443,
      rule: "Round robin",
    },
    {
      id: "c",
      name: "Load Balancer 2",
      protocol: "HTTP",
      port: 80,
      rule: "DNS delegation",
    },
  ];

  export let title = "";
  export let description = "";
  export let size: "compact" | "short" | "medium" | "tall" | undefined =
    undefined;
  export let zebra = false;
  export let sortable = false;
  export let stickyHeader = false;
  export let useStaticWidth = false;
  export let expandable = false;
  export let batchExpansion = false;
  export let selectable = false;
  export let radio = false;
  export let batchSelection = false;
  export let nonSelectableRowIds: string[] = [];
  export let nonExpandableRowIds: string[] = [];
  export let pageSize = 0;
  export let page = 0;
</script>

<DataTable
  {headers}
  {rows}
  {title}
  {description}
  {size}
  {zebra}
  {sortable}
  {stickyHeader}
  {useStaticWidth}
  {expandable}
  {batchExpansion}
  {selectable}
  {radio}
  {batchSelection}
  {nonSelectableRowIds}
  {nonExpandableRowIds}
  {pageSize}
  {page}
  on:click={(e) => {
    console.log("click", e.detail);
  }}
  on:click:header={(e) => {
    console.log("click:header", e.detail);
  }}
  on:click:row={(e) => {
    console.log("click:row", e.detail);
  }}
  on:click:cell={(e) => {
    console.log("click:cell", e.detail);
  }}
  on:mouseenter:row={(e) => {
    console.log("mouseenter:row", e.detail);
  }}
  on:mouseleave:row={(e) => {
    console.log("mouseleave:row", e.detail);
  }}
>
  <slot />
</DataTable>
