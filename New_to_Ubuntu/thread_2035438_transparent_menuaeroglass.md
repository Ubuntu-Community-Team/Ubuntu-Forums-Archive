---
title: "transparent menu/aeroglass"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by fractalman on 2012-07-30
I have just installed natty 11:04 on a fujitsu siemens v5535 laptop.  i have been trying to get compiz to make the menus transparent but it doesn't seem to be doing anything, i have tried the following guides

[http://jechem.blogspot.co.uk/2010/11/making-panels-tabs-and-menus.html](http://jechem.blogspot.co.uk/2010/11/making-panels-tabs-and-menus.html)

[http://askubuntu.com/questions/136193/how-can-i-get-transparent-right-click-menus-back-in-ubuntu-12-04](http://askubuntu.com/questions/136193/how-can-i-get-transparent-right-click-menus-back-in-ubuntu-12-04)

i am also trying to get the aeroglass effect where the top of the windows are transparent but it's not working as it should, i have followed this guide (#3) and several others but nothing is working


#3
[http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/](http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/)



i have already managed to get it to work on my pc but i want it on my laptop, i'm guessing it might be a graphics card problem or something , any ideas?

post any code you need and ill pop it up for you

thanks

---

### Post by fractalman on 2012-07-31
after some googling i have come across this command to test my system, it said on the webpage that all yes means compiz will work but i have a couple of no's,  is there any way i can change them to yes?


```

phi@BLACK47A:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no



```

would a different graphics driver make any difference at all?

---

### Post by Perfect Storm on 2012-07-31
It would be nice if you posted your computer specs as well. More importantly your videocard.

---

### Post by fractalman on 2012-07-31
Fujitsu siemens v5535 laptop


746mb ram(to be increased soon)
intel celeron cpu 550@2.00ghz
i'm running ubuntu 11:04 natty in classic mode

i ran lspci and for vga i have

```

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


```and then i ran 

lspci -v -s 01:11.0


```

phi@BLACK47A:~$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) (prog-if 00 [VGA controller])
    Subsystem: Fujitsu Technology Solutions Device 1125
    Flags: 66MHz, medium devsel, IRQ 9
    BIST result: 00
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d4000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at 9000 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>


```is it possible to increase my vga ram? 256m doesn't seem like a great deal

is that enough info?  i'm not sure what else you might need so just post any commands and i'll post the ouput 

cheers

---

### Post by Frogs Hair on 2012-07-31
You could purchase a new video card with more memory and have it installed. With a desktop this is a relatively easy job , but a laptop is tricky . The card has to be system compatible and fit in the space alloted by the chassis/case and it my be expensive. You would have to do some research to find out if it's worth the cost.

---

### Post by fractalman on 2012-08-12
Thanks for the replies, doesn't look like I'm going to be able to upgrade the graphics so stuck with it, no biggy!

---

