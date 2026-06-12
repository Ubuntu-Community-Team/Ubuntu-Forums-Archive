---
title: "Bash - sed regexp"
date: 2009-04-12
forum: Programming Talk
---

### Post by RuleMaker on 2009-04-12
I have have the following string:
```
OAS_query = 'context=trvl_btrav_36hr&pdsrch=300x170&temp=**72**&uv=1&humid=34&dew=42&wind=16&cond=clear_sunny&templ1=49&temph2=67&templ2=47&temph3=66&templ3=46&';
rsi=rsi_clean_array.join('&rsi=');function filterNum(str){var temp=str;temp=temp.replace(/[^a-zA-Z 0-9]+/g,'_');temp=temp.replace(/\s/g,'_');temp=temp.toLowerCase();return temp;}
```

...and I need to extract only the "72" that follows the "temp=".
I thought using sed would be the best solution but I cant manage to do this.

I'm new to bash scripting although I often use regular expressions with JavaScript.

---

### Post by odyniec on 2009-04-12
Assuming the part that you want to extract is always numeric, this expression should do it:
```
sed 's/.*temp=\([0-9]\+\).*/\1/;q'
```

---

### Post by RuleMaker on 2009-04-12
Thanks odyniec, works perfectly.

Could you clarify one thing (it's a bit different in JS), so I'm confused here:
s/ - means substitute
.* - means any string
temp= - exact string we were looking for
etc...
but what is this:
**/\1/;q**

---

### Post by odyniec on 2009-04-12
/\1/ - replace the matching part with the contents of the first sub-expression (in parentheses)
q - quit (don't process any more lines)

See the sed manual page for more information.

---

### Post by RuleMaker on 2009-04-12
Thanks!

---

