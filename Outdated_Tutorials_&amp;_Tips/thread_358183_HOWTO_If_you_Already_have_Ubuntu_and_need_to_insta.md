---
title: "HOWTO: If you Already have Ubuntu and need to install Windows"
date: 2007-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by iammeagain on 2007-02-10
This is my first how to, if there is anything i messed up on just correct me and if you aren't clear about something just ask. It is a good idea to read some of the stuff other's have posted to see if they had any of the same problems and to give you a better idea of whats going on. Also any suggestions on improvement are great too.  Im going to try and get some screen shots eventually. 

[COLOR="DeepSkyBlue"]I haven't had anytime to revise a lot of stuff i left out on this, so this would prbably be easier to understand :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)[/COLOR]

DISCLAIMER: Just like with any other tutorial, though its tested and should be safe, if you choose to follow this instructions, you are doing it at your OWN risk! (if that didn't scare you, you may continue...)

I used [COLOR="Magenta"](K)Ubuntu 6.06 and 6.10 [/COLOR]to do this along with [COLOR="Magenta"]Windows XP Professional.[/COLOR] 
I would expect this to be able to fix other distros of Linux too that use grub.
[COLOR="Red"]The easiest way[/COLOR] of installing Winblows and Ubuntu together is having Winblows installed first and then installing Ubuntu, but sometimes that isn't an option. If you can I would suggest taking that route instead of this workaround. 

Anyways this is for if you have installed (K)Ubuntu and you want to put Winblows back on your system. This can be tricky because only in a few rare cases does Winblows detect another OS. So you will have to reinstall Grub and also partitioning can be a bit scary the first couple times.

[COLOR="Red"][U][SIZE="5"]
Before anything else back up data! I'm not joking, REALLY![/SIZE][/U][/COLOR]

[SIZE="3"]**Partitioning and Installing Windows:**[/SIZE]

[COLOR="Blue"]_First_[/COLOR] You would want to boot a live (K)Ubuntu CD

[COLOR="Blue"]_Second_[/COLOR] Once its loaded start gparted, *(I think it might be under the System menu then the Administration, but search elsewhere if you don't find it i know its somewhere. If you completely can't find it open a terminal and type in **" [COLOR="SeaGreen"]sudo gparted[/COLOR] "**  (no quotes))*

[COLOR="Blue"]_Third_[/COLOR] With gparted resize your (K)Ubuntu partition, or do it however you want to make another partition for Windows. *(I don't believe you need to format it to anything, because you will format it anyways with the windows installer.)*

[COLOR="Blue"]_Fourth_[/COLOR] Tell gparted to apply the changes and reboot.

[COLOR="Blue"]_Fifth_[/COLOR] You now have to install windows, boot the Windows install CD and choose the right partition. Install it... wait a long time.... (when its done it will have written over your MBR, master boot record, which was grub. So thats why we have to reinstall it.)

**[SIZE="3"]Install Grub:[/SIZE]**

*Info* Windows erased the Master Boot Record (MBR) so now we have to fix that.

[COLOR="Blue"]_First_[/COLOR] Boot into (K)Ubuntu live Cd again

[COLOR="Blue"]_Second_[/COLOR] Open up a terminal, and type in [B]" [COLOR="SeaGreen"]sudo grub[/COLOR] "

[COLOR="Blue"][/B]_Third_[/COLOR] Type **" [COLOR="SeaGreen"]root (hd0,1)[/COLOR] "** Replacing the 0,1 with the appropriate #'s.* (You need to know what partition (K)Ubuntu is on. If you can't remember opening a new terminal and typing " [COLOR="SeaGreen"]sudo fdisk -l [/COLOR]", which will list your partitions. So hda1=hd0,0   and  hda2=hd0,1   and  hdb1=hd1,0  I hope that makes sense its a little tricky to explain.)*

[COLOR="Blue"]_Fourth_[/COLOR] Type in **" [COLOR="SeaGreen"]setup (hd0)[/COLOR] "*** (But replace it with the same thing it was above for you.)*

[COLOR="Blue"]_Fifth_ [/COLOR]Type **" [COLOR="SeaGreen"]quit [/COLOR]"** and reboot everything should be setup. *(Once you learn how its not nearly as hard as it seems.)*

[COLOR="Blue"]Sixth[/COLOR] OK you need to edit your grub menu to include Windows. I totally forgot that part. I dont have the tiem to add it now but i will later

---

### Post by Cannaregio on 2007-02-13
I needed to have windows xp back for my son on my clean ubuntu edgy box, so I followed this HOW TO  yesterday, but had considerable problems.

I have solved them now, so this could result useful if somebody else encounters the same or similar problems.
I also suggest to change the how to 'boot a live Ubuntu CD' into something like 'boot your Ubuntu version live CD': you better **_not_** use 'any' live distro, but the SAME live distro you have installed with instead, so in my case it was edgy, _not_ feisty and _not_ dapper.

after having made exactly what this HOW TO says, there was no restart after reboot, with various (many) mount problems and 
errors à la
"can't access tty;"
and the system froze completely. No tty, no ctrl+alt+del, nothing

If this happens to you you may want to try what I did.

1) from your live ubuntu  
check with gpart that your ubuntu partition boots (and not windows)

2) from your live ubuntu 
open a terminal and **_cfdisk_** your ubuntu partition
```
sudo cfdisk /dev/sda1
```
([COLOR="#ff0000"]/dev/sda1 in my case, YMMV[/COLOR])

3) from your live ubuntu
open a terminal and **_ fsck.extr3_** your ubuntu partition
```
sudo fsck.extr3 /dev/sda1
```
([COLOR="#ff0000"]/dev/sda1 in my case, YMMV[/COLOR])
this worked for me and repaired all my mount problems

Now you can boot into your ubuntu back again, BUT YOU WONT SEE A GRUB ENTRY FOR WINDOWS XP

So create it manually: Add the following to the bottom of your /boot/grub/menu.lst
```

# This is a divider, added to separate the menu items below from the Debian
# ones
 title		Other Windozian operating systems
 root

# This entry was NOT automatically added by the Debian installer for a non-linux OS
# on dev/sda2, I did it manually instead

title		Microsoft Windoze XP Professional edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Of course the code above is tailored for me: [COLOR="Red"]hd0,1 is my sda2 partition[/COLOR], where I originally installed windoze, after having created it with gpart, see how to
If necessary also modify your grub to give it more seconds before booting and don't have it hidden per default

Also it can happen that, when you now reboot, windows will still ask you to complete installation (even if you already did it the first time) and to insert your windows code again. Do it and then let it reboot.

---

### Post by jocheem67 on 2007-02-13
When I lost my grub the other day, I only had to do "grub-install /dev/sda"....

Ofcourse this was just a recover from something that was already there, but just not in the right form...well however....

I had another problem: I was triple-booting xp, feisty and edgy. Yhought to be clever and replaced my menu.1st that was in use, by the new feisty and complete menu.1st...
Result was that I couldn't boot anymore into nothing...
After a lot of seeking I just gave up and reinstalled feisty and edgy. My question: was there a solution using the live-cd?

---

### Post by bernardfrancois on 2007-03-05
I've just read [here]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub") that this method is overwriting the MBR. It's also possible to install grub on a partition using 'setup(hdX,Y)' (with X the number of the disk and Y the number of the partition).

I wonder if there's a way to backup grub before re-installing windows (for example by using **dd**...). A solution like that could be faster and could also keep the grub settings...

---

### Post by aindriuirl on 2007-03-05
Hi,
I had ubuntu and xp running happily on my laptop.  I reinstalled windows and now i don't know how to get my boot menu back.  I'm new to this so not everything makes sense yet.
Thanks, Aindriu

---

### Post by buried on 2007-03-16
No such command as gparted

---

### Post by hikaricore on 2007-03-16
> **buried said:**
> No such command as gparted

You may have to install it depending on which version of ubuntu you're using:

```
sudo aptitude install gparted
```

^ The easy obvious solution. ;-)

---

### Post by dreadlord_chris on 2007-03-28
> **aindriuirl said:**
> Hi,
I had ubuntu and xp running happily on my laptop.  I reinstalled windows and now i don't know how to get my boot menu back.  I'm new to this so not everything makes sense yet.
Thanks, Aindriu

That would be because, as already stated in this thread, XP overwrites the MBR (master boot record) - effectively bypassing any previously installed boot loaders (read: GRUB). Window's boot loader is loath to recognize **any other non-Windows OS**. This would be why it is **highly** recommended that you install Windows **first** then <insert favorite distro> Linux.

Just follow the instructions in this thread to restore GRUB...

---

### Post by tee2 on 2007-04-03
I followed this guide and now I can't boot into windows. My only options on the grub screen are linux and memtest86.

---

### Post by iammeagain on 2007-04-06
to Cannaregio:

I haven't heard of some of the steps you used. It is good that you got it back up and running and thanks for the suggestions. I hope you had it up and running for your son in time.

---

### Post by iammeagain on 2007-04-06
> **jocheem67 said:**
> When I lost my grub the other day, I only had to do "grub-install /dev/sda"....

Ofcourse this was just a recover from something that was already there, but just not in the right form...well however....

I had another problem: I was triple-booting xp, feisty and edgy. Yhought to be clever and replaced my menu.1st that was in use, by the new feisty and complete menu.1st...
Result was that I couldn't boot anymore into nothing...
After a lot of seeking I just gave up and reinstalled feisty and edgy. My question: was there a solution using the live-cd?

I don't know for sure if there is or not, but what you should always do is backup any important files you are changing. just copy them and rename them so you know they are a backup. I probably have 15 different xorg.conf files and a ton of sources.list files along with lots of different menu.lst files. They are usually fairly small files that make a huge difference so it doesn't do any harm to back them up.
So if you had backed it up you could have booted into a live cd mounted your hard drive and replaced the new menu.lst with the new one. Thats the way i would do it at least, there may be other ways also depending on how your system was setup.

---

### Post by iammeagain on 2007-04-06
> **bernardfrancois said:**
> I've just read [here]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=installed+windows+lost+grub") that this method is overwriting the MBR. It's also possible to install grub on a partition using 'setup(hdX,Y)' (with X the number of the disk and Y the number of the partition).

I wonder if there's a way to backup grub before re-installing windows (for example by using **dd**...). A solution like that could be faster and could also keep the grub settings...

If you find anything more on that let me know. I will take a look at that site eventually i hope. Once i get my computer back probably. Cuz Ttat probably would be more handy, your right. But I don't know how to go about doing that and would wanna test it a couple times before suggesting it to anyone. 
Thanx for the idea

---

### Post by iammeagain on 2007-04-06
> **tee2 said:**
> I followed this guide and now I can't boot into windows. My only options on the grub screen are linux and memtest86.

i don't have my linux box accessible right now but you need to edit (as root) your menu.lst file and add something like 
```

title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

But the root (hd0,1) being where your windows partition is. 

[COLOR="Red"](hd0[/COLOR] is the [COLOR="Red"]first[/COLOR] hard drive, [COLOR="Blue"](hd1[/COLOR] the [COLOR="Blue"]second[/COLOR] hard drive etc.

[COLOR="Red"],0)[/COLOR] is the [COLOR="Red"]first[/COLOR] partition, [COLOR="Blue"],1)[/COLOR] is the [COLOR="Blue"]second[/COLOR] parition etc.

get how it works?

---

### Post by jhenager on 2007-04-06
You can also use a utility to copy your MBR to removable media such as a CD, floppy or USB drive before installing Windows, and then copy it back afterwards, overwriting the boot sector created by M$. Then, the only thing remaining would be to add the new OS to grub.
The utility I have used in the past is boot.exe, which can be created on a bootable floppy.
[http://computing.net/howto/advanced/linuxnt/boot.exe](http://computing.net/howto/advanced/linuxnt/boot.exe)

---

### Post by WhiteCynz on 2009-10-06
You should really include the "Type “**find /boot/grub/stage1**” (Do note that there is a space after “find”)" line I found in another intruction, yours really helped me out I just thought this line would make it easier :) (I'm bringing Ubuntu 9.04 back btw) Also I got a "Error 27: Unrecognized command" when using the "sudo fdisk -l" cmd, but that could be my ubuntu live cd or something. Thanks for the help.

---

