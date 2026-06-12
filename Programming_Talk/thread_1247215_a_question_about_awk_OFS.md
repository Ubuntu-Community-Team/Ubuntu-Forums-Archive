---
title: "a question about awk OFS"
date: 2009-08-22
forum: Programming Talk
---

### Post by audit on 2009-08-22
How come when I enter:

 ```
echo a b c d |awk ' {OFS = ":"; print}'
```

my output is not ```
a:b:c:d
```

what am I doing wrong

---

### Post by audit on 2009-08-22
Please ignore I found the answer--i should have entered:

  ```
echo a b c d |awk ' {OFS = ":"; print $1,$2,$3,$4}'
```

---

### Post by ghostdog74 on 2009-08-23
you are using it wrongly, put your OFS in begin block. 
```

# echo a b c d |awk 'BEGIN{OFS = ":"}{$1=$1}1'
a:b:c:d

```

---

