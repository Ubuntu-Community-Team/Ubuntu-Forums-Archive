---
title: "Cold storage Bitcoin wallet"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by Big_Ted on 2014-08-16
Really new to Linux. I just bought a desktop loaded with Lubuntu, but I need Ubuntu so I can do a cold storage bitcoin wallet. How do I overwrite or remove Lubuntu?

Any help would be tremendous.

---

### Post by Bashing-om on 2014-08-16
Big_Ted; Hello:

IF ubuntu is to be the sole operating system at the intitial install stage ... don't worry about removing the old lubuntu. In the installer of ubuntu choose "erase disk and install ubuntu" and it will do just that .. erase the disk and install.
Now, I would question why Lubuntu is installed onto that machine .. maybe 'cause it is older hardware and Lubuntu is designed to run on that older hardware .
Verify that the machine has the horse power to support ubuntu.

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by yancek on 2014-08-16
Boot from the Ubuntu installation medium (DVD/flash drive) and install to the same partition on which you have Lubuntu and select to format that partition during the install.  Impossible to give more details as you haven't posted any details about your system and what else might be on it.  The tutorial below explains installing Ubuntu 14.04:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

It also contains a lot of useful information on partitioning.

---

### Post by Big_Ted on 2014-08-16
[TABLE]
[TR]
[TD="class: attrLabels"]Brand: [/TD]
[TD="width: 50%"][h=2]Dell[/h][/TD]
[TD="class: attrLabels"]									 			Processor Speed: [/TD]
[TD="width: 50%"][h=3]2.50 GHz[/h][/TD]
[/TR]
[TR]
[TD="class: attrLabels"]									 			Product Line: [/TD]
[TD="width: 50%"][h=3]Optiplex[/h][/TD]
[TD="class: attrLabels"]									 			Graphics Processing Type: [/TD]
[TD="width: 50%"][h=3]Integrated/On-Board Graphics[/h][/TD]
[/TR]
[TR]
[TD="class: attrLabels"]									 			Model: [/TD]
[TD="width: 50%"][h=2]170L[/h][/TD]
[TD="class: attrLabels"]									 			Memory: [/TD]
[TD="width: 50%"][h=3]2 GB[/h][/TD]
[/TR]
[TR]
[TD="class: attrLabels"]									 			Operating System: [/TD]
[TD="width: 50%"][h=3]Linux[/h][/TD]
[TD="class: attrLabels"]									 			Hard Drive Capacity: [/TD]
[TD="width: 50%"][h=3]40 GB[/h][/TD]
[/TR]
[TR]
[TD="class: attrLabels"]									 			Screen Size: [/TD]
[TD="width: 50%"][h=3]None[/h][/TD]
[TD="class: attrLabels"]									 			Operating System Edition: [/TD]
[TD="width: 50%"][h=3]Lubuntu 14.04 LTS (32-bit)[/h][/TD]
[/TR]
[TR]
[TD="class: attrLabels"]									 			Processor Type: [/TD]
[TD="width: 50%"][h=3]Intel Celeron D[/h][/TD]
[TD="class: attrLabels"]									 			Bundled Items: [/TD]
[TD="width: 50%"][h=3]Keyboard, Mouse[/h]



[/TD]
[/TR]
[/TABLE]

---

### Post by Big_Ted on 2014-08-16
Those are the specs ....

I don't need speed. I just need to accomplish cold storage.

Thanks for your responses.

---

### Post by Sanctimonious_Ape on 2014-08-17
Are you sure your bitcoin program won't run under Lubuntu?  It's my understanding that all the distros have the same basic underpinnings, just with more or less ornate paint jobs.  I'd give it a try first before going through the reinstallation hassle.  Another thing you could do would be to go into the Lubuntu Software Center program and install the "ubuntu-desktop" package - that should install everything the normal Ubuntu disto proper has (in theory).  You'll need to log out and switch environments at the login screen before logging in again if you want to see the new desktop, but that shouldn't be necessary just to run a program.

---

### Post by mörgæs on 2014-08-17
A 170 is too weak for Ubuntu. You chose right by giving it Lubuntu.

Which application are you trying to run to store bitcoins?

---

### Post by stalkingwolf on 2014-08-17
make sure your updates are current as well.

---

### Post by grahammechanical on 2014-08-17
Ubuntu uses the Unity user interface and that needs a graphic adapter that can do 3D hardware acceleration . Run this command to see if your graphic adapter can run Unity.

```
/usr/lib/nux/unity_support_test -p
```

This is what I see

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.5


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


You need to see Yes.

What makes you think that you need Ubuntu to run that application?

Regards

---

### Post by Rob Sayer on 2014-08-17
The Celeron D is at least 8 years ago and it was quite slow at the time.  It's a single core CPU.

As mentioned, lubuntu is a good choice.  I frankly wouldn't consider installing ubuntu with Unity on it ever.  Ditto for Cinnamon (Mint) which also needs 3D hardware acceleration just to run *itself*.

If you want to try any other ubuntu DE I'd suggest Xubuntu.  And turn off all visual effects if you install it.

Keep in mind that Lubuntu 14.04 is the first long term support release, so the Lubuntu you have is quite possibly end of life and unsupported.  You'll want to reinstall anyway.

And, as mentioned, it's quite beyond me why you'd need one ubuntu DE version to run that program.  This netbook has xubuntu 14.04 installed but I have a number of programs that come installed on other DEs.

---

### Post by pfeiffep on 2014-08-17
> **Rob Sayer said:**
> The Celeron D is at least 8 years ago and it was quite slow at the time.  It's a single core CPU.

As mentioned, lubuntu is a good choice.  I frankly wouldn't consider installing ubuntu with Unity on it ever.  Ditto for Cinnamon (Mint) which also needs 3D hardware acceleration just to run *itself*.

If you want to try any other ubuntu DE I'd suggest Xubuntu.  And turn off all visual effects if you install it.

Keep in mind that Lubuntu 14.04 is the first long term support release, so the Lubuntu you have is quite possibly end of life and unsupported.  You'll want to reinstall anyway.

And, as mentioned, it's quite beyond me why you'd need one ubuntu DE version to run that program.  This netbook has xubuntu 14.04 installed but I have a number of programs that come installed on other DEs.

I've been running Ubuntu with gnome fall back or flashback on a Celeron Dell Laptop quite successfully!

---

### Post by Big_Ted on 2014-08-17
> **mörgæs said:**
> A 170 is too weak for Ubuntu. You chose right by giving it Lubuntu.

Which application are you trying to run to store bitcoins?

I am using Armory. Maybe I made a mistake buying an old computer with Lubuntu installed. It was only 43 dollars including shipping.

---

### Post by mörgæs on 2014-08-17
A 170 should be almost free, but since you have bought it why not give it a try?

[https://bitcoinarmory.com/download/](https://bitcoinarmory.com/download/)

---

### Post by mörgæs on 2014-08-17
> **pfeiffep said:**
> I've been running Ubuntu with gnome fall back or flashback on a Celeron Dell Laptop quite successfully!

'Celeron' is a vague term meaning simply 'less than a Pentium'. It's a brand which has been in use for many years and it does not say anything detailed about the processor. A recent Celeron can be quite powerful.

Well, back on topic which is Bitcoin.

---

### Post by 3rdalbum on 2014-08-18
Any program that runs on Ubuntu will also run on Lubuntu. Stick with Lubuntu if you want.

I'm just curious why you didn't use a paper wallet for cold storage?

---

