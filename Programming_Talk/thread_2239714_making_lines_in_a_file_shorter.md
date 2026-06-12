---
title: "making lines in a file shorter"
date: 2014-08-15
forum: Programming Talk
---

### Post by peter_brickles on 2014-08-15
I have a list of longitudes in the following format  

> 


 53.961224 
 53.964072 
 53.96492 
 53.96392 
 53.96347




 in a text file but I need to make then just four digits after the decimal point  
 
> 

 53.9612 
53.9640 
53.9649 
53.9639 
53.9634

 

 does any one know of a one liner sed perl awk ? To accomplish this or any other ways without going through the 10k or  so lines by hand ?
 

 Any help would be gratefully appreciated  
 

 

 Pete

---

### Post by Vaphell on 2014-08-15
```
$ grep -Eo '[0-9]+[.][0-9]{4}' test.data 
53.9612
53.964[COLOR="#0000FF"]0[/COLOR]
53.9649
53.9639
53.963[COLOR="#0000FF"]4[/COLOR]
$ sed -r 's/([0-9]+[.][0-9]{4}).*/\1/' test.data
53.9612
53.964[COLOR="#0000FF"]0[/COLOR]
53.9649
53.9639
53.963[COLOR="#0000FF"]4[/COLOR]
$ awk '{ printf ( "%.4f\n", $1 ); }' test.data
53.9612
53.964[COLOR="#0000FF"]1[/COLOR]
53.9649
53.9639
53.963[COLOR="#0000FF"]5[/COLOR]
```

note that awk will properly round the number instead of just dropping digits.

---

### Post by steeldriver on 2014-08-15
... to add,

```

perl -ne 'printf("%.4f\n", $_)' test.data

```

```

while read val; do printf '%.4f\n' "$val"; done < test.data

```

The perl one has the advantage of being able to modify the file in-place (with the -i option)

---

