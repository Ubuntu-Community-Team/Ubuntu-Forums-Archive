---
title: "Questions - Please help me"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by avrilrox on 2008-05-04
Ok guys, i'm a windows user so i'm a complete newbie!

**Ok, first of all, my computer:**
[I]ASUS P5L-MX MOTHERBOARD
PENTIUM D 930 DUAL CORE 3.0GHZ
2x512 DDR2 667MHZ
ASUS AX550 (ATI)
SAMSUNG SATA II 80GB[/I]

**Installed OS:**
[I]Windows XP SP2
Ubuntu 8.04[/I]

Now, i've been having some problems with ubuntu.

**1.** I can't share files between them. Linux won't see Windows files and Windows won't see Linux files.

**2.** I can't connect to the internet. I'm using an USB wireless adapter (TRENDnet TEW-424UB) and there are no drivers for Linux. I've heard of ndiswrapper. I did download it and extracted the files.

After that, this is what i wrote in the console:

```
sudo make uninstall
sudo make
sudo make install
```

There are a lot of errors and when i write
```
sudo ndiswrapper -i mydriver.inf
```
returns an error.


**3.** Problems with my video card.

At first, everything was working fine. I set the appearance to the highest and it would work incredibly well but then i decided to install the official drivers for my video card and everything went wrong. I have to lower the graphics or it would take ages to move a window.

I tried aticonfig but i cant find anything useful.

Please help me. Thank you very much.

---

### Post by avrilrox on 2008-05-04
Oh, and it would be really cool to change the resolution. I tried aticonfig but it does not work. I want to set it to 1440x900

---

### Post by bobnutfield on 2008-05-04
> 
1. I can't share files between them. Linux won't see Windows files and Windows won't see Linux files.

You must mount your Windows partition to "see" their files.  Go to Places>Computer> and there will be an icon to mount your drive partitions.

Windows will not mount Linux partitions, so you will not be able to access Linux files from Windows on the same partition.  You can do it on separate machines communicating over a network with SAMBA installed.

Your video card must have the restricted drivers installed to function properly and achieve the resolutions you want.  Go to System>Adminstration>Hardware Drivers.  Read and follow the instructions there.

Ndiswrapper does not need to be installed from source.  Open a terminal and type:

sudo apt-get ndiswrapper-common

Hope this helps

Bob

---

### Post by bobnutfield on 2008-05-04
Sorry, not thinking properly.....


sudo apt-get install ndiswrapper-common

---

### Post by Victormd on 2008-05-04
> **avrilrox said:**
> Oh, and it would be really cool to change the resolution. I tried aticonfig but it does not work. I want to set it to 1440x900

Have you tried using envyng to install your graphics card? It's in the repositories. Just go to synaptics and search for it.

It will remove your current driver and install the most up-to-date driver from the ATI website...

---

### Post by ugm6hr on 2008-05-04
> **avrilrox said:**
> **1.** I can't share files between them. Linux won't see Windows files and Windows won't see Linux files.

**2.** I can't connect to the internet. I'm using an USB wireless adapter (TRENDnet TEW-424UB) and there are no drivers for Linux. I've heard of ndiswrapper. I did download it and extracted the files.

**3.** Problems with my video card.

At first, everything was working fine. I set the appearance to the highest and it would work incredibly well but then i decided to install the official drivers for my video card and everything went wrong. I have to lower the graphics or it would take ages to move a window.

1. As stated - you have to mount the Windows partition (find and click in Places).
To see the Linux partition in Windows - use: [http://www.fs-driver.org/](http://www.fs-driver.org/)

3. Why not revert to the original driver if it was working incredibly well?

---

### Post by kwacka on 2008-05-04
You may not need ndiswrapper, it depends on which chipset the Trendnet uses see answer #3 at:

[http://ubuntuforums.org/showthread.php?t=284683](http://ubuntuforums.org/showthread.php?t=284683)

---

### Post by avrilrox on 2008-05-04
> **bobnutfield said:**
> You must mount your Windows partition to "see" their files.  Go to Places>Computer> and there will be an icon to mount your drive partitions.

Windows will not mount Linux partitions, so you will not be able to access Linux files from Windows on the same partition.  You can do it on separate machines communicating over a network with SAMBA installed.

Your video card must have the restricted drivers installed to function properly and achieve the resolutions you want.  Go to System>Adminstration>Hardware Drivers.  Read and follow the instructions there.

Ndiswrapper does not need to be installed from source.  Open a terminal and type:

sudo apt-get ndiswrapper-common

Hope this helps

Bob

Ok, im gonna try that! Thanks!

> **Victormd said:**
> Have you tried using envyng to install your graphics card? It's in the repositories. Just go to synaptics and search for it.
Hmmm no... I dont know what that is...
To install the driver i wrote:
```
sudo sh driver.run
```

> **Victormd said:**
> 
It will remove your current driver and install the most up-to-date driver from the ATI website...

Yeah, i heard ubuntu could do that, but i cant connect to the internet. Look, i'm using Windows XP now. When i find something interesting, i write it down, restart my computer and start Ubuntu.

> **kwacka said:**
> You may not need ndiswrapper, it depends on which chipset the Trendnet uses see answer #3 at:

[http://ubuntuforums.org/showthread.php?t=284683](http://ubuntuforums.org/showthread.php?t=284683)


> **FrodoB said:**
> If your ID is 0457:0163 you have the SiS chipset then ndiswrapper is your only course of action, if it is  0ace:1211 it is  Zydas a zd1211 or zd1211b proceed with the Belkin F5D7050 ver 4000 instruction in the link above.

I think i have the Sis one because the filename contains SiS

---

### Post by avrilrox on 2008-05-04
> **bobnutfield said:**
> You must mount your Windows partition to "see" their files.  Go to Places>Computer> and there will be an icon to mount your drive partitions.

Windows will not mount Linux partitions, so you will not be able to access Linux files from Windows on the same partition.  You can do it on separate machines communicating over a network with SAMBA installed.

Your video card must have the restricted drivers installed to function properly and achieve the resolutions you want.  Go to System>Adminstration>Hardware Drivers.  Read and follow the instructions there.

Ndiswrapper does not need to be installed from source.  Open a terminal and type:

sudo apt-get ndiswrapper-common

Hope this helps

Bob

It says that the package ndiswrapper couldnt be found :(

---

### Post by avrilrox on 2008-05-04
I really want to get ubuntu to connect to the internet. I'm using the SiS chipset so i really need to get ndiswrapper working.

Please help me install it :(

---

### Post by Victormd on 2008-05-04
Ok. let's see what we can do...

[COLOR="Silver"]Now you're using your on-board ethernet card, right[/COLOR], and you're trying to get a usb wireless to work...
This is for a different wireless card but it might just work. I don't know how much you've tried but give this a go:
[http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)
It shows how to use ndiswrapper for a HP wireless using Dell drivers... :)

This is another one for USB wireless Atheros chip based also using ndiswrapper:
[http://ubuntuforums.org/showthread.php?p=4650292](http://ubuntuforums.org/showthread.php?p=4650292)

EDIT:
Just noticed that you're not using the onboard wireless... you're working from windows...

---

### Post by Victormd on 2008-05-04
Just found this link that says that this driver should work with your USB wireless:
[http://sourceforge.net/projects/zd1211](http://sourceforge.net/projects/zd1211)

Source:[http://www.linuxquestions.org/questions/linux-wireless-networking-41/trendnet-tew-424ub-262101/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/trendnet-tew-424ub-262101/)

This might also be a good reference (if you haven't visited it yet):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by avrilrox on 2008-05-04
> **Victormd said:**
> Ok. let's see what we can do...

[COLOR="Silver"]Now you're using your on-board ethernet card, right[/COLOR], and you're trying to get a usb wireless to work...

Ok, first of all, THANK YOU VERY MUCH.

Now, i'm using Windows XP SP2 and connected to the internet using the USB wireless adapter. It works fine.

I need to get it to work on Linux.

I'll be reading the pages you sent, thank you!

---

### Post by avrilrox on 2008-05-04
I cant understand anything :(
I'll read everything again.

If only i could make ndiswrapper work :(

Thank you!

---

### Post by Victormd on 2008-05-04
No problem. Let me know how things go... I think it will be tough to install anything without internet in ubuntu. You might have to download the packages in windows before trying to install them in ubuntu - but you'll have to be carefull because of the dependencies each package requres...

This might be the answer to why you can't get ndiswrapper to work...

Does your motherboard have an ethernet card? This would make your life so much easier when installing the packages...

---

### Post by avrilrox on 2008-05-04
> **Victormd said:**
> No problem. Let me know how things go... I think it will be tough to install anything without internet in ubuntu. You might have to download the packages in windows before trying to install them in ubuntu - but you'll have to be carefull because of the dependencies each package requres...

This might be the answer to why you can't get ndiswrapper to work...

Does your motherboard have an ethernet card? This would make your life so much easier when installing the packages...

Yay! I'm making progress! I managed to install ndiswrapper, i found some packages online and they did work. I might have been trying to install packages for older versions i think. I got the ones for hardy and i installed it.

Now, i can't install the inf file. I even logged in as root and it says that the file doesnt exist in /etc/.../ (cant remember).

Ndiswrapper seems to be installed correctly. I'm much happier now, looks like its gonna work.

Oh, you mean like using my ethernet card to connect to the internet and download packages? Thats a freaking good idea.

Thank you!

Can you help me install my driver? Thank you!

---

### Post by Victormd on 2008-05-04
Since I've never installed any USB wireless cards, it'll be a bit hard to help you. I did use ndiswrapper to install a wireless card on my wife's HP laptop (following a previous link I sent you using a Dell driver). That link is probably your best bet to get it working. However, I would also look into the link specific for your model (also posted earlier).
If you get internet working with your ethernet card, one thing that I've read is that some people experience problems with two cards installed at the same time. I didn't have this problem though... but thought I should mention it just to raise awareness.

Now, once you have internet from ubuntu, go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and under the UPDATES tab, mark ALL **Ubuntu updates**, close that window, open a terminal and type
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```
Now you can try to install your USB wireless...
I don't think I can be much more help than this... carefully review the links I posted as they might solve your problem. If you have any question, just ask. I'm sure someone else has run into the same problem as you and will be more than happy to help. I'm going out of town tomorrow but if I get a chance to check back, I will and if I can help, be sure that I will.

Good luck

---

### Post by ugm6hr on 2008-05-05
> **avrilrox said:**
> Now, i can't install the inf file. I even logged in as root and it says that the file doesnt exist in /etc/.../ (cant remember).

Ndiswrapper seems to be installed correctly. I'm much happier now, looks like its gonna work.

Oh, you mean like using my ethernet card to connect to the internet and download packages? Thats a freaking good idea.


It will be easier if you get online with ethernet first.

How did you install ndiswrapper?

You have to point ndiswrapper to the .inf and .sys files.

I haven't used ndiswrapper in Hardy - but it should work, provided your USB is compatible.

---

### Post by kwacka on 2008-05-05
Confirm your chipset using ```
lsusb
```As you are able to connect wirelessly using Windows you will have the .inf & .sys files somewhere on your windows partition, & possibly the setup disks that came with the card; although they might be inside an .exe file on a CD which won't do much good (you could try copying the .exe file and renaming it .zip & see if winzip/archive manager can open it).

Failing that, try one of the driver download sites.
 

Copy the .inf & .sys files to your /home partition (might be useful to set up a "drivers' folder for future use).

In your terminal ```
 cd /directory/holding/xxx.inf
ls *  (to see what files are in the directory, make sure xxx.inf & xxx.sys are there)
sudo ndiswrapper -i ./xxx.inf 
```

(the ./ tells ndisrapper (or any other application) to look in the current directory).

If you get no error messages:```
 ndiswrapper -l 
``` will hopefully list your card.

If all is well continue with the modprobe & depmod instructions from earlier posts.

N.B. Make sure you use the proper case, e.g. bcmwl5.inf is not the same as BCWL5.INF

---

### Post by avrilrox on 2008-05-05
> **ugm6hr said:**
> It will be easier if you get online with ethernet first.

How did you install ndiswrapper?

You have to point ndiswrapper to the .inf and .sys files.

I haven't used ndiswrapper in Hardy - but it should work, provided your USB is compatible.

I got ndiswrapper from here:

[http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)
[http://packages.ubuntu.com/hardy/i386/ndisgtk/download](http://packages.ubuntu.com/hardy/i386/ndisgtk/download)
[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

> **kwacka said:**
> Confirm your chipset using ```
lsusb
```As you are able to connect wirelessly using Windows you will have the .inf & .sys files somewhere on your windows partition, & possibly the setup disks that came with the card; although they might be inside an .exe file on a CD which won't do much good (you could try copying the .exe file and renaming it .zip & see if winzip/archive manager can open it).

Failing that, try one of the driver download sites.
 

Copy the .inf & .sys files to your /home partition (might be useful to set up a "drivers' folder for future use).

In your terminal ```
 cd /directory/holding/xxx.inf
ls *  (to see what files are in the directory, make sure xxx.inf & xxx.sys are there)
sudo ndiswrapper -i ./xxx.inf 
```

(the ./ tells ndisrapper (or any other application) to look in the current directory).

If you get no error messages:```
 ndiswrapper -l 
``` will hopefully list your card.

If all is well continue with the modprobe & depmod instructions from earlier posts.

N.B. Make sure you use the proper case, e.g. bcmwl5.inf is not the same as BCWL5.INF

Thank you, that was a really helpful post. I had just discovered it was caps sensitive (i got it to work) and i came here to post and... find your post! That's why it didn't work.

Now, i write ```
ndiswrapper -l
``` and it **does** appear so i think its been installed correctly. I dont know how to use depmod, i did run modprobe:
```
sudo modprobe ndiswrapper
```

---

### Post by uberlube on 2008-05-05
I successfully got a trendnet wireless usb to work in Linux about half a year ago. All i needed was the CD it came with that had the windows driver and ndiswrapper to get it to work. Also I had to use some command to change the USB 2.0 to a lesser speed to get it to work. I cant remember the command but I found it here in the Ubuntu forums so if you do some searching around you will probobally find it. Or hopefully someone will read this and post it for u. Hope that helps a bit.

---

### Post by avrilrox on 2008-05-05
> **uberlube said:**
> I successfully got a trendnet wireless usb to work in Linux about half a year ago. All i needed was the CD it came with that had the windows driver and ndiswrapper to get it to work. Also I had to use some command to change the USB 2.0 to a lesser speed to get it to work. I cant remember the command but I found it here in the Ubuntu forums so if you do some searching around you will probobally find it. Or hopefully someone will read this and post it for u. Hope that helps a bit.

Hey, Thank you. I run

```
sudo modprobe ndiswrapper
sudo depmod -a
```
I get no errors but Ubuntu won't see my USB adapter.

Also, when i run iwconfig i get:

```
lo
eth0
```

---

### Post by avrilrox on 2008-05-06
IT works now. IT wasnt the right driver. Im using Ubuntu right now and its working perfectly. It was not the right driver. You guys need to download the 8187b.

Thank you for all your support, it works wonderful now.

---

### Post by Victormd on 2008-05-07
Hey, just got back and saw that you got it to work. Good Job and have fun!

---

