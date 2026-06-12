---
title: "Can't connect to wireless"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by peteporchos on 2012-05-10
Sorry to bother you.

A few days ago I installed Lubuntu 11.10 on a Sony Vaio PCG-TR1MP.  This machine has 256 MB RAM and a 900 Mhz processor.  

While I was installing I selected the wireless adapter and completed the fields for SSID and password.  Everything went reasonably well and the whole thing got set up (bearing in mind this is my first ever venture into Linux).  I am confused by pretty much everything, but that isn't the problem.  

I used Chrome and downloaded TeamViewer and got that running and transferred some files.  So the wireless was working.

Now it doesn't connect at all.

How do I fill in the fields in the Edit Wireless connection dialogue box (I click on a space on the taskbar (there is no icon)) and enable wireless and edit - is this NetworkManager?)

I know my SSID
I know the WEP password
and the MAC address of the router

But,
I don't know about other things.

Mode presently = ad hoc
What goes in BSSID?
and cloned MAC address?

I can connect wired, by the way, but the whole point of using this machine is to use the wireless.

Thanks for you help,

Pete

---

### Post by westie457 on 2012-05-10
> **peteporchos said:**
> Sorry to bother you.

A few days ago I installed Lubuntu 11.10 on a Sony Vaio PCG-TR1MP.  This machine has 256 MB RAM and a 900 Mhz processor.  

While I was installing I selected the wireless adapter and completed the fields for SSID and password.  Everything went reasonably well and the whole thing got set up (bearing in mind this is my first ever venture into Linux).  I am confused by pretty much everything, but that isn't the problem.  

I used Chrome and downloaded TeamViewer and got that running and transferred some files.  So the wireless was working.

Now it doesn't connect at all.

How do I fill in the fields in the Edit Wireless connection dialogue box (I click on a space on the taskbar (there is no icon)) and enable wireless and edit - is this NetworkManager?)

I know my SSID
I know the WEP password
and the MAC address of the router

But,
I don't know about other things.

Mode presently = ad hoc
What goes in BSSID?
and cloned MAC address?

I can connect wired, by the way, but the whole point of using this machine is to use the wireless.

Thanks for you help,

Pete

Hi. Welcome to UF.

In the window you were editing earlier set the MODE to Infrastructure.

The BSSID is for when the Router is 'hidden' and must have the name of the connection in it. If router is not hidden leave blank.

The MAC address field can be left blank, only fill that in if needed.

Now to cover some bits you did not mention.

In the 'Wireless Security' tab the level of security must match what the router is set for. 'WPA and WPA2 Personal for preference. The password here is whatever you have already set up.

In IPv4 tab the method should be 'Automatic(DHCP) and check the box for requiring IPv4 addressing to complete this connection.

In the IPv6 tab, this should be set to 'Ignore' unless your ISP - Internet Service Provider - actually uses the protocol. Most do not.

Lastly check the boxes top and bottom 'Connect Automatically' and 'Available to all Users'. Click 'Save' wait a few seconds and check to see if you can connect.

If not post back here for further help.

---

### Post by peteporchos on 2012-05-10
Hello Westie,

Thanks for your reply.

I am unable to look at things at the moment, tomorrow maybe.

I'll let you know how I get one.

Pete

---

### Post by peteporchos on 2012-05-12
Hello Westie and others,

I haven't had a chance to look at this for a couple of days.

But now I have.

It's very strange.  I booted the machine this morning and the wireless connection is there, after two days of having been missing.  I noticed that a screen which had been visible during earlier booting was no longer there, it had said something like 'searching for network connections' (sorry, can't remember exactly).  It was on a blue background, though, and was there for a minute or so.  And then I wasn't connected wirelessly.

But back to the present situation.

There is no connection icon on the tastkbar.  By chance, just clicking on blank space, I can open what I think is NetWorkManager.  I enable 'wireless' and then 'edit connections' (which I had looked at before.  The name of my wireless connection appears to be 'wireless connection 1'.  Last used 'Never', which is odd as it is connected now!  When I open 'edit' for this connection the fields are filled in, as they were before, as you detailed above.

I downloaded WiFi Radar and can see that I am connected to my router and can see others as well.  

So, is this normal?  Shouldn't there be an icon on the task bar?  
Why is the connection reporting that it has never been used?

Incidentally, the wired connection, 'wired connection 1' is reporting that it was last used 23 minutes ago.  I haven't used this connection for three or four days.

Pete

---

### Post by peteporchos on 2012-05-14
You know, it's silly.

I gave up trying to get the wireless set up with this install (11.01) and decided to start the wholel process over again. I dread to think how long I wasted trying to get the previous set up to work.

Anyway: 

I downloaded 12.04, installed, upgraded using cable, restarted. Edited the wireless connection (as per Westie above) and then within about a minute the wireless connection kicked in.  It couldn't have been much simpler.   
So Precise Pangolin has my vote here.

Pete

---

