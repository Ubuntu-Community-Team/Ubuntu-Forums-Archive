---
title: "How to re-install WindowsXP on a dual-boot pc without uninstallin Ubuntu"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by ask_ on 2012-06-13
Hello,

I have Windows XP and LUbuntu11.10 running on dual-boot PC.
I wish to re-install Windows XP. I do not wish to re-install Ubuntu .
I would like to know is there a way to keep Ubuntu as it is and re-install Windows XP on the same partition that it was on before, using Windows XP cd.

I am not particularly against removing Ubuntu but would prefer if that is not the case.

P.S :- I am currently using 11.10 will upgrade to 12.04 in a month or so as I have not a fast internet connection. Hence satisfied with 11.10 as of now and would prefer not to re-install it.

Thanks.

Love the new look of the forums by the way.

---

### Post by tushar maroo on 2012-06-13
> **ask_ said:**
> Hello,

I have Windows XP and LUbuntu11.10 running on dual-boot PC.
I wish to re-install Windows XP. I do not wish to re-install Ubuntu .
I would like to know is there a way to keep Ubuntu as it is and re-install Windows XP on the same partition that it was on before, using Windows XP cd.

I am not particularly against removing Ubuntu but would prefer if that is not the case.

P.S :- I am currently using 11.10 will upgrade to 12.04 in a month or so as I have not a fast internet connection. Hence satisfied with 11.10 as of now and would prefer not to re-install it.

Thanks.

Love the new look of the forums by the way.
As you are re-installing windows-xp ,it will remove the grub menu of ubuntu , so after installing xp you have to re-install the grub menu from live Ubuntu disk.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
p.s.: ubuntu identifies the windows partitions but windows upto windows7 it cannot understand the other installations...

---

### Post by mastablasta on 2012-06-13
don't format the drive partition but simply install windowsXP to it and then (as mentioned) restore grub so you can boot in Ubuntu as well.

---

### Post by afixane on 2012-06-13
1. Install your XP normally, but do not remove ubuntu partition.
2. After installing XP, boot Ubuntu LiveCD
3.Go to terminal and type 
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair 

```
4. Open Boot Repair and try the "recommended repair" option

---

### Post by ask_ on 2012-06-13
Thanks everyone. Will tryout the above suggestions.
:guitar:

---

### Post by wilee-nilee on 2012-06-13
> **ask_ said:**
> Thanks everyone. Will tryout the above suggestions.
:guitar:

Just use the custom install to load the partition XP is in now.

Not sure if XP had a wubi install option, make sure you don't have a wubi install.

---

### Post by ashwinrao on 2012-06-13
> **wilee-nilee said:**
> Not sure if XP had a wubi install option, make sure you don't have a wubi install.

+1 for your post. OP doesn't mentioned how exactly he installed Ubuntu.  If it's a wubi install, re-installing XP will remove the Ubuntu entirely.

---

### Post by ask_ on 2012-07-01
Thanks everyone. It wasn't a Wubi install. I am yet to try out the suggestions as I didn't have access to the PC I mentioned as it is with my friend. Will try it out as soon I get access.

---

### Post by TheGuyWithTheFace on 2012-07-01
Just remember to back up your data first!

---

