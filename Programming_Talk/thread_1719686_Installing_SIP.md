---
title: "Installing SIP"
date: 2011-04-02
forum: Programming Talk
---

### Post by J91321 on 2011-04-02
Hi, I want to install PyQt3 because pip gives me an error I tried to install it manually. First I need to install sip when I tried make I get error:
```

siplib.c: In function &#8216;raiseNoWChar&#8217;:
siplib.c:10816: error: &#8216;PyExc_SystemError&#8217; undeclared (first use in this function)
siplib.c: At top level:
siplib.c:10825: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
siplib.c:10858: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
make[1]: *** [siplib.o] Chyba 1
make[1]: Leaving directory `/home/john/Python/sip-4.12.1/siplib'
make: *** [all] Chyba 2

```
I have Ubuntu 10.04.
Edit: Ok I solved it, I had to install python3-dev.

---

