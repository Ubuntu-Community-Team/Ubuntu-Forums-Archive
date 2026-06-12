---
title: "reinstall ubuntu from zero"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by cseljatib on 2008-05-07
hi there,

i am using ubuntu 8.04 in a lenovo t60. I have dual boot with WinXP, which i barely use.

I have been problems with my laptop for a while, and we already sent it to lenovo to be fixed, but the problems persist. I think, that all my problems start with i install Virtualbox to be able to run XP inside ubuntu without booting.

before of send the laptop back to lenovo for third time, i would like to install ubuntu from ZERO (i mean, in a clean partition), but i wonder how to do that???, and not installing VirtualBox

should i start with the installation CD, then go to Gparted, erase the current partitions (except the WinXP ones), and then install ubuntu as usual???

Please help me

thanks

---

### Post by scouser73 on 2008-05-07
When installing the Live CD, Ubuntu gives you the option to delete the partition and only have Ubuntu on the system.

From what I remember you need to choose the whole of the disk (thus giving Ubuntu the option of deleting the XP partition)

I hope this of use to you.

---

### Post by cseljatib on 2008-05-07
but i do not want to delete the XP partition, Can I not install ubuntu from zero, without touching XP?

how, please give me details

thanks

---

### Post by Het Irv on 2008-05-07
I think in the newest version of the installer on the live CD it gives you the option to shrink the existing partition and install Ubuntu on the resulting free space.  I haven't tried it yet, but I haven't heard any complaints about it.  If you have a way to, I would suggest backing-up XP, and then using the built in shrink tool to Install Ubuntu.  I think that you can adjust where Ubuntu will shrink it to.  Your other optionis to manually shrink the partiton using G-parted on the cd and Install Ubuntu on the freed space.

---

### Post by thisiam on 2008-05-07
You got it right, start the live cd and delete the ext3 partition and swap partition and leave the space unallocated and reinstall as normal. does lenovo support ubuntu for you? i would think that if they had a problem they would blame you for installing linux and wash their hands clean of your problem.

---

### Post by dondad on 2008-05-07
> **cseljatib said:**
> hi there,

i am using ubuntu 8.04 in a lenovo t60. I have dual boot with WinXP, which i barely use.

I have been problems with my laptop for a while, and we already sent it to lenovo to be fixed, but the problems persist. I think, that all my problems start with i install Virtualbox to be able to run XP inside ubuntu without booting.

before of send the laptop back to lenovo for third time, i would like to install ubuntu from ZERO (i mean, in a clean partition), but i wonder how to do that???, and not installing VirtualBox

should i start with the installation CD, then go to Gparted, erase the current partitions (except the WinXP ones), and then install ubuntu as usual???

Please help me

thanks


If you are already dual booting, then you can just select the manual partitioning and have the cd install over your old ubuntu. It will format that partition and do a clean load. It should detect the Windows partition and add it to grub.

I would make sure that I had any important data backed up before the install.

---

### Post by Delever on 2008-05-07
If I understand correctly, you installed ubuntu on your system using LiveCD "install" option, which divided your disk into two partitions. There is Windows XP on the first one, and Ubuntu on second one (and maybe swap partition). Now you have some data on first partition, and you don't want to delete it. You can get rid of Windows in several ways:

1. Never use them and just delete Windows and Program Files folders from ubuntu. Result: two partitions, one NTFS, another ext3, both accesible from ubuntu.
2. Move your data from first partition somewhere else. Now, if you do that, you can do what other posters said: delete all partitions and do clean install. Or you can format windows partition, to get rid of some undeletable windows files.

I assumed you have not installed Ubuntu using wubi (running installer from Windows and specifying where to put ubuntu on disk).

---

### Post by Het Irv on 2008-05-07
[COLOR="DimGray"][COLOR="Silver"]I think what he wants to do is set up a dual-boot, before he had only been running Ubuntu in a VM under XP, his computer has been messing up and he thinks it is the VM's fualt (I want to clarify that it might be the VM's fault, I just couldn't think of another way to put that sentence).

He needs help setting up a Dual-Boot.  The issue raised before though, was a valid one, I have heard many times of manufacturers have not worked on the hardware for a laptop (i.e. a hinge for the screen) because Linux was installed on the computer, they claimed it voided the warrenty.  This might be something you would want to check on.[/COLOR][/COLOR]

---

### Post by zvacet on 2008-05-07
> should i start with the installation CD, then go to Gparted, erase the current partitions (except the WinXP ones), and then install ubuntu as usual???

Yes!

---

### Post by cseljatib on 2008-05-07
hey guys,
just o be clear:
I have dual-boot, i mean i have ubuntu and WinXP. Later I installed VirtualBox in ubuntu to be able to run XP being inside ubuntu. Then I do not have any problem with setting the dual-boot, or anything related, 
Thisiam, dondad, and zvacet understood correctly, thanks!, i do not want to touh the XP partition, but i want to reinstall from zero ubuntu
	
I haven't had any problem with lenovo, inclusive i have an ubuntu sticker on it, and they haven't say nothing about it, yet.

thanks

---

