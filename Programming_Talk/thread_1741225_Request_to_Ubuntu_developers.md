---
title: "Request to Ubuntu developers"
date: 2011-04-27
forum: Programming Talk
---

### Post by ranjank on 2011-04-27
Hi all Ubuntu developers, you guys have done a very good job. I have 3 requests for developers.

1.Include a GUI based internet bandwidth meter in Ubuntu. It is one of the most wanted software in Ubuntu. In India we have very limited bandwidth [around 2GBpm]. We have to visit to portal of ISP every time to check bandwidth we consumed. If you guys develop a bandwidth meter which shows daily,weekly,monthly bandwidth it will be very very helpful for us.

2.Another thing Ubuntu lacks is option to watermark in videos. I saw a tutorial to add watermark via ffmpeg command, It is not easy for normal users.

3. In our laptop Ubuntu gives battery backup of around 4 hours whereas Windows gives 5.5 hours of back up. All settings are same,but also Ubuntu consumes more energy. Please try to decrease energy consumption of Ubuntu.

If you guys do this it'll be very helpful for all users.

---

### Post by slavik on 2011-04-27
overall: file bugs in launchpad. this forums is not for ubuntu dev requests.

1. what happens when you have a lan? your best bet is write a page scrubber to display the info, because what the ISP says is what they go by.

2. has nothing to do with ubuntu, look at the individual tools, maybe avidemux can do this as well (I am sure it can).

3. according to phoronix.com, this is an issue with current Linux kernels

---

### Post by ranjank on 2011-04-27
I don't know any kind of programming. Now I am writing bandwidth used everyday in a book. It takes so much time to calculate. I tried Avidemux, it doesn't do that.

Sorry for posting in wrong forum. To whom I have to contact for software development requests?

---

### Post by slavik on 2011-04-27
like I said, file launchpad bugs and ideas in brainstorm.ubuntu.com

---

### Post by ranjank on 2011-04-27
Thanks. This thread can be closed

---

### Post by |{urse on 2011-04-27
You can add watermarks via gui with kdenlive (it's not hard).

[http://tech.chandrahasa.com/2011/02/03/adding-watermarks-to-videos-in-kdenlive/](http://tech.chandrahasa.com/2011/02/03/adding-watermarks-to-videos-in-kdenlive/)

---

### Post by slavik on 2011-04-27
> **ranjank said:**
> Thanks. This thread can be closed
this is not ticket in a support channel :P

we don't close threads, we let them expire slowly :)

---

### Post by ranjank on 2011-04-27
Thanks for your help.I'll try it after release of Natty.

---

### Post by krazyd on 2011-04-27
There are many download meters available.

One of my favourites is a firefox extension: [http://netusage.iau5.com/](http://netusage.iau5.com/)

It supports the indian ISP Reliance.. but why not contact the author if you have a different ISP?

---

### Post by ranjank on 2011-04-27
> **krazyd said:**
> There are many download meters available.

One of my favourites is a firefox extension: [http://netusage.iau5.com/](http://netusage.iau5.com/)

It supports the indian ISP Reliance.. but why not contact the author if you have a different ISP?

I am looking for something like Shaplus Bandwidth meter. My ISP is govt owned BSNL.

---

### Post by deconstrained on 2011-04-27
A bandwidth meter would be more useful to put in a router than in Ubuntu; that way you could measure the usage of an entire household than just the computer running Ubuntu.

DD-WRT can do this;
[http://www.simplehelp.net/2008/09/11/how-to-use-the-dd-wrt-firmware-to-monitor-your-bandwidth/](http://www.simplehelp.net/2008/09/11/how-to-use-the-dd-wrt-firmware-to-monitor-your-bandwidth/)
If you reflashed your router with DD-WRT you could thus monitor your bandwidth usage.

Good luck!

---

### Post by ranjank on 2011-04-27
Router not supported.

---

### Post by deconstrained on 2011-04-27
What model router?

Also, what about Tomato?

---

### Post by ranjank on 2011-04-27
Utstarcom ut300r2u

---

### Post by deconstrained on 2011-04-27
From what I can gather, that's not a router, but a modem. If there's only one computer in the household and it connects to the internet through that modem, there's less advantage in trying to set up different firmware on the network appliance just to add bandwidth monitoring, so my suggestion wouldn't be of much use.

For what it's worth, 
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

---

### Post by ranjank on 2011-04-28
Yes it is a crap modem I got for free with Broadband connection. I need Graphical user interface based meter,not command line based.

---

### Post by deconstrained on 2011-04-28
Even better than both: conky. You can set it up so that it displays the bandwidth usage info on your desktop.

---

### Post by slavik on 2011-04-28
BSNL ... from what I heard, they are terrible. :(

---

### Post by ranjank on 2011-04-28
Yes!. What to do? we people at rural areas have no other options.Urban people has a lot of options. Private operators offer awesome service. If we complain to higher officers service will be good.BSNL is the cheapest operator in India[Mobile&Broadband].

---

### Post by dineshs on 2011-04-29
BSNL has 2 broadband networks called P2 and P3.
I am using BSNL broadband P3.To check usage I go to [http://data.bsnl.in/wps/portal](http://data.bsnl.in/wps/portal)  enter poratal id and password as given by BSNL  and proceed.If you are in P3 try this IP
10.240.16.195  or 10.240.64.195
Enter userid and password then proceed.I think this is easy.
To get session usage I use [COLOR="Red"]gnome-netstatus applet[/COLOR]  (install via synaptic and create a launcher on panel ie rightclick panel-add to panel-network monitor-add)
Have you already tried these?If you have any doubt regarding BSNL broadband please ask.

---

### Post by abhilashm86 on 2011-04-29
As far i see, you can go to system monitor to check download and upload happening at end of session, works great, i have not checked about integrating system monitor data with program. I think it can be done by script which keeps logs daily.

---

