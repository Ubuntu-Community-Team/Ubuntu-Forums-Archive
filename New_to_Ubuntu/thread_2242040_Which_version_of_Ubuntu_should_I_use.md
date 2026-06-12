---
title: "Which version of Ubuntu should I use?"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by Ben_Cook on 2014-08-30
Good morning everyone!  I'm looking for some advice on which version of Ubuntu to use on my old desktop.  I just had it given to me and it is currently running Windows XP.  Here is the basic specs :   Intel core 2 Duo, E6550 @ 2.33Ghz, 1.96 GB RAM.  So, I'm just wondering what would be the best OS to use in terms of both speed and features.  I have an old netbook that runs lubuntu quite well, and I like but I also like the newer, shinier OSes.  Just looking for opinions/advice before I get one.  Also, is dual booting a bad idea with this old of a machine?  Thanks!

---

### Post by Rob Sayer on 2014-08-30
I don't think that cpu has a built in gma.  What graphics card do you have?

You could run Unity on it with 2Gb if it was basically a gaming machine in its day ... ie. a serious video card ... *and* if that card is still supported in Linux.  You may not get 3D hardware acceleration for example.  And DEs like Unity need 3D accel just to run *themselves*, let alone other apps.

On a 2Gb Windows XP box I'd probably install Xubuntu.  I used LXDE for a while but Lubuntu 14.04 was such a clunky bug fest that, frankly, I'll never install it again.  I may install LXQt when it's out of beta though.  But Xubuntu is pretty good now.

I can't say which DE is best in terms of speed and features.  I don't think Unity is really that great in either.  KDE is the most powerful DE I've used, and you can really config it for speed, which you can't do with Unity.  That's what I use on my 4Gb i3 laptop.

My advice would actually be to just download all the live CD isos and boot them and try them yourself.

Dual booting isn't a "bad idea".  It has disadvantages, but if you need to do a BIOS update it's much easier to do that in windows.  I want at least one Windows partition because there are some tools you can't get in linux.  Not many but a few.  If you have a box with a newer version I'd keep that.  XP is unsupported,  so if you do keep it, *never* connect to the internet with it again.

---

### Post by ibjsb4 on 2014-08-30
> You could run Unity on it with 2Gb if it was basically a gaming machine in its day ... ie. a serious video card ... *and*  if that card is still supported in Linux.  You may not get 3D hardware  acceleration for example.  And DEs like Unity need 3D accel just to run *themselves*, let alone other apps.

If unity desktop does not work for you, the flashback desktop could be installed to this.  It can use a different window manager (metacity) and is less resource demanding.

---

### Post by fidelis2 on 2014-08-30
> **Rob Sayer said:**
> On a 2Gb Windows XP box I'd probably install Xubuntu.  I used LXDE for a while but Lubuntu 14.04 was such a clunky bug fest that, frankly, I'll never install it again.  I may install LXQt when it's out of beta though.  But Xubuntu is pretty good now.
Yes, indeed; a few months ago on my old 2 GByte RAM DELL Vostro with Intel dual core CPU, I replaced WinXP 32bit with Xubuntu 14.04 64bit, and now the very same PC provides a user experience at least as twice as fast as with WinXP. (User experience, not CPU power, but all harddrive accesses are clearly much faster, as is the usage of the two CPU cores.)
Also all this Vostro's users who were used to WinXP, like the new XFCE desktop which behaves in a similar way, in contrast to Ubuntu's Unity or Win8 or whatever. So minimal learning curve in our case.

It's so great to see old PCs to fly again -- with a proper OS like Ubuntu is, and the point here is that the slim and efficient XFCE desktop doesn't need as many resources as the Ubuntu desktop Unity, so is ideal for older PCs.

Oh, by the way, this old Vostro of mine has a mobile ATI graphics cards which wasn't supported anymore by ATI for years, so newer Windows software which needed up-to-date OpenGL drivers, didn't run anymore. Not so on X-/Ubuntu: the graphics card is fully supported now and suddenfly new software which didn't run on WinXP, does run on very the same hardware, like Blender, Java8, and so on.
That's some surprise!

I can clearly recommend to the original poster to try [Xubuntu]("http://www.ubuntu.com/about/about-ubuntu/derivatives"). Since it's an official Ubuntu derivate, you're in the Ubuntu community pool and basically have an Ubuntu installation just with a slimmer and more conventional desktop.


P.S. Personally I know XFCE for several years now and really like it. Xubuntu 14.04 runs very smooth. Many problems known from 13.x and 12.x are gone by now.

---

### Post by craig10x on 2014-08-30
I would do as previously suggested and download first ubuntu (with unity) and run it in live session to see if your hardware responds well to it...if not, then you could try xubuntu.

Or install the flashback session on ubuntu which will use less resources then unity...of course, to do that you would actually need to install ubuntu...

---

### Post by grahammechanical on 2014-08-30
How much memory of its own does the graphic adapter have? I have an Intel Core2 Duo 2.40GHz + 1GB RAM and it is running Ubuntu 14.04 with Unity very well. It also has an Nvida GT 220 with 1 GB of its own memory and I think that the size of the video memory and the capabilities of the video GPU make all the difference.

When you run the live session, open the terminal and run this command

```
 /usr/lib/nux/unity_support_test -p
```

You need to see something like this

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.6


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes



That is what I see on my machine. In fact my system runs Ubuntu and all the flavours very well. And then there is this

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

Regards.

---

### Post by Ben_Cook on 2014-08-30
Thanks for the responses everyone.  I've decided to go with Xubuntu.  But I've encountered a problem.  I had this machine given to me by friends who had it given to them.  Anyway, I can't save the bios settings.  It asks me for Bios password, and if I try to type in a random password it says incorrect.  But, if I press enter it takes me into the Bios where saving is completely disabled.  I've tried pressing F12 to just do boot order, but the only thing that shows up is the HDD.  Is there any way around this?  I am installing from a USB stick, which is good to go.

---

### Post by ThatBum on 2014-08-30
Try removing the CMOS battery on the motherboard, or locate a password jumper.

---

### Post by Ben_Cook on 2014-08-30
Ah...ok. Well this opening up a computer is new to me, but it is what I wanted to do anyway.  I read about the password jumper before, but it seems as though the battery might be easier to remove.  Thanks!

---

### Post by ibjsb4 on 2014-08-30
Bios passwords

[http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/](http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/)

---

### Post by Ben_Cook on 2014-08-30
Thank you...I removed the battery for a little bit and that did it.  I didn't see your reply until just now ibjsb4.  Unfortunately, when I opened up my computer I must have done something because my fan won't stop running.  It is on a very cold floor and it has been running constantly and it is very very loud.  Bt, I suppose that is a question for a different category.  Again, thanks for your help

---

