---
title: "Trouble getting help...."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by kjacobs on 2008-11-19
Okay one more try,

Being new to linux and ubuntu I've tried a couple times to get assistance with a networking issue in the normal networking thread with not even a single response. So now I'll try here.

I finally gave up trying to compile the linux driver for my usb wifi card and decided I would need to use ndiswrapper. However, I can't even get that up and going correctly based on the help instructions with ubuntu.

I am running Ubuntu 7.10 (because already had it on disk). I followed the instructions to go the Synaptic Package Manager and install ndisgtk. However, I can't find that file anywhere. I did find ndiswrapper and installed that. But, I do not see the wireless windows driver option under the admin heading. What do I do now?

I really like the Ubuntu system, but dealing with getting hardware working can be a challenge at best. I won't even mention compiling stuff...

---

### Post by tgalati4 on 2008-11-19
In a terminal:

>ndiswrapper -i yourwin98driverforyourUSBdongle.inf

>man ndiswrapper (for more info)

Search ndiswrapper in the forums for how to properly install it.

The forums are busy, so sometimes posts get overlooked.  There are 10 times as many people lurking in the forums as opposed to registered and logged in.  Only logged in folks can reply.  This evening: Currently Active Users: 7857 (522 members and 7335 guests).  That's 14 people lurking for answers for every logged-in member.

In Southern California, we had wildfires.  Only a few firefighters in each neighborhood, and low water pressure.  Houses were burning up in 20 minutes.  Sometimes all you can do is watch it burn.

Each new release of Ubuntu brings a wildfire to the forums.  All we can do is watch it burn.

---

### Post by cdtech on 2008-11-19
Hope your doing well, Good luck......

---

### Post by cdtech on 2008-11-19
> **kjacobs said:**
> I am running Ubuntu 7.10 (because already had it on disk). I followed the instructions to go the Synaptic Package Manager and install ndisgtk. However, I can't find that file anywhere. I did find ndiswrapper and installed that. But, I do not see the wireless windows driver option under the admin heading. What do I do now?

Sorry to hear about your wifi troubles. What exactly have you tried and can you give us the output of this command so we know what we're up against:
```
lshw -C network
```

Maybe we can nip this in the bud quickly.

---

### Post by kjacobs on 2008-11-19
Okay,

I opened a terminal and typed:
ndiswrapper -i zd1201u.inf

Then I got and error message, something about /usr/bin/ndiswrapper-1 (not sure what all it said.

Then ran the the above command again and it said the driver was already installed.

Ran lshw -C network and got this:

 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0e:a6:b2:b1:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

Hope this means something....

---

### Post by cdtech on 2008-11-19
I understand that you installed the "ndisgtk" have you tried to run that on a commmand line?
```
sudo ndisgtk
```

---

### Post by tariquepark on 2008-11-19
hi there,
you might want to try  lsusb in a terminal and post the results, as it seems only your lan adapter is being recognised

---

### Post by chrisod on 2008-11-19
Maybe he should try upgrading to 8.04 or 8.10? Wireless support has improved dramatically since 7.10.

---

### Post by kjacobs on 2008-11-19
Thanks so far for the help everyone....

I typed sudo ndisgtk

I got command not found

I typed lsusb and got this:

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0ace:1201 ZyDAS 802.11b WiFi
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I had thought about upgrading to 8.10...would that help?

---

### Post by muteXe on 2008-11-19
> **chrisod said:**
> Maybe he should try upgrading to 8.04 or 8.10? Wireless support has improved dramatically since 7.10.

What he said :)

---

### Post by cdtech on 2008-11-19
> **kjacobs said:**
> I followed the instructions to go the Synaptic Package Manager and install ndisgtk. However, I can't find that file anywhere.

If you ran "ndisgtk" in a terminal and the response was "command not found" then you didn't install the package. Try typing this in a terminal:
```
sudo apt-get install ndisgtk
```
Then:
```
sudo ndisgtk
```
and see what you get.........

---

### Post by tariquepark on 2008-11-19
> **chrisod said:**
> Maybe he should try upgrading to 8.04 or 8.10? Wireless support has improved dramatically since 7.10.

this would definately be my first stop, preferably to 8.10
that should make things fairly straightforward from there:)

---

### Post by kjacobs on 2008-11-19
Thanks to all, again...I appreciate the help. I was beginning to wonder if my new venture into linuxland was going to end in desparation and a bruised forehead. But, so far so good. I really do like the overall feel and smooth operation of Ubuntu. Won't be long before I migrate completely, I'm sure.

I left my "other" machine downloading 8.10 while at work today. It should have completed right after I left. Anyway, I will upgrade first and then see what we have to do from there.

Speaking of upgrading...do I need to do anything or can I just boot to cd and install over the top of 7.10?

---

### Post by Keen101 on 2008-11-19
if you downloaded the alternate install disc of 8.10 you could use it to upgrade. But, i'm going to assume you did not. Just try the live-cd and see if your wifi is recognized on the live-CD. If it is, i suppose you could just install over the old one.

---

