---
title: "No CD programs working!"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-13
I cannot burn .iso's onto CDs... I've tried the default thing, brasero, k3b, cdw, etc... None will burn. K3b can' find my drive, cdw says some weird thing about no image file, and the other 2 can't detect my media. 

Picture:

[img]http://img384.imageshack.us/img384/4779/frijun131256rd7.png[/img]

---

### Post by bumanie on 2008-06-13
Have you installed multi-media codecs yet? If not > sudo apt-get install restricted-extras Also go to the medibuntu site and follow the instructions there re enabling [multi-media]("https://help.ubuntu.com/community/Medibuntu") codes

---

### Post by wolfen69 on 2008-06-13
> **bumanie said:**
> Have you installed multi-media codecs yet? If not  Also go to the medibuntu site and follow the instructions there re enabling [multi-media]("https://help.ubuntu.com/community/Medibuntu") codes

you dont need codecs to burn .iso's.

---

### Post by Cypher on 2008-06-13
Can you burn other things to the CD? Audio/Mp3 or regular data files?

---

### Post by linkmaster03 on 2008-06-13
I tried what bumanie suggested. No luck.

Also, no Cypher, I can't.

This is what the normal thing shows:

[img]http://img122.imageshack.us/img122/1157/frijun131519eu4.png[/img]

After doing bumanie's instructions, brasero now shows:

[img]http://img384.imageshack.us/img384/4838/frijun131520qp6.png[/img]

When I try to access my CD drive from computer:///

[img]http://img68.imageshack.us/img68/8946/frijun131525do1.png[/img]

---

### Post by RomeReactor on 2008-06-13
Hi. Is this a fresh install? If not, how long have you had this problem?

It could be a permissions issue or a problem with fstab; Please post it here so others can take a look at it:
```
cat /etc/fstab
```

It could also be hardware failure; if you dual boot, try it in windows or--if you don't dual boot--in another machine, to see if you're able to burn discs there.

---

### Post by linkmaster03 on 2008-06-13
UGH! Windows can't find my drive either! What can I do from here? :(

```
brad@brad-laptop-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d4279e97-5eea-40f4-8f91-07e4c5f89b45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=958778d8-bb89-448a-8a2c-488d04662249 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
brad@brad-laptop-ubuntu:~$ 
```

---

### Post by nicfallenangel on 2008-06-13
Hi, I see you're working on a laptop, if it allows you to remove the CD drive from the computer and place it back in. If you can't remove it, turn off your computer and push in firmly on the cd drive, be careful not to use too much force or you could break your cd drive. If you boot back up and still can't get to your cd to read chances are either the board that controls the drive or the drive itself is bad.

Not too sure on how to do it in Ubuntu, but in windows check the device manager to see if the device is showing up in the DVD/CDRom drives list.

---

### Post by alienexplorers on 2008-06-13
DO you have the following file loaded:
> cdrdao


---

