---
title: "INSTALL UBUNTU-12.04.2-desktop-amd64"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by thusharavalsalan on 2013-07-12
Hi,


 I have ubuntu-12.04.2-desktop-amd64 downloaded on my PC.I want to install it on my laptop which is Asus 64bit.The disc image file is transfered to a pen drive and on clicking the installation button,its saying 'Insert a CD"

Please help me to install ubuntu on my lap along with preinstalled version of windows 7 professional.

---

### Post by VMC on 2013-07-12
I think what you did was copy the iso to the pen instead of install it to the pen. If you don't have a dvd then you can use [unetbootin]("http://unetbootin.sourceforge.net/") from your Windows OS.

Another method is using the Pendrivelinux that runs under Windows. Instructions found [HERE]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows").

---

### Post by fantab on 2013-07-13
The downloaded ubuntu**.iso** has to be **'burned'** to the USB and not copied or transferred. The tools suggested by 'VMC' should help you do just that, burn the .iso to USB.

The important thing to note before installing Ubuntu is your current Hard Disk Partition Scheme. If you are using 'msdos' Partition Table then you have a only **4 Primary Partitions** limit. If you already have four Primary Partitions then you have delete a partition and re-create that partition as **Extended Partition.** An Extended Partition is a Primary Partition which acts as a container for **Logical Partitions.** Within an Extended Partition we can create more than 100 Logical Partitions.

** Windows Partitions MUST be managed from Windows only using Windows Disk Management tools.

Once you've prepared and burned your Ubuntu.iso to the USB, boot with it and 'Try Ubuntu without Installing'. This option lets you to try Ubuntu before installing. Let the desktop load, then open the TERMINAL (Ctrl+Alt+T) and run the following command:

```
sudo parted -l
```

... and post its output here. It will also help if you can post a Screenshot of your HDD and its partitions from Windows.

---

### Post by 3rdalbum on 2013-07-13
> **thusharavalsalan said:**
>  I have ubuntu-12.04.2-desktop-amd64 downloaded on my PC.I want to install it on my laptop which is Asus 64bit.The disc image file is transfered to a pen drive and on clicking the installation button,its saying 'Insert a CD"

Can you describe exactly what you're doing to get to this "installation button"?

If you want to install Ubuntu from a pen drive, there's a special way to put the image on there: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Give those instructions a try and then boot up your computer from the USB stick, and click the "Install Ubuntu" button. It won't ask for a CD.

---

### Post by mastablasta on 2013-07-13
> **3rdalbum said:**
> Can you describe exactly what you're doing to get to this "installation button"?


probably running wubi. that one wants an image.

---

### Post by thusharavalsalan on 2013-07-15
yes,i am trying to run wubi.but its asking for a password.
I dont know how to proceed.
pls help me...........

---

### Post by MoebusNet on 2013-07-16
"Wubi is still on the 12.04 CD but the ability to install inside Windows from CD has been disabled."

[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

"The intention is to replace wubi.exe on the CD ISO in future releases with a dedicated CD Boot Helper, and then maintain wubi.exe as a separate executable. That appears to be the plan."

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Another option is to install Ubuntu alongside Windows (a dual-boot system) rather than inside of Windows. As always, the cheapest best thing you can do for yourself is to back up everything and own a Windows installation media so that if worst comes to worst you can reinstall Windows from ground zero, then recover your data.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


There are only two kinds of people in the world; those who back up everything, and those who wish they had...

---

### Post by mastablasta on 2013-07-16
another good option to install inside windows is in a virtual box. here is a nice how to: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

you will need at least 2GB ram inwindows and dual core CPU or good single core helps.

---

