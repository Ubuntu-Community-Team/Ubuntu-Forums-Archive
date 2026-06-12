---
title: "Internet connection problem ATT DSL problem"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by ladyredbrc on 2008-07-11
Hi,
I just downloaded and installed Ubuntu last night, and I have been working on this problem half the night and all morning. I can not figure it out. I have ATT fast access DSL, (Wireless modem). I have two computers-one has Windows XP. This is what I am connected to the internet with now, so I know that the modem is connected and working. The other has Ubuntu. I am completely new to Linux, but I thought that since I knew something (no expert) about Microsoft that I could figure it out fairly easily. I have since learned that is not true. 

My problem is connecting to the internet. I keep getting an address not found error. I am sure that the solution is very simple, or that I messed up somewhere but I don't know where. The installation went fine, no problems, but the install CD for ATT DSL will not run. I have the Ubuntu computer connected to the wireless router through an ethernet cord. The ethernet light is blinking on the modem and on the computer, ATT said that meant it was working. Is it something in the configuration? I have called ATT twice, but neither technician even knew anything about Ubuntu, so that was not really any help. They were very nice, even suggested that I try the TechSupport Plus level, but I am not paying $69.95 for another technician to tell me that they have never even heard of Ubuntu! I tried all the forums, searched the internet for help, but it seems like most of the guides and help are written in very technical terms that are difficult for an absolute beginner such as myself to understand.
 
Has anyone else had this problem? Can it be fixed? If so, would you please walk me through the steps? In the simplest terms? It will not offend me at all. 

I am sorry for rambling, but I am tired, frustrated and I am getting a headache. Any help anyone can give me would be greatly appreciated.  

Thanks!

---

### Post by mxcoldfire on 2008-07-11
Hi there and welcome to the Ubuntu Community.

I also have ATT Fast Access DSL, and I have had no problem with mine. What kind of network card does your computer have?

---

### Post by james_vanb on 2008-07-11
Also using ATT with no problems.  Wired connections generally connect without issues in ubuntu.  A couple questions - You mention both a modem and your computer being wired to a router.  Are you using both?  May help narrow issue to ubuntu config issue or router.

In upper right corner, you will find the network manager.  If you left click on it does it show your router (If you are using one).  If it does, click on it and see if it connects.  Otherwise, left click again and go to Manual Configuration.  Open your wired connection, untick roaming and set it manually.

Are you using security on your router?  If yes, have you set your router to allow access for the ubuntu computer?

If you are using a router, plug the computer directly into the modem and see if that works.  If it does, your router is not configured right.

BTW - ATT install cd won't work in ubuntu - It assumes you have windows.

---

### Post by ladyredbrc on 2008-07-11
Hi,
Thanks for replying.
I have a Lynksys Wireless G Notebook Adapter 2.4GHz. This computer is old, so it is not wireless ready. When I put it in, both the power and the link light come on, so I assume that (the card) works, too. But it won't even work if I take the card out and try to connect directly from the modem to the computer. 
You said that you are using ATT DSL successfully. Do you remember how you set it up, what you did, step by step? Maybe if I try that, it will work for me, too.
Thanks again

---

### Post by ladyredbrc on 2008-07-11
Thank you as well for your answer.
I may have confused the terms modem and router. I am sorry, I am not very technical. I have a wireless modem from ATT (2WIRE) and I have tried to connect the computer directly to the modem with the ethernet cord and that does not seem to be working.
I don't know if I have security set on the computer or modem. If I did, it is not something that I did on purpose. How can I tell?
Would you mind telling me what you did to set up your internet? I am sure that I have clicked something that I shouldn't have or not clicked something I should have, I just don't know enough about the system to figure out what that was. Do you think that re-installing Ubuntu would help?
Thanks!

---

### Post by markbuntu on 2008-07-11
I also am using att dsl and it worked for me right out of the box so you are most likely having trouble with your router.

Anyway, if you are connected directly to the dsl modem you can talk it with your web browser by using address 192.168.1.1. but that should not be necessary.

You don't even need to install anything to get the connection. I was having problems when I first got att dsl and the tech told me to remove the att windows software and talk to the modem with my web browser using the address above.

OK, try this. Disconnect the power from the modem and count to ten. Then plug it back in. Wait for all the lights to come on then right click on the little network thing in the task bar at the top left and make sure Enable Networking has a check mark next to it. Left clock on it and wired network should be selected.

---

### Post by ladyredbrc on 2008-07-11
OK, I am trying that now. 
Thank you.

---

### Post by ladyredbrc on 2008-07-11
OK, I tried that. All that came up was manual configuration. What should I do? 
Thanks

---

### Post by markbuntu on 2008-07-11
Did you reboot the computer since you connected it directly to the dsl modem?
Remove the wireless card and Network Manager should find the connection automatically when you reboot.

You can look in System/Adminstration/System log to see the log files that keep track of what is going on. The syslog should have messages from network Manager and dhclient if it is working. You can also look in the kern.log for messages that start with eth0 or eth1 or something like that.

The logs are your very good friends when something goes wrong or doesn't do what it is supposed to.

---

### Post by ladyredbrc on 2008-07-11
OK, I have looked at the system logs, but I really don't know what to do with any of that information. In the kern.log. The last one is:
e100: eth0: e100_watchdog: link up, 1000Mbps, full-duplex
The system log has a lot of information that I do not understand.
There were messages that said: dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
dhclient: send_packet: Network is down
dhclient: No DHCPOFFERS received
dhclient: No working leases in persistent database - sleeping

Do these things mean anything to you (or anyone else?)
Thank you in advance!

---

### Post by james_vanb on 2008-07-12
The "2 Wire" you are using is both a modem and a wireless router.  Not much info on the internet for your problem, however, the following may be a solution:

Install ndiswrapper through Synaptic.  There are 2 files - ndiswrapper common and ndiswrapper utils.

Open Places > Home Folder - Right click in an open area and click "Create Folder".  Name the folder ATT.

Insert the ATT install cd.  Look for a drivers file and specifically an XP driver file.  You are looking for WLanUIG.inf, WLanUIG,sys and WLanUIG,cat (If the cd has such a file - If it doesn't don't worry).  Copy those files to the Folder you created called ATT by dragging and dropping.

Open a terminal and type:

```
sudo ndiswrapper -i /home/(yourusername)/ATT/WLanUIG.inf
```

This will install the wireless driver you need.  Keep in mind that in ubuntu, commands are case sensitive.  Then type:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Now add ndiswrapper to modules:

```
sudo gedit /etc/modules
```

This will open the text editor.  Add "ndiswrapper" (without quotes) to the end of the list.  Save and close.

Now enter:

```
sudo ndiswrapper -m
```

REBOOT

Wireless should now connect.

This is the thread I found RE your Modem/Router - FYI:

[http://ubuntuforums.org/showthread.php?t=548450](http://ubuntuforums.org/showthread.php?t=548450)

---

### Post by ladyredbrc on 2008-07-12
Ok, I did what you said, thank you so much, because that has gotten me further than anything else I have tried. Now my problem is the a popup screen that says "Wireless Network Key Required". I have tried putting in the key off the modem itself, I have tried changing the personal password, nothing has worked so far. 
It gives me a choice of 4 
WPA Passphrase
WEP 64/128-bit Hex
WEP 64/128-bit ASCII
LEAP
I have tried all of them. I am so frustrated, I just don't know what it wants! But I do thank you for your help, thank you so much! Do you know anything about this?

---

### Post by james_vanb on 2008-07-12
Sounds like Security has been set in the router (Keeps others from accessing your connection - Requires a password to gain access - If you have another computer using Windows and set the router up on that computer, you may have set a password?  If you did, enter the password and/or see the link I provided below).  If you have a manual for it, it should explain how to configure the router including security settings.  At this point, turn the security off and make sure you can connect to the internet.  Then if you want to set security, see this:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wep](http://ubuntuforums.org/showthread.php?t=202834&highlight=wep)

---

### Post by jerome1232 on 2008-07-12
I worked for 2wire, by default they have wep enabled, should be a 10 digit number on the bottom of you're 2wire, it's between 2 bar codes.

it would be the WEP 64/128-bit Hex

(unless you guys changed it)

---

### Post by ladyredbrc on 2008-07-13
Thank you so much for taking your time to help me. I tried what you said, and it worked! (kind of) Instead of getting the two computers with a exclamation sign, I am now getting the bars at the top. But, there is no signal strength, so I still can't get to the net. I like everything else so far with Ubuntu, but this internet thing is killing me! Do you know what I should do?
Thanks

---

### Post by james_vanb on 2008-07-13
Have a desktop that loves Network Manager and a Laptop that doesn't.  Sometimes a reboot helps - Try it. Otherwise...Try Manual Configuration.

Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WEP and enter password as jerome1232 suggested if that worked for you.  Set Configuration to Automatic configuration (DHCP).  See if that gets you on.

You're close, stay on it.

---

### Post by jerome1232 on 2008-07-13
Also might want to try this you can bump the power up to 10 in that router (or 400 ma), if you have a computer that is connected to the 2wire,

[http://192.168.1.254]("http://192.168.1.254")
[http://gateway.2wire.net]("http://gateway.2wire.net")
[http://homeportal]("http://homeportal")

any of those links should take you into it's configuration screens.

If you click Home Network>>Wireless Settings>>(enter you password)>>adjust it's channel to 6 or 10, those two are usually good and power to like 8 or all the way up to 10 if you desire. May help with the signal. Make sure your router isn't next to a 2.4 ghz cordless phone base, they wreck havoc with wifi signal and I see that alot 'cuz these routers have to be near phone jacks for dsl.

---

### Post by jeffegg2 on 2008-07-15
> **james_vanb said:**
> Have a desktop that loves Network Manager and a Laptop that doesn't.  Sometimes a reboot helps - Try it. Otherwise...Try Manual Configuration.

Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WEP and enter password as jerome1232 suggested if that worked for you.  Set Configuration to Automatic configuration (DHCP).  See if that gets you on.

You're close, stay on it.

I'm showing 100% signal on my wireless, wep entered, and auto DHCP. Still it does not let me in. Darn ATT. The wired works, but I have wireless built in, why not use it!

---

### Post by BenFischer on 2008-07-27
I was trying to follow the post explaining what to code in the terminal, but every time i tried entereing the code it replied with "sudo: unable to lookup (computername) via gethostbyname()"
I'm not sure what that means, maybe someone knows what I'm doing wrong?  Thanks in advance, Ben.

---

### Post by james_vanb on 2008-07-28
> **BenFischer said:**
> I was trying to follow the post explaining what to code in the terminal, but every time i tried entereing the code it replied with "sudo: unable to lookup (computername) via gethostbyname()"
I'm not sure what that means, maybe someone knows what I'm doing wrong?  Thanks in advance, Ben.

Take a look at this:

[http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334](http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334)

Hope it helps.

---

