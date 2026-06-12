---
title: "Help with driver &amp; makefile?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by retropsp on 2008-07-15
Hey everyone I don't know if this is in the right section or not but I the help with making and installing a driver for a wifi usb adapter. The adapters chipset is Winbond w89c35dg I found someone that got it to work but the website was in italian so I translated it using google to find the linux driver then downloaded it but I don't know how to compile it or to install it.
be nice I am new to Ubuntu and to Linux.
This is what the read me says 

(To build driver
(     In your driver path, Driver/Linux/2.4/, run
(     # make
(
(      then the driver, w35und.o, will be created.
(
(	Notes:
(		Makefile.24: Makefile for kernel 2.4 series
(		Makefile.26: Makefile for kernel 2.6 series
(
(1. Installation
(
(	# insmod w35und.o
(	
(	Notes:
(	After your inserted this module to system, your can use special (commands
(	of user guider to connect your desired AP or IBSS station. After (connected,
( 	you can use this command to assign an IP address and up it.
(
(	# ifconfig wlan0 xxx.xxx.xxx.xxx. up 
 ----------------------------------------------
First do I have to have it in a specific folder?
Second What do I click on? 
Well just tell me how to do it :(:confused:
this is a screenshot of the folders th at came in the download
[http://i248.photobucket.com/albums/gg181/retropsp/folders.png](http://i248.photobucket.com/albums/gg181/retropsp/folders.png)
Thank you for your help!:confused:

---

### Post by Bachstelze on 2008-07-15
You have to click on Applications, Acessories, Terminal. ;) Installing a driver can **not** be done from the GUI. Also, could you please tell us the model of your wifi adapter, and provide a link to the driver? It seems pretty old, so it might not work with your Ubuntu.

---

### Post by houbysoft.xf.cz on 2008-07-15
Right click anywhere in the folder where your downloaded driver files are, and then click on "open terminal here". Then type "make" without the quotes of course, and then hit enter. Then post the result.

EDIT: Since you're new to linux, I suppose you never compiled anything -> you don't have the build-essential package. To correct that, open (again :)) the terminal, and type sudo apt-get install build-essential. It will ask for your password, just enter it and hit enter. Then try to type make again if it ouputed errors before.

---

### Post by retropsp on 2008-07-15
> **houbysoft.xf.cz said:**
> Right click anywhere in the folder where your downloaded driver files are, and then click on "open terminal here". Then type "make" without the quotes of course, and then hit enter. Then post the result.

EDIT: Since you're new to linux, I suppose you never compiled anything -> you don't have the build-essential package. To correct that, open (again :)) the terminal, and type sudo apt-get install build-essential. It will ask for your password, just enter it and hit enter. Then try to type make again if it ouputed errors before.

Thanks:) I will try it.

---

### Post by houbysoft.xf.cz on 2008-07-15
> **retropsp said:**
> Thanks:) I will try it.

:) btw, after that, a file called w35und.o should be created in the driver's directory if all worked. (I think this will not happen, unless you're lucky).

But anyway, if it really works and the file is created, you should open the terminal again :) and type in "sudo insmod w35und.o".

---

### Post by retropsp on 2008-07-15
> **houbysoft.xf.cz said:**
> :) btw, after that, a file called w35und.o should be created in the driver's directory if all worked. (I think this will not happen, unless you're lucky).

But anyway, if it really works and the file is created, you should open the terminal again :) and type in "sudo insmod w35und.o".

I didn't work:( well I tried right clicking and it did not give me the option to open the terminal so I opened it manually and put in the file then clicked run. but it still didn't work:(

---

### Post by houbysoft.xf.cz on 2008-07-16
And are you sure that you clicked NOT on any file, but anywhere else in the folder with the files? It should give you the option to open a terminal... or is this in xubuntu only? But if it will not give you the option to open a terminal, you will have to manually open one, but then not putting in the file, but navigating to the folder where you have the driver files.
Maybe you already know it, but in the terminal, changing directories is done with the "cd" command. So, for example, if you want to go to a directory named "exampledir", you must run "cd exampledir". If I take a look at your screenshot, the files are probably in /home/timothy/Documents/hal_142_o/linux.

So, open the terminal and type in these commands:

```
cd Documents/hal_142_o/linux
make
```

Then post the output here...

---

### Post by pishta on 2010-12-02
After looking all over the place and wading through BS "driver" links, I found this WIn driver. Maybe itll help. It works on my XP laptop fine. Not the greatest. but has more rnge than my internal antenna laptop. 

[http://www.novopos.ch/client/FIRICH/W-LAN/802.11.bg%20USB%20W-LAN%20Driver%20WINBOND%20W89C35DG.zip](http://www.novopos.ch/client/FIRICH/W-LAN/802.11.bg%20USB%20W-LAN%20Driver%20WINBOND%20W89C35DG.zip)

---

