---
title: "wicd or gnome Network Manager? In 9.04"
date: 2009-04-30
forum: Recurring Discussions
---

### Post by irv on 2009-04-30
Today was the first day I took my laptop on the road since I upgraded to 9.04. I had a wireless connection at home so I didn't even give it a thought. When I went to connect to the Internet, I didn't have a Network Manager. After I got home and fired up the Laptop I got right on but I still don't have a Network Manager so I can change anything without it. I am using wicd for my Network Manager. My question is, is there a problem wicd Network Manager in 9.04? If so I will go back to 
Network-Manager-Gnome?
Thanks for the help.

---

### Post by irv on 2009-04-30
Any advice would be great!
Thanks

---

### Post by irv on 2009-05-01
There are some real issues with wicd in 9.04. Seeing no one replied to my post, I un-install it and tried to install network-manager-gnome in its place. Here is what I got:
[IMG]http://wabashaweb.net/snapshot1.png[/IMG]
[IMG]http://wabashaweb.net/snapshot2.png[/IMG]
I am afraid to reboot my laptop because I may not have a network when it restarts. I still don't have a network manager.
All I can say is "HELP"! please

---

### Post by mikechant on 2009-05-01
The errors shown seem to relate to removing wicd.
What happens if you skip that and just try to install gnome network manager?

Also, it *is* possible to set up a network connection manually without a network manager (I think I've seen some threads on this board about it). It's fairly straightforward to set up a wired connection (even if it's just as a temporary measure to get your problem sorted out).

---

### Post by irv on 2009-05-02
> **mikechant said:**
> The errors shown seem to relate to removing wicd.
What happens if you skip that and just try to install gnome network manager?

Also, it *is* possible to set up a network connection manually without a network manager (I think I've seen some threads on this board about it). It's fairly straightforward to set up a wired connection (even if it's just as a temporary measure to get your problem sorted out).

Any way I try to install the network manager it first wants to remove wicd. I finally just left it installed and have to start it manually. Even thought I am connected to my network and Internet at startup I can't just start the wicd-client. I first have to run sudo wicd then run the client and everything works. I would like to have this all happen at startup but I am not sure how to do this. It use to work before I upgraded to 9.04. 
Without the client running I can't connect to the Internet when I am on the road.

---

### Post by Tankerdog2002 on 2009-07-19
Do not install wicd in 9.04 by all means.

It trashed my whole network on my new laptop. I couldn't even get online with cat5.

Everything is gone but wicd......All my network connections, etho, wlan, bluetooth.....all of it gone. Nothing left but the wicd box...and it's empty worthless 'schitt.

Can't even get on the net to use a package manager.

wicd couldn't connect Siamese twins joined at the butt.

Whoever created wicd should be shot.....then hanged.

---

### Post by irv on 2009-07-19
> **Tankerdog2002 said:**
> Do not install wicd in 9.04 by all means.

It trashed my whole network on my new laptop. I couldn't even get online with cat5.

Everything is gone but wicd......All my network connections, etho, wlan, bluetooth.....all of it gone. Nothing left but the wicd box...and it's empty worthless 'schitt.

Can't even get on the net to use a package manager.

wicd couldn't connect Siamese twins joined at the butt.

Whoever created wicd should be shot.....then hanged.

My problem was the upgrade from 8.10 to 9.04, it broke my wicd. It was working perfect in 8.10. I fixed it by completely removing wicd, instlling gnome network manager, uninstalling it and then re-installing wicd, and restarting the laptop. Everything is working perfect again. I think wicd is much better then gnome network manager.  When I am on the road it just finds every wireless network in range. Here is a screenshot of one of my trips.
[ATTACH]121656[/ATTACH]
I think there was something like 25 connections.

---

### Post by Wharf Rat on 2009-07-19
> **Tankerdog2002 said:**
> Do not install wicd in 9.04 by all means.

It trashed my whole network on my new laptop. I couldn't even get online with cat5.

Everything is gone but wicd......All my network connections, etho, wlan, bluetooth.....all of it gone. Nothing left but the wicd box...and it's empty worthless 'schitt.

Can't even get on the net to use a package manager.

wicd couldn't connect Siamese twins joined at the butt.

Whoever created wicd should be shot.....then hanged.
Couldn't agree more.

I did figure out enough to kinda get my laptop running - sort of.

Go to the US Ubuntu archive and dload the following to another machine.
Network-manager_0.7.1-0ubuntu1_i386.deb
network-manager_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb
network-manager_0.7.1-Oubuntu1_i386.deb

Copy  them to your PC using a flash drive or CD.

At a terminal run 
 sudo dpkg -i ~/Desktop/network*.deb

That will help. 
BUT!!  I still have to run:
sudo dhclient eth0

in order to get a name server.
For some reason, I get an error message that says.


There is already a pid file /var/run/dhclient.pid with pid 9023
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1c:25:12:85:6c
Sending on   LPF/eth0/00:1c:25:12:85:6c
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.64 from 192.168.1.254
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.


>>>>resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 192.168.1.64 -- renewal in 33060 seconds.


My wireless now works, but no wired connection.

Good luck!

---

### Post by gaylapdancer on 2009-08-28
Sorry to bump an old thread, but just running:

```
sudo apt-get install network-manager
```

purged this, frankly annoying, program from my system.

Just thought I'd mention this in case anyone else makes the mistake of installing it.

---

### Post by Roasted on 2009-09-17
This is honestly the first time I have EVER heard anybody speak negatively of wicd. All of this time I was using network manager and didn't have any issues but I decided to check out wicd just cause of all of the positive remarks I heard. As we speak I'm using wicd and it certainly looks nicer than network manager, but I'm surprised that there was this much negativity towards it. Do a lot of people have issues with it?

---

### Post by irv on 2009-09-17
> **Roasted said:**
> This is honestly the first time I have EVER heard anybody speak negatively of wicd. All of this time I was using network manager and didn't have any issues but I decided to check out wicd just cause of all of the positive remarks I heard. As we speak I'm using wicd and it certainly looks nicer than network manager, but I'm surprised that there was this much negativity towards it. Do a lot of people have issues with it?

I have been using wicd for well over a year now, and when I went from 8.10 to 9.04 I had some issues, but I believe it was because of the fact that when I did the upgrade it reloaded Gnome Network manager and that screwed up wicd. After un-installing the gnome network manager and reinstalling wicd it fixed the problem. I like you, agree it is much better that gnome network manager. When I am on the road, it seem to find all the wireless networks around me where I had some issues with the gnome.

---

### Post by bodhi.zazen on 2009-09-17
I had problems with networkmanager in Ubuntu 8.04.

In Ubuntu 8.10 + Network manager works fine, at least with all my wireless cards.

So really IMO it is a matter of choice and what features you need. Either one is fine.

Personally I do not use either on a wired network.

---

