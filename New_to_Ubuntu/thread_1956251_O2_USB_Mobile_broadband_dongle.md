---
title: "O2 USB Mobile broadband dongle"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by parcdulas on 2012-04-10
I have an O2 mobile USB dongle based on the HUAWEI 160 modem. As the dongle installs connect software for WINDOWS on a windows machine I am at a loss how to get it to work on UBUNTU. My UBUNTU machine does not have any web access until I can get the dongle to work so if any other software is needed I will need to download it on another machine (WINDOWS). UBUNTU does not seem to recognise the dongle except that it recognises that an external disk is available with no space on it (the dongle can have a memory card installed) As an absolute beginner with UBUNTU can anyone help me please?

Martin

---

### Post by gandaran on 2012-04-10
hi
which ubuntu release do you have?
I would recommend to have the latest ubuntu version installed and for the dongle there's no need to install any software, just run the network manager mobile broadband wizard from the panel network icon to choose country and your internet provider and check the box connect automatically in the setup then maybe reboot to start internet connection.
this works for almost any dongle but sometimes new dongle modems are not yet supported so it's recommended to have the newest ubuntu version, alternately there are some third party software to manage mobile connections but try the ubuntu network manager first.

---

### Post by parcdulas on 2012-04-11
Thanks. I have 11.10 I believe although I am away from the machine at present. It seems to be an O2 problem as they are sending me a new SIM card for the modem. With the new SIM I'll try it out on my return in a couple of weeks.

---

### Post by gandaran on 2012-04-11
> **parcdulas said:**
> Thanks. I have 11.10 I believe although I am away from the machine at present. It seems to be an O2 problem as they are sending me a new SIM card for the modem. With the new SIM I'll try it out on my return in a couple of weeks.
well, if the modem works on windows then it should work on ubuntu, 
the HUAWEI 160 modem has been around for sometime so I believe its well supported on ubuntu, just be careful choosing the O2 contract or pay and go internet package as it will not work without the right APN, mobile broadband is easy if you can get the right connection settings.

---

### Post by Roger49 on 2012-04-12
Hi,
I've just installed 11.10 myself, and run into what may be the same problem. My dongle is with 3, and worked well with 10.04 and 10.10. The problem may be User Privilege settings - it was with me.

Here is a post I have just made to a different thread.
Regards,
Roger49

Hi,
Fixed it.
I checked that the machine had detected the dongle with "lsusb", and it had.
If you right-click on the background, and choose "Applications", "System", "Users and Groups".
Click on "Advanced Settings", and enter your password.
Under the "User Privileges" tab is a list of tick-boxes. Printing and Modem use had not been ticked.
Click on the boxes you might need, save and close.
I now have Internet access.
I thought I would post it here for other users who are scratching their heads.
Regards,
Roger

---

### Post by Linux_junkie on 2012-04-12
I have a T-mobile dongle and I set it up through the network manager app.

Follow the following pics to setup your dongle in Ubuntu.  When you get to window in last pic just follow the wizard to set it up for your network. 

Any problems just ask.

---

### Post by parcdulas on 2012-04-22
I managed with difficulty to get the device working with a new sim under windows. Ubuntu still ignores it. With the device plugged in to one of the usb sockets i typed sudo lsusb to see if the modem was connected. it came up as:

Bus 001 Device 000: ID 12d1:1003 Huawei Technologies co., Ltd. E220 HSDPA Modem/E230/E270 HSDPA/HSUPA Modem

So it is definitely connected but I cannot get Firefox or Thunderbird to recognise it. When I click on the network icon in the top bar there is no mobile broadband available. If I click on "Edit Connections" that brings up the network connections dialogue box with a "Mobile Broadband" tab that allows me to set up two prepaid Pay-As-You-Go O2 systems but neither seem to work. So what can I try next?

---

### Post by Lateralis on 2012-04-22
I set one of these up on a laptop a couple of years ago.  Unless much has changed then it should be fairly straightforward.  Open the network manager, the wireless tab and then click to set up a new connection.  I can't remember the exact details which need to go in the dialogue box, but have a [read through this link]("http://community.o2.co.uk/t5/Mobile-Broadband/PAYG-E160-in-Ubuntu-8-10/td-p/36191"), which contains a wealth of information.  (The instructions should still work with 11.10/12.04, even though the OP in that link was installing the modem on an Ubuntu 8.10 system.)

---

### Post by Mark Phelps on 2012-04-23
> **gandaran said:**
> well, if the modem works on windows then it should work on ubuntu...


Sorry ... that generalization is not true in all cases.

I have an LG 4GLTE USB modem which works great in Windows and will not work at all in Linux distros -- because LG (through Verizon) supplies special drivers for this which are not available in Linux.

---

### Post by Roger49 on 2012-04-24
Hi again,
Your experiences are very similar to mine.
I found that lsusb would find the dongle.
I also found that in addition to checking the correct boxes in the "Users" section, I also had to become a member of a "Group" in the "Groups" section. One of which had a title like "www-data".
After doing that, my mobile broadband came back.
(Must check again tonight to see that its still there).
Good Luck,
Roger49

---

### Post by audiomick on 2012-04-24
To give you a bit of hope...

```
mick@mick-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Look familiar? ;)
I am posting using the USB modem. It is a German T-Mobile one, not O2, but I believe the guts of the things are the same.

Having said that, I didn't have any trouble getting it going on 10.04 or 10.10. Perhaps the permissions issue that was posted earlier?

There was a thing with a package called "usb-modeswitch" . The purpose of the package is to toggle the switch that is in the device that causes the windows installer to start when it is plugged in to windows if the device has never been installed, or to appear as a modem once it has been installed. Have a look to see if it is installed. I doubt, however, that this is your problem because firstly I believe the package is there by default on 11.10, and secondly, I gather you have already installed the device on a windows machine, so the mode should already be switched anyway.

---

### Post by gandaran on 2012-04-24
> **parcdulas said:**
> I managed with difficulty to get the device working with a new sim under windows. Ubuntu still ignores it. With the device plugged in to one of the usb sockets i typed sudo lsusb to see if the modem was connected. it came up as:

Bus 001 Device 000: ID 12d1:1003 Huawei Technologies co., Ltd. E220 HSDPA Modem/E230/E270 HSDPA/HSUPA Modem

So it is definitely connected but I cannot get Firefox or Thunderbird to recognise it. When I click on the network icon in the top bar there is no mobile broadband available. If I click on "Edit Connections" that brings up the network connections dialogue box with a "Mobile Broadband" tab that allows me to set up two prepaid Pay-As-You-Go O2 systems but neither seem to work. So what can I try next?
have you tried removing and plugging again the modem? ubuntu 11.10 fails to load some modems models at start up 
try it, wait about a minute then look in the panel icon for the mobile network.

---

### Post by audiomick on 2012-04-24
> **gandaran said:**
> have you tried removing and plugging again the modem? ubuntu 11.10 fails to load some modems models at start up 
try it, wait about a minute then look in the panel icon for the mobile network.

Ahh, mine is erratic. I use the dongle mostly with this laptop. Mostly, it will boot fine and find the dongle. Sometimes it doesn't, though, so I generally don't plug it in until the system is up.

---

### Post by parcdulas on 2012-04-29
The Huawei 160 works under Windows XP on my laptop but will not work under Ubuntu (dual boot on laptop and only operating system on desktop) I have to revert to windows on laptop to post. Ubuntu Network manager allows me to set up the mobile broadband and I have tried all of the possible plans/apn that are shown. One curiosity is that sometimes the network manager identifies Huawei broadband mobile but at others it has "any device" greyed out so I can't set it.

It seems to me that this is an issue with the specific entries into the mobile wizard as the pay and go entry (I pay for a months access for 4Gb of data) has APN: payandgo.o2.co.uk with the username and password as: payandgo. I have tried the mobile entry which has the APN: m-bb.o2.co.uk and the username:o2bb and password: password. I even tried the contract entry that used o2web as the username all to no avail. I have tried only plugging in the dongle after Ubuntu has fully booted but this makes no difference either. To re-itterate, the lsusb command indicates that the dongle is plugged in correctly and the LED on the dongle says it is connected to GPRS (needless to say in the heart of rural Wales there is no faster connection) Any other suggestions would be appreciated.

---

### Post by audiomick on 2012-04-29
> **parcdulas said:**
>  
It seems to me that this is an issue with the specific entries into the mobile wizard as the pay and go entry 
I'm not convinced of that.

This
> One curiosity is that sometimes the network manager identifies Huawei broadband mobile but at others it has "any device" greyed out so I can't set it.

Indicates that the computer is not seeing the device properly, or not consistently. When it is plugged in, it should always be seen be the wizard, or never. Not just sometimes. Also, as far as I know, if you set up the connection wrong it still should try and connect and then fail. From what you have written, it isn't even trying to connect.

I'm afraid, though, that I am at a bit of a loss as to what might be missing. Did you look to see if that usb-modeswitch package is there?

Another thing: do you have the same ubuntu version on the desktop and the laptop? Can you get the dongle to work with the desktop?

---

### Post by gandaran on 2012-04-30
parcdulas
try doing the same thing I did when I first used mobile broadband on ubuntu, at that time I didn't now anything about APN's or mobile broadband, spent nearly twos days and was about to give up before I got the bright idea of checking the modems installed software on windows, got the right details from windows, used the same on ubuntu and you know what? modem connected first time.
also don't have multiple setups on network manager, try working with just one.
you can also find out from other sources (google search?) if the pay and go APN is correct or even if your mobile internet provider can also use dynamic APN (in this case use blank APN on the setup) and about username and password usually mobile internet providers don't use them but you can check on the windows software.
hope you get it working.

---

### Post by toft on 2012-05-01
I am having problems with my own 3 mobile dongle.  Mine connected automaticaly after os install but will not download, only browse.
 
Just a thought re your problem though.
 
> **parcdulas said:**
>  (the dongle can have a memory card installed)
Martin
 
I seem to remember reading that card readers without a card in are not regognised/mounted.  Could this be the problem with yours?

---

### Post by parcdulas on 2012-05-15
As it works ok with windows but wont with ubuntu how do
I find out what APN/password it is using under windows?

---

### Post by gandaran on 2012-05-15
> **parcdulas said:**
> As it works ok with windows but wont with ubuntu how do
I find out what APN/password it is using under windows?
if you explore the windows software the modem installed you shoud find everything it uses to connect, I don't know which or never seen your modem software so I cant tell you exactly where to look but usualy going to the properties section is where you can find the details.

also on the ubuntu side,
if the modem mounts a memory storage card be sure you unmout the card first before trying a connection.

---

### Post by parcdulas on 2012-05-15
Thanks, I'll try that.

---

### Post by parcdulas on 2012-08-25
As mentioned on another thread I updated the flash firmware in the dongle from a Huawei site (searched for Huawei E160) and now 12.04 recognises the dongle. Note that the Network Manager Wizard has the wrong default entries so need to edit the setup.

Thanks to all,

Martin

---

