---
title: "HOWTO: Lucent Modem in Edgy Eft"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by GCR on 2006-11-01
Hey!

I am finally online with the latest and greatest from Ubuntu. After a week or so of trying to get online I managed to successfully find a proper way to compile and set the modules of my Lucent winmodem. If you've been trying to get the modem to work then this instructions *may* work. However, bear in mind that I am constantly learning new things and I'm no expert when it comes to Linux, though I have my fair amount of time working with it. So, do this at yor own risk, but if you do, hopefully it'll work.

NOTE TO MODS: I decided to create this since besides me there are several others having this same problem so I went ahead and made this HOWTO in order to make things easier for everyone. If there's any problem then please contact me and I'll make the necessary arrangements.

**Step 1 - Download the proper driver**

At first I tried with the *ltmodem* driver. But to no success got it to work. The cause was apparently some parameters that changed from newer 2.6 kernels and it failed to compile. Gentoo devs released a patch(I think) but even when I applied it I was not able to compile it.

so, here's the exact same driver I used:
[http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061005.tar.gz]("http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061005.tar.gz")

Save it, and extract it.

**Step 2 - Installation of the driver**

After extracting the driver, you have to issue a couple of command in order to compile the modules. ***cd to the extraced directory***. Then type the following:

```
sudo make all
```

Watch as the compilation flies by. If no errors are reported go on. If there is some error, make sure you have *build-essential* and *linux-headers* installed. I did this on a clean Edgy installation, so I used the packages that were included on the installation disk. Im not sure is updated ones will work.

If everything is OK, then time to install the drivers. In the terminal window, type:

```
sudo make install
```

Watch everything go by. If there were no errors reported, then the driver should be already installed. Now just a few more steps and you could be successfully using your Lucent modem in Edgy.

**Step 3 - Loading the module**

Simply type:
```
sudo modprobe martian_drv
```
in a terminal to load the *martian_drv*.

Just to make sure it loaded issue:
```
lsmod | grep martian
```
If everythings fine, keep goin' it's almost there.

**Step 4 - Additional Steps**

A couple more things are necessary. First, type the following and press enter no a terminal:
```
sudo martian_helper --daemon
```

Then make a link to the device by typing:
```
sudo ln -s /dev/ttySM0 /dev/modem
```
Now your */dev/modem* links to the modem itself.

**Step 5 - WVDIAL**

Configure wvdial by issuing:
```
sudo wvdialconf
```
This will create a *wvdial.conf* in your */etc/* directory.

Then fire up a nano and edit */etc/wvdial.conf*
```
sudo nano -w /etc/wvdial.conf
```
And change accordingly.

Below is my wvdial.conf so that you can use it as reference:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = *isp phone number*
New PPPD = yes
Stupid Mode = yes
Modem = /dev/ttySM0
Username = *username*
Password = *password*
Baud = 460800
```


NOTE:
This is my first HOWTO ever, so I am no expert in the field but I hope this can help many of you that, like me, are trying to configure your Lucent 56k modem in Edgy. If you have any questions, or suggestions feel free to reply or contact me whichever way and I'll do my best to help!

Good Luck =)

---

### Post by Matchless on 2006-11-04
Do you know where I can download the patch you were refering to. I will be installing soon and just want all at hand if possible.
Thanks

---

### Post by uber noob on 2006-11-04
Thanks for the great how-to! I only wish I would have found it earlier!

I did, however, get an error while doing "make all" but I carried on, and everything still worked out perfectly!

Thanks again!

P.S. I can't wait until my DSL modem arrives...How did we ever survive without broadband??

---

### Post by Turin Turambar on 2006-11-05
> **Matchless said:**
> Do you know where I can download the patch you were refering to. I will be installing soon and just want all at hand if possible.
Thanks

Here it is:

```

diff -Nru ltmodem-2.6-alk-8.orig/lt_modem.c ltmodem-2.6-alk-8/lt_modem.c
--- ltmodem-2.6-alk-8.orig/lt_modem.c    2005-12-12 03:18:55.000000000 +0200
+++ ltmodem-2.6-alk-8/lt_modem.c    2006-04-19 21:43:32.142640500 +0300
@@ -120,14 +120,14 @@
 static int vendor_id = 0;
 static int device_id = 0;
 
-MODULE_PARM(vendor_id, "i");
+module_param(vendor_id, int, 0);
 MODULE_PARM_DESC(vendor_id, "Vendor ID of the Lucent Modem e.g. vendor_id=0x11c1");
-MODULE_PARM(device_id, "i");
+module_param(device_id, int, 0);
 MODULE_PARM_DESC(device_id, "Device ID of the Lucent Modem e.g. device_id=0x0440");
 
 static int Forced[4] = {-1,-1,-1,0};
 
-MODULE_PARM(Forced, "4i");
+module_param_array(Forced, int, NULL, 0);
 MODULE_PARM_DESC(Forced, "Forced Irq,BaseAddress,ComAddress[,NoDetect] of the Lucent Modem e.g. Forced=3,0x130,0x2f8");
 
 static
diff -Nru ltmodem-2.6-alk-8.orig/serial.c ltmodem-2.6-alk-8/serial.c
--- ltmodem-2.6-alk-8.orig/serial.c    2005-12-12 03:07:17.000000000 +0200
+++ ltmodem-2.6-alk-8/serial.c    2006-09-21 21:53:08.055717500 +0300
@@ -732,7 +732,9 @@
     .devfs_name        = "tts/LT",
     .dev_name        = "ttyLT",
 #else
+#    if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,18))
     .devfs_name        = "tts/LTM",
+#    endif
     .dev_name        = "ttyLTM",
 #endif
     .major            = 62, 

```

However, to make things easier for everyone, I attached the driver with patched files. You just need to compile it and it will hopefully work! :)

---

### Post by GCR on 2006-11-06
Thanks for the patches!

I'll try them on to see if they work for me(Im almost certain that I did not patched them correctly lol)

---

### Post by dlanor78 on 2006-11-08
This does indeed get the modem working, but how do you get it to work after rebooting automatically?  I keep having to redo the ln -s part and the martian_helper --daemon part too.

---

### Post by GCR on 2006-11-09
I think thats a downside from the martian driver. But in my case I dont have to link again. I just type:

```
martian_drv --daemon
```

OR, you could try the prepatched drivers of LTModem that someone posted here :)

---

### Post by marcozs on 2006-11-11
> **dlanor78 said:**
> This does indeed get the modem working, but how do you get it to work after rebooting automatically?  I keep having to redo the ln -s part and the martian_helper --daemon part too.

one solution could be:
1) insert martian_drv in /etc/modules (where there are the modules to be started at boot)
2) insert martian_helper --daemon in /etc/rc.local (before exit 0) to autostart at boot that as well

has anyone got a better solution? 

BTW I can get connected only running wvdial from root cause it seems that only root has permissions to /dev/ttySM0 ... does anyone know how to make it work for the normal user as well?

Marco

---

### Post by Turin Turambar on 2006-11-12
Well you can try to fix permissions and links by a udev rule.

Go to /etc/udev/rules.d/

and make a file, called martian.rules

then add this text:

```

KERNEL="ttySM[0-9]", MODE="0660", GROUP="dialout", SYMLINK="modem"

```

Hope it works. :)

---

### Post by mirkov on 2006-11-23
Thx for the Howto. I had one problem with it, though.

On a clean edgy install, I got this error from make command:
sh tweakcore.sh marscore.o tweakcore.sh: 1: Syntax error: "(" unexpected

sh was a symlink to dash, which was the problem. After symlinking sh to bash, compile was successful.
sudo rm /bin/sh && sudo ln -s /bin/bash /bin/sh

---

### Post by [eXr] on 2006-11-28
[SIZE="4"]**New version martian-full-20061110**[/SIZE] ([link]("http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061110.tar.gz"))

Module: [COLOR="Sienna"]martian_dev[/COLOR]
Daemon: [COLOR="Sienna"]martian_modem --daemon[/COLOR]

**Problem with Dash (Edgy Eft) and the *make all***
I've a better solution than to change the symlink to sh. Just edit the file [COLOR="Sienna"]*./martian/modem/Makefile*[/COLOR] and in line 55 replace [COLOR="Sienna"]*sh*[/COLOR] with [COLOR="Sienna"]*bash*[/COLOR].

**Other comments**
The udev rule to symlink /dev/ttySM[0-9]* to /dev/modem can be added to the [COLOR="Sienna"]/etc/udev/rules.d/60-symlinks.rules[/COLOR] instead of a new file.

PD: dash = problems + problems + problems

---

### Post by blasedeviant on 2006-12-04
I followed the instructions, but get errors.

Does anyone know how to compile this for amd-64? I got an error saying something about linking i386 files to amd-64...

---

### Post by Bomper on 2006-12-21
New version [[COLOR="Orange"]martian-full-20061203.tar.gz[/COLOR]]("http://www.barrelsoutofbond.org/downloads/martian/martian-full-20061203.tar.gz")

NEWS:
[COLOR="Red"]New options for TTY mode/group/owner, country. 
Further automation scripts development.[/COLOR]

1.- $ sudo modprobe -v martian_dev

2.- $ sudo martian_modem --daemon --user=root --group=dialout --mode=0660

        $ ls -lisa /dev/ttySM0 
	9184 0 lrwxrwxrwx 1 root root 10 2006-12-12 22:35 /dev/ttySM0 -> /dev/pts/1

	$ ls -lisa /dev/pts/1
	3 0 crw-rw---- 1 root dialout 136, 1 2006-12-12 22:35 /dev/pts/1

 INFO:  [[COLOR="Orange"]http://martian.barrelsoutofbond.org/[/COLOR]]("http://martian.barrelsoutofbond.org/")

---

### Post by renatosilva on 2007-01-13
I'm desperated. I've got an error:

After I run wvdial, he stands on "ATVT<phone number>" (ATVT or something like...), then after few seconds he says: "No carrier. Trying again...", and do that in a infinite loop, while my modem make a strange sound (bleck, bleck, bleck...).

I've tried "Carrier Check = no" in /etc/wvdial.conf but doesn't work. 

Help me please!!!!!

---

### Post by renatosilva on 2007-01-14
I've got!!!!!!!!

I used a newer version of the driver and it works now!

blasedeviant: "martian_modem is a 32-bit application. It can be built on x86_64 the way prescribed, but you need 32-bit development environment for that. Second option is to use binary built on i386. ", from INSTALL file.

---

### Post by blastus on 2007-01-26
Excellent HOWTO GCR! 

I haven't been active on the forums for a very long time so I apologize to the other members for not being around to provide help with the HOWTO I created for Dapper. I'm glad this HOWTO exists because I don't have dialup anymore. :( I do get five hours free dialup a month but when you get high speed it's like you totally forget about dialup :)

---

