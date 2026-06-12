---
title: "Install Ubuntu on a USB device (newbie)"
date: 2023-06-11
forum: New to Ubuntu
---

### Post by desktop-user on 2023-06-11
Hi guys,

I am a newbie to the Linux environment and would I like to know if it is possible to install Linux (Ubuntu) on a USB device (flash drive, for example) and use it as if it were on an internal device on the PC?   Obviously with the limitation of the speed and storage of the USB device.

or not

It is only possible to install Linux (Ubuntu) on the PC's internal device and run it on a USB device only as a test or to try the system.

Many thanks

---

### Post by tea for one on 2023-06-11
Yes, you can install Ubuntu to a flash drive.
Essentially, you have three options:-
(a) A live system without persistence (test or to install Ubuntu to a PC)
(b) A live system with persistence (so that you can install and save additional software)
(c) An installed system with user and password log-in.

---

### Post by ActionParsnip on 2023-06-11
Absolutely. It's just a file system like any other. You'll need 2 usb sticks (one to install with and one to install the OS onto). Lots of guides on YouTube

---

### Post by desktop-user on 2023-06-11
Hi, thank you for the replies.   That made me hope! :P

So,can I install Ubuntu on a USB stick from the same system recorded (I think here it is burned.) on the DVD?   I burned (recorded) Ubuntu 22.04 on a DVD-R because I couldn't do the process through the Rufus software (make/do a bootable USB device with Ubuntu) using Windows 8 or 10 (I don't remember) 64 bits.   Rufus recognizes (shows) the device but, on the option to choose the ISO file, the Ubuntu ISO file is not displayed.   I don't know why this happens.

Therefore, I decided to burn it to a DVD-R and only then put Ubuntu to be started on a USB stick by Ubuntu itself.

I apologize if there was any grammatical error that made it difficult to understand.  I did what I could with the difference between the two languages (English and Portuguese).

Many thanks again!

---

### Post by oldfred on 2023-06-11
standard Ubuntu does not fit on DVD drives anymore.
And if system is older you do not really want Ubuntu, but a lighter weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie


Also is system UEFI or BIOS?
If UEFI, see this old but still current bug report on Ubquity installer. You need to partition in advance to be sure to have an ESP on external drive.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Multiple work arounds posted in bug report. Easiest for new user may be to use gparted to remove boot flag temporarily from internal drive.

---

### Post by desktop-user on 2023-06-12
> **oldfred said:**
> standard Ubuntu does not fit on DVD drives anymore.
And if system is older you do not really want Ubuntu, but a lighter weight flavor.
:D

I didn't want to download a lighter Ubuntu.  I was forced to do this.  I'm going to explain what happened.   Now I remember.

Firstly, I downloaded an Ubuntu ISO image file of about 7 GB (I think) on April from the main site.   As I couldn't put it on the 8 GB USB stick by Rufus, I downloaded an old version of Ubuntu (22.04.2 LTS) to burn it to a DVD.   I tried to contact support on the Rufus developers' website, but I didn't get an answer about this problem.


[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

> **oldfred said:**
> 
Also is system UEFI or BIOS?
If UEFI, see this old but still current bug report on Ubquity installer. You need to partition in advance to be sure to have an ESP on external drive.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Multiple work arounds posted in bug report. Easiest for new user may be to use gparted to remove boot flag temporarily from internal drive.

I think that's why the system is giving an error message while loading (right at the beginnig):
error: file '/boot/' not found.
_

However, on the laptop screen shows:
Try or Install Ubuntu
Ubuntu (safe graphics)

and I can use the system.

Yes, on the laptop screen shows UEFI with the memory stick in one of the options.  This laptop is an Inspiron (Dell) and came with Windows 8 pre-installed.

Later on, I will read the links you gave me more calmly. If I had any question, can I ask here.   But first, what would be "ESP on external drive"?

Thank you for the reply

[QUOTE=ActionParsnip]
one to install with[/QUOTE]
This expression means "to install the S.O."

and this "one to install the OS onto" means 'with the system already on the device".    Would It be this?

Thank you again

---

### Post by yancek on 2023-06-12
> But first, what would be "ESP on external drive"?
 

When installing to an external USB drive which you want to be independent of the main drive, you would need to create an EFI partition (vfat format) and install Grub to that partition.  You need to do this before the actual install and set the boot and esp flags on that partition.

> and this "one to install the OS onto" means 'with the system already on the device".    Would It be this?
 

Use one USB drive to write the Ubuntu iso to which you will use as the installer.  Have a second USB device which you want to write/install Ubuntu to.

---

### Post by oldfred on 2023-06-12
If system was originally Windows 8, then it was UEFI with gpt partitioning.
Microsoft has required vendors to install in UEFI/gpt mode since Windows released in 2012.

So best to install Ubuntu in UEFI boot mode.
Technically you can install in BIOS mode, but only because it is a separate drive.

The Ubuntu Ubiquity installer always installs boot files to first drive with UEFI. And then that will use the ESP on the internal drive where Windows has its UEFI boot files. Both share one ESP, with different folders.
If always booting from same system that will be ok. But if you ever want to use flash drive with full install to boot on any other system, it needs its own boot files in an ESP on the flash drive.

---

### Post by desktop-user on 2023-06-13
> **oldfred said:**
> If system was originally Windows 8, then it was UEFI with gpt partitioning.
Microsoft has required vendors to install in UEFI/gpt mode since Windows released in 2012.

So best to install Ubuntu in UEFI boot mode.
Technically you can install in BIOS mode, but only because it is a separate drive.

The Ubuntu Ubiquity installer always installs boot files to first drive with UEFI. And then that will use the ESP on the internal drive where Windows has its UEFI boot files. Both share one ESP, with different folders.
If always booting from same system that will be ok. But if you ever want to use flash drive with full install to boot on any other system, it needs its own boot files in an ESP on the flash drive.

Hey guys,

Help...relief! :D  Can somebody help me?  :D Despite the laughter, I'm not kidding.  I'm lost.  Let's take it easy, piece by piece.  Look at the title of the topic: newbie in parentheses.

Terms like "Ubiquity", "EFI partition (vfat format)" and "Grub", I don't even know what it is. Although I have already used the latter term.   So, it's no use saying these terms so directly because I don't know how to work in the Linux environment. I had a light experience with this system.

Despite having already installed Ubuntu and Kubuntu on an internal HD (laptop, currently old) and using Ubuntu on a pendrive in experimental mode, I only know how to use Windows.  So I have no idea what you guys are saying.

All I know how to do is create a bootable USB stick with Ubuntu and install it to an internal drive. But I can't do this because I'm not the only one using the laptop.   My father also uses it and he doesn't even know how to use Windows directly.

The little I read of the webpage that "oldfred" suggested ([https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379")) and I could understand was that the user installed the boot files in the wrong location.  But the reading was very unenjoyable for me.

From here, I understood that I can do what I want and that what I did was create a bootable USB stick with Ubuntu, in my case, by Ubuntu itself, because I couldn't use Rufus.   And that I used Ubuntu in "A live system without persistence (test or to install Ubuntu to a PC)" mode as said by the member "tea for one", but I want to use it in "**A live system with persistence (so that****you can install and save additional software)**" mode, said by the same member.

I also noticed that the term "persistence" is related to storage. Now I understood why the downloaded file and generated folder from the HP Officejet 4630 were no longer in place, as well as the scanned documents I saved in the Ubuntu Documents folder were gone when I shut down the system.   Conclusion, I had to do it all over again and send the documents by email.

I cannot use it on Windows because there is a problem with the Wi-Fi connection between Windows and the HP Officejet. And this one is giving problem with the scanner when connected by USB.

Member "ActionParsnip" said there are "Lots of guides on YouTube" for doing that.   Please, could someone here point me to a video on how to do this process that is more targeted to a newbie like me?

On YouTube, I typed "How to install Ubuntu on a USB stick" and what I found was "the procedure for creating a bootable USB stick with Ubuntu or another Linux system".

Thanks for all

---

### Post by tea for one on 2023-06-13
> **desktop-user said:**
> because I couldn't use Rufus. 
You say that you are familiar with Windows but you can't use Rufus?
Why not?

Rufus will allow you to make an Ubuntu live system with persistent storage using Windows 10/11.

---

### Post by yancek on 2023-06-13
The method of installing to a usb stick is identical to installing on a hard drive.  You need to know which drive is the internal and which is the usb.  You can find this information with the command:  sudo fdisk -l  which will list drives/partitions and will show the size of each.  Use the manual method of installing so you have control and can select the proper drive and partition on which to install.

---

### Post by oldfred on 2023-06-13
While I use a lot of the same terms in the link in my signature, if you go to that link & scroll to near the bottom is a section on Acronyms. One line & links to lots more info.
Most of the terms you will need to know to use a computer.

UEFI and gpt partitioning became Windows standards in 2012, so if using Windows you are using UEFI/gpt.

And yes in beginning I knew how to do things in Windows, and had to learn new terms for Linux. I used lots of Google, but many of my questions lead me to this site.

Installing Ubuntu and replacing Windows is very easy. Just click thru the install menus.
And similarly an install side by side or dual boot with Windows. Choices during install then do matter to not erase Windows.
But install to an external drive is a bit more complicated. Windows does not even allow it.

Full install to external drive.
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)
UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by desktop-user on 2023-06-15
> **tea for one said:**
> You say that you are familiar with Windows but you can't use Rufus?
Why not?

Rufus will allow you to make an Ubuntu live system with persistent storage using Windows 10/11.


Rufus does not show the ISO file in the choose file option, it only recognizes the USB device. This happens in all the versions I downloaded (including the last one - first I downloaded) and I didn't download it once (more than 2 times).

In the option to select the file, inside the Downloads folder, a folder named "MediaGet Downloads" appears. I checked if this folder exists and it doesn't. When I choose to show "all files", Rufus only shows some (not all).

I tried transferring the Ubuntu ISO image file to the Desktop, but Rufus still has the same issue of not showing it. But in this case, in the option to show all files, the software showed more files. Even putting the Ubuntu ISO image inside a folder, Rufus doesn't show this folder.

I deleted the downloaded file of the last version of Ubuntu from April 2023 thinking it was a problem with the file.

If Rufus had worked, I wouldn't have downloaded an old version of Ubuntu so I could burn it to DVD-R using Nero and then create a bootable USB stick from Ubuntu itself.
If I did this using Nero, the problem is not with the Ubuntu ISO image file, not with Windows and not with me, but with Rufus.   Do you agree?

[QUOTE= yancek]
The method of installing to a usb stick is identical to installing on a hard drive.[/QUOTE]

I've read something of the links that member "oldfred" has provided and, so far, the methods haven't looked identical to me.  He even says it's more complicated.

[QUOTE=oldfred]
Full install to external drive.
[https://askubuntu.com/questions/1698...p-disk-creator]("https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator")
UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

[https://ubuntu.com/tutorials/install...top#1-overview]("https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview")
[/QUOTE]

Thanks for the links. I will read more slowly. Just a question: the alternate installer that the user comments on the page "https://askubuntu.com/questions/1698...p-disk-creator" right after showing the "TestDrive" window in "note", this would it be Ubiquity?

Thank you again

[URL="https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview"]
[/URL]

---

### Post by oldfred on 2023-06-15
Does not look like it.
Testdisk comment is from an older question where answers have been updated.
Ubiquity has been the standard Ubuntu installer for years & still used by many flavors.
Newest Ubuntu installer is Subiquity.
But I find little difference between all installers - Basic info, partitioning, username & password & install software.

---

### Post by yancek on 2023-06-16
>  I've read something of the links that member "oldfred" has provided and,  so far, the methods haven't looked identical to me.  He even says it's  more complicated.


It is, I simplified things but the first thing you need to understand is Linux drive/partition naming conventions so you install to the correct location.  The biggest problem with an Ubuntu install to an external or usb drive is if you have an EFI install.  The Ubuntu developers have decided that it is  good idea to write the UEFI files to the first EFI partition found.  If you have no EFI partition on an internal drive, no problem.  If you do have one on another drive, it will write to that drive rather than the external EFI partition a user selects.  I had this problem when I installed Ubuntu to a USB even when I had removed the boot and efi flags from the internal EFI partition.  Other Linux systems don't do this AFAIK.  

The link below has some good, detailed information on using the manual install method with Ubuntu which discusses drive/naming conventions in Linux and should be useful but does not discuss EFI installs.


[https://www.forbes.com/sites/jasonevangelho/2018/08/29/beginners-guide-how-to-install-ubuntu-linux/?sh=3c0bf9dd951c](https://www.forbes.com/sites/jasonevangelho/2018/08/29/beginners-guide-how-to-install-ubuntu-linux/?sh=3c0bf9dd951c)

---

### Post by tea for one on 2023-06-16
> **desktop-user said:**
> Rufus does not show the ISO file in the choose file option, it only recognizes the USB device.
Rufus does show ISO files - otherwise there would be thousands of frustrated users.

Put the Ubuntu ISO file in the Downloads folder of Windows.
Using Rufus 3.21
Attach your target USB device
Rufus does not have [COLOR="#FF0000"]Choose File[/COLOR] - click on [COLOR="#0000FF"]Select[/COLOR].
Windows file manager opens and you navigate to Downloads.
Select your stored ISO.
Then adjust the slider for persistent storage.

---

### Post by C.S.Cameron on 2023-06-16
Here is a method for installing Ubuntu 22.04 on an External USB device that will boot either BIOS or UEFI: [https://askubuntu.com/a/1403793/43926](https://askubuntu.com/a/1403793/43926)
Here is a comparison between Persistent and Full install External USB devices: [https://askubuntu.com/a/1367263/43926](https://askubuntu.com/a/1367263/43926)

---

### Post by desktop-user on 2023-06-18
> **C.S.Cameron said:**
> Here is a method for installing Ubuntu 22.04 on an External USB device that will boot either BIOS or UEFI: [https://askubuntu.com/a/1403793/43926](https://askubuntu.com/a/1403793/43926)
Here is a comparison between Persistent and Full install External USB devices: [https://askubuntu.com/a/1367263/43926](https://askubuntu.com/a/1367263/43926)

"Cameron"! WoW!  What a coincidence!  If this really is your last name, our last name is similar.  Mine is Comeron. This name is of Spanish origin on my part, but there it is Comerón.  However, my aunt said that, in fact, this name has an Irish origin and that it was changed to Comerón in Spain.  I had an uncle who was also Cameron and some older half-relatives who were registered Camerão :mad: :D here in Brazil.

Thank you for the links.

---

### Post by desktop-user on 2023-06-19
> **tea for one said:**
> Rufus does show ISO files - otherwise there would be thousands of frustrated users.

Put the Ubuntu ISO file in the Downloads folder of Windows.
Using Rufus 3.21
Attach your target USB device
Rufus does not have [COLOR=#FF0000]Choose File[/COLOR] - click on [COLOR=#0000FF]Select[/COLOR].
Windows file manager opens and you navigate to Downloads.
Select your stored ISO.
Then adjust the slider for persistent storage.


I hadn't seen your answer.

I think the problem here is between Rufus and Windows. I downloaded Rufus 3.22 and earlier (3.21 and 3.11) on a netbook running Windows 7 Starter and Rufus showed the folders without any problems and some compressed files in the Downloads folder. Without displaying "ghost folder".  After that I ran those same versions of Rufus (including 64bit version 4) on this Windows and the same problem occurs. See the image:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292404&stc=1[/IMG]
**The image disappeared.  ****I will have to post it to another image store. ****Would you have any suggestions? **Can it be on imagevenue?    It was a picture of the Desktop in the background with Rufus in front of it to select the ISO file.

Descriptions:

Window title: Abrir = Open
Rest of window: "Este Comp...> Área de Trabalho >", (in English "This Comp...> Desktop >")
                       Next to "Nome:" (Name, in English), the description is "Todos os arquivos" (All files, in English)

Note the amount of items on the Desktop and what Rufus shows when I click on Select. In this case, I switched to the Desktop just to make it easier because in the Downloads folder there are many more files.

[QUOTE=yancek]
It is, I simplified things but the first thing you need to understand is  Linux drive/partition naming conventions so you install to the correct  location.  The biggest problem with an Ubuntu install to an external or  usb drive is if you have an EFI install.  The Ubuntu developers have  decided that it is  good idea to write the UEFI files to the first EFI  partition found.  If you have no EFI partition on an internal drive, no  problem.  If you do have one on another drive, it will write to that  drive rather than the external EFI partition a user selects.  I had this  problem when I installed Ubuntu to a USB even when I had removed the  boot and efi flags from the internal EFI partition.  Other Linux systems  don't do this AFAIK.  

The link below has some good, detailed information on using the manual  install method with Ubuntu which discusses drive/naming conventions in  Linux and should be useful but does not discuss EFI installs.


[https://www.forbes.com/sites/jasonev...h=3c0bf9dd951c]("https://www.forbes.com/sites/jasonevangelho/2018/08/29/beginners-guide-how-to-install-ubuntu-linux/?sh=3c0bf9dd951c")
[/QUOTE]

Thank you for the link.   Afterwards, I read more calmly.

---

### Post by desktop-user on 2023-06-21
> **tea for one said:**
> Yes, you can install Ubuntu to a flash drive.
Essentially, you have three options:-
(a) A live system without persistence (test or to install Ubuntu to a PC)
(b) A live system with persistence (so that you can install and save additional software)
(c) An installed system with user and password log-in.

Only a question:

I've been reading on the internet about this method of option (b) you commented "a live system with persistence" and in one article a user who performed this method said that the system only saves common files created during use, settings changed of the system itself and applications (softwares) of Linux (Ubuntu - in this case).  The user says that the installation method with persistent storage (a live system with persistence) is not able to keep the hardware drivers (peripherals) installed on the system. Is this information correct? If it's correct, what I'm thinking of doing won't solve it.

Peripheral installation also needs to be kept on the system for this method to work in my situation.

---

### Post by C.S.Cameron on 2023-06-22
On a persistent Live USB all updates are located in a file or partition named writable or casper-rw or home-rw.

When booting a persistent USB drive, the standard video drivers are loaded before the casper-rw partition, (or writable file).

If casper-rw contains Nvidia drivers, they end up in conflict with the video drivers already loaded.

You should do a Full install to USB if you want to use Nvidia drivers.

---

### Post by desktop-user on 2023-06-22
> **C.S.Cameron said:**
> **On a persistent Live USB all updates are located in a file or partition named writable or casper-rw or home-rw.**

When booting a persistent USB drive, the standard video drivers are loaded before the casper-rw partition, (or writable file).

If casper-rw contains Nvidia drivers, they end up in conflict with the video drivers already loaded.

You should do a Full install to USB if you want to use Nvidia drivers.

Yes, what is highlighted I already read on a page referred to me right here. But you didn't understand what I meant. I am not referring to internal hardware (devices inside the computer) but external devices. For example: printers, scanners...

For example: if I install a printer on a persistent Live USB, will the installed drivers for this printer be kept on the system the next time I run it?

---

### Post by C.S.Cameron on 2023-06-22
If the new driver does not conflict with a driver installed at boot you should be okay. 
When you install something on a persistent Ubuntu drive, it is written to the persistent file or partition, (casper-rw or writable), rather than to / and should be "persistent".
Give it a try, the worst that can happen is that you may need to replace the persistent file or partition, (back up the existing casper-rw partition).
You can copy-paste a casper-rw partition from a fresh persistent USB to the existing USB using GParted.

---

### Post by desktop-user on 2023-06-23
> **C.S.Cameron said:**
> If the new driver does not conflict with a driver installed at boot you should be okay. 
When you install something on a persistent Ubuntu drive, it is written to the persistent file or partition, (casper-rw or writable), rather than to / and should be "persistent".
Give it a try, the worst that can happen is that you may need to replace the persistent file or partition, (back up the existing casper-rw partition).
You can copy-paste a casper-rw partition from a fresh persistent USB to the existing USB using GParted.

The problem of conflict I don't believe it can happen because when I booted the USB stick with Ubuntu without persistence, the system installed the printer and I could use it.

But, as it was a live system without persistence, the installation did not stay on the system.   And there is a guide on the internet in which the user who performed the persistent method said that it is not possible to install external devices, such as printers, scanners...

That's why I asked this question.

Thank you

---

### Post by send2 on 2023-06-23
Might this page help you?: 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Maybe the page has something that can help you out...

---

### Post by desktop-user on 2023-06-24
> **send2 said:**
> Might this page help you?: 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Maybe the page has something that can help you out...

Thank you.   Now, there is no lack of internet pages for me to read. :D

---

