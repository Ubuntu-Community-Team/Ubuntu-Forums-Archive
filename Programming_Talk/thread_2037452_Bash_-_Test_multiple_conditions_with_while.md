---
title: "Bash - Test multiple conditions with while"
date: 2012-08-04
forum: Programming Talk
---

### Post by boukli on 2012-08-04
Hi all,

I would like to use in my script an instruction like the following :

> while $MY_VAR = "sth", or "sth else", or "another thing"
    do some stuff
done 

However, I have no idea how to write this. I know how to test multiple values with "for" or "case", but not with "while" or "until".  So, some help would be appreciated :P

---

### Post by codemaniac on 2012-08-04
> **boukli said:**
> Hi all,

I would like to use in my script an instruction like the following :



However, I have no idea how to write this. I know how to test multiple values with "for" or "case", but not with "while" or "until".  So, some help would be appreciated :P

combine your expressions with "&&" and/or "||" in order to test for multiple conditions.

---

### Post by steeldriver on 2012-08-04
it should be pretty much the same as the 'for' synatax I think - e.g.

```
while [ "$myvar" -eq "value1" -o "$myvar" -eq "value2" -o  "$myvar" -eq "value3" ]; do *stuff*; done

```or with the [[ ]] test operator,

```
while [[ "$myvar" == "value1" || "$myvar" == "value2" ||  "$myvar" == "value3" ]]; do *stuff*; done
```Or if you can express the different cases as a regular expression pattern you could do something like

```
while [[ "$myvar" =~ *pattern*  ]]; do *stuff*; done
```

---

