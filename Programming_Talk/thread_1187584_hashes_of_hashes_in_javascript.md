---
title: "hashes of hashes in javascript?"
date: 2009-06-14
forum: Programming Talk
---

### Post by slavik on 2009-06-14
idea is simple:

single HTML page with embedded javascript and html data.
html page loads and upon load, javascript code is called.
javascript code, parses the html data and creates hashes of hashes. (table headers and unique values for each column).

the problem:
javascript does not have true hashes. one way which I found to fake a hash is to use an object and set the property of what I want to store equal to 1. the problem is making this nest 2 levels or more.

for example:
```

var obj = new Object();
obj[document.getElementById('a').innerHTML][document.getElementById('b').innerHTML] = 1;

```

the above does not seem possible.

although maybe having a separate array of Objects?

---

### Post by Can+~ on 2009-06-14
So you're want to something in the lines of:

f(g(key)) 

(Where f and g are hash functions)

You'll have to define a g() function to generate a proper key for your pseudo hash. Something like (all strings)

f(key1 + separator + key2)

Separator is to avoid conflicts between similar named key1 and key2 like having K1="Hello", K2="World", and K1="Hello World", K2="".

---

### Post by slavik on 2009-06-14
the idea is to use hashes as sets, ie: get all unique values from a list of things.

---

### Post by slavik on 2009-06-15
got it! and it is easier than I thought ...

data is an array of objects
each object has a property of 'x' which is equal 'y'
'x' is the key, 'y' is the value.

this converts it to hash of hashes where
hash[x][y] = 1

original data has to be stored as is for future use. :)
```

				for (c in data) {

					for (key in data[c]) {

						if (fields[key] == undefined) {

							fields[key] = new Object();

						}

						fields[key][data[c][key]] = 1;

					}

				}
```

---

