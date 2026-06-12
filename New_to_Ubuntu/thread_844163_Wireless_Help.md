---
title: "Wireless Help"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by singh763173 on 2008-06-29
Hi, 

Ive finally got around to installing Ubuntu onto my laptop which i bought not so long ago. Ubuntu was never really planned to be installed but ive used it at work and liked it. Problem is, that i have to disable the LAN in my bios before i can boot into Ubuntu. This means i cant use my wired or wireless connection.

Ive been looking around but am completely dumbfounded by all the new jargon related to Ubuntu and was wondering if someone would be kind enough to help me out. I dont really want to purchase a new wireless adapter as i would like to get the one built in to work. But if it doesnt then i will buy one. Currently, Vista Device manager tells me i have this wireless card installed Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter. Can it get working and how please?

Many Thanks

SINGH763173

---

### Post by Otto-C on 2008-06-29
Suggest you provide the output from the following commands,
also the particulars of your laptop (make model etc.) for the help you need.

lspci -nn

ifconfig

iwconfig

lsb_release -d

uname -r

lshw -C network

---

### Post by singh763173 on 2008-06-29
hi otto, thanks for your reply.

im a noob to ubuntu so please excuse my ignorance :) where do i put these commands? is there an equivalent to Command Prompt?

Also its a Toshiba Satellite L300

Thanks in advance

---

### Post by Pjotr123 on 2008-06-29
Applications - Accessories - Terminal

That's where you can copy/paste the commands.  :-)

Also check this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by singh763173 on 2008-06-29
Hi Pjotri123, thanks for your reply.

Im currently away from the laptop atm so will do the commands tomoro. 

Problem now lies with the net. i cant actually download the updates at all as i dont have net connection cos i have to disable the LAN in bios. 

Is there another way to get suitable updates?

---

### Post by singh763173 on 2008-06-29
also sorry, i forgot to mention. i HAVE to disable LAN in bios otherwise Ubuntu never loads. the bar jus continues to scroll along. 

thanks in advance

---

### Post by singh763173 on 2008-06-30
Hi again, 

Attached is a open office document with the results of the commands.

Thanks in advance

- EDIT - 

Ok, ive just found the ODT file exceeds forum limit. so i have zipped it up.

Thanks

---

### Post by Otto-C on 2008-06-30
The information should provide some more knowledgeable than I
to assist you.

otto-c

---

### Post by singh763173 on 2008-06-30
does that mean you cant help?

thanks in advance

---

### Post by singh763173 on 2008-06-30
Someone please help. I really want to get this working :( and if it cant get working then please suggest a plug and play usb wireless adapter.

Please 

Thanks in advance

---

### Post by mbarvian on 2008-06-30
Hi.  I have a Toshiba laptop with the same wireless card.  Here's a guide (look at the first section) to get it working, but it doesn't support WEP, WPA, or WPA2 encryption, just unsecured networks:

[http://ubuntuforums.org/showthread.php?t=839108](http://ubuntuforums.org/showthread.php?t=839108)

Here's a different tutorial that works much better, but only on some laptops (I think it'll work on yours):

[http://ubuntuforums.org/showthread.php?t=792092&highlight=rtl8187b](http://ubuntuforums.org/showthread.php?t=792092&highlight=rtl8187b)

Hope one of these helps!

---

### Post by panhandle on 2008-06-30
Hi,

I was in your exact same situation with that Realtek wireless chipset.

My advice to you is to save yourself two weeks of misery and simply buy the Linksys WUSB54G USB dongle.

This has the RT-73 chipset. Natively supported, this device will work "out of the box" when you clean install Hardy.

Pick it up at Best Buy. The finest $35 I've spent in some time.

---

### Post by JC Casiano on 2008-06-30
I seem to remember posts a bit ago about blacklisting drivers for the 8187.  There is a file called "blacklist" in the /etc/modprobe.d directory.  If you use "vi" to edit it from the command line, you might see various versions of 8187 blacklisted; you need to be "su" to edit this file.  Perhaps you can add an additional line "blacklist r8187b" to it, and see if the OS will boot.  That doesn't solve your problems, as you would still need to connect to a network somehow to download any updates, but I hope it will give you an opportunity to try different adapters while booted until you can find one that works.  

I've had some luck with ndiswrapper for some of my machines, but I tend to get them working and then fallback to my Atheros adapters.  I think I might have an 8187 but if it's the one I'm thinking of I was forced to use it unsecured under ndiswrapper.  I'll try to find my post from several months ago...

---

### Post by singh763173 on 2008-07-01
mbarvian you are a genius my friend.

i have successfully connected to the net with that first link and am actually writing this post through ubuntu :D

cant thank you enough.

________________________

Now to be a pain the behind again :|

it seems that i need to add all those commands in terminal everytime i reboot. i also still have to have lan disabled in bios. 

and lastly ive gotten quite used to security on my net... and it jus feels weird without it lol, so im gonna try the second link if i can fix the other two probs :)

hope you can work ur magic again

many thanks

---

### Post by JC Casiano on 2008-07-02
You might still need to blacklist the driver if there is a built-in one, to keep Linux from locking up.  I saw a post that indicated it is "blacklist rtl8187".  

And to get ndiswrapper to autoload I believe you have to pass it the -m option post configuring.  I have ndiswrapper running for a rt2870 on my notebook, don't have to do anything special to load it, and I remember running that command but I don't remember if I ran it while configuring or post configuring.

---

### Post by singh763173 on 2008-07-02
JC Casiano, thanks for your reply. i did notice (as a test) that when i left the security on and tried to connnect it locked up. If i understand correctly, when you say blacklist the driver, does that mean i can use the security and not have it lock up?

Many Thanks

---

### Post by JC Casiano on 2008-07-03
I might have misunderstood your problem, but I thought that you were having a problem with Ubuntu hanging if the adapter was enabled while you were booting.  Since I didn't know what state you actually reached I assumed that you were actually able to get at least the splash page, which means the hardware didn't have to be entirely disabled (like completely shut off in BIOS or something).  The last time I had this problem, it was due to Ubuntu trying to load the built-in driver for the adapter.  I had to blacklist the driver to get in, then load the ndiswrapper driver to make it work correctly.  So, I think the answer to you last question was "yes"?

---

### Post by singh763173 on 2008-07-03
If the LAN is enabled in bios, ubuntu continues to try to load, (it doesnt hang, (by hanging i mean crash)). Im trying to find a way in which i can boot straight in and not have to disable it as i still have a vista boot partition and find its extra work going into bios, saving new settings and restarting.

Thanks

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by lio_013 on 2008-09-20
try this 
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)
it may help

---

