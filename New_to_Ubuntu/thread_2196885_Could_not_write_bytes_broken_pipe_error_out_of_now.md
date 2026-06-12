---
title: "Could not write bytes broken pipe error out of nowhere"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by shahan3.14 on 2014-01-01
I've already read the other posts and they're mostly talking about nvidia drivers and it's not helping.  I am new to Ubuntu and basically what happens is it boots to bios loads the purple screen once and then "could not ...".  I am posting this from an old iPad and am in great need of assistance I can't access any graphical applications and get it in to check stuff.  I can get to recovery mode and booting in fail safe graphics mode just blacks out and resets the recovery mode page.  I did fix broken packages and sudo rm .Xauthority.   I can get into a TTY shell command prompt, and got a warning when I tried to gksudo jockey-gtk .   I don't know how to get into my system to post more about what exactly is wrong with it...    I can boot Ubuntu from a USB but for some reason the wireless is not working at all... Perhaps this is tied to the problem?  This sucks . I know it is new years.  I could really use some help.  Thank you.

---

### Post by steeldriver on 2014-01-01
Hello and welcome to the forums

Can you tell us some more about your graphics hardware? You can use the 'lshw' command in a terminal

```
lshw -C display
```

No need to copy it all - the important parts are the product and the driver e.g.

```

$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
[B]       product: G84GLM [Quadro FX 570M]
[/B]       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: **driver=nvidia** latency=0
       resources: irq:16 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)

```

For your account issues you should start a separate thread in the 'Resolution Center' subforum

---

### Post by shahan3.14 on 2014-01-01
Okay, thank you, I am able to run pastebinit from the TTY of my laptop.  So for lshw -C display it is [http://paste.ubuntu.com/6674648/](http://paste.ubuntu.com/6674648/)

And the dmesg [http://paste.ubuntu.com/6674701/](http://paste.ubuntu.com/6674701/)

So from the lshw... "UNCLAIMED" uh doesn't look good.  Still posting from this old iPad thank you for the help!

---

### Post by steeldriver on 2014-01-01
Does the system have hybrid graphics? did you blacklist the intel graphics driver at some point?

Any hardware specs / model number you can give us?

---

### Post by shahan3.14 on 2014-01-01
I don't think it is hybrid.  And no I don't remember blacklisting anything on purpose.  It is a dell Inspiron n5010.  I believe the graphics card is "intel (R) HD graphics".      It's an intel core i3.  CPU is 64 bits.  I'm currently on the broken pipe laptop with a USB and Ubuntu is running but again the Internet is not working for some reason.  Do you need more information?  The model number is "reg. model: P10F"

---

### Post by steeldriver on 2014-01-01
when you're booting it from the USB what driver does it report (using lshw again, or 'lspci -vnn | grep -A10 VGA')? is it i915?

---

### Post by shahan3.14 on 2014-01-01
Yes under "configuration: driver=i915 latency=0". And then for the lspci it says "Kernel driver in use: i915". And "Kernel modules: i915"

---

### Post by shahan11 on 2014-01-01
I'm going to have to clean install and see if that fixes it.  Will post back soon.

---

### Post by squakie on 2014-01-02
I don't know if this will help at all or not, but here goes:

There used to be a boot option of i915.modeset=0 or i915.modeset=1.  I believe the 0 turns it off and the 1 turns it on.  This used to be seperate from the nomodeset option,  but I really don't know if nomodeset covers it all now.

EDIT:  This is a boot parameter to turn kernel mode setting on/off for the video.  You may want to try it if  you haven't started your reinstall yet.

---

### Post by shahan11 on 2014-01-02
> **squakie said:**
> I don't know if this will help at all or not, but here goes:

There used to be a boot option of i915.modeset=0 or i915.modeset=1.  I believe the 0 turns it off and the 1 turns it on.  This used to be seperate from the nomodeset option,  but I really don't know if nomodeset covers it all now.

EDIT:  This is a boot parameter to turn kernel mode setting on/off for the video.  You may want to try it if  you haven't started your reinstall yet.

Thank you but the clean install seems to have fixed it, I will save this for later just in case.  Thank you all for your help :)  

[SIZE=1]*How should I mark this post?*[/SIZE]

---

### Post by NM5TF on 2014-01-02
> **shahan11 said:**
> Thank you but the clean install seems to have fixed it, I will save this for later just in case.  Thank you all for your help :)  

[SIZE=1]*How should I mark this post?*[/SIZE]

you should mark the thread solved if it's fixed.....use the "thread tools" button next to your 1st post...

tommy

---

