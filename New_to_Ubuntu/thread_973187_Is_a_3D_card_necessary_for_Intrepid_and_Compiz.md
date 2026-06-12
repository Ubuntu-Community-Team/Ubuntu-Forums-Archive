---
title: "Is a 3D card necessary for Intrepid and Compiz?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by yogo on 2008-11-06
I have been reading all over and can not find out how to enable Compiz.

I have had Compiz working on my Desktop from Feisty to Gutsy to Hardy but can not be enabled in Intrepid.

I have run the Compiz check script and everything is OK, what I have is** [Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)] **for graphics, I have had desktop effects work nicely until Intrepid.

Here is output from compiz script
Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Will I be able to get desktop effects back on my system without a 3D card?

Thanks for any ideas.

---

### Post by gn2 on 2008-11-06
There's a bit in the [release notes]("http://www.ubuntu.net/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards") about it:

---

### Post by yogo on 2008-11-06
Thank gn2,

From reading your link I assume there is no way to get it working on my Desktop since it suggests to disable desktop effects.

Is there any type of work around?, there should be as they worked great on Ubuntu before Intrepid.

TIA

---

### Post by gn2 on 2008-11-06
I don't know if there's a fix yet. 
If you want the effects, for now it looks like it's back to 8.04.1 :(

Maybe someone in the [Desktop Effects]("http://ubuntuforums.org/forumdisplay.php?f=330") forum might know.

---

### Post by yogo on 2008-11-06
> **gn2 said:**
> 

Maybe someone in the [Desktop Effects]("http://ubuntuforums.org/forumdisplay.php?f=330") forum might know.

I posted in there about a week ago, still have no response, that is why I posted here, maybe I need to start a new thread there as I only posted in existing threads. Seem like you get answers much quicker in the newbie forum.

Thanks

---

### Post by philinux on 2008-11-06
There was an update came through today that blacklisted both those [http://www.ubuntu.net/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20](http://www.ubuntu.net/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20) cards in compiz. Seems like your best bet is get a graphics card. Nvidia probably.

---

### Post by yogo on 2008-11-06
Great I am just updating at the moment, hope the blacklisting helps, I am not going to get a graphics card for the Desktop, I would get an all new desktop so maybe blacklisting is my best bet for now.

How do I blacklist the onboard graphics if the update does not?

TIA

---

### Post by yogo on 2008-11-06
Just updated, did not solve anything.

I tried using the sticky from Desktop effects forum Blacklisted for dodging it at your own Peril, must admit this is  over my head but  the sticky did not work for me,

I had to do sudo apt-get remove compiz and sudo apt-get remove compiz-core to get my desktop back.

Any ideas other than ditch the desktop or rollback to 8.04?

---

