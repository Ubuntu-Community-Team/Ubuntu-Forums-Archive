---
title: "Can't Boot to Ununtu 10.04 netbook remix."
date: 2013-06-13
forum: New to Ubuntu
---

### Post by menikidis on 2013-06-13
After some search on google i downloaded boot-repair.iso and gave me the following results, i should tell u that this happened due to automatic updates :
[http://paste.ubuntu.com/5761429/](http://paste.ubuntu.com/5761429/)

---

### Post by mike555 on 2013-06-13
I'm thinking you should get a newer version (13.04) and do a clean install (backup first), you will probably need to get a version like xubuntu then if you want change the desktop to something like you want .

---

### Post by menikidis on 2013-06-13
i tried that before but it was to heavy, my netbook was craving !! at least isnt't there a way to get my stuff from the hard drive?

---

### Post by Cheesemill on 2013-06-13
You should be able to boot from any of the Ubuntu Live CD's to copy your files, if you don't have a CD drive you can make a bootable USB stick instead.

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

---

### Post by menikidis on 2013-06-13
> **Cheesemill said:**
> You should be able to boot from any of the Ubuntu Live CD's to copy your files, if you don't have a CD drive you can make a bootable USB stick instead.

[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

i tried that but my home folder does not have my stuff :/

---

### Post by grahammechanical on 2013-06-13
Are you saying that after using boot repair to re-install Grub to the MBR of sda you still cannot boot Ubuntu? You need to give a lot more information before anyone can offer advice. Do you see the Grub menu? Have you tried booting the earlier kernel - [COLOR=#000000]linux image: /boot/vmlinuz-2.6.32-21-generic? Have you tried Recovery mode>Resume? Specifically, what do you see as Ubuntu loads? What do you see when Ubuntu stops loading?

If you get to a desktop you might try activating a video driver. But without any clues what so ever, it is impossible to advise as to the action to take.

Regards.


[/COLOR]

---

### Post by Hylas de Niall on 2013-06-13
> **menikidis said:**
> i tried that before but it was to heavy, my netbook was craving !! at least isnt't there a way to get my stuff from the hard drive?

What are the specs of your netbook?

---

### Post by monkeybrain2012 on 2013-06-13
10.04 has reached end of life. Try lubuntu 12.04

---

### Post by fantab on 2013-06-14
> **menikidis said:**
> After some search on google i downloaded boot-repair.iso and gave me the following results, i should tell u that this happened due to automatic updates :
[http://paste.ubuntu.com/5761429/](http://paste.ubuntu.com/5761429/)

Try reinstalling Grub. Use 10.04 LiveCD/USB to do so.

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

MoreInfo: [https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

---

### Post by mastablasta on 2013-06-14
> **menikidis said:**
> i tried that but my home folder does not have my stuff :/


ofcourse it doesn't. the home folder in live OS (when you boot to it from USB) is not your hoem folder. you home folder is on the disk. so oyu need to first navigate to your disk and then find your home folder there.

you might need to run file manager wiht gksu command or as root.

---

