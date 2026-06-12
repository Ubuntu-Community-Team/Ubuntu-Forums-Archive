---
title: "Blacklisted PCIID '8086:2562' found - Error I get with Compiz"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-10-29
When I try to enable compiz it falls back to metacity!

compiz --replace:

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity
``` 

lspci output:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Any ideas why I have this blacklisted "PCIID '8086:2562'" now?

Any ideas on how I can sort this?

I am using Intrepid.

Thanks in advance!!

---

### Post by Tom--d on 2008-10-29
Look here, [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by pluckypigeon on 2008-10-29
> **Tom--d said:**
> Look here, [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Thanks for the thread link

I dodged the blacklist and obviously it didn't work.

It's a shame because it used to work so well :(

---

### Post by pluckypigeon on 2008-11-12
Anyone know of anything new to help solve this problem?? :(

Thanks in advance!

---

### Post by pluckypigeon on 2008-11-13
No one?

---

### Post by pluckypigeon on 2008-11-18
I'm still suffering with this problem.:(

---

### Post by pluckypigeon on 2008-12-08
Anyone know anything now?

---

### Post by pluckypigeon on 2008-12-12
HELP!:confused:

---

### Post by Ikar¡ on 2009-03-11
I'm stuck on the same here. And after several hours on google, did not get solution at all. Skipping the black list only freezes Ubuntu's desktop.

Damn.

---

### Post by pluckypigeon on 2009-03-11
> **Ikar¡ said:**
> I'm stuck on the same here. And after several hours on google, did not get solution at all. Skipping the black list only freezes Ubuntu's desktop.

Damn.

I went back to 8.04LTS. The intel 845g doesn't work with newer Linux anymore.

---

### Post by eap1935 on 2009-04-24
I have this annoying problem too. A workaround is to install the Compiz Fusion Icon. Launch it and the icon will appear in the task bar. Right click the icon and select Compiz as the Window Manager and Compiz will load properly. I have yet to find a way to get Compiz to load properly on boot, though.

Edit:

Ah, sorry, the fix at [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875) solves my problem. Also, my video card (listed in lshw) is Mobile GM965/GL960 Integrated Graphics Controller.

---

### Post by crjackson on 2009-04-24
> **pluckypigeon said:**
> When I try to enable compiz it falls back to metacity!

compiz --replace:

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity
``` 

lspci output:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Any ideas why I have this blacklisted "PCIID '8086:2562'" now?

Any ideas on how I can sort this?

I am using Intrepid.

Thanks in advance!!

Check this thread [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Psquared on 2009-05-23
This is baloney and the same reason I left openSUSE. 

It is ignorance or laziness (or both) by programmers. They fix one thing and break something else even more crucial. (and NO I can't do any better because it is not MY job. But if I did cr@ppy work like this at my job I'd be collecting unemployment.)

Point is, on my fresh install with Jaunty I could enable effects with no problem whatsoever using the Intel 9xx video card on my laptop. The ONLY thing I installed after that which could possibly have anything to do with video is Skype, flash and Sun Java.

Effects can be enabled with Jaunty, but stick with JDK and don't use Sun's version. I am not sure what the trade off might be, but either that or flash caused the problem. Stick with the primary repos .... I don't care what you read about getting something or other to work.

I am going to do a reinstall of Jaunty and NOT use Sun's Java, despite advice left here to do just that.

Canonical .... if you are listening, you and openSUSE are going to get left behind if you don't fix this stuff and start putting out updates that actually update and don't break a working installation.

---

### Post by glenn69 on 2011-03-03
Removing the hardcoded blacklist from within compiz works...until you update compiz.  Here's a link to that solution

[http://ubuntuforums.org/showthread.php?t=1467202](http://ubuntuforums.org/showthread.php?t=1467202)

---

