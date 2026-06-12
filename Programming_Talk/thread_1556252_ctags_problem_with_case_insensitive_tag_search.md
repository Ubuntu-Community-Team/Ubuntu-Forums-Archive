---
title: "ctags problem with case insensitive tag search"
date: 2010-08-19
forum: Programming Talk
---

### Post by mensch0815 on 2010-08-19
Hi,

I'm using ctags with VHDL which is an case insensitive language. I've defined my own rules for it, as the version of ctags does not support VHDL.
My problem is, that ctags does distinguish between "ab_CD_ef" and "ab_cd_ef" although it's the same variable. 
I tried the "i" flag in my rules, like this one:
```
--regex-vhdl=/^[ \t]*type[ \t]+([^ ]+)[ \t]+is/\1/t,type declarations/i
```Unfortunately ctags doe distinguish in a case sensitive manner. 
Any ideas how to solve this Porblem?

For more info on my file have a look at [http://motzblog.wordpress.com/](http://motzblog.wordpress.com/)

Best regards,
Matthias

---

