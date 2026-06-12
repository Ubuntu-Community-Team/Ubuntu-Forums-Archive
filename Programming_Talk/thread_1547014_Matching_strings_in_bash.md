---
title: "Matching strings in bash"
date: 2010-08-06
forum: Programming Talk
---

### Post by Grenage on 2010-08-06
I'm having a nightmare understanding string matching in bash:

```
#!/bin/bash
#migrate.sh
#0.01 test run

filename=LOLROFLCOPTER_WIN.WOOT

for (( i=0; i<${#filename}; i++ ))
do
        if [[ $filename:$i:1 == L ]]
        then
                echo "FOUND THE BLIGHTER!"
        fi

        echo ${filename:$i:1}
done

```

For neither love nor money, I can't get $filename:$i:1 to match "L".  I've tried single brackets (not entirely sure how it differs), encapsulating the variable in quotes, removing spaces (nor am I sure why spaces matter), and everything else I can think of.

Many Google searches have resulted in various syntaxes, none of which are working in this application.  Can anyone tell me where I am going wrong?

---

### Post by DaithiF on 2010-08-06
Hi, try:
```
if [[ "${filename:i:1}" == "L" ]]
```

---

### Post by Grenage on 2010-08-06
I forgot the curly braces around the expression - I feel like such an idiot.  Thank you so much.

---

