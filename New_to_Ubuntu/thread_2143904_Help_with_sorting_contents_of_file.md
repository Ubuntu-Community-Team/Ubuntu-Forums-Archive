---
title: "Help with sorting contents of file"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Come TO love on 2013-05-10
i have file and i try sort them by mark field 

```


name:mark:sex
Sara:300:f
John:245:m
Lei:387:m 
Faene:229:f


```

output should be like this


```



name:mark:sex 
Faene:229:f 
John:245:m 
Sara:300:f 
Lei:387:m




```


   i try this commend sort +2n file  but i get error !

---

### Post by steeldriver on 2013-05-10
try

```

$ sort -t':' -n -k2,2 file
name:mark:sex
Faene:229:f
John:245:m
Sara:300:f
Lei:387:m

```

---

### Post by Come TO love on 2013-05-10
> **steeldriver said:**
> try

```

$ sort -t':' -n -k2,2 file
name:mark:sex
Faene:229:f
John:245:m
Sara:300:f
Lei:387:m

```

thaaaaanks alot:p

---

### Post by Come TO love on 2013-05-10
ok i try now extract who have mark greater than 250
how can do that?!

output should be:

```


name:mark:sex
Sara:300:f
Lei:387:m


```

i try do that by this command
sort -t':' -n -k2,2 -gt 100: file

---

### Post by steeldriver on 2013-05-10
easier with awk

```
$ awk -F":" 'NR > 1 && $2 > 250 {print}' file
Sara:300:f
Lei:387:m

```

(the "NR > 1" part is just to skip the header line)

---

### Post by Come TO love on 2013-05-10
> **steeldriver said:**
> easier with awk

```
$ awk -F":" 'NR > 1 && $2 > 250 {print}' file
Sara:300:f
Lei:387:m

```

(the "NR > 1" part is just to skip the header line)




Thank you very much intelligent =D>

---

