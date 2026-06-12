---
title: "Upgrade/change Ubuntu 14.04 to Ubuntu 16.01 problems"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by rlr1925 on 2016-08-20
Hello Ubuntu's guru. I am new to forum and to Ubuntu. I have laptop with Ubuntu 14 and tried to upgrade to version 16 and could not I think because of low internet stream. (Something happened to internet connection on this laptop, as on others it is fine)
Laptop is HP Pavilion g6, with the only one Ubuntu 14.04 OS. I have already prepared USB drive with Ubuntu 16, went through download Ubuntu and Unetbootin-windows-625 on the machine with Windows 10 which has good internet. 
As I understood the next step is to access BIOS and make boot USB priority to start. I could not find BIOS on my machine. 
Can anybody please help!   How to find BIOS - once I managed to click on ESC key and open window with 3 lines, I do not remember them already but there was not any to open window with BIOS to make priority for USB drive

---

### Post by oldfred on 2016-08-20
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

      
 Some HP will not boot a flash drive that is gpt partitioned.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)

If flash drive not correctly configured as bootable, it will not show in UEFI/BIOS.
       
 Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
           
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2016-08-20
You need to press a certain key after you see the motherboard splash screen and before the Grub boot menu appears. Immediately after the motherboard splash screen there should be another screen with some information about the computer. The information on that second screen should include the key to press to enter the BIOS/UEFI settings utility. Do you not see any information about what key to press?

Do you have a motherboard user guide? That will give the information you need. Perhaps you can go to the manufacturer's web site and download a user guide.

Regards

---

### Post by rlr1925 on 2016-08-21
Thank you! I managed to get to BIOS menu during restart computer and change the order to boot from CD/DVD, there was not any other options. USB was connected and screen got black and still black after an almost hour running. I will leave it running for the night, but have a feeling that I will not achieve anything.

---

### Post by rlr1925 on 2016-08-21
Could somebody explane the difference between Ubuntu for desktop and for server? I created disk for desktop, looks like I should do it for server if I want to run OS from laptop but not from USB.

---

### Post by oldfred on 2016-08-21
Server has no gui.
Desktop has Unity gui, but other flavors have the various other Linux gui. And each flavor includes in distribution different appliations, but everything is in same repository.

What video card/chip?

Did you click on some of the HP specific issue links above?

---

### Post by mastablasta on 2016-08-22
> **rlr1925 said:**
> Thank you! I managed to get to BIOS menu during restart computer and change the order to boot from CD/DVD, there was not any other options. USB was connected and screen got black and still black after an almost hour running. I will leave it running for the night, but have a feeling that I will not achieve anything.

1. it can be named differently than USB drive. 
2 it is possible to load the OS on DVD or to put onl ythe boot manager on CD (such as for example PLOP) that would then allow booting from USB.

i believe g6 have AMD GPu if i am not mistaking. they could even be hybrids. plenty AMD gpus lost their support (= it was switched ot opensoruce driver) with 16.04. we would need to know what GPU(s) you have. 

you might be able to boot using nomodeset:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


to get the informaiton on hardware use this command and copy paste the result here using the code tags (# icon in "Go Advanced" answer):
```
lshw -sanitize
```

> **rlr1925 said:**
> Could somebody explane the difference between Ubuntu for desktop and for server? I created disk for desktop, looks like I should do it for server if I want to run OS from laptop but not from USB.

server is for servers (e.g. web servers, file servers, DNS servers, routers...) which are usually headless (no monitor) so the image doesn't contain any graphical user environment. it has only command line. since servers usually do not have any powerfull graphics card, the install on server version is text mode only. you do not want server or net install (mini.iso) unless you are familiar with the OS. suggest you stay with desktop at least for now. if you are interested how server (or mini.iso/barebones) install and end result looks like i sugest you try it in virtualbox,. here is a how to guide with pics and all: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by rlr1925 on 2016-08-22
> **oldfred said:**
> HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

      
 Some HP will not boot a flash drive that is gpt partitioned.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)

If flash drive not correctly configured as bootable, it will not show in UEFI/BIOS.
       
 Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
           
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

**oldfred, **thank you!
1 and 2nd link I went through and found how to get to start menu. Start menu has only 2 option - from HD or CD/DVD also, there is no CD driver.
3rd link does not work
4th - I read, but I am just a user and not computer guru, it is very dark for me UEFI and BIOS.
I created USB - first downloaded on other laptop Unetbooting-windows625 then Ubuntu 16.04, after that opened Unetbooting and created disc on USB. Is it correct? 
Then I started laptop with Ubuntu, pressed Esc key, got window with start up option, changed priority to boot from CD/DVD and got black screen. But laptop worked hard, I left it to run in the night. In the morning it was switched off and started in a usual manner.
Is it possible that downloads from USB failed because Ubuntu has not been updated? I hag several attempts to download updates and because of poor internet connection they all failed. Now I connected through wire and process is going a little a bit faster. But file libllvm3.8v4 failed already and there are so many more files to download and install. 
****

---

### Post by rlr1925 on 2016-08-22
[**[COLOR=#DD4814][B]mastablasta**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=964486") Thank you. I will try to create CD. Or just wait for updates to be installed and the try again to upgrade to 16.04 on-line via wired internet connection.

---

### Post by rlr1925 on 2016-08-22
[**[COLOR=#DD4814][B]mastablasta**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=964486") Thank you. I will try to create CD. Or just wait for updates to be installed and the try again to upgrade to 16.04 on-line via wired internet connection.

---

### Post by rlr1925 on 2016-08-22
Thank you for your help!
Good news and bad news. I managed to upgrade to version 16.04, looks like there is problem with Wi-Fi connection and it is still there in the new version. During upgrade comp was connected via wired Ethernet. And while it was wired all the internet pages opened very fast. Now with Wi-Fi connection can not open sites in Mozilla or Google.

---

### Post by rlr1925 on 2016-08-22
What I want to say - everybody says that it is very easy to install Ubuntu, but it is not true. May be it is easy to install, but before installation you need to prepare USB (this I already done, but did not use, so do not know, whether it works or not)  or even more difficult - to create CD and to do this you need to compare files.  For me it is not straight forward and easy.

---

### Post by mastablasta on 2016-08-23
> **rlr1925 said:**
> What I want to say - everybody says that it is very easy to install Ubuntu, but it is not true. May be it is easy to install, but before installation you need to prepare USB (this I already done, but did not use, so do not know, whether it works or not)  or even more difficult - to create CD and to do this you need to compare files.  For me it is not straight forward and easy.

1. download (if you use torrent download there is no need to compare any files)
2. burn the ISO file to DVD (easy to do)
3. boot from DVD andinstall.

it's the same thing for any OS. even Windows. it is used a lot when .iso is needed. 

another option is
1. download
2. use USB creating software and create the install USB
3. boot from USB and install.

and finally there are the preinstalled options or you can buy the USB: [SIZE=2]https://shop.canonical.com/product_info.php?products_id=1206
[/SIZE]

---

### Post by rlr1925 on 2016-11-05
Thank you everybody for help. I managed to reinstall Ubuntu 16.10, works very nicely. 

But couple things need to be corrected:
1. How to log-in without password. In settings for account users "Automatic login" is ON.
In Security and Privacy I unticked "Require password" after Waking and Returning. But every time when I switch on machine it requires password for keyring. 

2. On switch on I get message - the system can not recognize your e-mail. Do not remember exact words.

Tried to google but could not find for last Ubuntu.

---

### Post by oldfred on 2016-11-06
Best to ask new questions with new forum post with title that pertains to issue.

For password at log in. 
Go to System Settings, User Accounts (lower right corner), and unlock with your password to allow changes.

---

