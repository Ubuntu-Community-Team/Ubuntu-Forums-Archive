---
title: "How install Ubuntu 12.04 along with Windows 7?"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by BSG Fan on 2013-08-08
My new laptop says in the board that is Windows Vista, but it says is Windows 7.

So, since I am already an Ubuntu user, I want to install side by side (in a partition) Linux without losing the Windows.

I tried before but I failed:
I put the Ubuntu 12.04 CD-ROM and re-started the laptop, but nothing happened to the usual Ubuntu window showing up and tell me what to do.

How I do this?

BSG Fan

---

### Post by linuxonbute on 2013-08-08
Do you mean it just booted into windows?

---

### Post by BSG Fan on 2013-08-08
> **linuxonbute said:**
> Do you mean it just booted into windows?

I put the Ububtu CD ROM and it booted only back to Windows.

---

### Post by linuxonbute on 2013-08-08
Have you set the PC up so the first boot device is the CDRom drive?
If not then it wont boot from it unless you press (I think ) F12 as it starts up and then choose to boot from the CD

---

### Post by oldrocker99 on 2013-08-08
Go into the BIOS for your computer and enable the optical drive as the first boot device; OR get a 4GB thumb drive, and use **unetbootin** (available for Windowsm Mac and Linux) to write the image to the USB, then set the BIOS to boot first from the USB. Booting from a flash drive is **much** faster than a CD, and so is the installation. When it is ready to install, tell it to install side-by-side with Windows. When done, it will default to Ubuntu, but will give you a menu from which you can select to boot into Windows.

---

### Post by BSG Fan on 2013-08-08
okay, okay. It seems that the first device is not the CD ROM.

I tried F12 and nothing happened to get into the BIOS...

I restart the laptop (Windows 7 Home Premium) and it still take me to the Windows start without seeing any command to stop/open the BIOS

what I do?

---

### Post by 3rdalbum on 2013-08-08
> **BSG Fan said:**
> okay, okay. It seems that the first device is not the CD ROM.

I tried F12 and nothing happened to get into the BIOS...

I restart the laptop (Windows 7 Home Premium) and it still take me to the Windows start without seeing any command to stop/open the BIOS

what I do?

Try other keys. The key to press to get into BIOS setup is not always F12. On some computers it's F2, or Tab, or Escape, or Backspace, or I'm sure one of several different keys it could be. If you look carefully at the screen just after turning the computer on, it should tell you which key to use.

---

### Post by slw210 on 2013-08-08
It would help to know what computer?

Usual keys for BIOS..... F2, F10 or Delete.

---

### Post by BSG Fan on 2013-08-08
ok, I will try.

question:
it is obligatory download first the Ubuntu Installer (wubi.exe) first? 
The McFee Antivirus is telling me that such download/file is filled with virus, malware, etc.

---

### Post by BSG Fan on 2013-08-08
this is absolutely my biggest hell in Ubuntu till now...   I tried the Escape Key and it worked, but I saw it for just a second and went straight to Window.
Too many restart can not be good for a computer,

---

### Post by linuxonbute on 2013-08-08
As the PC starts up look very carefully at the bottom left hand corner of the screen.
This is the very first screen before Ubuntu or Windows is loading. It will tell you 
which Function Key to press to get into setup

---

### Post by BSG Fan on 2013-08-08
Okay, I did it and I used the Delete [Del] key and I saw the list that you can see in the picture attachment.
I tried Enable Boot Logging but it sends me only to the same: Windows.
I do not think the other options in this list can help me to see the BIOs, right?

Once again, my pc is a laptop Acer AMD Athlon 2 X2 Dual. 
I already tried the F1,F2,F12,F11 command in futile, including the space bar, and the tab.

What I am doing wrong?

---

### Post by linuxonbute on 2013-08-08
You are leaving it too late!
You will have just 1 or 2 seconds during which you can get into the BIOS.
You will probably need to look for the correct option  the first time then do a reboot and already have your finger poised to press the button.
Keep pressing and releasing it rapidly. If you have done it at the right time you will see some message about starting setup.
The first screenshots you posted are Windows messages - much later in computer terms than the one you need.

---

### Post by oldfred on 2013-08-08
The screens you show are the Windows recovery/repair screens. While there make a Windows repairCD as you may need that later and is always good to have.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

New versions of Ubuntu do not fit on CD anymore. Most now need DVD or flash drive to install. Did you correctly extract ISO and not just copy to the CD?
       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by BSG Fan on 2013-08-08
User linuxonbute, you were so right! I was so slow pressing the key.

Users **linuxonbute, Oldfred, Slw210, 3edalbum**, and **oldrocker99**
THANK you for the help. I did it!
I waited that the Windows icon (if  can describe it in that way) showed up and I immediately pressed (I let it pressed on) the F2 and the panel popped out. I went to BIOS and I pressed F5/f6 at the same time, and Bingo!
Now the first boot option is CD ROM.

But let see what happens now....




I still have a question.
I already downloaded the Wubi,,, 
What I do first?
I put the CD-ROM and the Wubi will open to transmit through the partition process to make room alongside with Windows 7?

---

### Post by oldfred on 2013-08-08
Wubi can only be installed from inside Windows. It is for a test of Ubuntu that is longer term than just using live installer or flash drive. It does allow updates but a full partitioned install is then suggested if you like Ubuntu.

With most Windows 7 system all 4 primary partitions are used. So you have to delete one primary, shrink Windows using Windows disk tools and then you can install Ubuntu.

Examples to review:
 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)


 Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

