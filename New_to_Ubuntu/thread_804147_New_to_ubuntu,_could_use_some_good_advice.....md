---
title: "New to ubuntu, could use some good advice...."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by EK228 on 2008-05-22
Afternoon ladies and gents,

I am in the middle of a quarter of college and was lucky enough to take a intro to Linux course.  The course uses Fedora, but after 4 failed installs I looked around and thought that ubuntu would be a better fit.  And I love it, every single part, the control is amazing.  But...

I have ran into a couple of problems, perhaps some of you kind folks could help me out, here they are:

1. I have a USB keyboard, and my system is set to dual boot.  Windows XP Pro runs on my master IDE drive, and Ubuntu 8.04 runs on my slave.  Now I installed Grub and selected Ubuntu as my default, and it loads just fine, except if I want Windows.  You see my keyboard is alive during the intial boot, so I can access CMOS setup and such, but then goes dead during the GRUB boot so I can not select Windows XP.  Once Ubuntu loads the keyboard comes back to live and works just fine.  Is there a patch or perhaps a setting I need to change?  Not that I miss XP all that much but it would be nice to have the option since its there....

2.  I took a look in the help files and they talk about a device manager, I can not seem to find one anywhere under any menu, do I need a patch or an add on to get this ability?

---

### Post by spiderbatdad on 2008-05-22
Sometimes you can set leagcay support or usb legacy support in the BIOS.
Possibly plugging into a usb port as opposed to a hub.
Those are the only two solutions offered in response to numerous bug reports against the kernel...that I found.

---

### Post by camccall on 2008-05-22
My guess is that you need to enable Legacy USB Support in your Bios.

---

### Post by ardvark71 on 2008-05-22
> **EK228 said:**
> Afternoon ladies and gents,


You must mean "ladies and germs." :-P

> **EK228 said:**
> But...

Always the "but," this thing is supposed to work out the box! What's wrong with these programmers anyway??                       :lolflag:

Seriously though...

1. If the legacy USB setting in the motherboard doesn't work or if it doesn't have one, if your motherboard has a PS/2 port, you could just buy a USB to PS/2 adapter for your keyboard and that should do the trick.

2. The "Device Manager" is under "System" and "Administration," if I remember correctly, on the tool bar on the top of the screen. Let me know if I'm wrong. :---)

Best Regards...

---

### Post by EK228 on 2008-05-22
> **ardvark71 said:**
> 
2. The "Device Manager" is under "System" and "Administration," if I remember correctly, on the tool bar on the top of the screen. Let me know if I'm wrong. :---)

Yes that is what where the help file directs me also, but it simply is not there, how can I add it?  I can connect to the internet so I can add stuff if that will help....

---

### Post by EK228 on 2008-05-22
> **camccall said:**
> My guess is that you need to enable Legacy USB Support in your Bios.

Yes I took a look and it would appear my system does not support that and doesn't offer the choice.  I guess I will try to get the adapter plug.  Thanks.

---

### Post by stalkier on 2008-05-23
> **EK228 said:**
> Afternoon ladies and gents,

I am in the middle of a quarter of college and was lucky enough to take a intro to Linux course.  The course uses Fedora, but after 4 failed installs I looked around and thought that ubuntu would be a better fit.  And I love it, every single part, the control is amazing.  But...

I have ran into a couple of problems, perhaps some of you kind folks could help me out, here they are:

1. I have a USB keyboard, and my system is set to dual boot.  Windows XP Pro runs on my master IDE drive, and Ubuntu 8.04 runs on my slave.  Now I installed Grub and selected Ubuntu as my default, and it loads just fine, except if I want Windows.  You see my keyboard is alive during the intial boot, so I can access CMOS setup and such, but then goes dead during the GRUB boot so I can not select Windows XP.  Once Ubuntu loads the keyboard comes back to live and works just fine.  Is there a patch or perhaps a setting I need to change?  Not that I miss XP all that much but it would be nice to have the option since its there....

2.  I took a look in the help files and they talk about a device manager, I can not seem to find one anywhere under any menu, do I need a patch or an add on to get this ability?

I had the same prob bud.I had to use a USB to PS2 adapter. (Had it laying around)

---

### Post by ardvark71 on 2008-05-23
> **EK228 said:**
> Yes that is what where the help file directs me also, but it simply is not there, how can I add it?  I can connect to the internet so I can add stuff if that will help....

That's weird. :confused:

I wouldn't think it would be under a different name. 

This program is installed automatically as part of the base OS so I wouldn't know how to otherwise obtain it.

You could try combing through the packages in the repositories under Synaptic (just make to enable all the repository types,) and see if you are able to find something similar. Probably under "Utilities."

Let us know how it goes....if I find something, I'll post back.

Best Regards...

---

### Post by spiderbatdad on 2008-05-23
> **ardvark71 said:**
> That's weird. :confused:

I wouldn't think it would be under a different name. 

This program is installed automatically as part of the base OS so I wouldn't know how to otherwise obtain it.

You could try combing through the packages in the repositories under Synaptic (just make to enable all the repository types,) and see if you are able to find something similar. Probably under "Utilities."

Let us know how it goes....if I find something, I'll post back.

Best Regards...

In 8.04 it appears to have been replaced with System>>Administration>>Authorizations. Weird name.

---

### Post by ardvark71 on 2008-05-23
Hi SpiderBatDad...

Thank you for the heads up!

---

### Post by EK228 on 2008-05-23
> **ardvark71 said:**
> That's weird. :confused:

I wouldn't think it would be under a different name. 

This program is installed automatically as part of the base OS so I wouldn't know how to otherwise obtain it.

You could try combing through the packages in the repositories under Synaptic (just make to enable all the repository types,) and see if you are able to find something similar. Probably under "Utilities."

Let us know how it goes....if I find something, I'll post back.

Best Regards...


Yes I took a look at utilities, and updated my system, but still nothing.  So let me understand something here, everyone else using this OS has a device manager, and I don't?  I downloaded the OS from this website ubuntu 8.04 lts, so I know it is up to date and correct...  What could have gone wrong?

Also after looking around there is alot to take in, any pointers you can offer?  Could utility programs or advise to get me off in the right direction?  heh I have a feeling i will be up all night playing with this new toy, its freaking awesome.:guitar:

---

### Post by EK228 on 2008-05-23
Ha I was just not looking in the right place, i did find the legacy keyboard support, thanks guys !!

---

### Post by EK228 on 2008-05-31
Hmmm I took a look at authorizations and thats not what I was looking for, it simply lets me control authorizations, lol.  Still no device manager, perhaps it has been removed and replaced by something, kind of like how root is hidden but sudo works for most things?

---

### Post by sports fan Matt on 2008-06-01
The advice I ccan give is not specific..but when things go wrong, like you have, just dont get overally upset.

A.  Most things can be fixed easily.  Dont give up!
B.  We are a great group here and can and will help.  
C.  Linux isnt Windows-its just different.  Overall, its a new experience but a fun and enjoyable one..Have Fun!

---

### Post by khernandezpardo on 2008-06-01
Hi EK228, don't feel lonly, I've installed three times (due to major errors of mine manipulating partitions in Vista) ubuntu this week, none of those times (including now) I've been able to find the hal device manager... and "Authorizations" isn't the same at all. If I find a solution, I'll post it.

---

### Post by ad_267 on 2008-06-01
It appears that the device manager doesn't come with 8.04 by default. You can install it with the gnome-device-manager package.

---

### Post by tact on 2008-06-01
> **EK228 said:**
> Hmmm I took a look at authorizations and thats not what I was looking for, it simply lets me control authorizations, lol.  Still no device manager, perhaps it has been removed and replaced by something, kind of like how root is hidden but sudo works for most things?
Yep the hardware manager application that previous versions of ubuntu had is not included in 8.04  -   so don't be worried when people tell you its under System>Admin or System>Prefs etc...you don't have an x-files version.

What hardware info are you actually looking for?  It won't help get your cmos to recognise a keyboard at boot.  

If you really need it back install gnome-device-manager
(You will find it in synaptic and can install via gui..  or install from CLI with sudo apt-get install gnome-device-manager)

---

### Post by khuston on 2008-06-05
Has anyone figured out how to get to a hardware/device manager in 8.04 edition yet?  I installed the gnome device manager.  It lets me view the hardware installed, but there seems to be no way to disable hardware.

---

