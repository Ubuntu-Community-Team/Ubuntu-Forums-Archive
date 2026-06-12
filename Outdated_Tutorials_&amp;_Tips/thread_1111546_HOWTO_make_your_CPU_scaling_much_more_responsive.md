---
title: "HOWTO: make your CPU scaling *much* more responsive"
date: 2009-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by graysky on 2009-03-30
If I'm not mistaken, Intrepid comes pre-configured with powernowd which dynamically controls your CPU scaling based on your actual CPU load.  CPU scaling = throttling or speedsteping of your processor.  Most modern processors have this native as a power-savings/heat reduction feature.

The defaults for powernowd are low multiplier when CPU load is <=20 % and high multiplier when CPU load >=80 %.  I don't like these settings because there are times when an application uses my CPU but the load doesn't hit 20 % (tar for example) and therefore my CPU multiplier is only 6x when it could be 8.5x.

Changing these 20/80 options is trivial.  Simply edit your /etc/defaults/powernowd to select a more responsive range.  I'm using 10/20 on my system.  In other words, low multiplier when load is <=10 % and high multiplier when load is >=20 %.

Physically, edit your /etc/defaults/powernowd:
```
OPTIONS="-q -u 20 -l 10"
```

If 20/10 isn't to your liking, use whatever you want.  A more agressive setting might be "-q -u 10 -l 5" for example.  As you can infer, the -u defines the upper range (i.e. when load hits this value, full power) and -l defines the lower range (i.e. when load drops to this value, drop the multiplier).

Enjoy!

---

