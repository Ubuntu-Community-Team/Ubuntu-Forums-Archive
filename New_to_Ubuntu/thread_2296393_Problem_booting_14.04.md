---
title: "Problem booting 14.04"
date: 2015-09-25
forum: New to Ubuntu
---

### Post by Stroman on 2015-09-25
Installed Ubuntu 14.04 from disk (ISO DVD) onto new SSD, MSI AM1l MOBO with AMD 5350 Kabrini APU. Install went okay. Added updates. After updates added system would start to load then go to black screen. After forced restart using "tab" key could get into Ubuntu options menu. Selecting "safe mode" and choosing "resume" option system would load and run okay. Shutdown is normal. Also used "repair broken packages" and ran memory check. Has made no difference. I also installed this onto another computer with MSI MOBO using IBM hard drive. Behaves exactly the same way. Any help with this issue would be greatly appreciated. I am limited in my knowledge level about Ubuntu but have run versions 9.04 and 12.04 without too many problems. Thank You,
Stroman

---

### Post by Bashing-om on 2015-09-25
Stroman; Hi !

Graphic's driver ? Is this box running Nvidia or ATI OR Optimus for the graphics ?

Maybe take a look in 'Additional Drivers'  and see what options are offered .

If Optimus technology ( hybrid graphics ) may have to manually install the driver.

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Stroman on 2015-09-25
Thanks Bashing-Om,
Video is on chip with the Kabrini 5350. Probably an AMD driver but not sure.
Stroman

---

### Post by Bashing-om on 2015-09-25
Stromanl Well;

Then, let's find out what for sure we are working with,
Post back - Between Code Tags - the outputs of terminal commands:
```

lspci | grep "VGA\|3D"
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And try and match a driver to the hardware.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

