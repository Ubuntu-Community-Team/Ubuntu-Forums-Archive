---
title: "PS3, Mediatomb and Router Trouble on 8.04"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Teabicky on 2008-11-08
Have just spent some time setting up mediatomb for use with my ps3 and have edited the .mediatomb/config.xml file as needed but my PS3 still says that there is no media server found.

Once Mediatomb is opened in terminal I can't see any sign of an ip address and I think there should be one. I have a Belkin Wireless G Router 2.4Ghz - 802.11g and this works fine (e.g. my notebook works wirelessly as does my PS3 for gaming and browsing).

When I use the command iwconfig I get this response:

> lo        no wireless extensions.

eth0      no wireless extensions.

Am I right in thinking that this is the reason that mediatomb is not working or am I barking up the wrong tree?:confused:

---

### Post by Teabicky on 2008-11-08
Using this thread [http://ubuntuforums.org/showthread.php?t=333652](http://ubuntuforums.org/showthread.php?t=333652) I have found my IP Address and configured it into Mediatomb with the command:

> sudo mediatomb -i <ip address>

This is how mediatomb looks now

> MediaTomb UPnP Server version 0.11.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2008-11-08 15:07:10    INFO: Loading configuration from: /home/flanagan/.mediatomb/config.xml
2008-11-08 15:07:10    INFO: Checking configuration...
2008-11-08 15:07:10    INFO: Setting filesystem import charset to UTF-8
2008-11-08 15:07:10    INFO: Setting metadata import charset to UTF-8
2008-11-08 15:07:10    INFO: Setting playlist charset to UTF-8
2008-11-08 15:07:10    INFO: Configuration check succeeded.
2008-11-08 15:07:10    INFO: Initialized port: 49153
2008-11-08 15:07:10    INFO: Server bound to: 192.168.2.3
2008-11-08 15:07:11    INFO: MediaTomb Web UI can be reached by following this link:
2008-11-08 15:07:11    INFO: [http://192.168.2.3:49153/](http://192.168.2.3:49153/)


My PS3 still says there is no server........can anybody help?

---

### Post by Teabicky on 2008-11-08
Anybody.......

---

### Post by Teabicky on 2008-11-10
Please........

---

### Post by philinux on 2008-11-10
In nobody is replying It could mean nobody knows the solution. Have you asked on the mediatomb forum?

---

### Post by Teabicky on 2008-11-10
Nope, but it sounds like a good idea thanx!! I'll give it a go, i'd hate to have to start using windows again to stream music to my PS3.

---

### Post by philinux on 2008-11-10
I've been toying with the idea of getting a ps3 for the media pc side, blueray and the odd game.

---

### Post by Teabicky on 2008-11-10
It's a good machine if u like gadgets n stuff.  I use it for pretty much all of my multimedia needs.... you can even install a linux OS on it but I'm not that clever or brave.

---

### Post by billgoldberg on 2008-11-10
Are you sure  Upnp is turned on in your router?

---

### Post by philinux on 2008-11-10
> **Teabicky said:**
> It's a good machine if u like gadgets n stuff.  I use it for pretty much all of my multimedia needs.... you can even install a linux OS on it but I'm not that clever or brave.

Yes, it's Yellowdog Linux is specially tweaked to work with. Sounds straight forward to install it.. One problem at a time though eh. [http://www.terrasoftsolutions.com/support/hardware/sony.shtml](http://www.terrasoftsolutions.com/support/hardware/sony.shtml)

---

