---
title: "Question about Ubuntu with Wubi"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Bavarian on 2008-07-02
Hi all.First thank you for the CD's who i received yesterday :)I have a little question.I have dual-boot with Windows Xp and Mandriva Linux One 2008.Normal i boot with graphical Grub.I want to install Ubuntu with Wubi but i'm afraid because,is there any chance Wubi to delete Grub or some record on Grub?

Thanks.

---

### Post by avtolle on 2008-07-02
On my computer, installing Ubuntu through Wubi added another selection to the Vista bootloader. I'm also dual-booting LinuxMint5. Grub gives the "normal" selections for Mint and Vista; selecting Vista, I then have the option to boot Vista or Ubuntu. Wubi does not affect grub, or any records on grub, as the installation of Ubuntu is as a "folder" in Vista, and not as a separate kernel and o/s to be booted upon startup. HTH.

---

### Post by jualin on 2008-07-02
Yes, installing Ubuntu with the Wubi installer doesn't affect Grub since it uses Windows Boot Loader. However like avtolle said you will have to select "windows" from the Grub and then select Ubuntu.

---

### Post by Bavarian on 2008-07-02
Thank you so much,that was exactly what i want to know.

P.S Sorry for bad english i'm from Bulgaria.

---

### Post by jualin on 2008-07-02
No problem dude, English is not my first language either. I live in United States but I am from Cuba.

---

### Post by Bavarian on 2008-07-03
Hi again.How i can install that driver in command line without internet connection if the driver is on USB flash or CD?
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) that is the driver.Or if there is now way to install it how i can configure my wireless on command line?Because i can't start Gnome on a Samsung R60 notebook.

---

### Post by Bavarian on 2008-07-03
Or my last chance.How i can load VGA driver on command line to get basic graphics to configure wireless and then download drivers.Please help if someone know i want to share Ubuntu with one my friend.

---

### Post by jualin on 2008-07-04
> sudo dpkg-reconfigure xserver-xorg And then just select the "Vesa" drivers which work almost with any video card.

---

### Post by ChameleonDave on 2008-07-04
This thread ought to be moved to the Wubi forum.  It's a specialised area.

---

### Post by jualin on 2008-07-05
I also found this [link]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") which seems very informative. I would pay particular attention to the part of **Method 2**. However I don't know if the first two commands "sudo apt-get update and sudo apt-get install ..." need an internet connection or can be excluded from the process. You can try installing the driver or you can use the command I gave you on post 8 to use the Vesa drivers and get at least some kind of Graphic User Interface. Hope this helps!

---

