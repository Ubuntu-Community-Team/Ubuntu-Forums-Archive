---
title: "mixing ubuntu with windows 8"
date: 2014-10-31
forum: New to Ubuntu
---

### Post by pdlethbridge on 2014-10-31
I have a 3tb drive that I  could use or a 35 gig and 2 8 gig drives  to install windows Now becaus Im having trouble locating drives for a canon multi functin printer, the scaner won.t work and I have anothe driver  A hauppaug tv tuner. The only way I can get thes to work is in windows. Whate wouldork best for me

---

### Post by oldfred on 2014-11-01
Is system UEFI or BIOS?

With a 3TB drive you have to use gpt partitioning not MBR(msdos). Otherwise with MBR you have a max of 2.2TB.

And Windows only installs and boots from gpt partitioning with UEFI. But newer than XP will read NTFS partitions on gpt partitioned drives.

I have not installed Windows since XP, but 8GB seems a bit small, most recommend at least 30Gb for a minimal Windows. The NTFS partition has to hav 30% free for Windows to run well. So trying to squeeze it into to small of a partition may make it very slow.

---

### Post by pdlethbridge on 2014-11-01
So if I make the first partision say a 50 gig ntfs that will take windose and I can use the rest for linux distros. Now which win distro should I use. OEM or retail 
Now this sounds like me
I have not installed Windows since XP,

---

### Post by oldfred on 2014-11-01
Unless you have newer hardware you cannot install any Windows on a gpt drive. It has to be UEFI boot.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
Know nothing about Windows versions anymore.

---

### Post by pdlethbridge on 2014-11-01
If I have windows on one hard drive will           i still be able to use thanother drive for linux or does windows screw up the bios so bad that iur becomes un usabl

---

### Post by oldfred on 2014-11-01
It is not Windows per se, but UEFI with secure boot that has been the issue.

Best case is to have Windows on one drive and Ubuntu on another drive. But if system is newer and UEFI capable hardware, you need to install both Windows and Ubuntu in the same UEFI or BIOS boot mode. 

If a new user and willing to disconnect drive, better to only have Windows drive connected installing Windows and only have Ubuntu drive connect when installing Ubuntu. And then Ubuntu drive can still be gpt whether UEFI or BIOS boot and if you have both an efi partition for UEFI boot (now or in future) and a bios_grub partition for BIOS boot you can boot either way. But you want BIOS or UEFI depending on how you install Windows.

---

### Post by pdlethbridge on 2014-11-01
I don't feel I'

m outdated
 I have a quad core

 I have an fx amd processor.quad core
 16 gigs of memory upgradable to 32 gigs I could even run an extra video card and monitor if I wanted. my parts are really new

---

### Post by pdlethbridge on 2014-11-01
so the mothboard should be okay I don't mind unplugin a drive as long as windows doesnt shut me out of ubuntu

---

### Post by oldfred on 2014-11-02
If installing on two drives you should use something else or manual install. That also gives the option to add a /home partition. Default install is just / (root) & swap with grub installed to sda.

And how you boot installer for both Windows & Ubuntu is how it installs. UEFI and BIOS are not really compatible, so once in one mode you cannot switch. Or grub menu can only offer to boot systems installed in the same boot mode as grub/Ubuntu is installed in.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

      [/URL]
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by pdlethbridge on 2014-11-03
Im  plan on  using 2 computers side by side

---

### Post by oldfred on 2014-11-04
Networking issues should be another thread. With Networking in the title. You would have to use Samba.
I thought you wanted install info?

---

### Post by pdlethbridge on 2014-11-21
My latest scem is I got a 250 gig hard driv from tiger on the real cheap so 








i will install windoz on that one and my other 250 gig will be un pluged to keep ubuntu safe and I'll stil use 2 computers with a kvm switch

---

### Post by pdlethbridge on 2014-11-23
It turnes out that the msi 970 gammer board is uefi ready as I can start in  uefi or legace mood. Also the board lets me use the mouse to make changes in the bios I couldnt do that on my other msi board.
If I want to change the boot order all I have to do is put the mouse on what I want and move it to the left. It has a bunches of cool stuff . Even with all the goodys I still can't load windoz. What I've tried is disconnect the linux HDand and use its sata cable to hook up the dvd

---

### Post by pdlethbridge on 2014-11-23
I have tryed to install windoed but only  get    to the collecting info  and give the key code.

---

### Post by pdlethbridge on 2014-11-25
the board I have is the msi 970 gaming with 16 gig ddr3 memory 


its benn runing super with 14.04 but I was having troubles installing windoz. My brother said ther was a big learning curve. I goofed loading the key code. Like a dumby I left off the first 2 sets of code as they were on the line above and I finaly figued that.
As I went through the instal it told me to remove the install media and instal the driver mediam which I assum was for the mother borad whice I couldnt find And then if that wasn't enough the system went totaly dead.

---

### Post by pdlethbridge on 2014-11-25
You can stop laughing any time now Any dumby coud have done that:lolflag:[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by pdlethbridge on 2014-12-15
After I stoped crying I ended up geting a new msi motherboard and it works super the other board and the power supplie went back and tiger was kind enough to replace both of them I'll have a new full towe cas to put everythiung into by the end of the week The raygo case worked but it was tight to work in . 
And now news about windoz I have it installed and it was very easy with the motherboard I have I disconectid 1 driv an did the windoz install first. I left it pluged in and installed ubuntu.. on the boot afte the b screen it gave me choics to boot ubuntu or its testing software and windoz was at the bottom of the list. ubuntu is the default starting os Vdery cool

---

### Post by pdlethbridge on 2014-12-16
As a new tip. If you  creat a ntfs file in you ubuntu os windose will see it as an extra drive vere cool I scaned som stuff in windoz and transferd them to ubuntu.and you can transfer fills back anc forth

---

