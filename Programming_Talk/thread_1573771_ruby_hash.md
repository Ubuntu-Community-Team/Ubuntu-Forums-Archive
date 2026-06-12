---
title: "ruby hash"
date: 2010-09-13
forum: Programming Talk
---

### Post by cybo on 2010-09-13
i'm trying to learn ruby and i have a question about the following code

```
data = []
line = "first_name=david;last_name=black;country=usa"
record = Hash[*line.split(/=|;/)]
data.push(record)
```

what does the '*' mean in the hash creation? what does it do?

i.e. the following line

```

              |----------- what does this star do? 
              |
record = Hash[*line.split(/=|;/)]
```

help is appreciated

---

### Post by dv3500ea on 2010-09-13
Let's break it down:
```

line.split(/=|;/)

``` splits the string ```
"first_name=david;last_name=black;country=usa"
``` into the array ```
["first_name", "david", "last_name", "black", "country", "usa"]
```.

```
Hash[key1, val1, key2, val2, ...]
``` uses its arguments to create a hash ```
{key1 => val1, key2 => val2, ...}
```.

The '*' converts the array into a list of arguments. This works in any form of function. eg.
```

def add a, b
    a+b
end
add(1, 2) #-> 3
add([1,2]) #-> ERROR
add(*[1,2]) #-> 3

```

**Summary:** 
```

Hash[*line.split(/=|;/)] ==

Hash[*["first_name", "david", "last_name", "black", "country", "usa"]] ==

Hash["first_name", "david", "last_name", "black", "country", "usa"] ==

{"country"=>"usa", "last_name"=>"black", "first_name"=>"david"} !=

Hash[["first_name", "david", "last_name", "black", "country", "usa"]]


```

---

### Post by cybo on 2010-09-13
thanks for the explanation.

---

