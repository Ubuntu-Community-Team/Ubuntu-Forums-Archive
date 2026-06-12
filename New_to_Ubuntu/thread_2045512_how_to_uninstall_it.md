---
title: "how to uninstall it?"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by speedman2202 on 2012-08-21
hello guys

it's seems that i cant use ubuntu and i have to use Lubutnu ...i have dual boot (winxp , ubuntu) i just want uninstall ubuntu to get install lubuntu and remove Grup menu when my pc boot up and i hope someone give me link to install Lubuntu


thx

---

### Post by sandyd on 2012-08-21
If you remove the grub menu - how are you going to boot into windows?

---

### Post by Frogs Hair on 2012-08-21
You can install Lubuntu on the same partition as Ubuntu and this would simply overwrite Ubuntu. I have a Win 7 and Ubuntu dual boot and am not familiar with the Lubuntu installation process or dual booting with XP.  

[http://launchintolinux.wordpress.com/2012/04/04/installing-lubuntu-a-step-by-step-guide-to-dual-booting/](http://launchintolinux.wordpress.com/2012/04/04/installing-lubuntu-a-step-by-step-guide-to-dual-booting/)

---

### Post by Bufeu on 2012-08-21
> **sandyd said:**
> If you remove the grub menu - how are you going to boot into windows?Using Windows' own bootloader?

---

### Post by black veils on 2012-08-21
you only need to use the lubuntu install media to install over ubuntu, keeping your dual-boot. follow the wizard, and choose to replace ubuntu, make sure you are choosing the correct option! and before anything, backup your data.

[d]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")[ownload]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")

---

### Post by marlow59 on 2012-08-21
just go on with the process of installing Lubuntu, and choose the advanced installation mode to chose the partition to install Lubuntu on : point it to the Ubuntu partition and that's it. You can't remove GRUB and keep the dualboot. it's highly recommended to keep grub and not mess up with Boot-loaders if you're not an experimented user.

---

### Post by speedman2202 on 2012-08-21
if i dont want install lubuntu and remove ubuntu from my pc .... just del ubuntu partitions only??? or it will grup menu will still remain :|


thx all for replay

---

### Post by marlow59 on 2012-08-21
you may only format the ubuntu partition then =)

---

### Post by Bufeu on 2012-08-21
> **speedman2202 said:**
> if i dont want install lubuntu and remove ubuntu from my pc .... just del ubuntu partitions only??? or it will grup menu will still remain :|


thx all for replayJust remove the partitions Ubuntu is installed on and use your Windows CD to start "System Repair" (follow [this guide]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")), or use a live-CD of Ubuntu to install Windows' own bootloader: [http://ubuntuforums.org/showpost.php?p=4635639&postcount=6](http://ubuntuforums.org/showpost.php?p=4635639&postcount=6).

---

### Post by marlow59 on 2012-08-21
I can't follow you right know. What do you want to do? uninstall ubuntu and let only windows on your pc, or install lubuntu over it or what ?

---

### Post by speedman2202 on 2012-08-21
> **marlow59 said:**
> I can't follow you right know. What do you want to do? uninstall ubuntu and let only windows on your pc, or install lubuntu over it or what ?
both

uninstall ubuntu and let only windows on your pc and install lubuntu over it

---

### Post by marlow59 on 2012-08-21
So finally you want a pc with only lubuntu on it, right ?

---

### Post by sandyd on 2012-08-21
> **speedman2202 said:**
> both

uninstall ubuntu and let only windows on your pc and install lubuntu over it
Then you can't remove grub.

There can only be one main bootloader installed in the MBR.

The Windows bootloader does not work with linux.

Right now, just do this.


Boot into Lubuntu, and run
```

sudo apt-get remove ubuntu-desktop
sudo apt-get install lubuntu-desktop

```^^THAT will install the default ubuntu desktop. When you get to the login screen next time, select "Unity" as your desktop.

No need to uninstall

---

### Post by speedman2202 on 2012-08-21
> **marlow59 said:**
> So finally you want a pc with only lubuntu on it, right ?

no , i just wanna know ...how to remove ubuntu and make my windows boot with it's own bootloader ...... and also know how to remove ubuntu and install/overwrite lubuntu  just in case ......if u have another clear instruction , i would like to know ... thx :)

> **sandyd said:**
> Then you can't remove grub.

There can only be one main bootloader installed in the MBR.

The Windows bootloader does not work with linux.

Right now, just do this.


Boot into Lubuntu, and run
```

sudo apt-get remove lubuntu-desktop
sudo apt-get install ubuntu-desktop

```^^THAT will install the default ubuntu desktop. When you get to the login screen next time, select "Unity" as your desktop.

No need to uninstall


ok , i will boot with lubuntu cd and go live and do ur command ... but i whave two partion for ubuntu ( /boot , /swap) ... so am i remain them or just del them if i am going to install lubuntu???

also if i just wanna remove ubuntu system from my whole computer and want mt winxp boot with its own bootloader???

thx for replay and help .... i am appreciate that :)

---

### Post by sandyd on 2012-08-22
Oops - read a bit fast and got a bit mixed up ;) , sorry about that.

Can you boot into Ubuntu right now?

If you can, just run the fixed commands above, and that should install lubuntu through its metapackage. If not, install Lubuntu over it

If you want to remove Ubuntu, you will have to reinstall/store the Windows Bootloader, as Grub is linked to your L/Ubuntu installation.

---

