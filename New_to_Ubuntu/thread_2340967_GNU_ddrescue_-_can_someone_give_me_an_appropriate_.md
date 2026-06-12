---
title: "GNU ddrescue - can someone give me an appropriate command-line to run in terminal ?"
date: 2016-10-23
forum: New to Ubuntu
---

### Post by easybullet3 on 2016-10-23
i'm a newbie to Linux. 
but i'm a confident Windows user.


I have a damaged hard drive with many bad sectors from my parents windows computer, attached via Sata cable to a _**Virtual**_ Ubuntu (on my Windows Desktop).
i want to use ddrescue (GNU) to create a Disk Image.
Can someone  tell me what to type into the ubuntu Terminal to achieve the following:

[LIST]
[*][COLOR=#ff0000]invoke ddrescue.[/COLOR]
[*][COLOR=#ff0000]skip over bad sectors[/COLOR] (to avoid wasting hours and hours of time).
[*][COLOR=#ff0000]create a Log (map file)[/COLOR] to enable ddrescue to resume itself if the computer hangs or crashes or restarts.
[*][COLOR=#ff0000]avoid imaging the Windows System Files (MBR) partition[/COLOR] (as i dont intend to restore windows.. _I only want to recover data_ and not waste time imaging windows OS files).
[/LIST]


_Extra Questions_ (to add to the above):

[LIST]
[*][COLOR=#ff0000]Am I supposed to Un-Mount the damaged drive before invoking ddrescue ?[/COLOR]  how can I do this ?
[*][COLOR=#ff0000]Will I be able to run ddrescue a _2nd time_ more thoroughly to try to image the sectors that were skipped on the 1st image and then _MERGE_ these 2 images to create a more complete image ?[/COLOR]
[*][COLOR=#ff0000]Can I control how often the mapfile saves itself ?[/COLOR]
[*][COLOR=#ff0000]Can I control how many attempts it makes to read a sector before skipping to the next sector ?[/COLOR]
[/LIST]

[U]
Software/hardware info[/U]:
i'm running Ubuntu GNOME from a USB Memory Stick (virtual machine, and with Persistence on my Windows 7 Desktop computer).
Faulty Hard drive is connected to the motherboard with Sata Cable.

PS: Am I correct in doing this with Virtual Ubuntu ?  or would I be better off installing ubuntu as a dual boot on my windows desktop ?
i am under the impression that the virtual machine Persistence setting will allow for the ddrescue mapfile to resume itself if the computer crashes or restarts.

---

### Post by sudodus on 2016-10-24
> **easybullet3 said:**
> i'm a newbie to Linux. 
but i'm a confident Windows user.


I have a damaged hard drive with many bad sectors from my parents windows computer, attached via Sata cable to a _**Virtual**_ Ubuntu (on my Windows Desktop).
i want to use ddrescue (GNU) to create a Disk Image.
Can someone  tell me what to type into the ubuntu Terminal to achieve the following:

- invoke ddrescue.

Install:
```
sudo apt-get install gddrescue
```

Read the well written info pages with good examples, read them at least twice:
```
info ddrescue
```
> 
- skip over bad sectors[/COLOR] (to avoid wasting hours and hours of time).

Maybe you can start with Example 1: 'Rescue a whole disk'> 

- create a Log (map file)[/COLOR] to enable ddrescue to resume itself if the computer hangs or crashes or restarts.

Maybe you can start with Example 1: 'Rescue a whole disk'> 

- avoid imaging the Windows System Files (MBR) partition[/COLOR] (as i dont intend to restore windows.. _I only want to recover data_ and not waste time imaging windows OS files).

This will be difficult or impossible with ddrescue> 

+ Extra Questions (to add to the above):

+ Am I supposed to Un-Mount the damaged drive before invoking ddrescue ?[/COLOR]  how can I do this ?

Yes:

```
sudo umount /dev/sdx*
```
where x is the target drive (a, b, c or whatever) > 

+ Will I be able to run ddrescue a _2nd time_ more thoroughly to try to image the sectors that were skipped on the 1st image and then _MERGE_ these 2 images to create a more complete image ?[/COLOR]

 Example 1 does that> 

+ Can I control how often the mapfile saves itself ?[/COLOR]

I don't know/remember using any mapfile with ddrescue, so I say 'maybe'.> 
+ Can I control how many attempts it makes to read a sector before skipping to the next sector ?[/COLOR]
Yes, with the -r option> 

Software/hardware info:
i'm running Ubuntu GNOME from a USB Memory Stick (virtual machine, and with Persistence on my Windows 7 Desktop computer).
Faulty Hard drive is connected to the motherboard with Sata Cable.

PS: Am I correct in doing this with Virtual Ubuntu ?  or would I be better off installing ubuntu as a dual boot on my windows desktop ?

I would run ddrescue in a persistent live system booted into the bare metal, not in a virtual machine. You can create a pendrive with a persistent live Ubuntu Gnome with mkusb.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
> 
i am under the impression that the virtual machine Persistence setting will allow for the ddrescue mapfile to resume itself if the computer crashes or restarts.

---

