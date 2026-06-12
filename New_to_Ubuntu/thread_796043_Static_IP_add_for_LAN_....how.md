---
title: "Static IP add for LAN ....how"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-05-16
From time to time I require a  static IP add. But I have yet to work out where it is done...and when finished, I need to go DHCP.....

The reason is that I have to set up network devices with default factory IP add.

---

### Post by Aearenda on 2008-05-16
I don't understand what you are trying to achieve with the default factory address. You can edit /etc/network/interfaces, then restart networking, or simply go to System->Administration->Network, unlock, select an interface, choose 'Properties' and turn off roaming mode. Then make the settings you want.

Oh wait - I think I get it - devices like routers and wireless access points that don't have DHCP?
This will work. Just set back to roaming mode when done.

---

### Post by Ducatiboy Stu on 2008-05-16
I am talking devices/equipment that connects to a LAN..

ie a hardware device like a PABX or voicemail syst that is conected to a customers LAN/WAN. These devices can be configuered via a web browser or SSH

They normally come with an IP add from the factory that is different to the customers IP addressing..

So I have to set my laptop to a fixed IP add in order to congifure the device, then switch the laptop back to DHCP mode

---

### Post by nicedude on 2008-05-16
Then do as he stated and unlock your network manager and turn off roaming, then setup all your ip settings however you want. When your done just go back into network manager and select roaming mode again.

If you do IT work for a living this should make sense and be easy as pie :-)

---

### Post by Aearenda on 2008-05-16
Good - then what I said about System->Administration->Network should work :-)
It's the equivalent of setting a static IP address in the network control panel on Windows.

---

### Post by nicedude on 2008-05-16
yes it will, if he wanted to he could do the whole thing with ifconfig commands from the command line but that would be pretty silly way to go about it unless you write a script and then that would have to be changed to reflect every customers different addresses so wouldn't be worth the time. This isn't even networking 101 level stuff here so it shouldn't be hard to figure out.

COMMAND TO LAUNCH NETWORK MANAGER
network-manager <- just paste that into a terminal and it will pop up

I want an IT job that lets me buy a ducatti motorcycle :-(

---

### Post by Ducatiboy Stu on 2008-05-16
> **nicedude said:**
> yes it will, if he wanted 

I want an IT job that lets me buy a ducatti motorcycle :-(

Lucky for me I am NOT in an IT job

I actually install/maintain PABX & telecommunication systems...But changing technology has ment a merging of IT & Telecoms....blah...blah...blah


I ride a Ducati as a release from the stress of dealing with IT managers.....especially when it comes to vlan switching and voip intergration


Thanks Guys for your help...I know it was a simple Q, with a simple answer but it had me stumped...

I do love some of the inbuilt features that Linux has RE- Networks... :guitar:

---

