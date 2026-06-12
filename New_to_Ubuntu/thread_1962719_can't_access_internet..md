---
title: "can't access internet."
date: 2012-04-21
forum: New to Ubuntu
---

### Post by mlplatt on 2012-04-21
I have, after much tearing of hair and gnashing of teeth managed to install Ububtu 11.10 on my computer alongside Windows Vista already running Firefox via a wireless router. 

What I cannot do is to establish contact with the internet server which automatically starts up when I run Windows on the same machine. I have read with some bafflement other threads on this subject and have enabled all wireless connections that I can find.  I still get notices either informing me that "Firmware is missing" or "Failure to mount location  - Failure to retrieve share list from server" neither of which I understand.  

Firefox on Ubuntu remains dead unlike its counterpart on Vista. 

I have asked my server - PlusNet - for help only to be told that they can't offer advice on Linux systems. 

I would be most grateful for suggestions that a small child might understand ... No on second thoughts not a small child ... they doubtless would have no difficulty. But a geriatric idiot?

Malcolm.

---

### Post by westie457 on 2012-04-21
> a geriatric idiot?

I think not. You are not the first to have problems with wireless setup and you won't be the last.
Here are some commands for you to run in a terminal.
```
lspci -vnn

rfkill list all

lsmod
```

You can open a terminal the quick way by pressing Ctrl+Alt+T.

Post the output of those commands in a New Reply here and paste it between [ code][ /code] tags by clicking the # symbol at the top of the message window.

Welcome to the Forum

Thank you

---

### Post by grahammechanical on 2012-04-21
I am using Plusnet. apart from the instruction being suitable for Windows I had little problems setting up and using wireless to connect to Plusnet through the router/modem supplied.

Can you make a wired or ethernet connection to the router? That should work without any difficulty.

You may need an internet connection to download drivers. It all depends if the issue is with Ubuntu recognising your wireless adapter or you being umfamiliar with how things are done in Ubuntu.

Perhaps we should start from the beginning. The information that westie457 has asked you to provide will help us.

Me? I would like to know if you see an icon for the network manager in the top panel to the right? If so, what do you see when you click on it? Do you see your wireless connection to PlusnetWireless in the list? Is there a tick mark against the two lines: Enable Networking & Enable wireless.

If you have manually set up connections, then I suggest that you go to Edit Connections and delete them. Let Network Manger do the work. Re-boot and see what Network manager shows you when you click the icon.

Regards.

---

### Post by mlplatt on 2012-04-22
Thanks Westie and Graham. 

Westie I have done as you suggested and have the output of the commands. I am however not sure how to get them to you. I cannot of course send them through the Ubuntu programme. I have printed them out and could I suppose scan them but can I attach them to these posts via Vists? The thought of typing almost five pages is depressing. Or am I missing something? 

Graham. I can't connect via ethernet. Well I could do but it is a lengthy and back breaking business which involves moving the whole computer after finding plugs etc currently hidden between an immovable desk and a wall. So I would rather not try unless as a last resort. 
I have a small segment icon on the top right of the screen which resembles a windscreen wiper pattern. I do not see on it any wireless connection to Plusnet, indeed the wireless connection line is greyed out. 

 There is a tick mark against the two lines: Enable Networking & Enable wireless.

I deleted all connections and rebooted but without success. 

Thanks for the welcome

Regards, 

Malcolm

---

### Post by xedi on 2012-04-22
Edit: Seeing chamber's response I misunderstood your problem, so ignore this.

> **mlplatt said:**
> Thanks Westie and Graham. 

Westie I have done as you suggested and have the output of the commands. I am however not sure how to get them to you. 

You can mark the output with your mouse, then right click with your mouse, select copy and then paste it into a reply here (either again through the context menu or ctrl + v)

You also can use the shortcut ctrl + shift + c (note, that in the terminal the usual copy shortcut ctrl + c will instead stop whatever process is going on at the moment there. Quite handy, if something will not finish when doing terminal stuff or you accidently gave a wrong command)

---

### Post by chamber on 2012-04-22
Your Ubuntu partition will have access to your Vista partition. Copy the output of your terminal into gedit and then save the text file to your Vista partition and copy and paste/upload it into your reply from there. 

No need to scan or type all that out.

---

### Post by mlplatt on 2012-04-23
Hi Chamber - My apologies but this is where the stupid idiot bit really kicks in. I am not at all sure how partitions work . I presume one was installed from the disk I bought after all attempets to download and install Ubuntu failed miserably. 

Where and what is gedit? And how do I find the Vista partiton and save gedit into it? 

My ignorance depresses me. Would I, in cosideratiojn of my incompetence, be better served by looking at one of the linux programmes that I understand run within Windows and would thus presumably be able to pick up on the Vista internet connection?  

Malcolm.

---

### Post by chamber on 2012-04-23
Gedit is the default text editor in ubuntu, you can access it by hitting Alt + F2 and typing gedit

When installing Ubuntu alongside Vista you will have created a different partition to install Ubuntu into.

You can access your Vista partition by going to Places, Selecting your Vista partition (it may be called OS or something similar) and then navigating through the exlorer window until you find your user desktop.

In Vista it will more than likely be C:\Users\$Username\Desktop

I am not in front of an Ubuntu machine at the minute and have not used 11.10 so there may be some discrepancies however the basics should be the same.

You could also find that if you were able to plug your machine into the router then Ubuntu would more than likely be able to detect your Wireless card and download suitable drivers for this to work.

---

### Post by audiomick on 2012-04-23
> **mlplatt said:**
> I am not at all sure how partitions work .

A partition is simply a block of storage space on your disk drive. It can be the whole drive, or there can be several partitions on a drive. You can look at it this way: the drive is a cupboard for storing stuff in. Partitions are like shelves in the cupboard. Here is a link explaining pretty much all of what a normal user needs to know. It is a fair bit of text, but it should help you understand what you need to know. Don't panic: it is not that complicated.
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

> 
Where and what is gedit?
Gedit is a text editor. It is one of many available for Linux, and is the standard text editor on Ubuntu. If you are using 11.10, then I assume you are using the Unity desktop. Click on the ubuntu symbol at the top left to open the dash. Type "gedit" in the search box. Click on the icon to open it. If you want to open it from the terminal, just type "gedit" in the terminal and enter. If you want to open a specific file in gedit, from the file manager right click on the file and choose "open with gedit". From the terminal
```
gedit /path/to/file
```
If you don't understand the terminal references, don't worry about it for now. That will come with time. ;)

> 
And how do I find the Vista partiton and save gedit into it?

In the file manager, you should see an icon in the left hand panel that corresponds to your Vista partition. Click on that. This will mount the partition. When it is mounted, there will be a symbol next to it that looks a bit like the eject button on a CD player. If you want to unmount the partition, click on that. This is the same action as safely dismounting a USB drive before you unplug it.

You can also save a text file directly out of Gedit using the "save as" option. Bear in mind that Windows may not recognise the file as a text file, and not automatically open it with it's text editor. I think you can get around this by manually adding the ending, i.e. save it as "filename.txt" . 

 > 
My ignorance depresses me. Would I, in cosideratiojn of my incompetence, be better served by looking at one of the linux programmes that I understand run within Windows and would thus presumably be able to pick up on the Vista internet connection?  

Malcolm.

Don't get depressed, the problems are not insurmountable. I don't know enough about how a wubi install, the one that is "inside" windows, so I don't know if you will have better luck with your wireless by that route. I would suggest sticking it out a bit longer, though. It is worth the effort to get it going right and to learn how it works.

Edit: I would also advise you to plug in the machine to the router with a cable and let the system look for drivers for the wireless card. I believe this should happen automatically. You might need to run the "hardware drivers" utility by hand.

---

### Post by westie457 on 2012-04-23
@ mlplatt

An answer to your question >  Would I, in cosideratiojn of my incompetence, be better served by looking at one of the linux programmes that I understand run within Windows and would thus presumably be able to pick up on the Vista internet connection?

The short answer is **no**.

The explanation to that answer is as follows.
The Linux program that runs inside Windows (WUBI.exe) actually creates a virtual partition and file-system that Windows cannot read or understand.
The virtual partition runs outside of Windows and consequently cannot make use of the Windows drivers as they are not loaded into the system.

You are not the first person to have thought that installing via wubi would allow the use of Windows driver. I did for a while.
Also you will not be the last.

The advice to copy to your Windows partition and post from there is good and will work. As soon as you can post that info we will be able to give better help and advice.


EDIT: @ audiomick
> I would also advise you to plug in the machine to the router with a cable and let the system look for drivers for the wireless card. I believe this should happen automatically. You might need to run the "hardware drivers" utility by hand

Certainly on my laptop with no cable attached the system informed me that 'Additional Drivers' were available even though I was not able to download and install them. The drivers in question were for the wireless chip.
So far in my case after a clean install those Drivers were offered, usually within 2 minutes of starting the system. Even when those drivers were the wrong ones they were still offered.

---

### Post by audiomick on 2012-04-23
> **westie457 said:**
> EDIT: @ audiomick


Certainly on my laptop with no cable attached the system informed me that 'Additional Drivers' were available even though I was not able to download and install them. The drivers in question were for the wireless chip.
So far in my case after a clean install those Drivers were offered, usually within 2 minutes of starting the system. Even when those drivers were the wrong ones they were still offered.

Now that you mention it...

I think I observed that on mine a couple of times too. 

@ mlplatt:
You might get a more compact ouput that tells you what your wireless card is with
```
sudo lshw -class network
```

Here is what I get. You can see my wireless card right at the start, and that it is currently switched off.
Note that when you type your password in the terminal, you will not see what you are typing. Just type in the password and hit enter.

```
mick@mick-laptop:~$ sudo lshw -class network
[sudo] password for mick: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:13:d4:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d6d00000-d6d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:d7:01
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.100.186 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:1000(size=256) memory:d3120000-d3120fff memory:d3100000-d311ffff(prefetchable)

```

---

### Post by mlplatt on 2012-04-23
Thank you all.



I will follow your advice and stick with it. In spite of myself I have begun to develop a fascination. doubtless morbid, with the problem. 

It will be tomorrow now before I can start to venture along the lines suggested in copying the info to the Windows partition.

Today I was convinced that after all the solution might rest in comnnecting directly via an ethernet cable. So I finally managed to dismantel my work space and transport the computer to the router. It didn't work although it occurs to me that the fault might indeed lie in some basic error of mine.   

With the ethernet connection in place.

Under "System Settings  - Networks" there is only one icon which is rather surprisingly (for me) labelled "Windows Network". Attempts to establish a Wired connection  were met with messages ... *'Unable to mount location  - failed to retrieve share list from server*.'


Under Wireless it was* Firmware missing.*


From the file menu, still with ethernet connection, I tried "Connect to server" again. This may be where I am going wrong. Against **Server** I entered *PlusnetWireless* or *PlusnetWireless2C4etc.* The port is already shown as 21. Whether this latter is correct or not I do not know. Against **Type** I selected *FTP with login*


Then there is a space titled **Folder**. I have no idea what is required here so I left it blank. 


Underneath is a section for **User Details** - User Name and Password. I don't know which are required here. My own name and password for access to the server or the router user name and password as established by Plusnet. 


The net result was failure with the message *Plusnet name or service not known*.


So ... I will try again tomorrow. 



Thanks again for all your help and support. 


Regards,


Malcolm

---

### Post by audiomick on 2012-04-23
> **mlplatt said:**
> 

With the ethernet connection in place.

Under "System Settings  - Networks" there is only one icon which is rather surprisingly (for me) labelled "Windows Network". Attempts to establish a Wired connection  were met with messages ... *'Unable to mount location  - failed to retrieve share list from server*.'

What you are describing there sounds like the utility to connect to windows shares and such like on an established network. I can't look to be sure, as I only have 10.04 on this machine.

What you are looking for to establish network connections should be in the task bar at the top on the right. If there is no connection, I believe it is an icon shaped like a segment of a circle or a fan, if you like, with nothing in it. If you have a wired connection, the icon should be a fat arrow pointing up with another one pointing down right next to it. When you have a wireless connection, you have the fan shaped icon again, but filled with concentric curves like when you throw a stone in water.

Left click on that to stop the connection, or start it when it is deactivated. Right click on it for, amongst other things, changing the connection settings.

I'll attach a screenshot that I made for someone else. My mouse is pointing to the icon, and the menu is open. The icon in the picture is a different one again, the one you get with a 3G Dongle, but the principle is the same, and the position is where you should be looking for it.

---

### Post by mlplatt on 2012-04-24
Hi All,

It never rains but it pours!

I can't boot into Ubuntu this mornng. 

I get -

(hd 0,0) FAT16 No WUBILDR
(hd 0,1) NTFS5 No wubildr
(hd 0,2) NTFS5 No wubildr
(hd 0,3) Invalid or null
(hd 1,0) FAT32 No WUBILDR
(hd 1,1) Invalid or null
(hd 1,2) Invalid or null
(hd 1,3) Invalid or null

I have tried both with and without the CD in the drive.

Any suggestions?

In the meantime audimick I have been using the connectio icon. It is what I described in an earlier post as resembling windscreen wipers. Your description of it as a fan is far more elegant. The wired and wireless connections are always shown as greyed out and refuse to activate when I click on them. When I was trying to connect through '*Connect to Server*' the fan rippled and a small window opened beneath it saying 'Disconnected' everytime the attempt failed. 

I will send you the info earlier discussed but first I need to get back into Ububnu iteslf. 

Incidentally this morning I contacted PlusNet about the rather indifferent wireless connection I was getting on Windows and they have now altered the settings for that which has resulted in an distinct improvement in signal strength so perhaps that also might help.

---

### Post by audiomick on 2012-04-24
> **mlplatt said:**
> Hi All,

It never rains but it pours!

I can't boot into Ubuntu this mornng. 

I get -

(hd 0,0) FAT16 No WUBILDR
(hd 0,1) NTFS5 No wubildr
(hd 0,2) NTFS5 No wubildr
(hd 0,3) Invalid or null
(hd 1,0) FAT32 No WUBILDR
(hd 1,1) Invalid or null
(hd 1,2) Invalid or null
(hd 1,3) Invalid or null

I have tried both with and without the CD in the drive.

Any suggestions?


That looks like a reason for a new thread. I think you will get help for that quicker if you start a thread with an appropriate title. I have no idea, sorry. When you get that sorted, you can come back here and pick up on the Internet problem.

---

### Post by mlplatt on 2012-04-25
O.K. It is working again after a couple of re-installations 

Back to the original problem.

I have got the details on to gedit but am still lost on how to get the print out onto the Vista partition. If you will bear with me Michael, you mention the file manager which I take to be the strip on the left of the screen. On my computer this displays only a 'Home', Firefox, 3 Libre icons, a Settings and a couple of miscellaneous others. Nowhere can I find any mention of Vista nor any icon relating to it. I am sure this is because of my complete ignorance of Ubuntu but could you be a little more explicit? 

Failing that I notice that Libre uses the same file extension as Open Office. Could I copy it to a CD and open it in Vista with the latter then paste it here?

Regards,

 Malcolm

---

### Post by chamber on 2012-04-25
When you open your file manager what are the names of the drives that appear down the left hand side?

---

### Post by mlplatt on 2012-04-26
Hi,

Alas I am still not really sure where the File Manager is.

Initially when Ubuntu appears the screen it shows icons on the left 

Dash Home
Home folder
FireFox Web Browser
Libre Office Writer
Libre  Office Calc
Libre Office Impress
Ubuntu Software Centre
Ubuntu One
System Settings
Workspace Switcher
343 GB File System

Searching for File Manager elicits the information that it can be accessed through Home and this gives me a window which does not mention File Manager but which lists on the left

**Devices**

343 GB

**Computer**

Home
Desktop
Documents
Downloads
Music
Pictures
Videos
File system
Rubbish Bin
[B]
Network[/B]

Browse Network


______

Where do I go from here?

Regards,

Malcolm

---

### Post by chamber on 2012-04-26
It will be the 343 GB drive that you can see.

Click into that and see what there is.

---

### Post by xedi on 2012-04-26
When you click on home, then you open the file manager. In Ubuntu when you open folders (such as your home directory) what you see then is the Nautilus file manager, which manages all those folders and files (similar to explorer on Windows), so based on your last post you are on the right track.

My guess is that the "343 GB File System" is your Windows partition (it doesn't matter whether you open it through the launcher or through the file manager, clicking on the launcher will open the file manager). You should see there familiar files and folders. Assuming you have saved your output in common text format with Gedit or LibreOffice, you can then copy that file to your Windows partition somewhere, where you'll find it again when booting Windows again.

Your suggestion to use a CD would work, too, (or USB Stick for that matter) but copying it directly from your Ubuntu partition to the Windows partition is more straight forward (ironically it wasn't in this case but from now own you'll know how to do it and it will be more straight forward in the future :)

---

### Post by westie457 on 2012-04-26
Hi, now we are rolling.

The 343GB file system is your Vista partition.

Now in Ubuntu locate the file you created in gedit, right-lick and select 'copy,. Navigate to the 343GB partition and paste the file where you can find it easily.

Reboot into Vista locate and open the file and in the 'Edit' menu select all then copy.

Come back here while still in Vista, click 'New Reply', then click the # at the top of the window - [ code] [ /code] brackets will appear - paste into the small space between those brackets.

We will then have most if not all of the required info to help you further.

---

### Post by mlplatt on 2012-04-26
Rolling perhaps but intermittently at best. 

I have been trying for the last hour to copy the file into Vista but without success either as a .txt file via gedit or latterly as an.odt file via Libre. 

It seems that the only files I can see are ones created before the partitioning. I have tried  transferring to documents and also, to make it obvious, to desktop but without success. I have even opened a new File on the Vista desktop to welcome the printout. But that doesn't come up in Ubuntu either. 

I will keep trying .....

Regards Malcolm

---

### Post by mlplatt on 2012-04-26
Still not getting anywhere. The file just does not transfe. Perhaps I should look at the CD route after all ... If I can find how to burn a CD on Ubuntu. Or is it something I need an Internet connection to download? Can you guide me?

Regards Malcolm

---

### Post by mlplatt on 2012-04-26
I have uploaded as a .txt file the printouts taken from Ubuntu and transferred to Open Office on Vista. 

It is the best I can do for the moment. I just hope it works

Regards,

Malcolm

---

### Post by mlplatt on 2012-04-26
If at first you don't succeed ....

It covers the following commands lspci -vnn : rfkill list all : lsmod : sudo lshw -class network

---

### Post by westie457 on 2012-04-26
Thanks for the info. We now know you have a Broadcom 4318 chip.

Try to install the driver this way.

Try to install the driver this way.

1, Boot your machine normally then load the CD into the tray.

2, Click on Places and open anything listed there. If you see anything that looks like 700 MB Filesystem choose that.

3, Navigate your way through pool > main > b > build-essential and double-click on the .deb file it should then install with Software Centre. If it (build-essential) is not there go back one level to the b43-fwcutter folder and install that.

4, Remove the CD and reboot.


If still no luck then you will have to try the instructions here.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Scroll down about 1/6th to the section that starts with 'STA no internet' and follow those instructions.

---

### Post by mlplatt on 2012-04-27
Hi,

This is getting embarrassing but I cant find Places!

The nearest I get is when I go via Home and select View. This gives me access to a 'Sidebar' which in turn lists ' Places' and 'Tree'. 'Places has a dot before it but clicking on it seems to have no effect. 

What am I doing wrong?

Regards,

Malcolm

---

### Post by westie457 on 2012-04-27
Sorry about that, it was my fault. I mis-read the version you are using. (note to self - get eyes tested).

Anyway, clicking on the house symbol in the panel on the left of the screen opens your home folder. In that window at the top left is your devices (partitions, other hard drives if fitted, USB sticks if plugged in and mounted and CDs/DVDs in the tray). If they have names they are listed by name. If not they are listed by size so you probably should look for 700MB file system. Attached is a screenshot that shows my set up and the device that has the install ISO on it. It is the bit highlighted in orange.

If after all this it does not work what would be the chances of you plugging a cable from your computer straight into the back of the router?

PS: Read in one of your earlier posts something about developing a morbid fascination on getting this sorted. That is exactly how I got started. This is fun to do and when its sorted you will be glad you stuck with it.

---

### Post by mlplatt on 2012-04-28
Hi Westie,

Curiouser and curiouser.

Today there was a new development in that each time I boot into Ubunto I get the following message -

***Unable to mount 44GB File4 system***

*DBus error.org.gtk.Private.RemoteVolumeMonitor.Notfound: The * volume was not found *

(actually there is something else marked by * but I can't read my own writing!)

I don't know if it is relevant but it is new.

What is also new is that again for the first time 44GB System is listed under Devices. There is no pool file in it however. 

Thus the files listed under **Devises **are 

44GB File System. 
My Book.
Ubuntu 11.10i386.
343 GB File System

In the latter there is apool file which eventually leads to the b43-fwcutter folder which however won't install .. the click point remains grey.. I haven't located yet the  build-essential  folder. 

I can connect to the router by an ethernet cable but I can't get any internet connection that way either.  If you read back through the post I have covered this. 

Fun .. Well intriguing yes. I only wish I had started it when things were not quite so hectic :)

---

### Post by westie457 on 2012-04-30
Hi mlplatt

First things first, apologies from me for not replying sooner.

Now back to your original issue. At a guess I would say that the one you need to look at is Ubuntu 11.10i386. Refer back to my earlier post for what to do.

I am getting the next stage ready if this does not work.

Concerning the error message about the volume not found I have no idea what caused it.

IMHO there is not a lot we can do about it until you have internet access on the Ubuntu system. The error might magically disappear when you have the wireless chip working.

---

### Post by mlplatt on 2012-04-30
Please don't apologise. I am only too grateful for whatever time you can spare. I myself have been tied up for most of the day and may not be able to get here at all tomorrow. 

I didn't mean to distract you about the new window. I just wondered if it was relevant. 

I found pool under Ubuntu 11.10i386 and followed it as you described to b43-fwcutter folder. I didn't see any build-essential or .deb file.

I couldn't see an instal instruction ..only an open. Clicking on this brought the message 
[I]
"Internal Error. The file "media.b43-fwcutter_014-9_i386.deb" could not be opened.[/I]

Is there a separate install possibility? 



By the way without wishing to distract you further one thing that does niggle away at the back of my mind is my failure to complete the "Connect to server" instruction.I mentioned this in an earlier post. Grahammechanic also uses PlusNet which elicits no response for me. There is also in that box a space marked 'folder' which starts with a '/ 'and which I left blank as I had no idea what it refers to. Nor am I entirely sure what user and password they want. Could it be that simple?


Regards and thanks again.


Malcolm

---

### Post by westie457 on 2012-04-30
Hi here is the next stage after the debacle of the last one failing. Build-essential has been removed from the ISO. As stated in the link you will have to boot into Windows (silly me, you are already in Windows to post in this Forum)

Go to here
[http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)
And follow the instructions exactly as they are written. Keeping everything crossed your wifi router should now be recognized.

As for the bit below.

> By the way without wishing to distract you further one thing that does niggle away at the back of my mind is my failure to complete the "Connect to server" instruction.I mentioned this in an earlier post. Grahammechanic also uses PlusNet which elicits no response for me. There is also in that box a space marked 'folder' which starts with a '/ 'and which I left blank as I had no idea what it refers to. Nor am I entirely sure what user and password they want. Could it be that simple?
I am guessing that it has something to do with 'Samba' and 'SSH' - networking to another computer.

Personally I have managed to set that up once in 3 years of trying then I ended up wiping the hard drive on one machine and have not been able to set it up since. Not an issue for me as the content of each machine is very nearly identical.

When the wireless is working feel free to start another thread about setting up 'Samba'.

---

### Post by mlplatt on 2012-05-03
Westie  Work outside computers is all pervading at the moment. I will be tied up until Monday I think .. I have also to work out how to get the file onto the flash drive. I have only ever used one to input music before burning to disk.  

So I have not given up ... just trying to find time

Regards,

Malcolm

---

### Post by mlplatt on 2012-05-03
I have managed to get the b43 file onto the Ubuntu Desktop but when I right click on it there is no 'Extract Here' listed amongst the options. 

I have tried clicking on 'Open' but that just lists the contents of the file. 

I have typed the appropriate command into the terminal but without a reaction.

Malcolm

---

### Post by westie457 on 2012-05-03
Hi, have just seen where I went wrong.

Try this:-

Right-click the downloaded file, select 'Open with Archive Manager'.
At the top of the next window is a button marked 'Extract', hit that  then hit another button also called 'Extract' at the bottom right of the pop up window. This will create a new folder containing the extracted driver files, the name of the folder will just be 'b43' with no .zip extension.

Follow the directions posted earlier remembering to use the newly created folder.

After this your wireless should be working. Post back here with the news - good or bad- for the next steps.

Catch you later.

---

### Post by mlplatt on 2012-05-04
Hi. 

Another snag. When I try to open with archive Manager  get 

"Could not open b43.
archive type not supported."

Malcolm

---

### Post by westie457 on 2012-05-05
Now that is strange. 

Aahh got it now, that download has a .zip extension (windows) not a tar.gzip extension (Linux). Work a round for this is as follows:-

Have just tried this


In Windows right-click the downloaded file select extract here.

This will extract the files to a directory called b43, inside there will probably another directory also called b43 - this one contains the extracted files - and is the one that needs to be copied over to your Ubuntu Desktop.

In Windows Explorer the path will be something like c:\users\'your name'\downloads\b43\b43   in the main window will be a list of files.

So remembering to copy over just the one folder and following the earlier post's instructions for the commands in the terminal it will work.

Again post back here with any news for the next steps.

---

### Post by mlplatt on 2012-05-07
I copied over the b43 file within the b43 file duly extracted.

When I typed the frst line into the terminal. I got the message -

*"cannot create directory 'lib/firmware/b43'; file exists"*

Malcolm.

---

### Post by westie457 on 2012-05-07
That is okay, just run through all of those commands.

All being well your wireless should work after a reboot.

As always post back with the news.

---

### Post by mlplatt on 2012-05-09
Hi Westie,

SUCCESS!!!

And as proof this is accessed from Ubuntu. 

I can't thank you enough. Sorry for all the occasions on which I was more than usually obtuse. Your patience was quite exemplary :)

Warmest Regards,

Malcolm

---

### Post by westie457 on 2012-05-09
HOORAY.

Glad it is now working and you have access to the internet.

Do you still need help with some of the other issues you were reporting at the start of this mini-marathon?

Go ahead and enjoy yourself.

When you get chance could you mark this as [COLOR="Red"]solved[/COLOR] using [COLOR="Red"]Thread Tools[/COLOR] at the top of the page. Thank you.

---

### Post by mlplatt on 2012-05-11
Hi Westie 

The box telling me that there was an error involving D44 has disappeared. 

There are a couple of points that I would like your advice on. On the desktop I am left with a file b43. Is there somewhere lees evident that it can be moved to. Presumably it is needed somewhere so I can't bin it. Or is it just a copy?

Secondly, and this should perhaps be the subject of a fresh thread, when I turn on the computer it goes straight to Ubuntu and I have to scroll down to select a line relating to Windows and click on it before I can get to the main screen giving me the choice of Windows or Ubuntu. 

Is is possible to go straight to a screen giving me the option to go to Windows or Ubuntu?

Thanks again,

Malcolm

---

### Post by westie457 on 2012-05-11
> **mlplatt said:**
> Hi Westie 

The box telling me that there was an error involving D44 has disappeared. 

There are a couple of points that I would like your advice on. On the desktop I am left with a file b43. Is there somewhere lees evident that it can be moved to. Presumably it is needed somewhere so I can't bin it. Or is it just a copy?

Secondly, and this should perhaps be the subject of a fresh thread, when I turn on the computer it goes straight to Ubuntu and I have to scroll down to select a line relating to Windows and click on it before I can get to the main screen giving me the choice of Windows or Ubuntu. 

Is is possible to go straight to a screen giving me the option to go to Windows or Ubuntu?

Thanks again,

Malcolm

Hi to be on the safe side DO NOT bin it in case you need to use it some time in the future. Instead move to somewhere you can find it easily Where you move that folder to is not important as the necessary files have been installed.

About the Grub issue one thing you can try is open a terminal type in and run ```
sudo update-grub
```this should then give you the options at boot time.
If not then by all means start a new thread about it. Changing Grub is not my strong point.

Good luck.

---

