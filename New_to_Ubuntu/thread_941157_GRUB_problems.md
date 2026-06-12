---
title: "GRUB problems"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by zamadatix on 2008-10-07
im sad to say ubuntu isnt right for my desktop -much better for my laptop- so i decided to remove its partition with the cool pen drive linux os based of mandriva on my usb drive. well i now have learned that even if you remove the partition grub still wans to load and obviously fails. so i need to know how from the ubuntu live cd (im in it) to get rid of all traces of grub and boot into my windows without problems.

as usual thanks for any help

---

### Post by zamadatix on 2008-10-07
if we could hurry my computer is making the widest assortment of noises and its kinda scaring me...

---

### Post by zamadatix on 2008-10-07
hate to reply to my own post but i was looking around in the search and found that your supposed ot replace it not just delete it (obvious now...) so what i need is a way to restore the windows boot loader.

---

### Post by Gregmond on 2008-10-07
What you actually need to do from memory is boot off a windows CD and then do:
```
fdisk /mbr
```Its been a while since I had to do this, but its along the lines of repair mode and you need a command prompt. You may also be able to do this by booting into windows (if that is still possible on your system).

---

### Post by zamadatix on 2008-10-07
i dont think ill be able to easily find the disk in my closet but i have a bartpe disc that will probably do the same thing.


i found the disk, i tried booting  it spun and grub said failed  loading... ill try bartpe

---

### Post by Gregmond on 2008-10-07
bartpe should do it, basically what you need is a windows based cmd prompt and the windows fdisk command.

There may be a way from a Live CD but I am unfamiliar with it.

---

### Post by WWSmith36 on 2008-10-07
The bartpe build disk should work.  At boot select the recovery console.  When you get to the command line.  I believe the command is -

```
fixmbr
fixboot
```

Hope this helps

---

### Post by zamadatix on 2008-10-07
im in bartpe but running into a small problem fdisc isnt recognized and none of the other codes worked

---

### Post by caljohnsmith on 2008-10-07
Here's a way you can install a Windows-compatible MBR (Master Boot Record) from your Live CD: first enable all your repositories in System > Prefs > Software Sources, and then download the "mbr" package:
```
sudo apt-get install mbr
```
Then run the following command on your HDD:
```
sudo install-mbr -i n -p D -t 0 /dev/[COLOR="Red"]sda[/COLOR]
```
If your HDD is not sda, be sure to change the above command accordingly. Let me know how it goes.

---

### Post by zamadatix on 2008-10-07
just to try and solve this faster, could i just put grub on and not ubuntu?

---

### Post by zamadatix on 2008-10-07
heck im tired ill just reinstall ubuntu and keep it there

---

