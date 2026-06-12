---
title: "OpenGL with Intel X3100 (965) graphics card"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by bertjebusdriver on 2008-07-06
Hi all, I am stuck with a problem and I hope you can help me out.

Basically, I can't use OpenGL at all. The screensavers using OpenGL crash and I can not play games like Neverlands, Spring and Scorched3D. 

My system specs are:

Laptop, Dell Inspiron 1525.
X3100 (965) on-board, shared memory graphics card.

First of all, do you think it will be possible at all to use OpenGL on my configuration?
Secondly, I tried installing the Intel drivers as outlined on:

[http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html)

However (me being quite a newbie), the installing procedure is too difficult. I have no clue how to rebuild the kernel as to include 'AGPGART' and the installation of the other parts also abort. So if you think this might solve my problem, can you please give me a guideline how to do it myself?


Thanks a lot!

Richard

Some (relevant) indications:
- /etc/X11/xorg.conf has a section "device", which looks awfully empty. Throughout some fora I have seen that "intel" or "i860" should be an entry, but by now I did not dare to change it. 
- Compiz runs fine.

---

### Post by kuja on 2008-07-07
With regards to the xorg.conf file, as of the 8.04 release, could very well be left completely blank and everything will still work ... everything is more or less detected on the fly. 

With regards to the OpenGL issue, I would try disabling compiz and see if it worked then.

---

### Post by malanco on 2008-07-07
hi im not an expert here at linux but i had the same problem as you, i didnt have any direct rendering, try this command at the terminal:

glxinfo | grep -i direct


if u get direct rendering: no, just uninstall the xserver-xgl package, because with intel drivers you dont need it.

---

### Post by bertjebusdriver on 2008-07-07
Kuja, Malanco, thanks for your replies. I used your tips, but alas, no avail.

In response:

- Compiz is disabled now.
- This is the output of glxinfo:

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

- xserver-xgl wasn't installed previously (I tried installing and de-installing it to see what happens, but didn't do anything).

So if you think that my Intel drivers are okay, maybe I just should enable 'direct rendering'?

Thanks again,

Richard

---

### Post by kuja on 2008-07-07
Here's a sample /etc/X11/xorg.conf you might be able to look off of ... I've also got an X3100. I can't say that it'd work without question for you, but I can say maybe you'd be able to glean something useful from it.

[http://ubuntu.pastebin.us/?show=dc5f383a](http://ubuntu.pastebin.us/?show=dc5f383a)

---

### Post by bertjebusdriver on 2008-07-08
I was checking out a utility called 'compiz-check' 

[http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

which returned the following information:

```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

```

However, my xorg.conf "Device" section looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver      "intel"
EndSection
```

Any suggestions on how to load the intel driver?

Thanks again,

Richard

---

### Post by glenn69 on 2008-07-23
Any luck getting the intel driver to load.  I have the same problem.  X auto detects and uses the vesa driver for my Intel GM965 card.

I've had no luck changing it in xorg.conf to "intel"

---

### Post by herrBua on 2009-01-21
I have the same graphics card and I don't really know how, but my Ubuntu is using the Intel drivers :S

I did nothing to change it, it was like that out-of-the-box. However I am running 8.10 so it was probably fixed when changing versions :S

This is what compiz-check returned:

> 
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y


and this is my xorg.conf
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

I hope this can be of some help ^^

---

### Post by blackened on 2009-01-21
This should get you going hopefully:

```
sudo apt-get install xserver-xorg-video-intel
```

Optionally, edit xorg.conf, and add this (fbdev = x will use kernel framebuffer device interface) to the "Device" section:

```
	Option		"UseFBDev"		"true"
```

Restart X.

---

### Post by igknighted on 2009-01-21
guys, look at the date of the posts in this thread...

---

### Post by blackened on 2009-01-21
Bah, you expect us to do something so logical? What are we, robots?

No really, I'm sheepish now.

---

