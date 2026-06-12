---
title: "formatting a text file for csv"
date: 2014-04-02
forum: Programming Talk
---

### Post by peter_brickles on 2014-04-02
HI guys i have a text file as below 

> 
South Gloucestershire           Myglobe LTD                          Ideal Pharmacy              1 High Street
Havering                        Nl Wade Ltd                       Day Lewis Pharmacy              143 Avon Road
Barnet                          Thankey BP                     Westlake Pharmacy          1015 Finchley Road



as you can see spaces are not consistant and some colums will contain strings incluing spaces.

Any one know how i can format such sa a neat csv file ? 

Many thanks

---

### Post by Vaphell on 2014-04-02
you didn't say what/how many columns are supposed to be there and how to recognize them.
Is there a rule that distinguishes between space-as-delimiter and space-as-part-of-value?

---

### Post by peter_brickles on 2014-04-02
sorry didn’t notice the list had lost formatting 4 colums 




```

South Gloucestershire           Myglobe LTD                          Ideal Pharmacy              1 High Street
Havering                        Nl Wade Ltd                       Day Lewis Pharmacy              143 Avon Road
Barnet                          Thankey BP                     Westlake Pharmacy          1015 Finchley Road


```

---

### Post by Vaphell on 2014-04-02
so the columns are separated by a bunch of spaces?

assuming that single spaces belong to value and 2+ spaces/tabs = separator:

```
$ awk 'BEGIN{ OFS=","; FS="[ \t][ \t]+"; } { $1=$1; print; }' addr.txt
South Gloucestershire,Myglobe LTD,Ideal Pharmacy,1 High Street
Havering,Nl Wade Ltd,Day Lewis Pharmacy,143 Avon Road
Barnet,Thankey BP,Westlake Pharmacy,1015 Finchley Road
```

---

### Post by peter_brickles on 2014-04-02
Thank you very much worked great

---

