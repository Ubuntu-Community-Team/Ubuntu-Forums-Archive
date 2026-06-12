---
title: "filter returns both cat and empty string"
date: 2022-02-26
forum: Programming Talk
---

### Post by maclenin on 2022-02-26
Essentially, I am trying to filter the cat from this array...
```
var x = [
{"a":"cat", "b":"old", "c":"gray"},
{"a":"dog", "b":"young", "c":"brown"},
{"a":"", "b":"old", "c":"white"}
];

var f = {};

var result = [];

```

...using this function:
```
function search(f) {
result = x.filter(function(o) {
return Object.entries(f).every(function([k, v]) {
return v.includes(o[k]);
});
});
console.log("search f ", f);
console.log("search result ", result);
}

```

However, when I run the search...
```
function testSearch() {
f = {a: 'cat'};
search(f);
}

```
...I get both the cat and the empty string.
```
"search f "
{"a":"cat"}
"search result "
[{"a":"cat","b":"old","c":"gray"},{"a":"","b":"old","c":"white"}]
```

Not sure why.

Thanks for any guidance!

---

### Post by spjackson on 2022-02-27
Let's read the code and try to guess what language it might be... I guess Javascript.

The reason you are getting the result you are seeing is because
```

'cat'.includes('');

```
is true. Whereas,
```

''.includes('cat');

```
is false.

Instead, I think you mean
```

o[k].includes(v);

```

---

### Post by maclenin on 2022-02-27
Indeed!

Many thanks for the clarity!

---

