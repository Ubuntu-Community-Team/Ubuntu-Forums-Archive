---
title: "instaled ubuntu 11.10 but..."
date: 2012-02-18
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-02-18
i installed ubuntu 11.10 with partition along with windows-7 but while booting im not getting options to select OS (that is its directly opening widows-7)........

---

### Post by sadaruwan12 on 2012-02-18
How did you install the 2 OS's. Windows first Ubuntu 2nd or the other way around.

---

### Post by rishiar4 on 2012-02-18
first window-7 then ubuntu 11.10

---

### Post by sadaruwan12 on 2012-02-18
ok it seems like the grub loader hasn't been configured best thing do a reinstall of the ubuntu with default settings only at the partition table select the appropriate option below link will help you if you want to learn more.

[link]("http://thpc.info/dual/win7/dualboot_win7+ubuntu1110_grub_mbr_on_win7.html")

After doing that report back.

---

### Post by rishiar4 on 2012-02-18
Could u tell me how to uninstall this ubuntu ??

---

### Post by bogan on 2012-02-18
Hi!, **rishiar**4

> **rishiar4 said:**
> i installed ubuntu 11.10 with partition along with windows-7 but while booting im not getting options to select OS (that is its directly opening widows-7)........ Have you tried pressing the Shift key during the boot time.

That should give you the grub menu to choose from.

  Chao!, **bogan**.

Edit: Don't give up yet, there are more things you could try before re-installing.

---

### Post by sadaruwan12 on 2012-02-18
Tell me how did you installed the ubuntu used a bootble media like a USB or a CD or used the Wubi windows installer ?

If you've used the bootble media approach then you don't need any un-installation just re-install it.

---

### Post by raja.genupula on 2012-02-18
1. are you getting any grub menu if you hold shift key at system booting ? 

in any case its better to post the bootinfoscript , please look at my signature for that link ..


all the best.

---

### Post by rishiar4 on 2012-02-18
> **sadaruwan12 said:**
> Tell me how did you installed the ubuntu used a bootble media like a USB or a CD or used the Wubi windows installer ?

If you've used the bootble media approach then you don't need any un-installation just re-install it.

i installed ubuntu using a cd (that is in kept the cd and restarted the pc)

---

### Post by Lisiano on 2012-02-18
Did you check in your BIOS that there is no "Bootloader virus protection" enabled? Once that stopped me on a old laptop and didn't let me install Grub.
Also did you just tell the installer to install alongside Windows 7 or did you pick "Manual" or something like that?

---

### Post by sadaruwan12 on 2012-02-19
If you've done that and you got to the ubuntu live cd session and after that you double clicked the install ubuntu icon from there you installed it.

Please tell me if I'm correct or not.

If you have done that it's very strange that the GRUB didn't got installed but redo it again if you're having troubles see the following guide it'll help you through the steps.

[Installation Guide From Softpedia]("http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml")

---

