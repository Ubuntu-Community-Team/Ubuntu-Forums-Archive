---
title: "Ubuntu error while installing...."
date: 2014-04-28
forum: New to Ubuntu
---

### Post by niveditavasant1 on 2014-04-28
Hi all

I am using Toshiba Satellite L500 laptop installed with Windows 8.1 and 2GB RAM
I am just been able to install any version of ubuntu on my laptop. been trying it for a year and half.

here is the screenshot of the error
[ATTACH=CONFIG]252605[/ATTACH]

can anyone tell me how to solve this error and go about it.

and yes i get completely confusing with the installation type during the ubuntu installation process.

---

### Post by stozz2 on 2014-04-28
_**Be Aware**_ That Once You Have Installed Ubuntu on your Toshiba Laptop A simple Factory Restore it will not be as simple, if you choose to create a dual boot Computer.
It is still possible but would require some work done with disk partions.

Second 8.1 on a dual core processor with 2 meg of ram.... must be driving you spare !! ( also suspect that you don't have the factory setting stored on your computer )
 
Now that I have got that out of the way this is what you need to do.

What you need to do :
**1 st** Download a version of Ubuntu as an ISO file.
**2nd** Burn that ISO to a CD or DVD
**3rd** Power off your machine then remove both the battery and the power cord from the back of the machine.
**4th** Place the power cord back into the machine but leave the battery out.
 *(Leave as an option for Hard Reboot, by pulling the Cord, can force the computer to do a reboot)*
**5th** In some cases by default, the CD Drive is the first point of call for the computer when looking for an Operating system.
To change the default Start up Drive, you need to reboot the computer so that the Toshiba logo appears on the screen.

You may need to reboot the machine by pulling out the power cord if the Windows Splash screen continually appears immediately after the machine is powered back on

Known [**Bios Start up Keys]**
To enter into bios Try one of the following [DEL];[F1]; [F2]; [F10]; [F11]; [F12]
 
Once the Computers manufactures Logo appears hold down the[**Bios Start up Key]**and continue to hold the key down

You should then enter into the Computers Bios.
Once you have, seek out the menu item Boot Order, where you must place the Cd Drive as being the first drive in the boot order.
save your setting and reboot the machine with the Ubuntu live CD in your drive.

---

### Post by su:bhatta on 2014-04-28
> **niveditavasant1 said:**
> Hi all

I am using Toshiba Satellite L500 laptop installed with Windows 8.1 and 2GB RAM
I am just been able to install any version of ubuntu on my laptop. been trying it for a year and half.


Hi Nivedita,

What you are trying to do is install Ubuntu using Wubi, which installs Ubuntu inside your Windows partition.
Wubi is a project that has been abandoned.
Best to avoid a Wubi install.

It will be best if you follow [**[COLOR=#000000]stozz2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1920308")'s advise and download the ISO and burn it to a disc or make a bootable USB (in case your Toshiba laptop supports that) 
and try getting a live session, meaning, run the Ubuntu installation from the DVD itself and see if everything is working fine.

In case it does, you can use Windows to partition you hard drive and make about 20Gb's of free space and install Ubuntu in that partition.
Here is the Ubuntu Guide to install the latest Ubuntu14.04: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
The page has screenshots to make it easier for you.

Also, does your laptop has UEFI boot?

Edit: I dont know why [**[COLOR=#000000]stozz2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1920308") is advising Step3 & Step4 in the post#2, maybe from his personal experience, but in most cases, a simple reboot would do.
You might have to go to BIOS and select CDRom drive as the first boot device.

---

### Post by 3rdalbum on 2014-04-28
You can't install Ubuntu anymore using the Windows-based utility. You need to download Ubuntu 14.04 and burn it to a DVD (using the "Burn ISO Image To Disc" function of your burning software) and then boot your computer from that DVD.

---

### Post by niveditavasant1 on 2014-04-29
ok thanks....

Can i try using USB drive?

---

### Post by 3rdalbum on 2014-04-29
Oh yes, you can create a bootable USB. Just use the instructions on the Ubuntu website.

---

### Post by kyle19 on 2014-04-29
Before your pc starts up go to bios and boot from your usb then when unetbootin, linux live usb or what ever you used to install on flashdrive comes up select install or try ubuntu without installing, then install from there

---

### Post by Impavidus on 2014-04-29
> **su:bhatta said:**
> 
Also, does your laptop has UEFI boot?

Most likely it does, as most laptops with Win8. And most likely this is the reason why wubi didn't work, as it is known to not work on UEFI systems. That's one reason why wubi has been discontinued and why you have to install as a real dual boot.

This link might come in handy: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by niveditavasant1 on 2014-04-29
ok will try using USB.. 

will let you know what happens

---

### Post by niveditavasant1 on 2014-05-02
Hi all,

I tried installing ubuntu using USB Drive...
It worked..

But the problem was when i clicked "install ubuntu inside windows" and continue button - the computer restarts and windows boots up.
I dont know why.. it should go to the next step in ubuntu setup. but it didn't happened.

and i am really confused on how to proceed when i click on "something else Option" i really dont know how to install ubuntu using this "something else" option.

---

### Post by su:bhatta on 2014-05-02
hi nivedita,
as pointed out earlier you should not try to do "install ubuntu inside windows". Or did you mean "Install alongside windows" ?

Look at the page : [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
To use the 'Something Else" option you have to first make a free partition in your hard drive.

Suggest you first boot into the Windows and using Windows tools, make a free partition of about 15-20 Gb.Don't have to format it, just make a partition.

Then when you reach the screen 'Something else' you can choose that new partition you had made to install Ubuntu.
You have to choose a mount point , easiest is choosing '/ ' and also format the partition as Ext4.

But first use 'Try Ubuntu' and see if you are successful in getting a Live session. Then go for Install.

---

