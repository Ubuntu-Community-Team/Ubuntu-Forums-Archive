---
title: "Incompatibility between Text::Iconv and Dynaloader"
date: 2009-07-17
forum: Programming Talk
---

### Post by bondinho on 2009-07-17
Hi,

I recently set up an ubuntu 9.04 server and I uploaded on it a perl script which perfectly worked on Hardy and Intrepid. But on the new server, when I run it, I get the following message error:

Text::Iconv object version 1.7 does not match bootstrap parameter 1.4 at /usr/lib/perl/5.10/DynaLoader.pm line 219.
Compilation failed in require at perl.pl line 9.

Here is what I have at line 9 of the script:
```
use Text::Iconv;

```May anyone help me please?

---

