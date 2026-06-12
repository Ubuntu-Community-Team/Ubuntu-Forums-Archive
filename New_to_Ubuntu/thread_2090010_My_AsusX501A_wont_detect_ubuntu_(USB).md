---
title: "My AsusX501A wont detect ubuntu (USB)"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by Nooreazy on 2012-11-30
WEll guys, I'm seriously getting tired of my new laptop. As soon as i got it, the thing was preloaded with windows 8 and all these subtle programs which was driving me MAD!(They got rid of the start button, can you believe that?!). So i did what i thought would be a logical choice which was to try and install the latest ubuntu. 

So I downloaded 12.10 and put the thing on my USB (Laptop has no CD Drive) with  Pen Drive Linux's USB Installer. I used this guide ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)). I went to my bios after that and I just disabled windows boot loader so i can just use the usb(It said UIEF something like that) to boot and i hit enter then saved as i rebooted i was just sent back to the bios menu again!. 


I tried to do this method with 12.04 and i even tried to install through wubi which worked some what, It gave me a selection to choose ubuntu(the selection menu looked very windows 8ish) at the start up but my computer just restarts and im forced to choose windows 8. 

some one any one please help, im seriously getting frustrated with windows 8 thx.

Edit: This is my laptop [http://www.newegg.com/Product/Product.aspx?Item=N82E16834230600&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA](http://www.newegg.com/Product/Product.aspx?Item=N82E16834230600&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA)

---

### Post by gnusci on 2012-11-30
I think you have to set in BIOS that you are using a USB-Drive or something like that.

[http://pcsupport.about.com/od/tipstricks/ht/bootusbflash.htm](http://pcsupport.about.com/od/tipstricks/ht/bootusbflash.htm)

---

### Post by Nooreazy on 2012-11-30
> **gnusci said:**
> I think you have to set in BIOS that you are using a USB-Drive or something like that.

[http://pcsupport.about.com/od/tipstricks/ht/bootusbflash.htm](http://pcsupport.about.com/od/tipstricks/ht/bootusbflash.htm)

I tried to set USB to boot as the first option, that didn't work. Then I entirely disabled the option to boot windows and left my usb in the list, that too didn't work i was just sent back to the bios.

---

### Post by squakie on 2012-12-01
Rather than trying to select as a boot option, check your BIOS for the boot device settings.  In some BIOS's you selected the device you want to boot by moving it to the top of the list of boot devices - usually by the up arrow key.  So you would want USB storage as the top entry.  If this device isn't at the top of the list it won't look there first to boot.  Save the changes to your BIOS an your system will reboot.  If that doesn't get you booted, then perhaps the USB image was created incorrectly.  If you simply copied the files to the USB it won't be correct and boot.  You need to use a tool such as unetbootin (available to run in Windows or Linux) to create the USB image for you.

If neither of those work, then see if your PC has a function key you can push as the system is initializing that will bring up a boot device menu, then select USB storage there.

If that all fails, then we need to look deeper.

---

### Post by Myglaren on 2012-12-01
I am having the same problem with my recently purchases Asus laptop, tried many variations but the USB dongle is not recognised when the machine boots.
It was bought with W7 loaded with the express intention of replacing that with QQ.

I can't create a boot CD either - a newly purchased Zoostorm desktop (no OS) now running QQ will tot write to DVD - says device already mounted?

My old Toshiba laptop (using that now) won't write to DVD either - can't see it in Startup Disc Creator, it won't recognise a bootable USB dongle either (one of the reasons for buying the Asus)
Had to install 11.04 then upgrade to 12.10 as it is getting a bit flaky and hoped a reinstall would cure it an I would be able to create a startup disc for the Asus machine - bitter disappointment ensued.

---

### Post by jbalazs on 2012-12-01
First turn your computer off, insert the usb stick, turn your computer on
When you get the first page of the ASUS press ESC button several time
You will get a menu where you can select your usb stick

---

### Post by NikTh on 2012-12-01
> **Nooreazy said:**
> 
So I downloaded 12.10 and put the thing on my USB (Laptop has no CD Drive) with  Pen Drive Linux's USB Installer. I used this guide ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)). I went to my bios after that and I just disabled windows boot loader so i can just use the usb(**It said UIEF something like that**) to boot and i hit enter then saved as i rebooted i was just sent back to the bios menu again!. 

Hi, 
as you said UEFI and Windows 8 , I assume (but I'm not sure) the secure boot is enabled. 

Try to download **Ubuntu 12.10 64 bit** , as is the version of Ubuntu that working out of the box with most systems with secure boot On. 

Also you can try live-DVD  instead of USB ( I don't know if the usb-creation program is responsible for the unbootable Ubuntu) of **course you have to use external DVD**. 
Do not forget to burn the DVD to lowest speed (2x , 4x).

You can try another program like [**Unetbootin**](http://unetbootin.sourceforge.net/) to create the live-USB.

Thanks

---

### Post by squakie on 2012-12-01
> **NikTh said:**
> Hi, 
as you said UEFI and Windows 8 , I assume (but I'm not sure) the secure boot is enabled. 

Try to download **Ubuntu 12.10 64 bit** , as is the version of Ubuntu that working out of the box with most systems with secure boot On. 

Also you can try live-DVD  instead of USB ( I don't know if the usb-creation program is responsible for the unbootable Ubuntu) of **course you have to use external DVD**. 
Do not forget to burn the DVD to lowest speed (2x , 4x).

You can try another program like [**Unetbootin**]("http://unetbootin.sourceforge.net/") to create the live-USB.

Thanks

I'm not the OP, but I wanted to thank you.  If I ever (and that's a BIG if) decide to replace Windows 7 with Windows 8 on my dual-boot desktop, I've got to remember that.  I had read several months ago about this secure-boot thing but I didn't realize it had been implemented yet.

---

### Post by Nooreazy on 2012-12-02
> **squakie said:**
> Rather than trying to select as a boot option, check your BIOS for the boot device settings.  In some BIOS's you selected the device you want to boot by moving it to the top of the list of boot devices - usually by the up arrow key.  So you would want USB storage as the top entry.  If this device isn't at the top of the list it won't look there first to boot.  Save the changes to your BIOS an your system will reboot.  If that doesn't get you booted, then perhaps the USB image was created incorrectly.  If you simply copied the files to the USB it won't be correct and boot.  You need to use a tool such as unetbootin (available to run in Windows or Linux) to create the USB image for you.

If neither of those work, then see if your PC has a function key you can push as the system is initializing that will bring up a boot device menu, then select USB storage there.

If that all fails, then we need to look deeper.

I think we need to look deeper indeed. I have used both "universal USB installer" And "unetbootin"(the lastest versions) and I've attempted numerous times to make a proper Ubuntu Live USB(I didnt drag and drop the .iso) 

The .iso's I've used at
ubuntu-12.04.1-desktop-amd64
ubuntu-12.04-desktop-i386
ubuntu-12.10-desktop-i386

These are all downloaded from the ubuntu website and I've tried every iso atleast twice. 

Furthermore I tried to use wubi installer and that went somewhat sucessful. After I choose to reboot the computer using wubi installer I could click on ubuntu on the windows boot loader but as soon as i clicked itmy computer would reboot and give me an error message (its alot of jargon to me) And I am forced to choose windows 8 again.

Also I've messed with bios a bit,I set my USB to boot as option #1 and that didnt work i was sent back again to windows 8. The I tried to disable secure boot onmy bios and even disabling windows boot manager (HDD) from the boot menu. That too was unsuccessful. I am literally stuck. BTW if any one's wondering yes i did save the bios settings and had my computer reboot.

---

### Post by Nooreazy on 2012-12-02
> **NikTh said:**
> Hi, 
as you said UEFI and Windows 8 , I assume (but I'm not sure) the secure boot is enabled. 

Try to download **Ubuntu 12.10 64 bit** , as is the version of Ubuntu that working out of the box with most systems with secure boot On. 

Also you can try live-DVD  instead of USB ( I don't know if the usb-creation program is responsible for the unbootable Ubuntu) of **course you have to use external DVD**. 
Do not forget to burn the DVD to lowest speed (2x , 4x).

You can try another program like [**Unetbootin**](http://unetbootin.sourceforge.net/) to create the live-USB.

Thanks
unetbootin doesnt have Ubuntu 12.10 64 bit as an option :(. Also i disabled secure boot in the bios and my ubuntu still wont boot :(.

---

### Post by squakie on 2012-12-02
You can download the 64-bit version from ubuntu, then point the process to the ISO.

---

### Post by NikTh on 2012-12-03
> **Nooreazy said:**
> unetbootin doesnt have Ubuntu 12.10 64 bit as an option :( This is not necessary. Download Ubuntu 12.10 64bit from [here]("http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64.iso") and create a bootable USB as usual , with unetbootin.
> **Nooreazy said:**
> Also i disabled secure boot in the bios and my ubuntu still wont boot :(.

Well , the truth is that I haven't secure boot system and I cannot guide you through the whole progress , but try the 64bit 12.10 version. I have a hope that will work :)

---

### Post by Myglaren on 2012-12-04
> **Myglaren said:**
> I am having the same problem with my recently purchases Asus laptop, tried many variations but the USB dongle is not recognised when the machine boots.
It was bought with W7 loaded with the express intention of replacing that with QQ.

I can't create a boot CD either - a newly purchased Zoostorm desktop (no OS) now running QQ will tot write to DVD - says device already mounted?

My old Toshiba laptop (using that now) won't write to DVD either - can't see it in Startup Disc Creator, it won't recognise a bootable USB dongle either (one of the reasons for buying the Asus)
Had to install 11.04 then upgrade to 12.10 as it is getting a bit flaky and hoped a reinstall would cure it an I would be able to create a startup disc for the Asus machine - bitter disappointment ensued.

QQ installed now - it was not a secure boot machine after all but when the BIOS was set to boot either from the DVD or USB, it forgot when restarted.
Pressing "Esc" while the splash screen was on gave various boot options which worked perfectly and QQ is installed and working now.

The write to CD/DVD problem remains but is a recognised bug, apparently.

---

### Post by squakie on 2012-12-05
Glad you found that and that it worked - that's what I was pointing at in my first post (#4).

---

