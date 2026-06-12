---
title: "how to install this driver"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by ankabiatch on 2014-11-09
Hi i just installed Ubuntu 14.04 LTS. Im connected with cable, for now but I want to get wireless with my adaptor (DWA-131 Wireless USB rev.B) to work. It doesn't come up in extra program software  ([SIZE=1]Extra stuurprogramma's in dutch[/SIZE]) so I went to the site ([http://www.dlink.com/uk/en/support/product/dwa-131-wireless-n-nano-usb-adapter?revision=deu_revb](http://www.dlink.com/uk/en/support/product/dwa-131-wireless-n-nano-usb-adapter?revision=deu_revb)) and downloaded DWA-131 Linux driver. Now I have this; *DWA-131_rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730.tar.gz* :? I have unpacked it searched some commands but I don't get it to work could someone guide me trough this?

---

### Post by ian-weisser on 2014-11-09
Well, according to the search box on this forum, 'DWA-131' install questions have appeared, and been solved, several times before.
Like [this one]("http://ubuntuforums.org/showthread.php?t=2200493").
Might some of those previous threads help you through the process? The process really hasn't changed.

If those threads are too confusing, we are happy to help you through the process.

---

### Post by ankabiatch on 2014-11-09
I've tried like evey thread and this stil doesn't work ](*,)
WTF how am I going to this, this is stupid am really considdering deleting ubuntu :/
Pls help

---

### Post by buzzingrobot on 2014-11-09
The file you've downloaded is a compressed archive that does not contain a driver.  It contains source code for a driver.  To use it, you would first need to compile it successfully and install it successfully.  How to do *that* is not a small matter, and likely a topic for another thread, or three.  If you did that, the tools that managed software updates on your system would not be aware of its existence.  You would be responsible for acquiring and installing updates, if any, on your own.

Before going that route, search for a driver that has already been compiled and packaged for a system like Ubuntu so you can install it easily and correctly. You want a file that ends with '.deb'.

---

### Post by ankabiatch on 2014-11-10
I have compiled this file with alien to a deb file but it said it was badly compresses when i tried to istall. still doesn't work.
Ive tried this; [http://samiux.blogspot.be/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.be/2010/05/howto-realtek-8192su-usb-dongle.html) but my Makefile is different. Why can't i just find a proper tutorial?!? :(

---

### Post by ankabiatch on 2014-11-10
> **buzzingrobot said:**
> The file you've downloaded is a compressed archive that does not contain a driver.  It contains source code for a driver.  To use it, you would first need to compile it successfully and install it successfully.  How to do *that* is not a small matter, and likely a topic for another thread, or three.  If you did that, the tools that managed software updates on your system would not be aware of its existence.  You would be responsible for acquiring and installing updates, if any, on your own.

Before going that route, search for a driver that has already been compiled and packaged for a system like Ubuntu so you can install it easily and correctly. You want a file that ends with '.deb'.

Can't seem to find such file

---

### Post by ankabiatch on 2014-11-10
Found this it seems to work for a lot of people exept for me;

"@bmjbmj - thanks for the guide, but now that i have installed the driver  i want to clarify some details for your instructions so that others do  not run into the problems i had:
1. download the driver (bmjbmj's link didn't work, but you can get it at the bottom of this page: [http://www.realtek.com.tw/downloads/...true#RTL8192SU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU")
2. cd ~/Downloads/
3. unzip [the name of the driver you downloaded, versions vary]
4. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/
5. now open nautilus and navigate to the above directory, copy the name of the tar.gz archive in the driver folder
6. tar -xvzf [the tar.gz archive name that you copied]
7. cd ~/Downloads/[the name of the driver you downloaded, versions  vary]/driver/[the name of the archive you just decompressed, without  "tar.gz" at the end of the name]/
8. remember, if the files and folders get confusing, look in nautilus to find the names you need.
9. Build the driver using these four commands in order, each may take a couple minutes, be patient:
   a. sudo su
   b. make clean
   c. make 
   d. make install"

STILL DOESN WORK I GET ERROR!
"kan status van &#8216;8712u.ko&#8217; niet opvragen: Bestand of map bestaat niet            make: *** [install] Fout 1"  -   
Transtalion; cannot request status "8712u.ko": File or folder doesn't exist         make: *** [install] error 1

WHY WHY WHY WHY


After step "a."  this comes up;
r*oot@Anka-FL289AA-B14-SR5612BE:/home/anka/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405#*  -_HERE I CAN TYPE COMMANDS AGAIN_-

Should I wait until the normal "*~/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$*"  comes up or should I fill in the make clean command?

I do this, then fill in next command (again, not *"~/Downloads/rtl8......$"* line). The make command I get this error.
"cc1: some warnings being treated as errors
make[2]: *** [/home/anka/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Fout 1
make[1]: *** [_module_/home/anka/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Fout 2
make[1]: Map '/usr/src/linux-headers-3.13.0-32-generic' wordt verlaten
make: *** [modules] Fout 2
root@Anka-FL289AA-B14-SR5612BE:/home/anka/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405#"

---

### Post by buzzingrobot on 2014-11-10
> **ankabiatch said:**
> 
"kan status van ‘8712u.ko’ niet opvragen: Bestand of map bestaat niet            make: *** [install] Fout 1"  -   
Transtalion; cannot request status "8712u.ko": File or folder doesn't exist         make: *** [install] error 1


It's telling you that it cannot locate that file, which should have been created during the compilation but appears not to have been created. Any number of things may cause that, including an error in the code, or, perhaps, that the source code is no longer compatible with current Linux kernel version.

> After step "a."  this comes up;
r*oot@Anka-FL289AA-B14-SR5612BE:/home/anka/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405#*  -_HERE I CAN TYPE COMMANDS AGAIN_-

Should I wait until the normal "*~/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405$*"  comes up or should I fill in the make clean command?


Run the make command.

Using "sudo..." temporarily allows you to execute commands as the root user, which is necessary because the compilation and install procedure needs to create and place files in locations in the file system that ordinary users do not have permission to alter. That rather lengthy line beginning with "root@..." is the system's way of telling you that you have successfully made that switch. Once the command finishes, type "exit" to return to your normal status.

Determining the reasons for the other errors you list would require someone with developer skills assessing the source code and the errors.

Tar archives of source code are intended for use by developers, not ordinary users, and especially not new ordinary users. They're a tradtional way of compressing multiple source code files into a single archive for the convenience of developers.  They are not intended to be used for software installation by ordinary users. You really need to find this driver already compiled and packaged for installation on the version of Ubuntu you are using.  If it can't be found, it may be that it cannot be successfully compiled on current systems, which would require the vendor to release an update.

---

