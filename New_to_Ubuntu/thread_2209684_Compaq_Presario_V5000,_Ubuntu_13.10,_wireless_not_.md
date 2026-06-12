---
title: "Compaq Presario V5000, Ubuntu 13.10, wireless not working"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by sue3 on 2014-03-06
I just replaced the hard drive in this laptop and installed Ubunto 13.10 as the only operating system. There is no other os on the hd. I had wireless with the old hd ( Win XP). After the install, from a cd, I no longer have wireless. I have read similar posts and tried the codes given, but no luck. What can I do?

---

### Post by varunendra on 2014-03-06
Welcome to Ubuntu Forums sue3!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us sufficient information to determine and fix the problem.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by sue3 on 2014-03-11
First I want to apologize for taking so long to reply.  I have been  having problems with getting the file to download.  I have it saved to a  CD and have it installed on my Ubuntu desktop.  Oh and in step 2 you  say to double click the file and click on run, run never came up, the  file just opened in plain text.  I can copy and paste but how can I get  it sent back to you? Do I copy it to another CD? I can't get internet  any way with the Presario V5000 so I can't reply to you via that  computer. What am I doing wrong?

---

### Post by varunendra on 2014-03-11
> **sue3 said:**
> ..in step 2 you  say to double click the file and click on run, run never came up, the  file just opened in plain text.

Hello sue3,

Please see the 'Note' below the step 2, which states this behaviour and how to change it :
> **2)** Double-click the file > select "Run" in the opened dialogue box. Provide your password when asked.
**[NOTE 1: ****Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable**. To change this-
**Open any folder > go to Files > Preferences > Behavior tab > select "Ask each time"** option under "Executable Text Files" section.**]**

I don't need that file, it is the script itself which I already have :)
I need the report that it would generate after being run as mentioned in the instructions post.

You will have to copy that generated report file (**wireless-info.txt**, or **wireless-info.tar.gz**) to a USB flash drive or memory card etc., then attach it or copy-paste the contents of it in your next post.

This post is an example of how the file would look like that I need : [http://ubuntuforums.org/showthread.php?t=2082305&p=12373823#post12373823](http://ubuntuforums.org/showthread.php?t=2082305&p=12373823#post12373823)

---

### Post by sue3 on 2014-03-11
I need to apologize for taking so long to reply, but I have been having problems with copying the wireless script.  I saved it to a CD then copied it onto the Presario V5000 desktop.  When I opened it, I wasn't given the "run" command, the file just opened up. My question to you is, how do I get the information from the Presario with Ubunto with no internet to you in this forum? Do I copy it to another CD? Can I take screenshots with my tablet and send them to you? As you can see, I am an absolute beginner.

---

### Post by varunendra on 2014-03-11
I had replied to your same post in the other thread. That post and my reply to it have now been moved here on my request to the mods, please see my answer above.

You have to change the behaviour of the system (as mentioned in the 'Note' part quoted above) so that it offers to "Run" the file instead of opening it as a simple text file.

Then I'll need the report file that it generates after running the script. The report file would be named "wireless-info.txt" or "wireless-info.tar.gz", and will be located in your Home directory or wherever you have "Run" the script from.

How you move that file to a system with internet connection is upto you. Writing that much information by hand would be more trouble than fixing the wireless. :)

---

### Post by sue3 on 2014-03-18
Varun, I must be really dumb because I just can't seem to be able to do step 2.  I only have the folders that came with the install, when I go to any file (desktop, documents, etc) that's where I'm stumped.  There is no preferences or behavior tab, only properties and that does not have anything about executable. Although I have found out that my network controller is Broadcom.Corp BCM4311 802/g/b/g wlan I have typed this into the search box in this forum and haven't been able to find the same thing. So I still have the same problem.  Under network connections, I have the correct wireless connection and password but I can't get internet even when it is wired directly from the modem to the computer running the Ubuntu. I have tried to save the file that gave me the network controller onto a CD but again, I just cant get it to work.  I've tried to save that into a file format to save to my desktop so I can drag and drop it so I can copy it and then post it here but I can't seem to find the correct commands to save it into a file that can be saved and copied. I can copy it but thats all.   I thought that I was average on computer knowledge, but this makes me just frustrated and stupid!   What am I missing?????

---

### Post by Hadaka on 2014-03-18
hi sue3..give this a try please.
open a terminal  ctrl/alt/t and enter...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -rf wl
```
BOOT
hopefully you now have ethernet....wired connection
if yes ..
then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT

---

### Post by squakie on 2014-03-18
Will she also need to add b43 to modules or is that handled by one of the steps?

---

### Post by varunendra on 2014-03-19
> **sue3 said:**
> ..I only have the folders that came with the install, when I go to any file (desktop, documents, etc) that's where I'm stumped.  There is no preferences or behavior tab, only properties and that does not have anything about..

When you open any file or folder, you get its "Menubar" at the top of its window. When I say "Goto File > Preferences....", I mean to click on the "File" option on that menubar, which will further open a drop-down menu where you have to click "Preferences". This will open the "Preferences" dialogue box where you'll get the tab I mentioned. *(by the way, you don't have to feel bad about not being able to find it. First, I should have been more clear, so its my fault, and secondly, these _same_ steps may not apply to 'All' Desktop environments, so the steps may be slightly different if you are NOT using the default 'Ubuntu' setup.)*.

But if you are sure the card is **BCM4311**, the fix Hadaka suggested should work. However, if you still can't get Ethernet (cable) connection after what he suggested, here's an alternative way to manually download the required firmware for that card on another computer, and install it manually on Ubuntu -

Just to be extra safe, to make sure a possibly driver conflict doesn't freeze your system during the process below, please run this command first to remove the conflicting driver, if it is installed (you can open the terminal with "Ctrl-Alt-T" shortcut keys) -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot. Now the steps to install the firmware for the correct driver "b43" -

[indent]**1)** Download the "linux-firmware-nonfree" package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)
**2)** Copy it to your Ubuntu Desktop (using a pen-drive or whatever way you like).
**3)** Assuming it is on the Desktop of your Ubuntu installation, open a terminal (Ctrl-Alt-T) and run the following command to install it -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```
**4)** Let the above command finish its job, then Reboot and see if you have a working wifi.[/indent]

If this doesn't seem to make it work, please report back with the following outputs -
```
lspci -nnk | grep -iA2 net
lsmod
```
You can either copy-paste the outputs to a text file, move it to a different computer with working internet connection and post the files or its contents here.

Please don't hesitate to ask questions if you are having problem following any of the suggestions. We are here to help, and we do it with pleasure.

**@squakie,**
> Will she also need to add b43 to modules or is that handled by one of the steps?
The steps that Hadaka or I suggested are *usually* sufficient to load "b43" correctly. The b43 module automatically loads if a suitable card is found, unless it is still blacklisted somewhere. The default blacklisting done by the "bcmwl-kernel-source" package is removed automatically with the "apt-get purge bcmwl...." command.

So what Hadaka or I suggested above should be all that is needed. It rarely needs to be added to the /etc/modules file, when there is some additional (and mysterious) problem that prevents it from loading automatically.

---

### Post by squakie on 2014-03-19
Thanks!  I'll keep that in mind now if I see something like this again and feel brave enough to try to help ;)

---

### Post by sue3 on 2014-03-24
OK, first I want to thank all of you for all the help.  I've had some personal problems that have kept me from trying to fix this problem.  Now, of all things, I can't remember my password! When I set it up, Linex wouldn't let me use the password I wanted to use so I had to keep changing it until it would.  Trouble is now, I forgot what word I used.  Arrrggggggggg!!!!! I'll keep trying and I'll get back to you.

---

### Post by varunendra on 2014-03-24
> **sue3 said:**
> Now, of all things, I can't remember my password!
How to reset your password : [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) :)

---

### Post by sue3 on 2014-03-24
Varn, I finally found the file,preference, behavior, I just didn't go up high enough to find it on the page,thank you. I ran all the codes you guys gave me and I still don't have internet, wired or wireless. Besides that problem I can't figure out how to copy the terminal screen to a CD or flash drive, so I can let you see the results. I ran that last code you gave and it said "no such file or directory"  I installed the firmware and have results from that but can't get it to you. Again, help!

---

### Post by varunendra on 2014-03-24
If you could run the "wireless_script" on the system, it should have generated a file named "wireless-info.txt" or "wireless-info.tar.gz" in the same place where you ran the script from. Can you find and post that file here?

---

