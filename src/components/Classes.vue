<template lang="pug">
.home
  nav.ph3.ph5-ns
    .nowrap.overflow-x-auto
      a.link.dim.mr3(@click="filter('new')") new
      a.link.dim.mr3(@click="filter('popular')") popular
      a.link.dim.mr3(@click="filter('all-time')") all-time
      a.link.dim.gray.f5.f4-ns.dib.mr3(@click="reset()") clear
  ul
    li(v-for='organization in organizations')
      org-block(v-bind:organization='organization')
</template>

<script>
import OrganizationBlock from './support/OrganizationBlock'

export default {
    name: 'classes',
    components: {
        'org-block': OrganizationBlock
    },
    data () {
        return {
            msg: 'Organizations',
            originalData: [
                {name: 'class 1', desc: 'this is what they do.', filter: 'new,popular,all-time'},
                {name: 'class 2', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 3', desc: 'this is what they do.', filter: 'popular,new'},
                {name: 'class 4', desc: 'this is what they do.', filter: 'popular,all-time'},
                {name: 'class 5', desc: 'this is what they do.', filter: 'all-time'},
                {name: 'class 6', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 7', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 8', desc: 'this is what they do.', filter: 'all-time'}
            ],
            organizations: [ // a temporary copy of the orig
                {name: 'class 1', desc: 'this is what they do.', filter: 'popular,all-time'},
                {name: 'class 2', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 3', desc: 'this is what they do.', filter: ''},
                {name: 'class 4', desc: 'this is what they do.', filter: 'popular,all-time'},
                {name: 'class 5', desc: 'this is what they do.', filter: 'all-time'},
                {name: 'class 6', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 7', desc: 'this is what they do.', filter: 'popular'},
                {name: 'class 8', desc: 'this is what they do.', filter: 'all-time'}
            ]
        }
    },
    methods: {
        filter (filterBy) {
            var filteredData = []

            console.log('info', filterBy)
            this.originalData.forEach((org) => {
                console.log('info', org)
                if (org.filter.split(',').includes(filterBy)) {
                    console.log('info', 'true')
                    filteredData.push(org)
                }
            })

            this.organizations = filteredData
        },
        reset () {
            this.organizations = this.originalData
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
