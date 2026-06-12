---
title: "Wireless Firmware Missing Ubuntu 11.10"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by firmware43 on 2011-11-18
I have downloaded Ubuntu 11.10. 

The wifi connection is enabled but I am unable to connect to the internet as it says that it that it is not ready and **Firmware Missing**...

I have checked a lot of forums & I keep getting references **b43-fwcutter**. I tried to follow the instructions on the page but was unable to do much.

I used this command : (as advised on [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43))

~$ lspci -vvnn | grep 14e4

I got 14e4:4312 (rev 01) in the end, which is supported.

I don't have wired internet so will have to change OS to Windows before I download anything. I can't understand what I am supposed to do on this page. The b43-fwcutter doesn't seem to be there:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Can you also post the links of the things I would need to download?

---

### Post by Gone fishing on 2011-11-19
Have you used the additional drivers tool?

You will need a working internet connection - can be difficult if your wireless isn't working, try a cable to the router. 

Then run ```
sudo apt-get update
``` just to make sure the package information on your computer is up to date. Now open additional drivers and a driver for your Broadcom wireless should be found install the recommended driver and you should be good to go.

---

### Post by firmware43 on 2011-11-19
How do you goto Additional Drivers??? And I can't do that.I can access my wireless through Windows but not from Ubuntu... BTW how can we check which STA driver we have?

---

### Post by Gone fishing on 2011-11-19
In the dash search for additional and you will see the additional drivers tool. Then open it, however, for it to work and download the needed drivers you will need a working internet connection in Ubuntu, so use a cable. After the drivers have been installed the wireless should work.

---

### Post by firmware43 on 2011-11-19
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

On this page they have said something regarding being able to do it without internet connections. I will be able to download the files but not directly on to Ubuntu. I will have to transfer them to a USB and then use it. 

(In some places I have seen things like this : System-->Administration-->Additional Drivers. Can the Additional Drivers be accessed via this route. If yes, then how do we open System then Administration? Are they like folders in Windows or something else?)

---

### Post by Gone fishing on 2011-11-19
The way I am suggesting will probably install the Broadcom STA proprietary rather than b43 driver. The tool will pick the best available driver. However if you cant get access then the link you gave should work I'd follow > the STA - No Internet access
However, it would be easier if possible just to plug the PC into a router using a network cable.

---

### Post by realitykid on 2011-11-19
firmware43, do you even have a router or a modem for your internet service? Or is it strictly a local wireless connection?

If you have a router or a modem, you will be able to use an ethernet cable to connect it to your computer.

---

### Post by firmware43 on 2011-11-19
I am obviously not very knowledgeable regarding this...
Can you tell me what I should do in normal english which I might be able to understand as some of the things written on that page are way over my head...

So if you could take some time out to help me and make it simpler and easier to understand, could you post a step-by-step process that I can follow and I will keep post the result of the commands that I type.

---

### Post by firmware43 on 2011-11-19
> **realitykid said:**
> firmware43, do you even have a router or a modem for your internet service? Or is it strictly a local wireless connection?

If you have a router or a modem, you will be able to use an ethernet cable to connect it to your computer.
It is a local wireless connection. I am in a residential area so it is kind of like a public network. i.e. No network cable possible.

---

### Post by Gone fishing on 2011-11-19
Sorry 

So you could follow the STA - No Internet access note in step 1 it points out that you can

> Step 1.

install the packages listed below by double clicking or navigate the install media and install these packages consecutively in a terminal (under the desktop menu Applications > Accessories > Terminal): 

It just going to be a little fiddly if this your first time using Linux? Possibly it is worth pointing out that the proprietary drivers are not included in the install for legal reasons - however Linux Mint (based on Ubuntu) comes with all the drivers codecs etc pre-installed.

---

### Post by firmware43 on 2011-11-19
Can you tell me the difference when you download WUBI and then load Ubuntu, what difference does it make when you give 5GB 10GB or 30GB for Ubuntu Installation Size? How are different sizes benifitial?

---

### Post by realitykid on 2011-11-19
> **firmware43 said:**
> Can you tell me the difference when you download WUBI and then load Ubuntu, what difference does it make when you give 5GB 10GB or 30GB for Ubuntu Installation Size? How are different sizes benifitial?

It just gives Ubuntu more space to store data. So if you'd like to install a lot of applications or store a lot of information inside Ubuntu, the more space the better. Other than that, I don't think that there any real benefits to giving Ubuntu more space.

---

### Post by pierreyy on 2011-11-19
is there a way where you can access the Internet ? ( coffee shop, a friend, whatever)

try to install the additional drivers before changing the operating system

---

### Post by firmware43 on 2011-11-19
[FONT=monospace]This is what I got : 

[/FONT]../pool/main/d/dkms 
:/dkms/$ sudo dpkg -i dkms*../pool/main/p/patch 
:/patch/$ sudo dpkg -i patch*../pool/main/f/fakeroot 
:/fakeroot/$ sudo dpkg -i fakeroot*../pool/restricted/b/bcmwl 
:/bcmwl/$ sudo dpkg -i bcmwl-kernel-source*
No Such File Or Directory - For each command

---

### Post by firmware43 on 2011-11-19
> **pierreyy said:**
> is there a way where you can access the Internet ? ( coffee shop, a friend, whatever)

try to install the additional drivers before changing the operating system

I can access the internet but only when I boot via Windows otherwise it won't work. My friends have their internet working but all use wifi. So I can access the net, but not via Ubuntu.

BTW when I reinstalled Ubuntu, they asked me to update my driver (the wifi one) but i had to connect to the internet for that.

Is there some way that I can download the drivers online via windows and install them on Ubuntu using USB?

---

### Post by firmware43 on 2011-11-19
I downloaded the driver from here : 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

There is a read me also there. Can you explain to me what I am supposed to do?

---

### Post by Gone fishing on 2011-11-19
Your friends have wifi OK you could get them to setup internet connection sharing [http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing](http://windows.microsoft.com/en-US/windows-vista/Using-ICS-Internet-Connection-Sharing) then plug into their computers using a cable.

Or borrow a cheep wifi usb dongle and try that - most work

---

### Post by firmware43 on 2011-11-19
Hey! Thanks for the tip. I am a newbie so I don't know much about this. I always wanted to know about networks and how they work. Any idea where I can get good information on this and other related topics? 

I will try this thing tomorrow and get back to you. Thanks a ton guys. Don't close this thread.

---

