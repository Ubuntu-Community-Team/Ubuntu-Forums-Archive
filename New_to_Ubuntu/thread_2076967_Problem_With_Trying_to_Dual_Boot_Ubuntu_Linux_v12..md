---
title: "Problem With Trying to Dual Boot Ubuntu Linux v12.10 With Windows XP"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by XPSucks on 2012-10-27
Hello Ubuntu Community!
 
I recently became interested in trying to dual boot Ubuntu Linux v12.10 with Windows XP. After downloading the Windows installer for it, I ran it, and when it asked me to restart at the end, I did, and when it gave me the option at boot-up to choose either between Windows XP or Ubuntu, I chose Ubuntu, the boot-up went fine, until it asked me for my password, as soon as I entered my password, the background appeared, and the desktop never loaded. I rebooted thousands of times, but still I get nothing but the desktop background.
 
How can I fix this?
 
Thanks in advance!
 
~ David B

---

### Post by newb85 on 2012-10-27
Welcome Ubuntu and the forums!

First, you should know that using the Windows installer doesn't actually set your machine up dual-boot.  It sets up a VM designed to run Ubuntu that runs on Windows, even though you have to run it at the beginning of the Windows boot-up process, and it bypasses the Windows environment.  It does avoid Windows' using a lot of the resources it would need to run the full Windows environment, but it is nonetheless running on Windows.

It could be that a 12.10 Windows install won't run on XP.  I really don't know.

It could also be that your hardware isn't powerful enough to run 12.10.  What are your system specs?
[list=1]
[*]HDD/SDD space
[*]RAM
[*]Graphics Card
[*]Processor
[/list]

---

### Post by XPSucks on 2012-10-27
Okay, so how can I uninstall Linux? It looks like I have to go back to the Ubuntu website, and download the file that you get when you order a CD.

My C: drive can hold 27.9 GB of data, and I currently have 8.83 GB free (this information is from Windows XP, although I have Linux installed on the same drive). My laptop has a history of having a difficulty functioning on Windows XP Service Pack 3, so I am running Windows XP Service Pack 2.

It appears as though I selected the wrong thing to install. I want to run Ubuntu completely independently, without needing to rely on Windows XP for anything.

The laptop is a Compaq Evo N600c.

Thanks in advance!

(My username implies the I do not particularly like Windows XP, but I do not want to completely get rid of it. At one point, I was running a dual installation of Ubuntu, but I want to replace it.)

~ David B

---

### Post by newb85 on 2012-10-27
According to the [Ubuntu Wiki for Wubi]("https://wiki.ubuntu.com/WubiGuide"),

> Run the uninstaller in "Control Panel > Add or Remove Programs" for Windows XP or lower or "Control Panel > Programs and Features" for Windows Vista or Windows 7. Alternatively, you can run: C:\ubuntu\Uninstall-Ubuntu.exe.
If the uninstaller fails, try downloading and running [Uninstall-Ubuntu.exe]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe").

I'm not sure how much space Wubi allocates, so check how much free space you have after you remove Wubi.

---

### Post by newb85 on 2012-10-27
A quick search for your machine brought up Pentium III and 256MB RAM.  I doubt that will support Ubuntu, although for the cost of a CD* and a little time, you can try.  Whether or not it works, I think you will get a much more satisfying experience out of Lubuntu.  You can download it at [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/").  Again, for the cost of a CD and a little time you can try it out.

I recommend you go with 12.04, rather than 12.10.  Make sure you steer clear of 64-bit versions.

*If you create a bootable USB, you can even save yourself the cost of a CD or two.  Read about it at [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").

---

### Post by XPSucks on 2012-10-27
What is the difference between Ubuntu and Lubuntu? Before typing this, I ran the wubi file, and uninstalled Ubuntu. As I am typing this, I am downloading the Ubuntu ISO file to a flash drive. I will see how this works.

---

### Post by newb85 on 2012-10-27
Simply putting the .iso file on the USB won't do the job.  You need to set the USB up as bootable media.  The Universal USB Installer at pendrivelinux will do this.

Lubuntu is an official variant of Ubuntu.  It's much lighter-weight.  The main difference is the Desktop Environment.  It also has some different default applications.  It uses the same software repositories, so everything that can be installed on Ubuntu can also be installed on Lubuntu.  In fact, you could install Unity (the Desktop Environment for Ubuntu) and all Ubuntu's default applications, and you would essentially have Ubuntu.

See [https://help.ubuntu.com/community/Lubuntu]("https://help.ubuntu.com/community/Lubuntu") for more info.

---

