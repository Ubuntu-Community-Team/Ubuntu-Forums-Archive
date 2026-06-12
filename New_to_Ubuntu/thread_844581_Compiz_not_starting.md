---
title: "Compiz not starting"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by pteri498 on 2008-06-29
I have an ATI IGP 340M graphics chip in a relatively old laptop.

I just updated it to 8.04. However, the special graphics effects (compiz) won't work. The setting in System > Preferences > Appearances > Visual Effects reverts to None with an error of "Desktop effects could not be enabled"

I had these effects working in previous versions of Ubuntu.

When I run compiz, I get the following output:

```

$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

$ lspci | grep ATI
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

I'm at a loss of what to do. Any ideas?

Thanks.

---

### Post by sayakb on 2008-06-29
At a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by pteri498 on 2008-06-29
Hmm nope, same problem. Do I need to install XGL or something?

---

### Post by philinux on 2008-06-29
Have a look in,

System>Admin>Hardware Drivers

---

### Post by pteri498 on 2008-06-29
Good thought.

No proprietary drivers are in use. I have a vague memory of my video driver being listed as a proprietary driver.

Am I missing this?

---

### Post by starcannon on 2008-06-29
try this:

```
sudo apt-get install fusion-icon
```

then run it like this

```
fusion-icon -f
```

this is how I did it on an old inspiron 5100 with an aging ati card in it, default install no proprietary drivers.

Let us know how you get on.

GL

---

### Post by pteri498 on 2008-06-29
I got it!

I found this page: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

I downloaded it and ran it, and it told me exactly why my card wasn't working: compiz was blacklisting it. The program then removed the blacklist, and it ran beautifully.

Thanks, everyone.

```

$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) Y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) y

```

---

