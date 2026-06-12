---
title: "HOWTO: Using a GSM Cellphone as a GPRS Modem (Sony Ericsson K800i / W800i)"
date: 2007-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by mafitzpatrick on 2007-06-29
This tutorial follows on from [the original tutorial given here]("http://ubuntuforums.org/showthread.php?t=166617").

For those of you with Sony Ericsson K800i & W800i it is possible to use these phones as modems without using KPPP, wvdial or any other application. I discovered this after trying the method in this tutorial & getting a connection but being unable to browse - so if you have this same problem, try this alternative method. This may also work with other Sony Ericsson phones (and indeed other makes entirely) but I can't test.

**Setting Up Your Phone**

First step is to set the mobile phone up to act as a modem.  Go to Settings (bottom right icon on the main icon-menu) and move across until you find Connectivity. This is the section for setting up any networking or file transfer settings for the phone.

In this list is an entry for USB.  Clicking this should bring up a list showing USB Internet (and also "USB Connection" although this will be greyed out if your phone is not connected).  Select USB Internet and then you will be presented with another list showing "Turn on" and "USB data accounts".

First select "USB data accounts".  Here you can choose which account to use to transfer the data - normally you will not want to use a WAP account (for cost reasons) and should instead choose Internet.  On my Vodafone account this was labelled as "Contract Internet" on Orange it is labelled "Orange GPRS Internet" and so on.  Check your contract or talk to your provided to find out which to use if you're unsure.

When you select an account you will be back to the previous list.  Now select "Turn on" and you will be presented with a message informing that the phone will now automatically access the internet when a USB is connected.  Your phone is now ready to use.

**Connecting Your Cable**

Simply plug in the USB cable into your computer and then into the phone.  You phone should display a menu when this happens offering you "Transfer mode" or "Phone mode".  Select the second one and your phone will turn itself into a modem.  

Then... open Firefox and browse.

It really is that simple (for me at least!)  As far as I can tell the phone is being used by Ubuntu as a sort of USB Modem / ADSL Modem - with the phone handling all the connection.  A lot easier than opening PPP programs etc.

Let me know how you all get on - if you have success with more phones than listed here drop a note and I'll update the list.

---

### Post by online14230 on 2007-07-13
GONNA TRY THIS TONIGHT... iLL LET YOU KNOW as soon as I get online from my PC. I cant WAIT!!!

ps: sorry bout the caps... kb faulty.

---

### Post by JetPack on 2007-07-14
Also see my post for the SE w880i.

[http://ubuntuforums.org/showthread.php?p=3017271#post3017271](http://ubuntuforums.org/showthread.php?p=3017271#post3017271)

---

### Post by online14230 on 2007-07-14
Im back.
I tried it last night...
no joy. It connects and IMMEDIATELY disconnects. Im assuming its a problem with ppp because Ive checked all the other tutorials and I can pair the phone, I can browse its files but I JUST CANT GET IT TO STAY CONNECTED. I have no idea what Im doing wrong, but Im gonna go home tonight and try again...

Oh yeah, Im running Dapper and I have a W550i. I tried using the cable as supplied and then I tried using bluetooth...

---

### Post by OuTcRy on 2007-08-30
your problem might be the dialing number.
For example every article that i read says for my p990i is *99***1#
but when i dialed this number, it connected and disconnected.
but when i entered *99***8# i am connected but the connection is hanging.my problem is this :D

---

### Post by t0p on 2008-07-02
> **mafitzpatrick said:**
> 
Let me know how you all get on - if you have success with more phones than listed here drop a note and I'll update the list.

Thanks for the info, mafitzpatrick!! I'd **thank** you too, but there doesn't seem to be a **thank** link in this thread....

---

### Post by extent on 2008-07-02
Hi, i cannot find one website with the correct settings to enter on my computer for my k800i, which is on O2 network. For the internet on my phone it is prepaid gprs,  which is £7 per month, so is not dial up. My laptop internet setup, requires a service name, service phone nos, password and IP address etc to use my phone as a modem, so i am completely stuck. Since it is not dial up, i do not know what to enter on my computer for the internet access phone number it asks for. Can anyone help, if they have managed to get it working on an O2 k800 mobile phone? The internet service on my phone has a limit of 200mb per month, and would prob be slow using it as a modem on my computer, but i wanted to try it out at least once. Thanks very much for any help if possible :)    edit - managed to get it working, but only for o2.co.uk! Surely if it can work for one website i just need the setting to get it working for all http? Unless i need a certain program on the pc to view pages via mobile/proxy?

---

### Post by extent on 2008-07-03
I got it working on my vista laptop for all websites, using my phone as a usb modem! My phone is on uk o2 network. This should be the same for xp. I used the mozilla browser instead of IE, and in tools>options for connection settings, used 193.113.200.195 for http proxy, Port 8080, and selected to use this proxy server for all protocols.

---

### Post by Zymoan on 2009-06-17
I tried this on my old Acer Travelmate 220 running GOS 3.01 and it worked a treat. Excellent thank you for the advice. Now just hope O2 don't kick off. I have unlimited web bolt on but I don't think they're keen on using phone as modem. Am hoping they will be ok with light useage for email / limited browsing etc.

---

