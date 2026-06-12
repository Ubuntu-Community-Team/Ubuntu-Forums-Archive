---
title: "Only install with security boot enable"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by sdvf on 2014-04-20
Hi, i'm trying to install ubuntu dual boot with windows 8.1. The problem is that it only install if the security boot option is enable. But after installing, when it boot i've got the message at beginnig ">>Checking media precence    >>No media presence", and 5 secounds after that it load the grub to choose what OS loggin.

Now i'm trying to install mint 16 and it's the same thing. Only install if security boot is enable.

How can i fix it?

BTW, i've got W( with UEFI....

---

### Post by sdvf on 2014-04-20
update - now not even with security boot enable. I try to boot with USB, the options open on the screen, i click to install mint and the screen goes black for ever. What's happening?

---

### Post by grahammechanical on 2014-04-20
> [COLOR=#000000]>Checking media precence >>No media presence", [/COLOR]

That might be happening because the boot system (UEFI) is set to look for an OS on a USB port before it looks for an OS on the hard disk. We need that setting if we are to install Ubuntu from a USB memory stick. The only way to find out if I am right is to change the boot priority in UEFI to the hard disk.

Have you been able to install Ubuntu on that machine? does it load correctly? Secure boot is not an issue with Ubuntu not since 12.10 was released. If Windows was installed in EFI mode then Ubuntu has to be installed in EFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As for Linux Mint that is not something that I give support for. It could be that Mint does not have a signed kernel that will let it run its installer when secure boot is on. It could be that there is something wrong with the ISO on the USB memory stick.

Regards.

---

### Post by sdvf on 2014-04-20
2nd update - This time i tried again ubuntu 14.04. Security boot disable - boot from usb and this what i've got [IMG]https://gajendrak.files.wordpress.com/2012/03/fig2grub.gif[/IMG]


Not that especific version, but something like that.

Note - i've got windows installed yesterday. Delete all partition, windows got installed from scratch. Creat 3 partition. 1 for windows, other for Data, other for Ubuntu.
What the hell is going on? Jesus...

---

### Post by sdvf on 2014-04-21
bump

---

### Post by sdvf on 2014-04-21
> **sdvf said:**
> Hi, i'm trying to install ubuntu dual boot with windows 8.1. The problem is that it only install if the security boot option is enable. But after installing, when it boot i've got the message at beginnig ">>Checking media precence >>No media presence", and 5 secounds after that it load the grub to choose what OS loggin.

Now i'm trying to install mint 16 and it's the same thing. Only install if security boot is enable.

How can i fix it?

BTW, i've got W( with UEFI....
[HR][/HR][COLOR=#000000]

[/COLOR]> **sdvf said:**
> 2nd update - This time i tried again ubuntu 14.04. Security boot disable - boot from usb and this what i've got [IMG]https://gajendrak.files.wordpress.com/2012/03/fig2grub.gif[/IMG]


Not that especific version, but something like that.

Note - i've got windows installed yesterday. Delete all partition, windows got installed from scratch. Creat 3 partition. 1 for windows, other for Data, other for Ubuntu.
What the hell is going on? Jesus...

Help me

---

### Post by WoodenWalker on 2014-04-21
Hello, I'm sorry you are having this issue. I may not be able to offer much help (especially with Mint as I am very unfamiliar with it), however I can try my best to help with an Ubuntu dual boot install. First things first, you are booting in UEFI mode with secure boot and fast boot off, correct? Or am I wrong on that?

---

### Post by monkeybrain20122 on 2014-04-21
Well MicroSoft doesn't like dual boot and it went out of its way to make it difficult, so my approach is to wipe Windows whenever I see it. :)

---

### Post by WoodenWalker on 2014-04-21
I've definitely noticed this as well, but not all users wish to completely be rid of Windows for various reasons (I personally don't use it anymore though.) Lol

---

### Post by oldfred on 2014-04-21
Are you getting grub> from live installer or after you have installed.

If you install in BIOS mode, it may have converted drive from gpt to MBR(msdos) partitioning and Windows does not correctly convert. It leaves backup gpt partition table so Linux tools get confused whether you have MBR or gpt?

If you can boot live installer.
From terminal post this:
       sudo parted /dev/sda unit s print

If you cannot boot Live installer, have you verified that download was correct?

---

### Post by oldfred on 2014-04-21
Duplicate threads merged. Do not create duplicate threads on same topic.

---

### Post by sdvf on 2014-04-21
> **d.b.king said:**
> Hello, I'm sorry you are having this issue. I may not be able to offer much help (especially with Mint as I am very unfamiliar with it), however I can try my best to help with an Ubuntu dual boot install. First things first, you are booting in UEFI mode with secure boot and fast boot off, correct? Or am I wrong on that?
That's correct. Ubuntu 14.04 is what i want. Mint was an alternative.

---

### Post by sdvf on 2014-04-21
> **oldfred said:**
> Are you getting grub> from live installer or after you have installed.

If you install in BIOS mode, it may have converted drive from gpt to MBR(msdos) partitioning and Windows does not correctly convert. It leaves backup gpt partition table so Linux tools get confused whether you have MBR or gpt?

If you can boot live installer.
From terminal post this:
       sudo parted /dev/sda unit s print

If you cannot boot Live installer, have you verified that download was correct?
I'm getting grub> befor the installation.

if i'm getting grub> how can i get in terminal? Is there any short key?

Download is fine because i tried change to UEFI off on bios and it goes directly to installation.

---

### Post by oldfred on 2014-04-21
If that is from installer, then you may not have a valid download or a full correct install into your flash drive.
You cannot get to terminal as that is after system has booted. And grub is before system has booted as it is the boot loader. Grub has its own minimal terminal which you are in with grub>. But then can only run some grub related commands.

Verify download is correct.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then try new install to flash drive or DVD.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
      
 [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
[/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

Other installers:

 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)




[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

---

### Post by sdvf on 2014-04-21
One more note for you guys.

In this week this is the 2nd time i've installed windows 8.1. At the first i've installed, then installed 14.04. No problem occurred. No grub> at the beggining, no nothing. Everything works fine, except the boot repair that was unable on 14.04 at that time. So i'll tried 13.10 and all orks fine. I've installed boot repair for dual boot but when i boot he laptop, the message "[COLOR=#000000]>Checking media precence >>No media presence" wass allways there. And it longs for 5 or more secounds. So i tried install all over again. Delete all partitions and start all over. After that you guys know what happens...grub> at beggining.[/COLOR]

---

### Post by WoodenWalker on 2014-04-21
I personally had lots of issues with getting 14.04 to run dual-boot on a W8.1 system last I tried. I finally ended up getting it to work by installing 13.10 in UEFI mode by running with secure boot set to on (Windows was getting mad when I installed without it) and fast-boot set to off. Then I ran boot-repair from the live cd. After that I just upgraded it to 14.04. Have you attempted an earlier version yet? (I'm not sure if it makes a difference, I'm just more familiar with 13.10)

---

### Post by sdvf on 2014-04-21
md5sum says that they are different...

---

### Post by WoodenWalker on 2014-04-21
I'm not sure if you mentioned this before or not, but what type of machine are you attempting to install on? Dell, HP, Asus, etc...

---

### Post by sdvf on 2014-04-21
> **d.b.king said:**
> I personally had lots of issues with getting 14.04 to run dual-boot on a W8.1 system last I tried. I finally ended up getting it to work by installing 13.10 in UEFI mode by running with secure boot set to on (Windows was getting mad when I installed without it) and fast-boot set to off. Then I ran boot-repair from the live cd. After that I just upgraded it to 14.04. Have you attempted an earlier version yet? (I'm not sure if it makes a difference, I'm just more familiar with 13.10)
Inatall windows with security boot enable, and the install ubuntu 13.10 with security boot enable too? No, i didnt try that. I'm up to anything now.
The thing is, 1 more day to install and get windows as i like.

---

### Post by sdvf on 2014-04-21
> **d.b.king said:**
> I'm not sure if you mentioned this before or not, but what type of machine are you attempting to install on? Dell, HP, Asus, etc...
Toshiba

---

### Post by WoodenWalker on 2014-04-21
Yes. If I remember correctly, Ubuntu is secure boot compatible since 12.xx (not sure which one), but 13.10 and 14.04 should both work with secure boot still set to on as well as in UEFI mode. I think I had an issue with getting a proper entry to appear in the boot loader though. It's been a long few weeks so I can't entirely recall. Also, make certain that the version of Ubuntu you are installing is the 64 bit version.

---

### Post by sdvf on 2014-04-21
> **d.b.king said:**
> Yes. If I remember correctly, Ubuntu is secure boot compatible since 12.xx (not sure which one), but 13.10 and 14.04 should both work with secure boot still set to on as well as in UEFI mode. I think I had an issue with getting a proper entry to appear in the boot loader though. It's been a long few weeks so I can't entirely recall. Also, make certain that the version of Ubuntu you are installing is the 64 bit version.
I'm getting 13.10 now. First i'l try with universal USB installer. If it not works, i'll do everything again.

Format all partitions, then install Windows, then pray to install ubuntu.

I'll save 100GB for ubuntu. Is there a proper way to install it? I mean, how i set the partitions? \boot, \home, etc?

---

### Post by WoodenWalker on 2014-04-21
I don't think there is any true, set way to install it. It kinda depends on how you wanna do it. I tend to have a 1G partition for \boot on my system, 6G for swap, 10G for \tmp, and then whatever else for \. Make sure you have Windows fast boot turned off as well. If it is on, then all other media will get skipped during boot and it will go straight to windows. This can lead to some nasty problems. It is a separate feature from "Fast boot" in the UEFI firmware settings. I'm not too familiar with W8 so I will need to look up where you can find it on your system.

Edit: Windows "fast boot" might be known as "fast startup" in the system.

---

### Post by sdvf on 2014-04-21
Yes, it's off.

I must installed ubuntu on free space or in one of that partitions?

---

### Post by WoodenWalker on 2014-04-21
I would install it in the free space, unless you want to partition out the free space for your own custom layout.

---

### Post by sdvf on 2014-04-21
Well, ubuntu 13.10 on usb bootable. Security boot disable as i installed windows 8, boot from usb, the the menu of installation it poops up. Ok, press "install ubuntu" and there's the black screen....ctrl+alt+del, change security boot to enable and here we go. All works, start instalation, after install ask me to reebot and then i'll enter "try ubuntu without install". Open terminal, install boot repair and poops a message warning me to change security boot to disable. Press continue and that's fine. Open repair boot, repair boot recomended and thats it. Reboot, and there is the same old message: "[COLOR=#000000]>Checking media precence >>No media presence" 5 secounds after that here i got the dual boot menu.

Well, lets try all over again, but this time with security boot disable when install windows.[/COLOR]

---

### Post by WoodenWalker on 2014-04-21
I'm really sorry, but I'm at a loss... Lol. I would recommend Wubi loader, but I hear it doesn't work for Win8. I'll do some research and see if I can't find a walkthrough to help.

Edit: Maybe this link can help you some? [http://ubuntuforums.org/showthread.php?t=2185869](http://ubuntuforums.org/showthread.php?t=2185869)

---

### Post by sdvf on 2014-04-21
This is amazing. To install boot repair correctly i need desable security boot. But i need security boot enable to loggin ubuntu. So? This is....i don't even get words for this...

---

### Post by WoodenWalker on 2014-04-21
Well, you don't have to have secure boot enabled to access ubuntu. Many people recommend installing it with secure boot set to off. I've just noticed some issues with getting Win8 to actually run if you change that setting though. I wish I could help more. I'm not really too familiar with these new UEFI and Win8 machines. My computer is still BIOS and I dual boot CentOS and Ubuntu 13.10 (I don't like using newest versions of things). I really hope you find a way to accomplish it. Microsoft really wanted to make it a pain to dual boot. They said "it's my way or the highway". Lol

---

### Post by sdvf on 2014-04-21
At first i've installed windows with security boot disable and then, to install ubuntu i'd got to change it to disable or i've got a black screen. Now i'v installed windows with security boot enable and i only can install ubuntu with security boot enable or i got the same blask screen after press "install ubuntu".

The solution is what i've choose right now. I'll install windows on my machine. I give up installing ubuntu here.

Thak's guys anyway

---

### Post by oldfred on 2014-04-21
Black screen is not a boot issue, but  a video driver issue which is common whether BIOS or UEFI.

What video card/processor?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

