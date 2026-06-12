---
title: "interrupted upgrade"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by fourinchdragslicks on 2012-06-26
while upgrading to 12.04, my computer was restarted, and i cannot boot into 12.04,  or 11.10.  12.04 recovery is not working right, and 11.10 recovery is not helping, i have tried a few different methods to restart the upgrade process through terminal on a live cd but so far have had no luck so i am hoping to start out here with guidance directed at my specific problem.  most of my data is off the ubuntu partition of my drive, but there are some things that i would like to remove still ( and ideally bookmarks from firefox) but when i get to the main folder i do not have permission to view/move all of the desktop contents.  I dual boot windows 7.  I think that is everything to get someone with alot more experience started, I appreciate your help.

---

### Post by ikt on 2012-06-26
> **fourinchdragslicks said:**
> when i get to the main folder i do not have permission to view/move all of the desktop contents.

If you can't try running nautilus as root (Terminal > sudo nautilus) that should give you root access to all folders which means you can go anywhere and touch anything :p

And then I'd back everything up and reinstall :)

---

### Post by audiomick on 2012-06-26
As above, except that you should actually start nautilus using
```
gksu nautilus
```
since it nautilus is a graphical application. I can't remember exactly what it was, and it is very often not an issue, but graphical applications should be started with "gksu" or "gksudo" rather than with "sudo". It is the same thing, but the "gksudo" takes into account something or other that "sudo" isn't aware of.

---

### Post by kansasnoob on 2012-06-26
> **fourinchdragslicks said:**
> while upgrading to 12.04, my computer was restarted, and i cannot boot into 12.04,  or 11.10.  12.04 recovery is not working right, and 11.10 recovery is not helping, i have tried a few different methods to restart the upgrade process through terminal on a live cd but so far have had no luck so i am hoping to start out here with guidance directed at my specific problem.  most of my data is off the ubuntu partition of my drive, but there are some things that i would like to remove still ( and ideally bookmarks from firefox) but when i get to the main folder i do not have permission to view/move all of the desktop contents.  I dual boot windows 7.  I think that is everything to get someone with alot more experience started, I appreciate your help.

I assume from what you're saying that grub does show both the Precise and Oneiric kernels in the boot menu. Is that correct?

If so how many operating systems are installed on that machine?

Also, could you please be a bit more specific about what happens when you try the recovery mode? What errors are shown on the screen?

BTW I expect to be busy with Quantal iso-testing beginning later today and probably not ending until Thursday so I may take quite a while to reply :(

I have two fairly specific thoughts in mind about how to rescue the failed upgrade, one depends on how many (and which) operating systems are installed, the other depends on the amount of free space you have so it would also be helpful to see a screenshot of Gparted (all drives if you have more than one) if you're familiar with Gparted.

At the very least also include the output of:

```
sudo parted -l
```

---

### Post by kansasnoob on 2012-06-26
Just thought to add:

I hate to be a turd in the punchbowl but the OP included "Lubuntu" in the title so NO nautilus is involved!

---

### Post by fourinchdragslicks on 2012-06-26
I should say hat when I get into the main folder, through a live cd, I cannot do anything.

---

### Post by fourinchdragslicks on 2012-06-26
> **kansasnoob said:**
> I assume from what you're saying that grub does show both the Precise and Oneiric kernels in the boot menu. Is that correct?

yes. Precise is in the "front" grub menu where I can choose from precise, precise recovery, older ubuntu install some memory test options and windows 7... Next menu is same thing but oneric 

If so how many operating systems are installed on that machine?

supposed to be just 1 install of ubuntu and windows 7

Also, could you please be a bit more specific about what happens when you try the recovery mode? What errors are shown on the screen?

the error if you try to start precise is 'GLIBC_2.14 not found (required by /lib/libply.so.2)'

BTW I expect to be busy with Quantal iso-testing beginning later today and probably not ending until Thursday so I may take quite a while to reply :(

I have two fairly specific thoughts in mind about how to rescue the failed upgrade, one depends on how many (and which) operating systems are installed, the other depends on the amount of free space you have so it would also be helpful to see a screenshot of Gparted (all drives if you have more than one) if you're familiar with Gparted.

At the very least also include the output of:

```
sudo parted -l
```

I am switching between a tablet and using my regular computer (live cd and attempting to do something from the grub menu)

---

### Post by fourinchdragslicks on 2012-06-26
gparted screenshot

---

### Post by fourinchdragslicks on 2012-06-26
precise recovery open network connections gets errors GLIBC_2.14 not found
and 
ifup: failed to open statefile /var/run/network/ifstate: no such file or directory

---

### Post by kansasnoob on 2012-06-27
Quantal iso-testing has kept me quite busy, sorry for the delay.

Can you download and burn a 12.04 disc?

I'm assuming you want to stay with Lubuntu but I'm not sure which image you need:

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)

Since you're partially upgraded to 12.04 you'll need that disc to work with.

If 11.10 was i386 (aka: 32 bit) you'll want to stay with 32 bit ............ and vice versa if 11.10 was 64 bit.

Once you have a proper 12.04 disc (or USB drive) to work with I'll explain more.

---

### Post by fourinchdragslicks on 2012-06-27
i am not sure why it says lubuntu.  I am running 64 bit os's on 64 bit hardware.  last night i installed 12.04 in (?) windwos 7, onto a different partition than by existing ubuntu instalation(s).  I was able to remove my files, and now have them backed up seperate from the installation.  lesson learned, laziness is setting myself up for stress later.  I can now just do a fresh install of 12.04 in the partition that I was originally using and just redo my personal tweaks.  I was just trying to avoid that by running the upgrade.

---

### Post by kansasnoob on 2012-06-28
I'm going to assume this is solved based on your last post but I would like to point out a couple of things:

#1: In your last post you say, "i am not sure why it says lubuntu". I guess because you chose the lubuntu prefix:

[ATTACH]220371[/ATTACH]

#2: The screenshot you included in post #8 indicates pending doom due to a lack of free space in your Windows partition!

---

