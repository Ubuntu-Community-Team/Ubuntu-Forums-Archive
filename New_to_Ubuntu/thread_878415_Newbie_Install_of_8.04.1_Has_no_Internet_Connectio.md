---
title: "Newbie Install of 8.04.1 Has no Internet Connection."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by SidTheKid on 2008-08-02
Just installed Ubuntu 8.04.1 from a downloaded iso. Everything went well and I have a dual-boot scenario up and running with Windows XP. The weird thing is, Ubuntu doesn't recognize my network connection. I use a USB USRobotics modem on this machine to connect and it has been flawless in XP for two-plus years. I'm on Hughesnet satellite service---in fact, I'm using XP to post this query. Never a problem, dynamic stuff, and all. A few months ago, I ran an earlier Ubunto distro in livecd mode and had connectivity without any action on my part (at least, I *think* I had connectivity then---it seemed, at the time, that everything was perfectly normal in Ubuntu without any action on my part (livecd version). Any ideas?

---

### Post by K2712 on 2008-08-02
Have you check the [wired ethernet troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=87644")?

If you still have problems, post the output of the following:

```
ifconfig -a
```
```
lshw -C Network
```
```
lspci
```

---

### Post by SidTheKid on 2008-08-03
Thanx, K2. Will do first thing tomorrow. Your help is much appreciated.

---

### Post by SidTheKid on 2008-08-03
K2, I should have said that the USRobotics modem is wireless! I've since looked at a bunch of previous threads concerning problems with wireless connections and, so far, am getting nowhere. I have no idea how to fo the "code tests" you suggested.

My ISP is Hughesnet (satellite) and, in Windows XP on the same machine (dual boot), Firefox works flawlessly (NOT SO, SEE EDIT, BELOW). In both, FF is set "no proxy". That's it, no other settings are required. Everything is dynamic and automatic. Hmmmmm? Any additional ideas?

EDIT: Well, I was wrong about that. I've now got no connectivity in Windows, either. I'm looking into the situation in Windows and am hoping I find an answer that will also correct the connection problems in Ubuntu. For the sake of clarity, I have two desktop computers sharing a keyboard, monitor, and mouse via a wireless KVM switch. I have installed Ubuntu 8.04.1 on one of these machines (the one I'm NOT on right now).

EIDT2: I later discovered that the USRobotics Wireless USB Modem installation in Windows had become corrupted and I had to completely reinstall the modem in Windows XP. Of course, this didn't do me any good with Ubuntu and, when I tried to do the same in Ubuntu, the latter will not open files on the modem's CD. So, I'm still stuck, wondering what to do to get internet connectivity.

I poked around and found "terminal" and typed K2's commands and each one opened a bunch of stuff that I have been unable to copy and paste to a folder that I can access from Windows (to post here). The "Copy" command seems to work, but, when I go to paste into the folder, the "Paste" line in the dropdown box is grayed out. Guess there's a whole lot I have to learn about Linux, huh?

---

### Post by CatKiller on 2008-08-03
> **SidTheKid said:**
> I have no idea how to fo the "code tests" you suggested.

Applications -> Accessories -> Terminal.

---

### Post by SidTheKid on 2008-08-03
What ????

Please see my EDITs in my previous (last) post.

---

### Post by TJCIB on 2008-08-03
go to Applications and you can find the text editor in the first menu.

Copy you terminal outputs to there, then you can transfer the file to your windows machine using a pen drive.

You could also do it in Open Office, just be sure to save it in a compatible format.

---

### Post by K2712 on 2008-08-03
> **SidTheKid said:**
> K2, I should have said that the USRobotics modem is wireless! 

Are both of your machines connected to the modem wirelessly, or via ethernet?

Also, you can take a screenshot of the output of those commands using Gimp.

File->Acquire->Screenshot->Take a screenshot of a single window

When you hit snap, your cursor will turn into a crosshair, just click on the terminal window and then save the resulting image file to paste here.

---

### Post by Ed J on 2008-08-03
You might need to use ndiswrapper to get your wireless adapter to work.  Do a search for "ndiswrapper" it is well documented, I've used it successfully in the past, but not enough to give you a tutorial. GL

---

### Post by Ptero-4 on 2008-08-03
First. How is the modem connected to the PC (not to the ISP)? through the USB port or via wireless card?
Second. if it is connected to a USB port can you send also the output of
```
lsusb
``` just to see if the modem get recognized at all.
Or if it connects to your wireless card post the lsusb and ```
lspci -v
``` to see if your wireless card is supported.

---

### Post by TJCIB on 2008-08-03
I agree.

If you are connecting to your wireless modem via a wireless adapter, it's hard to tell which one is not working.  I would say find the documentation for your wireless card/adapter first, get that up and running.

I'll bet it's not a modem problem, but an adapter setup issue.

Just curious: what type of wireless adapter are you using.

Also, what is the model of your wireless modem?  Is it the 9108?

---

### Post by SidTheKid on 2008-08-03
Okay, folks, according to the USRobotics website, it looks as though this particular modem is incompatible with Linux and no driver updates cure the deficiency.

I have a spare D-Link AirPlus G DWL-G510 Wireless PCI Adaptor, anyone know if it'll work with Linux?

---

### Post by TJCIB on 2008-08-03
You haven't said exactly which modem it is, but if its the one I think it is: After reading some threads, you should be able to get internet through that modem/router.

It seems the trouble people have been having is getting the print server function to work.  This says to me that if you get your wireless adapter working, you should but cruising the information superhighway real soon...

Its best to search the forums for your wireless adapter first.  You are experiencing a common problem.

---

### Post by SidTheKid on 2008-08-03
> **TJCIB said:**
> go to Applications and you can find the text editor in the first menu.
Many thanx, TJ, good advice to keep handy. However, in this case, it appears that the modem is incompatible unless someone has a way around the problem :(.

---

### Post by TJCIB on 2008-08-03
Can you tell us exactly which modem it is?
USRobotics _________________

with some model number or something?

---

### Post by SidTheKid on 2008-08-03
> **K2712 said:**
> Are both of your machines connected to the modem wirelessly, or via ethernet?

Also, you can take a screenshot of the output of those commands using Gimp.

No, K2, the other machine is connected with a CAT5 cable to the router.

The terminal output is several screens long. I think the best way would be the cut and paste approach you suggested. I'm running out of time right now and may not be able to get much more done tonight. There are a couple of other things I need to check out.

---

### Post by SidTheKid on 2008-08-03
> **TJCIB said:**
> Can you tell us exactly which modem it is?
USRobotics _________________

with some model number or something?

Sorry about that---the model number is USR5422. It is a 802.11g 54Mbps USB Adaptor.

---

### Post by SidTheKid on 2008-08-03
> **TJCIB said:**
> I agree.

If you are connecting to your wireless modem via a wireless adapter, it's hard to tell which one is not working. 

But, TJ, I have a third desktop (wife's) and a laptop that have no problem connecting wirelessly. This rules out the router as the culprit. Has to be the USRobotics adaptor.

---

### Post by SidTheKid on 2008-08-03
> **Ed J said:**
> You might need to use ndiswrapper to get your wireless adapter to work.  Do a search for "ndiswrapper" it is well documented, I've used it successfully in the past, but not enough to give you a tutorial. GL

Whoa, Nellie!! Ed, the sourceforge website Installation Instructions are absolute Greek to me!! See here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/). An old electronics engineer friend from years back who cut his teeth on Unix can probably waltz right through this stuff, but, not I. This is too bad, since ndiswrapper sounds like the answer to my problem. Many thanks, anyway :popcorn:.

---

### Post by SidTheKid on 2008-08-03
Ptero, I ran "lsusb" and  the USRobotics wireless adaptor was listed. Running "lspci -v" didn't list a reference to the USRobotics adaptor, just mostly a ton of nvidia stuff.

The router is a Buffalo Air Station Wireless G unit. It is connected to a second desktop via a CAT5 cable, and, to the computer with Ubuntu via the USRobotics wireless USB adaptor which is just like a thumb drive, plugged in to a USB port on the computer. This device has been working perfectly under Windows XP.

---

### Post by CatKiller on 2008-08-03
> **SidTheKid said:**
> Whoa, Nellie!! Ed, the sourceforge website Installation Instructions are absolute Greek to me!! See here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/). An old electronics engineer friend from years back who cut his teeth on Unix can probably waltz right through this stuff, but, not I. This is too bad, since ndiswrapper sounds like the answer to my problem. Many thanks, anyway :popcorn:.

Perhaps this page might be better; [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Plus, of course, there's plenty of information on this forum. Shout if you get stuck.

---

### Post by Ptero-4 on 2008-08-04
> **SidTheKid said:**
> Ptero, I ran "lsusb" and  the USRobotics wireless adaptor was listed. Running "lspci -v" didn't list a reference to the USRobotics adaptor, just mostly a ton of nvidia stuff.

The router is a Buffalo Air Station Wireless G unit. It is connected to a second desktop via a CAT5 cable, and, to the computer with Ubuntu via the USRobotics wireless USB adaptor which is just like a thumb drive, plugged in to a USB port on the computer. This device has been working perfectly under Windows XP.

First off. The USRobotic thing is a USB wireless dongle that you bought? or is a piece of special equipment that your ISP gave you and that functions as the "bridge (like the DSL modem for ADSL users or the cable modem box for cable modem users)" between your Satellite conection and your router (which I guess is the one sharing the conection among your PC's)?

Second, by what you said from your lsusb it might seem that at least linux sees the usb thing and you might need drivers (you might need to take the windoze ones and install them via the "windows wireless drivers" control panel in the System>Administration menu).

---

### Post by SidTheKid on 2008-08-04
Thanks, Petero. The USB adaptor is one I purchased and is a standalone wireless adaptor.

Ah, you have reinforced my hope that I'm on the right track because I have already started the Ubuntu process to get the Windows driver "adapted", but, the procedure is more than a bit foreign to me (since I've been a lifelong Windows victim). I don't know enough to verbalize what I have done so far. Suffice it (I hope) to say that I am messing with such things as ndisgtk, and the like, and am getting acquainted with the "terminal". 

However, something I did a bit ago caused the Ubuntu system to freeze and I had to reboot the computer. It was while I was trying to install/adapt the Windows driver. Can't blame the system for freezing up---I've been quite a burden to it during this procedure. I'm still trying and won't stop until I see total success! Of course, for that to happen, I'll have to pick your brain(s) again---many more times. Hope you don't mind. The help of all is certainly appreciated. Thank you, all.

---

### Post by louieb on 2008-08-04
A quick [Google Linux Search]("http://www.google.com/linux") found this guy who got a USR5422 up and running with  ndiswrapper.  Looks like a real pain but at least now you know it can be done. See post #4.
[http://ubuntuforums.org/showthread.php?t=712017](http://ubuntuforums.org/showthread.php?t=712017) 

The DWL-G510 Wireless PCI Adaptor may or may not work. Seems it was made with two different chip sets the RALINK and the Atheros.
The later should work. You will just have to stick it in and try it.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by SidTheKid on 2008-08-05
> **CatKiller said:**
> Perhaps this page might be better; [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Cat, your link (quoted above) states (in bold) that those instructions are not for Ubuntu desktop CDs, which is what I am using. However, I went through them and, it would appear, successfully installed the two, or three, packages it said were needed via Synaptic, but, nothing is working yet.

QUESTION: Is there a wireless adapter that I can purchase that will work right out of the box? I would really like to get my Ubuntu setup going full bore before I have to learn how to manually set up stuff in what is still to me a foreign "language". Besides, I'm no programmer and all my experience has been manipulating things in the Windows OS through its GUI.

EDIT: After posting this, I searched further and the **Belkin ME1001-USB Wireless USB 2.0 Adapter 802.11g** product is claimed in a linux forum to be immediately functionsl out of the box. Any experience out there among you good people?????

I should add that I have purchased two good books: *Ubuntu For Non-Geeks,*and *Ubunto Linux Toolbox*, although the latter is daunting at this time.

---

### Post by CatKiller on 2008-08-05
> **SidTheKid said:**
> Cat, your link (quoted above) states (in bold) that those instructions are not for Ubuntu desktop CDs, which is what I am using.

Does it? Sorry, I hadn't read the page, not having done any NDISWrapper stuff myself. I just thought it might be easier to follow than the page you linked to before.

---

### Post by SidTheKid on 2008-08-05
Okay, here is a whole new approach that I'm hoping will be a foolproof way to get my Ubuntu computer connected to my network. Please tell me that I can install a wired (CAT 5) PCI card and have immediate connectivity. Please say YES !!:)

---

### Post by louieb on 2008-08-05
I've run Linux on computers with a 2 dollar PCI NIC,  picked up at  the local swap meet.  Haven't seen a wired NIC that did not work out of the box yet.
I've use NetGear,  USR, Intel and   But probably 99% of 10/100 speed PCI NICs will be plug and play.

---

### Post by CatKiller on 2008-08-06
I only have a sample size of 8, but every single computer that I've connected to a wired network has worked straight away.

---

### Post by SidTheKid on 2008-08-08
Well, Louie and Cat, my own experience follows your lead, I'm happy to say. First, I used the liveCD to check if the hardwired lan connection worked. It did and I am now reformatting the C:\ drive with the Ubuntu partitioning utility to get rid of Windows and devote the entire computer to Ubuntu. It's a great feeling to be dumping Micro$oft and all the leach software companies such as Adobe (Photoshop, etc.) and Symantec, and the myriad companies (like Symantec) that impose a one-year limit on your "purchase" before requiring a "license renewal". What BS the commercial software industry has become. Well, they will pay the price as Linux distros slowly, but surely, infiltrate the ranks of M$ victims.

Of course, I do want to keep a Windows XP partition up on one of my machines for Autocad and Photoshop, but, I can't think of anything else that Ubuntu doesn't provide. Heck, I've been a very happy camper with WordPerfect v.9 for years. Never even thought of using Word. Also, have been a Firefox and Thunderbird fan for years and never blinked in the transition from  the bloated M$ crappola.

Sorry for the happy rant, but, this *is* an exciting time for this computer user. And, thanx for all the help you guys have provided in this thread. For now, I'm not going to sweat wireless compatibility. I'll wait until I know my way around Ubuntu before I revisit that issue. Enough to have hardwire service.

Later, ...

---

