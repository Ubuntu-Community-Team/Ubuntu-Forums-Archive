---
title: "Hyper terminal"
date: 2020-06-15
forum: Programming Talk
---

### Post by zkab on 2020-06-15
I am testing terminal Hyper and get a syntax error when adding a section.
According to documentation [https://openbase.io/js/hyperborder/documentation](https://openbase.io/js/hyperborder/documentation) this
is to be included ... 

[HTML]module.exports = {
  config: {
    ...
      hyperBorder: {
        borderColors: ['#fc1da7', '#fba506'],
        borderWidth: '8px'
      }
    ...
  }
}[/HTML]

but I get syntax error in my configuration adding section hyperBorder...

[HTML]module.exports = {
  config: {
    // choose either `'stable'` for receiving highly polished,
    // or `'canary'` for less polished but more frequent updates
    updateChannel: 'stable',

    // ZKAB
    hyperBorder: {
      borderColors: ['#fc1da7','#fba506'],
      borderWidth: '8px'
    }
[/HTML]

Where have I missed?

---

### Post by zkab on 2020-06-15
SOLVED ...
[HTML]
    // ZKAB
    hyperBorder: {
      borderColors: ['#fc1da7','#fba506'],
      borderWidth: '8px'
    },[/HTML]

---

