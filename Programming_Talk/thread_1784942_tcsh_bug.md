---
title: "tcsh bug?"
date: 2011-06-17
forum: Programming Talk
---

### Post by sadams6696 on 2011-06-17
Hi folks,
Is this a bug in tcsh ?
-----
foreach i (01 02 03 04 05 06 07 08 09)
if ($i < 10) set i = "0"$i
echo $i
end
-----

I get 001 through 007 printed out, but for 08 and 09:
if: Badly formed number.
It works if I take the leading "0" off 8 and 9, but not with "08" and "09".

Here's my info:
cruncher2:~> /usr/bin/tcsh --version
tcsh 6.17.00 (Astron) 2009-07-10 (i486-intel-linux) options wide,nls,dl,al,kan,rh,nd,color,filec
cruncher2:~> uname -a
Linux cruncher2 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux

Any help would be greatly appreciated!

---

### Post by squaregoldfish on 2011-06-17
This isn't a bug. tcsh interprets any number starting with 0 as an octal (base 8 ) number. It therefore gets confused by 08 and 09, since they're not valid octal numbers.

To make tcsh behave 'normally', you should always strip off leading zeroes.

HTH,
Steve.

---

### Post by sadams6696 on 2011-06-20
> **squaregoldfish said:**
> This isn't a bug. tcsh interprets any number starting with 0 as an octal (base 8 ) number. It therefore gets confused by 08 and 09, since they're not valid octal numbers.

To make tcsh behave 'normally', you should always strip off leading zeroes.

HTH,
Steve.

-----

Thanks squaregoldfish. It's interesting that this wasn't an issue in tcsh up to at least version 6.14.00  . Looks like a bunch of script editing is in my future! Thanks again!

Steve

---

