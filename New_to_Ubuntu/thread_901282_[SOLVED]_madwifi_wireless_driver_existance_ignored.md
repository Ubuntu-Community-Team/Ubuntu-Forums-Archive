---
title: "[SOLVED] madwifi wireless driver existance ignored on aspire one"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by jezza43 on 2008-08-26
hi there
I'm just starting to use Ubuntu.
I installed Ubuntu 8.04.1 on my aspire one and followed the instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) to get my wireless working. The driver downloaded and built fine but when I run "sudo modprobe ath_pci"
I just get an empty prompt back:

jezza~$ sudo modprobe ath_pci
[sudo] password for jezza:
jezza~$ 

I also tried ipconfig but it doesn't detect the Madwifi wireless driver, or any wireless.
It says:

jezza~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jezza~$

I read that it should be telling me about "eth1" or "wlan0" but I get no acknowledgement that my wireless even exists.
If I go to the main menu and choose System > Administration > Network,
the "Network Settings" tool also denies the existence of wireless on my netbook.(It has Wired connection and Point-to-Point connection, but no Wireless connection.)

I'm not sure why this is happening, can someone help? Thanks.

---

### Post by django0909 on 2008-08-26
At the empty prompt enter your password and push enter. You won't see anything, but it is there.

---

### Post by nicedude on 2008-08-26
I am going to assume you typed your password at prompt after "sudo modprobe ath_pci" and that after doing so your output of iwconfig does not contain any wifi enabled devices? If I am correct then you did not get the driver installed correctly or another driver is conflicting with it ( such as Ndiswrapper one ). Also you might want to have a look at System -> Administration -> Hardware Drivers and see if the restricted driver manager "jockey" is trying to manage this interface as well ( I uninstall it but others think it is important ).

All I can say for sure is that I have an Acer 5520 and it is working fine with a Madwifi driver I patched up myself for injection. So if you need specific help then PM me the answer to whether Hardware Drivers lists Atheros and the putput of the following commands and I can try to help you get it going.

iwconfig

lspci -nn

lshw -C Network

Armed with that I can try to see whats going on for you, but I would bet it is that the madwifi driver was not installed correctly so please also give me some heads up on how you tried to install it.

---

### Post by aadb on 2008-08-26
I have just purchased the Acer Aspire One and followed the instructions as per the wiki.

I am having exactly the same problems with the wireless drivers/configuration as the initial poster.

**Edit:**  I may have found the problem.  
It seems that re-enabling the restricted drivers via system>administration>hardware drivers after installing the madwifi drivers via the wiki, then using the one's wireless switch at the front of the One sets everything in motion.

At least that is what I found.
There maybe a more technical reason/solution but I don't have the time to delve deeper right now.

---

### Post by jezza43 on 2008-08-29
After much fiddling (and help from a friend) the wireless driver still hadn't appeared. There was no trace of it in the boot logs either - Ubuntu didn't even bother to load the Madwifi driver.
But then I rebooted and the wireless driver came back. (I have no idea how, but it did)
So now it's working. I'm typing this post over my wireless. :)

I haven't reinstalled the linux-restricted-modules, but it still works.
I might see if the wireless works with the linux-restricted-modules installed, so the package updater doesn't keep telling me "There are 4 updates available." every time I boot Ubuntu.

---

### Post by jezza43 on 2008-08-29
In case someone else has the same problems on the Aspire One that I had, here are the results of the PM:
Ok your iwconfig shows your wifi is loaded, but with which driver I am not sure. Your System -> Administration -> hardware drivers thingy is Jockey or "the restricted drivers manager" it only controls WIFI & NVIDIA or ATI chipset video drivers, for this reason I just remove Jockey all together and manage my own stuff. 

As for if you have Nvidia or ATI graphics you can easily use envyng to install the best driver for you and it usually finds a newer/better one than Jockey does anyway and my wifi I control myself by loading a Madwifi driver by hand. 
I looked at the guide you mentioned and if you followed all the steps that guy is outlining then it should be OK. Here is a guide that I wrote on getting the AR5007 to work in 32bit Ubuntu Hardy ( you have a AR5007 as well, per your lspci output ).

So if you want my guide might be a good read for you to see what is done and why to make the wifi work as I try to explain allot of the stuff as I go. Also if in the Hardware Drivers "Atheros" wifi adapter is checked then that is wrong as it will be trying to use the jockey managed driver with your chipset and instead you need a much newer driver - like the one in the guide you followed or in my guide. 

So if that is checked then uncheck it and reboot and see if iwconfig still shows ATH0 as present. Please do that and then tell me if ATH0 is present and give me the output of "sudo iwlist ath0 scan" and let me see what that says as that will tell us whether ATH0 can see access points to connect to.

Also to manage what network you connect to you use the network manager applet here is the command to open it "network-admin" then click unlock and type password -> Now click Wireless and you can configure your network settings there.

Here is a link to my guide on the AR5007
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

