<template>
  <div class="container">
    <div id="app">
      <h1 class="title">Vue Query Builder Demo</h1>
      <a class="btn btn-default github-link" href="https://github.com/dabernathy89/vue-query-builder">Source on GitHub</a>

      <hr>

      <vue-query-builder
        :rules="rules"
        :maxDepth="3"
        :labels="labels"
        :initialQuery="initialQuery"
        @query-updated="queryUpdated"
        ></vue-query-builder>

      <hr>

      <pre>{{ JSON.stringify(query, null, 2) }}</pre>
    </div>
  </div>
</template>

<script>
  import VueQueryBuilder from '../src/VueQueryBuilder.vue';

  export default {
    components: {
      VueQueryBuilder,
    },

    methods: {
      queryUpdated (query) {
        this.query = query;
      }
    },

    data () {
      return {
        initialQuery: {
          "logicalOperator": "Any",
          "children": [
            {
              "type": "query-builder-rule",
              "query": {
                "rule": "first-name",
                "selectedOperator": "equals",
                "selectedOperand": "First Name",
                "value": "John"
              }
            },
          ]
        },
        query: null,
        labels: {
          removeRule: "<span class='glyphicon glyphicon-remove'></span>",
          removeGroup: "<span class='glyphicon glyphicon-remove'></span>",
        },
        rules: [
          {
            type: "text",
            id: "a-text-field",
            label: "A Text Field",
          },
          {
            type: "text",
            id: "first-name",
            label: "First Name",
          },
          {
            type: "numeric",
            id: "a-numeric-field",
            label: "A Numeric Field",
          },
          {
            type: "radio",
            id: "a-radio-field",
            label: "A Radio Field",
            choices: [
              {label: "Val 1", value: "val1"},
              {label: "Val 2", value: "val2"},
              {label: "Val 3", value: "val3"}
            ]
          },
          {
            type: "checkbox",
            id: "a-checkbox-field",
            label: "A Checkbox Field",
            choices: [
              {label: "Val 1", value: "val1"},
              {label: "Val 2", value: "val2"},
              {label: "Val 3", value: "val3"}
            ]
          },
          {
            type: "checkbox",
            id: "a-checkbox-field-with-multiple-operands",
            label: "A Checkbox Field With Multiple Operands",
            operands: ['operand1','operand2','operand3'],
            choices: [
              {label: "Val 1", value: "val1"},
              {label: "Val 2", value: "val2"},
              {label: "Val 3", value: "val3"}
            ]
          },
          {
            type: "radio",
            id: "a-radio-field-with-multiple-operands",
            label: "A Radio Field With Multiple Operands",
            operands: ['operand1','operand2','operand3'],
            choices: [
              {label: "Val 1", value: "val1"},
              {label: "Val 2", value: "val2"},
              {label: "Val 3", value: "val3"}
            ]
          },
          {
            type: "custom",
            id: "a-custom-text-field",
            label: "A Custom Text Field",
            operators: ['equals','does not equal'],
            inputType: "text"
          },
          {
            type: "custom",
            id: "a-custom-number-field",
            label: "A Custom Number Field",
            operators: ['=','<>','<','<=','>','>='],
            inputType: "number"
          },
          {
            type: "custom",
            id: "a-field-with-multiple-operands",
            label: "A Field With Multiple Operands",
            operands: ['val1','val2','val3'],
            operators: ['=','<>','<','<=','>','>='],
            inputType: "number"
          },
        ]
      }
    }
  };
</script>