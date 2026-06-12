---
title: "bash implementation of pick command"
date: 2010-04-17
forum: Programming Talk
---

### Post by piyush.neo on 2010-04-17
pick command is used to select its arguments interactively.
i have made it to take its arguments from stdin...
why the break statement is not working??
```

if [ $# -eq 0 ];then
read data;
set $data;
fi
for i
do

        echo -n "$i? "
        read response
        case $response in
        y*)echo "$i";;
        n*)break;;
        esac
done     

```
:(

---

