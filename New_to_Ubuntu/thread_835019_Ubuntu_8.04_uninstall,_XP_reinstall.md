---
title: "Ubuntu 8.04 uninstall, XP reinstall"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by HiThere on 2008-06-20
Hi all
I have an hp nc6400 laptop that came with windows xp pro.
I installed ubuntu 8.04 over it, and formatted the HDD so nothing else was left during install. Meaning only ubuntu is on the HDD.
Due to work etc i need to reinstall XP pro on the system.
I tried booting from xp cd to reinstall it but it says no HDD detected when i press ENTER for clean a clean XP install.
Is there a way to remove ubuntu and start with a clean XP HDD, as ill just install ubuntu on my home pc.

---

### Post by shae on 2008-06-20
If you are using an SATA drive, you will need to enable IDE legacy mode in your BIOS before installing XP.  XP does not have SATA drivers by default.  Another possibility is slipstreaming SP3 onto your disk.

---

### Post by bumanie on 2008-06-20
Open gparted from a live cd and format the hard drive to ntfs. From the live cd > sudo apt-get install gparted Windows should then recognise the hard drive. You could always have a dual boot system if hard drive space is not an issue. If you do this, it is easier to install windows first, followed by ubuntu.

---

### Post by HiThere on 2008-06-20
> **shae said:**
> If you are using an SATA drive, you will need to enable IDE legacy mode in your BIOS before installing XP.  XP does not have SATA drivers by default.  Another possibility is slipstreaming SP3 onto your disk.

the hp bios seems very limited :(
under device configuration it only has "sata native mode" and thats enabled

---

### Post by madjr on 2008-06-20
> **HiThere said:**
> Hi all
I have an hp nc6400 laptop that came with windows xp pro.
I installed ubuntu 8.04 over it, and formatted the HDD so nothing else was left during install. Meaning only ubuntu is on the HDD.
Due to work etc i need to reinstall XP pro on the system.
I tried booting from xp cd to reinstall it but it says no HDD detected when i press ENTER for clean a clean XP install.
Is there a way to remove ubuntu and start with a clean XP HDD, as ill just install ubuntu on my home pc.


the HDD problem is not because of ubuntu, it's a hardware/bios issue.

check your computer Bios and see if it detects the HDD.

you can then use the Ubuntu live-CD to format the Drive (partition editor).

Also, depending on your windows applications you need you can run them in **WINE** or **virtualization** windows XP (with **virtualbox**) and run all your windows apps.

[http://www.youtube.com/watch?v=nQIrdyoeg1w](http://www.youtube.com/watch?v=nQIrdyoeg1w)

[http://www.youtube.com/watch?v=ynJZAqiSG9c](http://www.youtube.com/watch?v=ynJZAqiSG9c)

---

### Post by HiThere on 2008-06-20
> **bumanie said:**
> Open gparted from a live cd and format the hard drive to ntfs. From the live cd  Windows should then recognise the hard drive. You could always have a dual boot system if hard drive space is not an issue. If you do this, it is easier to install windows first, followed by ubuntu.

Thanks all for offering help :)
My HDD should be fine as i was just running ubuntu perfectley on it. The HP laptop bios dosnt seem to have very many options "F10 to enter ROM setup"
I ran the livecd ran gpartedi deleted the main space and formatted it to NTSF. under gparted i now have "/dev/sda1 (ntsf)", "dev/sda2 (extended)" and "/dev/sda5 (linux swap)"
sda2 and sda5 are both "locked" so i cannot format them. I restarted and ran the XP cd and still it says no hdd detected :(

---

### Post by adobrakic on 2008-06-20
All i did was start up the ubuntu live cd, use gparted to free up a little space, and then put in the windows xp pro cd on restart. then once all the **** comes up, it asks where to install windows to, and you can just make it install over ubuntu.

btw, sorry for bad grammar and spelling (maybe), im tired at the moment.
good luck btw :D

---

### Post by HiThere on 2008-06-20
> **madjr said:**
> the HDD problem is not because of ubuntu, it's a hardware/bios issue.

check your computer Bios and see if it detects the HDD.

you can then use the Ubuntu live-CD to format the Drive (partition editor).

Also, depending on your windows applications you need you can run them in **WINE** or **virtualization** windows XP (with **virtualbox**) and run all your windows apps.

[http://www.youtube.com/watch?v=nQIrdyoeg1w](http://www.youtube.com/watch?v=nQIrdyoeg1w)

[http://www.youtube.com/watch?v=ynJZAqiSG9c](http://www.youtube.com/watch?v=ynJZAqiSG9c)

thanks for your time and effort unfortunatley i need a clean xp system :(

---

### Post by bumanie on 2008-06-20
Seems like a bios issue. I have a fairly new computer and had no trouble installing xp to a sata hard drive. You could try a bios upgrade, I guess, but not convinced this solve your problem. Do you have an old ide hard drive anywhere. I remember reading, that someone else with a similar issue, installed an ide, put xp on it and then copied the installation to the sata drive - might be worth a try. If you want to get rid of sda2 and sda5, firstly delete the extended partition.

---

### Post by HiThere on 2008-06-20
> **bumanie said:**
> Seems like a bios issue. I have a fairly new computer and had no trouble installing xp to a sata hard drive. You could try a bios upgrade, I guess, but not convinced this solve your problem. Do you have an old ide hard drive anywhere. I remember reading, that someone else with a similar issue, installed an ide, put xp on it and then copied the installation to the sata drive - might be worth a try. If you want to get rid of sda2 and sda5, firstly delete the extended partition.

Ye i tried still wasnt able to delete sda2 and sda5 :(
I think it might be a sata issue but the problem is the hp laptop has a very restricted bios with very little to configure, dont know if there is a way around this?

---

### Post by HiThere on 2008-06-20
Just found a "disk sanitizer" option in HP bios. its said to delete all data on HDD so ill try that i guess :lolflag:

---

### Post by bumanie on 2008-06-20
From the sound of things, I think the bios is likely the issue. I guess if it's a laptop, you don't have too many choices. I always stay away from proprietary desk-top computers due to the fact that they usually use minimalist parts/motherboards etc. I buy parts and construct the computer myself, thus aren't hampered by such issues, of course buying a laptop, is different. In the interim, you could always reinstall ubuntu and get windows working in virtualbox. It doesn't support 3D acceleration, but otherwise runs windows well. If you want to get rid of everything off your hard drive you could use something like darik's boot and nuke. With limited bios options, it is hard to find a solution. I guess all you motherboard drivers have been installed. If you have a motherboard driver disk, install the drivers again and see if that makes a difference. Sorry, don't feel as though I am being very helpful.

---

### Post by madjr on 2008-06-20
> **bumanie said:**
> From the sound of things, I think the bios is likely the issue. I guess if it's a laptop, you don't have too many choices. I always stay away from proprietary desk-top computers due to the fact that they usually use minimalist parts/motherboards etc. I buy parts and construct the computer myself, thus aren't hampered by such issues, of course buying a laptop, is different. In the interim, you could always reinstall ubuntu and get windows working in virtualbox. It doesn't support 3D acceleration, but otherwise runs windows well. If you want to get rid of everything off your hard drive you could use something like darik's boot and nuke. With limited bios options, it is hard to find a solution. I guess all you motherboard drivers have been installed. If you have a motherboard driver disk, install the drivers again and see if that makes a difference. Sorry, don't feel as though I am being very helpful.

yea i run virtualbox in seemless mode which is cool

[IMG]http://ubunturoot.files.wordpress.com/2007/12/virtual-semless.png?w=429&h=273[/IMG]



or use different **workspaces** for each 1 :)

[IMG]http://ubunturoot.files.wordpress.com/2007/12/virtual-cube.png?w=433&h=275[/IMG]

---

