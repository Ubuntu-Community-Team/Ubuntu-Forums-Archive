---
title: "Handle SAS drives with Ubuntu-based GNU/Linux live distribution"
date: 2020-06-27
forum: New to Ubuntu
---

### Post by jojo2000 on 2020-06-27
Hello Guys,
I have to check and clone 4 SAS drives connected to HBA ARECA (1320 series). 

Unfortunately the live distro that I use has no drive for this controller and therefore the drive is not detected. 
I'm not very familiar with installing drivers in Linux so thank you in advance for any suggestions or help.

Jojo

---

### Post by CelticWarrior on 2020-06-27
Welcome.

[https://www.areca.com.tw/support/downloads.html](https://www.areca.com.tw/support/downloads.html) has drivers for any supported Ubuntu release. I suggest you download them and follow instructions. If in doubt please come here and describe the problem.

---

### Post by jojo2000 on 2020-06-27
Great, thanks Celtic Warrior.

I had already taken a look at the instructions at the Areca support but it seemed to me they were referring to an OS installed on the hard disk and not distro live as I have.

Anyway I will try to double check

---

### Post by TheFu on 2020-06-27
> **jojo2000 said:**
> Great, thanks Celtic Warrior.

I had already taken a look at the instructions at the Areca support but it seemed to me they were referring to an OS installed on the hard disk and not distro live as I have.

Anyway I will try to double check

Just try it.  What do you have to lose?

The "Live Try Ubuntu" environment supports package installation using an overlay file system in RAM. At reboot, anything installed is lost.  Of course, there is a limit to what can be installed, due to the available RAM on the system. On any desktop/server computer made the last 15 yrs, I'd be surprised if all the drivers needed caused any issues due to lack of RAM.

You can use other tools to make USB boot "Try Ubuntu" environments that come with overlay persistent file systems, so installed, upgraded, and settings are maintained.  **mkusb** can do this.  Takes about 10 minutes to figure it out.

---

### Post by jojo2000 on 2020-06-28
Just try it.  What do you have to lose?

The "Live Try Ubuntu" environment supports package installation using an overlay file system in RAM. At reboot, anything installed is lost.  Of course, there is a limit to what can be installed, due to the available RAM on the system. On any desktop/server computer made the last 15 yrs, I'd be surprised if all the drivers needed caused any issues.

> **TheFu said:**
> You can use other tools to make USB boot "Try Ubuntu" environments that come with overlay persistent file systems, so installed, upgraded, and settings are maintained.  **mkusb** can do this.  Takes about 10 minutes to figure it out.

Ok I'll try "Try Ubuntu" too. I was using Caine a live distro for forensic analysis. I did USB boot with Rufus, that works very well. 
I have to imaging some SAS drives connected to an Areca HBA and unfortunately the drives are not detected.

I think that I need to install manually the drives of HBA and so far I don't know how. The instructions from the Areca website appear for systems already installed, and not live.

---

### Post by kurt18947 on 2020-06-28
You can do a 'full install' to a USB drive that will function exactly as a hard drive install except a little slower. It's also possible to create a live USB with persistence. I'm not sure which would work better for your purposes. Here are directions on creating a full install on a USB:

[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by jojo2000 on 2020-06-30
In the end I chose the installation of Ubuntu to a hdd. 

Based on the information provided by Areca Support (see attachment), sadly I was unable to detect the drive connected to the HBA controller. 
While executing those commands I do not get any errors, it seems that everything is successful. 

But if I give the "fdisk -l" command I don't see the drive listed, while with the "lspci" command I see the ARECA controller, so the card is detected.

---

### Post by jojo2000 on 2020-07-03
I was unable to install the Areca drivers, so as I also had an HBA LSI (9300-8i) the latest version of Ubuntu detected it, and now I am cloning the drives. 

Thanks to everyone who gave me suggestions.

---

