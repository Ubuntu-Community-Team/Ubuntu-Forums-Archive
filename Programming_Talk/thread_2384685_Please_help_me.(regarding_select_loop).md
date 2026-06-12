---
title: "Please help me.(regarding select loop)"
date: 2018-02-10
forum: Programming Talk
---

### Post by mak. on 2018-02-10
Whenever I execute this code and I type any of the items in the 'FRUIT' list, it does not echo the lines for that condition. Instead a new empty line appears with #? at its start. Why is this happening? What should I do to fix this?
Code:
#!/bin/bash
select FRUIT in pear guava grapes banana all none
do
case $FRUIT in
pear|banana) echo "Out of stock."
;;
guava|grapes) echo "Wait in line."
;;
all) echo "You may pay either in cash or card."
;;
none) echo "Don't waste my time then."
break
;;
esac
done

---

### Post by spjackson on 2018-02-10
> **mak. said:**
> Whenever I execute this code and I type any of the items in the 'FRUIT' list, it does not echo the lines for that condition. Instead a new empty line appears with #? at its start. Why is this happening? What should I do to fix this?


You are being prompted again because what you type does not match any of the valid **numbers**.
```

$ cat foo.sh
#!/bin/bash
select FRUIT in pear guava grapes banana all none
do
case $FRUIT in
pear|banana) echo "Out of stock."
;;
guava|grapes) echo "Wait in line."
;;
all) echo "You may pay either in cash or card."
;;
none) echo "Don't waste my time then."
break
;;
[COLOR=#ff0000]*) echo "$Invalid option"
;;[/COLOR]
esac
done
$ ./foo.sh 
1) pear
2) guava
3) grapes
4) banana
5) all
6) none
#? pear
Invalid option
#? 2
Wait in line.
#? 5
You may pay either in cash or card.
#? 6
Don't waste my time then.

```

---

### Post by mak. on 2018-02-11
Thanks.

---

