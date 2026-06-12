---
title: "Convert decimal to little-endian hex with bash commands?"
date: 2008-12-15
forum: Programming Talk
---

### Post by jasper.davidson on 2008-12-15
Does anyone know of an easy way to convert a decimal value to a little-endian hex value? I found at least a few ways of converting decimal to hex (big-endian):
```
echo "10 i 16 o [COLOR="Blue"]<decimal number>[/COLOR] p" | dc
echo "ibase=10; obase=16; [COLOR="Blue"]<decimal number>[/COLOR]" | bc

```
So if I convert say "9698547", I get "93FCF3", but I would like it to be in little-endian format or "F3FC93". Is there possibly an easy way to do this without making a bash script to swap the bytes around manually? Or is there maybe a single awk/sed command that would swap the bytes around? Thanks in advance for any help.

---

