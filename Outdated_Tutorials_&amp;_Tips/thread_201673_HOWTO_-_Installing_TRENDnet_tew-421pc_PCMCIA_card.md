---
title: "HOWTO - Installing TRENDnet tew-421pc PCMCIA card"
date: 2006-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jaa1180 on 2006-06-22
Ok... here we go. 
This is very easy.
1. First, you need the driver for the card. Go [here]("http://www.trendnet.com/downloads/info/tew-421pc.htm") and download the zip file. You need find out if your card is a B1 or A. Mine is a B1.

Download driver file, unzip to desired location. Inside the new folder, you will have "Drivers" and "Utility" folders. In the drivers folder, you will have all the Winders OSs.

2. Install ndiswrapper and the gui if you want to. 
```
apt-get install ndiswrapper-utils ndisgtk
```

3. With that installed we now need to install the driver. I used the Windows 2000 driver. 
```
ndiswrapper -i /path/to/drivers/Windows\ 2000/Mrv8000c.INF
```
The GUI install still does not work, however it is nice to view the installed driver. 
Now check to see it is installed.
```
ndiswrapper -l
```
You sould see something like...
```
Installed ndis drivers:
mrv8000c                driver present, hardware present

```

4. Ok, all is well. You have installed the drivers, now we need to setup the device. 
```
sudo gedit /etc/network/interfaces
```
Add this below the > # The primary network interface

```
iface wlan0 inet dhcp
```
Save and close file. 

5. Go to System --> Administration --> Networking
Go into the properties of you new wireless device and properly configure it for you wireless network, adding the ESSID and whatever else. Click OK.

6. Activate the device. You should still have the Network Settings box up. Highlight the Wireless Conection and click the button "Activate". Click OK.

7. You should be good to go now. I restarted my networking again after unplugging the wired connection just to make sure everything was nice and clean.
```
/etc/init.d/networking restart
```
You may not have to...

Now change your nice little networking icon, usually beside your clock, to wlan0 and you will see the signal bar graph. 
BAM! Done. Enjoy you new wireless card.
==================================
UPDATE:
As indicated in other posts on this one, be sure to install ndiswrapper1.8 as this will solve several issues. Be sure to read the other posts on this subject. They are most helpful. :)

---

### Post by skale on 2006-07-12
I still have a problem. The /etc/network/interfaces has no such section, just a "loopback" interface. I don't know whether to add this to the end or what. Any suggestions?

edit: Nevermind. Works anyway.

---

### Post by jaa1180 on 2006-07-12
What is in the file? 
Add in:
```
iface wlan0 inet dhcp
``` 
below # The primary network interface

Have you done that yet?

---

### Post by acamargob on 2006-07-23
Add in:

iface wlan0 inet dhcp

that line is already on the file under wlan0. but the card doesn't appear on networking

---

### Post by TrueJk7 on 2006-09-15
Thanks again man! Awesome, well laid-out walkthrough. One problem though I am having is, I don't have an internet connection to start on. Believe it or not I have no Ethernet ports and only the TEW-421PC to rely on for connection. Any suggestions there. Thanks!

EDIT:

OK I did find an answer [here]("http://www.ubuntuforums.org/showthread.php?t=243566&"), for installing the ndiswrapper without an internet connection... but under the network admin pannel it's only showing a ppp0 modem. (which I know I don't have) So the break down is...

Steps #1 - 3 are prefect. Everything seems good.

Step #4: The problem here is the line 
> 
# The primary network interface 

That did not exist in "/etc/network/interfaces" the header information was there so I just added that line. I figure it'd be fine anyways because it's just a comment. 

Then I added the line 
```

iface wlan0 inet dhcp

```
on line 5 of the file. 

then after that, existed
```

auto lo
iface lo inet loopback

```

So the entire file reads (after modifications
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)

# The primary network interface
iface wlan0 inet dhcp

```

And when I go to the Network Admin pannel. The wireless device is not there. The only thing is the modem device I know I don't have. Sooo... I am completely lost. If anyone has any suggestions, please let me know. 

Further Trouble shooting:
 - I tried to remove the lines (other than the commented lines) and only have the one pertaining to the wireless devices and it didn't work.
 - I tried what was mentioned in step 7 of the howto and it still didn't work
 - I tried to even close all the applications and restart (you can tell I'm migrating from windows still) and still no resolve.

So, please, I'm using this for school and I'd like to have a laptop that I could use a little bit more. (hopefully get open office running on the thing soon too). Well I'll be out for now. Send in posts if anyone has an idea what is going on. 

Peace,
Newbie

---

### Post by TrueJk7 on 2006-09-16
The Newbie found the answer! 

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") had some awesome supplimental information for my situation. All done through terminal. And all worked! 

Now I'm gonna enjoy my awesome distro of linux!

Peace,
Newbie

---

### Post by Opsidian on 2006-09-25
everything has gone well so far but I'm now getting this.
Installed ndis drivers:
2000 mrv8000   invalid driver!

I've tried the drivers that came with the card and even the downloaded one and still getting the same issue, any ideas?

---

### Post by magiceraser06 on 2006-11-22
Hey guys.

well, i am in about the same spot as the rest of you.  Everything installed fine. It says the driver is present and installed.  

It even shows up via  ndisgtk.  So i know its setup.  But now the only thing is actually have it show up in NETWORKING and be able to be configured.  I have an unsecured network, so there shouldn't be any conflicts.

Also, for the file  etc/network/interfaces,  what should the full file look like?  Can anyone post their working configuration?  

HELP! Im a noob to linux.

thanks guys.


EDIT:
So,  I figured out how to get the card working.  I followed these steps.

**Install ndiswrapper and drivers 

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

** Set ndiswrapper to load on startup 

sudo ndiswrapper -m
gksudo gedit /etc/modules

** Add the following module to the list 

ndiswrapper


Ok, all is well. You have installed the drivers, now we need to setup the device.

Code:

sudo gedit /etc/network/interfaces

                 >>>>>  This was where a lot of people, including me, ran into some confusion.  THe original file just had a bunch of auto eth0 and iface eth0, blah blah.   

Add these lines at the VERY BEGINNING of the file

# The primary network interface
iface wlan0 inet dhcp


                >>>>>On a side note:  I am using my laptop, which ONLY has wireless, so I edited my inteface file to only include the previous two lines.  If you have a eth0, then you should be able put that line under these two and still be ok.. You experts out there, can you validate this?
Save and close file.

THEN RESTART. I don't care what anyone says, just restart that damn thing. Ubuntu loads like 30 sec anyway, so your not really wasting time.

---

### Post by mi_were on 2006-11-25
](*,) ](*,)  and a bit more is where i am! i have read and reread the advise here and i must admit that i'm not as clever as i thought:rolleyes: 

when i try to " sudo ndiswrapper -i mydriver" i get that it cannot be copied
"at /user/sbin/ndiswrapper line 135"

please point me in the right direction!

---

### Post by mi_were on 2006-11-25
hold the presses i downloaded the manufacturer's drivers and tried again and it worked!:-D :-D

---

### Post by magiceraser06 on 2006-11-26
Glad to hear it. I actualy had so much more trouble getting it set up in KDE than in Gnome.  I reinstalled Dapper, since Edgy... well... was edgy, so I got rid of it for something more stable.  Dapper install was easy as pie.  The ndisgtk seems to really only work well in Gnome and Dapper environments based on my testing.  I couldn't get the GUI to load up in KDE.

But, yeah, I downloaded the drives via the link given at the beginning of this post.  Use ndisgtk to install the drive.  The green light went on the card and I was giddy.   

Hope that helps y'all out there.  As a side note, when i did a fresh install of dapper. Edited my /etc/apt/sources.list then coded the following as ROOT user.  

aptitude update
aptitude upgrade
aptitude install ndiswrapper-utils ndisgtk

Then went to SYSTEM -----> ADMINISTRATION ----> WINDOWS WIRELESS DRIVERS.

I selected the drivers downloaded from [here]("http://www.trendnet.com/downloads/info/tew-421pc.htm").

and everything worked right out of the box.

---

### Post by akajonesy on 2006-12-23
I'm resurrecting this thread so as not to start the same thread over. 
I've followed all the instructions, here and in attached links, but I still do not get the card recognized. 
I have the TEW-421 (A) card though (texas Instruments). 

Of interest: when I look in the ndiswrapper folder the INF file has a red "x" on it 

I may have done something wrong when installing ndiswrapper since when I enter:

> sudo modprobe ndiswrapper
it gives me: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

if I enter lspci the network controller is listed as:

05:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

IWCONFIG:

lo    no wireless extensions
sit0  no wireless extensions

IFCONFIG

nothing happens.

Can I use this card at all?

thx

---

### Post by akajonesy on 2006-12-23
actually Ive decided to open a new thread after all here [http://ubuntuforums.org/showthread.php?p=1923148#post1923148]("http://ubuntuforums.org/showthread.php?p=1923148#post1923148") since my version of this card seems to be a different one.

---

### Post by jaa1180 on 2006-12-30
Ok. Let me know if it is still not working.
-Jeff

---

### Post by ajslater on 2007-03-28
fwiw a friedn has the b1 version of this card and my kernel insertion problems were solved by installing the 1.8 version of ndiswrapper-utils intead of the 1.1 version.

AJ

---

### Post by PhillD on 2007-04-02
Hi,

I am using XUbuntu and despite following all the instructions, I could not get my wireless card to show up in the networking manager.  I was getting  the error 

Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

When trying to run 

sudo modprobe ndiswrapper

The fix was to install ndiswrapper1.8 as suggested by ajslater.

I was wondering, considering how useful this post has been, if the originator could amend their post to instruct the user to install version 1.8.  Also that you would need to run 

sudo modprobe ndiswrapper

in between steps 4 and 5.

---

### Post by jaa1180 on 2007-04-11
Thanks for the update. I will update the instructions.

---

### Post by gangolli on 2007-06-22
Thanks. This worked fine for me.  Wanted to add that there is yet another version (C1.0R)  of this card out.  Follow the instructions on TRENDnet's site to identify your  card and get the proper drivers.

---

### Post by Lupin_IV on 2008-10-24
G'day,

i google this thread, cause i am installing my trendnet wlan card (its a TEW-421PC in C1.1 version)
i am using the original driver win2000 from trendnet with ndiswrapper.
my notebook is a compaq evo n600c - ubuntu 8.4.1

some things strang.
if i pulgin a wlan usb stick from d-link
i can connect to my fritzbox 7170
.. if i try the wlan card.. it cant connect.
i followed your instructions.. but.. some how i cant connect.

any ideas for solutions?

thanks
Lupin_IV

---

### Post by jaa1180 on 2008-10-24
> **Lupin_IV said:**
> G'day,

i google this thread, cause i am installing my trendnet wlan card (its a TEW-421PC in C1.1 version)
i am using the original driver win2000 from trendnet with ndiswrapper.
my notebook is a compaq evo n600c - ubuntu 8.4.1

some things strang.
if i pulgin a wlan usb stick from d-link
i can connect to my fritzbox 7170
.. if i try the wlan card.. it cant connect.
i followed your instructions.. but.. some how i cant connect.

any ideas for solutions?

thanks
Lupin_IV

What happens? Do you get any errors?

---

### Post by Lupin_IV on 2008-10-26
i didnt get any errors.. that was the strang thing.

well.. i swapt the card now for a stick.

just plugged it in.. and works perfectly. that 'll do.

thanks for your quick repley.

:) have a nice day

---

### Post by earnoth on 2010-01-16
Update to this thread, tried to do this on Ubuntu 9.10, had to make the following minor adjustments:

```
# apt-get install ndiswrapper-utils-1.9
```

After executing ndiswrapper -i on the driver file, I found it necessary to also execute the following command:

```
# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

```

Lastly, the driver needs to be loaded into the kernel:
```
# modprobe wlan0
```

At this point, the interface should be viewable with ifconfig.

---

### Post by -Vlad on 2010-09-08
> **magiceraser06 said:**
> 
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf


This is where I get "no ndiswrapper utils found!", even though it says "ndiswrapper-utils is already the newest version." one command before (I installed ndiswrapper earlier). This is very frustrating and if this laptop wasn't so underpowered i'd be back to Windows 7 in a snap. BTW, the wireless network card I'm trying to persuade to work was recognized properly during Ubuntu installation and does connect to my wireless network about 5% of the time ](*,)

---

