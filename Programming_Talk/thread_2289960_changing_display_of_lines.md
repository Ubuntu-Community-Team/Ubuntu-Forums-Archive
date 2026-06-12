---
title: "changing display of lines"
date: 2015-08-08
forum: Programming Talk
---

### Post by peter_brickles on 2015-08-08
i have a file which contains the following lines 

> 
apple - pears 
oranges - bananas 


is any way to get the file to swich  so it displays 

> 
pears -apple
bananas - oranges


any help would be appreciated guys

---

### Post by steeldriver on 2015-08-08
Is the difference in whitespace (no space between the - and apple) significant? if not I'd probably do something like

```

awk '{print $3" - "$1}' file

```

or

```

awk '{print $3,$2,$1}' file

```

---

