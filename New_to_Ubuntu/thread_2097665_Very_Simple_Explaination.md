---
title: "Very Simple Explaination"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Publisher on 2012-12-24
Please explain in VERY SIMPLE terms how to install graphics drivers. Please understand I cant even find the System> Admin> Hardware link I have read about. So when I say simple explanation that is what I mean.

Thank you for understanding.

---

### Post by Bucky Ball on 2012-12-24
Welcome to the forums. What release of Ubuntu are you using? (12.04 LTS, 12.10?) Is it Ubuntu and not another flavour; Xubuntu, Kubuntu?

If you are using a newer release it is 'Additional Hardware', not just 'hardware'.

Have you done an update? You may not need the third-party driver (there is already an open-source one installed for it) or there may not be one at all. What problem are you having, exactly?

---

### Post by Publisher on 2012-12-24
Hi, I am using Ubuntu 12.10 I have updateted (as far as I know). The problem is that everything moves at snail pace, ie opening firefox or thunderbird everthing really. Hope that helps.

---

### Post by fdrake on 2012-12-24
you graphic drive os not handling gnome 3 very well maybe.

1. + follow prev suggestion

2. if you don't mind using the classic gnome 2 I'd really suggest you to use it . You can switch betweeen the 2 of them: check link

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop)

at least you'll have a working/productive enviornment right the way.

---

### Post by Cheesemill on 2012-12-24
What graphics card do you have?
If you're not sure you can find out by typing the following into a terminal:
```
lspci | grep VGA
```

---

### Post by Bucky Ball on 2012-12-24
To open a terminal, Applications>Accessories>Terminal, copy and paste Cheesemill's code, hit 'enter' and post the output of that command back here, please. ;)

Just confirming; you have installed Ubuntu to a separate partition on the hard drive? This is not a Wubi install (inside Windows) or running from a USB dongle? If you are trying Ubuntu from the install DVD or USB _*prior*_ to installing then this would explain the sluggishness (and also the inability to install drivers, or find them, perhaps).

---

### Post by grahammechanical on 2012-12-24
The really simple way for 12.10 users is to open System Settings from the Power cog menu and select Software Sources and open the Additional Drivers tab.

That should list four video drivers. One will be Nouveau the open source driver. The other three should be different versions of the proprietary driver. At least this is the case with Nvidia.

If you did a fresh install of 12.10 and ticked the box allowing third party software to be installed then you most likely are already using a proprietary video driver. I have had problem with what is called Nvidia-current. You could try Nouveau. I find it acceptable. Or one of the two experimental Nvidia drivers.

Regards.

---

### Post by 3rdalbum on 2012-12-24
> **grahammechanical said:**
> The really simple way for 12.10 users is to open System Settings from the Power cog menu and select Software Sources and open the Additional Drivers tab.

+1. Listen to this man.

Its important to remember that Ubuntu changes very quickly. Instructions from an old version will not work with a new version.

Looks like the instructions you were trying to follow were from Ubuntu 10.10 or earlier - like trying to follow Windows 95 instructions on Windows 8.

---

### Post by Publisher on 2012-12-24
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
This is info from "Terminal"
  The installation is stand alone, on its own drive no other o/s installed.

---

### Post by Publisher on 2012-12-24
> **grahammechanical said:**
> The really simple way for 12.10 users is to open System Settings from the Power cog menu and select Software Sources and open the Additional Drivers tab.

That should list four video drivers. One will be Nouveau the open source driver. The other three should be different versions of the proprietary driver. At least this is the case with Nvidia.

If you did a fresh install of 12.10 and ticked the box allowing third party software to be installed then you most likely are already using a proprietary video driver. I have had problem with what is called Nvidia-current. You could try Nouveau. I find it acceptable. Or one of the two experimental Nvidia drivers.

Regards.

 Thanks for explanation.  There are no proprietary drive drivers in use according to the message given.

---

### Post by squakie on 2012-12-24
The only driver that USED to be available was from OpenChrome, but I don't even know if it's available any more.  The S3 unichrome wasn't supported by the kernel, and pre-unity days you couldn't run any "eye candy" like compiz.  Compiz is required, from what I understand, for Unity.  So what ever you might choose would need to use a different desktop rather than unity.  Just be forwarned the performance will be lousy anyway.

---

### Post by deadflowr on 2012-12-24
[https://answers.launchpad.net/ubuntu/+source/yelp/+question/126426]("https://answers.launchpad.net/ubuntu/+source/yelp/+question/126426")

See if post 3 and its links help you out.

---

### Post by Bucky Ball on 2012-12-24
Yea, I have the VIA on an old desktop. I'll check it out later but pretty sure it is using the default open source drivers. Get back to you ...

As mentioned, doubt that's got the grunt for Unity. You might try xfce desktop environment or lxde. To install xfce, go to Software Centre and do a search and install of xfce4. Log out, hit the 'Sessions' pop-up and choose 'xfce4 session' (or something like it), log back in again.

---

### Post by squakie on 2012-12-25
> **deadflowr said:**
> [https://answers.launchpad.net/ubuntu/+source/yelp/+question/126426](https://answers.launchpad.net/ubuntu/+source/yelp/+question/126426)

See if post 3 and its links help you out.

Yeah, that's the openchrome driver I mentioned.  That's also an old post - I'm not sure if xorg.conf will be recognized now or not, since with the "new" X these options can go in separate config files.  Hopefully this will work - but does anyone know if the openchrome driver is included now?  I always had to download it back when I had a new (now several years old and not in my possesion) Gateway laptop that used that IGP.

---

### Post by Bucky Ball on 2012-12-25
VIA graphics should work out of the box. They are not gonna get any better. Nothing you can install to improve it. This much I know; I've tried ...

The Unichrome stuff is old ...

---

### Post by Publisher on 2012-12-25
> **Bucky Ball said:**
> Yea, I have the VIA on an old desktop. I'll check it out later but pretty sure it is using the default open source drivers. Get back to you ...

As mentioned, doubt that's got the grunt for Unity. You might try xfce desktop environment or lxde. To install xfce, go to Software Centre and do a search and install of xfce4. Log out, hit the 'Sessions' pop-up and choose 'xfce4 session' (or something like it), log back in again.

My thanks to you for this excellent suggestion it works well. At least I now have a starting point. Thank you to everyone for your help.:D

---

### Post by Bucky Ball on 2012-12-26
Great to hear that's working for you. There are lighter desktop environments you might like to spin. Pretty easy to do. Lxde is lighter again (and find in Software Centre, as above) but you can use different apps with different DEs also (I use PCmanFM as a file manager in Xubuntu, among other things, for instance). You don't need to stick with the default applications.

I actually run the full install of Xubuntu on a powerful, modern laptop cos I love it! But you might want to try installing Xubuntu (or Lubuntu) instead of Ubuntu for a better result with older hardware. The default applications are much lighter than what you'll find in Ubuntu and you won't have Unity in the background, even though you're not using it. 

Good luck and good news. If you consider this thread is solved please mark it as such to help others and post a new thread with any further issues. That doesn't close or lock this one if you have any other questions/ideas ... ;)

---

