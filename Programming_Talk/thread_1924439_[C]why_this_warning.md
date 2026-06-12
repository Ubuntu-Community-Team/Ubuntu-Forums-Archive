---
title: "[C]why this warning?"
date: 2012-02-12
forum: Programming Talk
---

### Post by rschirin on 2012-02-12
can someone explain me this?

```

ro@beethoven:~/Scrivania/o_fine$ gcc -c -Wall proxy_invio.c
proxy_invio.c: In function &#8216;main&#8217;:
proxy_invio.c:1028:26: warning: variable &#8216;len2&#8217; set but not used [-Wunused-but-set-variable]
```

in proxy_invio.c

```
#define GETMHTTP "GET mhttp://"

main(){
int len2;
.
.
.
.
len2=strlen(GETMHTTP);
.
.
.

```

---

### Post by schauerlich on 2012-02-12
Well, read the warning. You give 'len2' a value (the result of strlen()), but then never use the variable anywhere else. If you think you did use the variable somewhere, then chances are you made a typo.

---

