---
title: "Re-installing 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by ameanjoe on 2008-05-02
Aloha, friends,
Since doing the download/up-grade to 8.04 I've had way too many problems booting and have become more familiar with grub than I really wanted to be. I was running 7.10 with no problems, booted cleanly, and I probably should have left it alone. My question now is:
Can I do a re-download/re-install of 8.04 or will it cause my computer to explode? And if I can't, is it possible to down-grade to 7.10 and not lose all of my data and downloaded software???
I appreciate any suggestions and/or advice...
ameanjoe

---

### Post by Michael.Godawski on 2008-05-02
From what I heard a downgrade is much more likely to nuke your system than an upgrade.

I have done 5 Upgrades from Gutsy to Hardy in this week because everything was not working. Then I just booted into the old 22 kernel and voila.

Back up your data and give the upgrade a try.

[https://help.ubuntu.com/community/DowngradeHowto?highlight=(downgrade](https://help.ubuntu.com/community/DowngradeHowto?highlight=(downgrade))

---

### Post by jonaphant on 2008-05-02
sorry it may sound stupid but how can you boot into the old 22 kernel in ubuntu 8.04? i'm new to linux and ubuntu and i'm trying to learn more about it.

---

### Post by Michael.Godawski on 2008-05-02
During the booting process there is this entry 

grub loading stage 1.5 something something 
and a countdown running 2 seconds..
there you have to hit escape and you can choose which kernel to run or if you want to boot into the recovery mode.

But I cannot promise you that my solution will work for you too. But it is definitely worth a try.

---

### Post by jonaphant on 2008-05-02
> **Michael.Godawski said:**
> During the booting process there is this entry 

grub loading stage 1.5 something something 
and a countdown running 2 seconds..
there you have to hit escape and you can choose which kernel to run or if you want to boot into the recovery mode.

But I cannot promise you that my solution will work for you too. But it is definitely worth a try.

thank you very much , i'm trying it tomorrow, maybe it would fix some issues i'm having with 8.04

---

### Post by Paqman on 2008-05-02
> **ameanjoe said:**
> 
Can I do a re-download/re-install of 8.04 or will it cause my computer to explode? And if I can't, is it possible to down-grade to 7.10 and not lose all of my data and downloaded software???


You can't do a downgrade, no. You'd have to reinstall using a Gutsy disk.

Besides backing up all your data, if your /home isn't on a separate partition then you'll want to back that up. You might also want to back up /etc/fstab if you've added anything to it. You can generate a [list of installed packages](http://ubuntuforums.org/showthread.php?t=261366) to make the reinstall go a lot smoother. Between that and restoring your /home you could be back to a good Gutsy setup pretty quickly.

---

### Post by jonaphant on 2008-05-02
> **Michael.Godawski said:**
> During the booting process there is this entry 

grub loading stage 1.5 something something 
and a countdown running 2 seconds..
there you have to hit escape and you can choose which kernel to run or if you want to boot into the recovery mode.

But I cannot promise you that my solution will work for you too. But it is definitely worth a try.

hi, i tried it and only the 2.6 kernel appears  ???=(

---

### Post by Cypher on 2008-05-02
Gusty uses 2.6.22 and Hardy uses 2.6.24 Kernels. So in the GRUB menu if you did an upgrade, instead of having 2 Ubuntu boot options, you will have 4. If you did a (re)install, then you'll only have two options using 2.6.24..

---

### Post by jonaphant on 2008-05-02
> **Cypher said:**
> Gusty uses 2.6.22 and Hardy uses 2.6.24 Kernels. So in the GRUB menu if you did an upgrade, instead of having 2 Ubuntu boot options, you will have 4. If you did a (re)install, then you'll only have two options using 2.6.24..

thank you haha that explains it all, sorry i'm just a noob:lolflag:

---

### Post by Cypher on 2008-05-02
That's cool..we all have to start someplace..;)

---

