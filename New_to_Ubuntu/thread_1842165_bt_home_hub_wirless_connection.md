---
title: "bt home hub wirless connection"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by ijr900 on 2011-09-10
Hello to all here at the Linux community,i have made the switch to Linux a month ago and have removed windows totally,my only problem is now going wireless with my BT home hub,can anybody talk me through this or are their previous threads on this subject many thanks Ian

---

### Post by SavageWolf on 2011-09-10
What is the problem? It should be a simple matter of clicking the "network connections" icon thing and selecting it from a list...

---

### Post by haqking on 2011-09-10
> **ijr900 said:**
> Hello to all here at the Linux community,i have made the switch to Linux a month ago and have removed windows totally,my only problem is now going wireless with my BT home hub,can anybody talk me through this or are their previous threads on this subject many thanks Ian


There are other threads on this, though i have never had an issue with BT or there hub in terms of connecting.

I changed it for a netgear as i dont like the hub and think it is slow.

What is your issue ? connecting ?

What ubuntu version are you using ?

have you entered the connection ino manually or you cant see the wireless at all ?

Cheers and welcome to the forums

---

### Post by ijr900 on 2011-09-10
well I am connected with a Ethernet cable,but the thing is i am an absolute beginner really and haven't a clue how to do it, I right click on the connection icon the enable wireless box is ticked,I can go to edit connections and select wireless then new connection,add,then i am asked for an ssid,got that,then it  asks for mode,no idea what to put in there,next is a bssid,not a clue,mac address,i haven't got a mac,then mtu well why noy please help,keep tripping over the wire many thanks Ian

---

### Post by haqking on 2011-09-10
> **ijr900 said:**
> well I am connected with a Ethernet cable,but the thing is i am an absolute beginner really and haven't a clue how to do it, I right click on the connection icon the enable wireless box is ticked,I can go to edit connections and select wireless then new connection,add,then i am asked for an ssid,got that,then it  asks for mode,no idea what to put in there,next is a bssid,not a clue,mac address,i haven't got a mac,then mtu well why noy please help,keep tripping over the wire many thanks Ian


all you need is mode to infrastructure, enter your SSID of the network setting.

Enter WPA or whatever

and thats about it, it defaults to DHCP

this is to create a permanent one.

Does it not see the connection already ?

you do have a mac address (it is the uniqe hardware address of your network card or routers network card) however you dont need to enter that information

---

### Post by ijr900 on 2011-09-10
what does enter wpa mean,lost there,also when i type in the details the apply box doesn't activate,so im stuck

---

### Post by haqking on 2011-09-10
> **ijr900 said:**
> what does enter wpa mean,lost there,also when i type in the details the apply box doesn't activate,so im stuck

Does your system already see the wireless connection from your router ?

if so click on it and it will ask for a key to connect.

Your BT homehub comes with a default WAP key, on a plastic card which you can enter to connect.

If you cant see them then enter the details i mentioned, like i say the default key is on the card they provide you

---

### Post by ijr900 on 2011-09-11
no the wirless connection is not visible

---

### Post by haqking on 2011-09-11
> **ijr900 said:**
> no the wirless connection is not visible


ok so have you created a manual connection, entering the information that comes with your router ?

---

### Post by grahammechanical on 2011-09-11
Did you say that when you click on the network icon (two arrows going in opposite directions when connected by ethernet) that you do not see a list of available wireless networks in range?

If so, then is there a tick mark against Enable Wireless? In other words is wireless switched on?

You may need to install a wireless driver. Go to System Settings and run Additional Drivers and activate a wireless driver if one is available. You need to be connected by ethernet because the driver is downloaded and installed for you.

You do not say what version of Ubuntu you are using. I am assuming 11.04, Natty Narwhal. Click on the Ubuntu icon in the top left corner and in the search field type Additional Drivers and click on the icon that appears.

If you are using an earlier version of Ubuntu then you will need other directions. This is why you need to give proper information like Ubuntu version number and computer model and such stuff.

If you have a laptop then the user manual might give information about needing to switch the wireless adapter on through the keyboard. Is there another operating system on this machine?

Regards.

P.S. A help document was installed as standard. That gives you information on making a wireless connection. Check it out.

---

