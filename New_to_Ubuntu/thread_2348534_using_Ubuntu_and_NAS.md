---
title: "using Ubuntu and NAS"
date: 2017-01-04
forum: New to Ubuntu
---

### Post by dave6 on 2017-01-04
Hi all

Maybe that should be NAS with Ubuntu, I had an old computer here laying in the house so I ripped out the DVD drive and fitted a 4gb IDE drive which I installed NAS onto with the help of you-tube video->  [https://www.youtube.com/watch?v=jLRkiElXUaw](https://www.youtube.com/watch?v=jLRkiElXUaw)
I got 17 minutes into it and because he is using win7 or the like I am at a loss what to do next.

My thinking behind using NAS is to be able to show watermarked photographs to customers.  So to do so, with my way of thinking is A: www dot justme dot com as my web site domain then as I add files to this I could or would crate a file for each customer eg Jan1234-2017 
So then I could email them out the link some like [www.justme.com/Jan1234-2017](www.justme.com/Jan1234-2017) which they in turn would click on and see only THEIR images 

I may be totally wrong in what I am trying to do, any help would be welcomed 

Dave

---

### Post by rkillcrazy on 2017-01-04
Watching the aforementioned video, I noticed the guy tries to connect to it, via something like **\\xxx.xxx.xxx.xxx\share**, at about 17:23.  Are you saying you had an issue making that connection?

---

### Post by dave6 on 2017-01-05
It's been about 6 - 16 weeks since I last turned on the NAS computer, I made the www folder don't want the media folder after the point of making the www folder I don't know what next to with it on this Ubuntu computer I type in it's IP address and I am into it's software every time.
Must turn it back on today some time and just check at which part I get lost on.

Dave

---

### Post by mastablasta on 2017-01-05
otherwise.... you could just install Ubutnu server and then add Piwigo galery or something. 

Another option if this would be digital downloads website - install wordpress (secure it) and add one of the gallery plugins.
Yet another option is to use something like Opencart (or zencart) and then show sample photos and sell via that - it has everything you need to sell online.

---

### Post by TheFu on 2017-01-07
NAS is for LAN use, not internet use. Generally, the protocols used by NAS devices are not secured for use over the Internet.

Perhaps you want a web server with authenticated access to specific directories for specific customers?  Something like NextCloud or owncloud, if properly secured could be used this way.  **Nextcloud** has a "share files" section - I suppose images could be shared that way.  The only downside is that it is a php webapp and those tend to be more easily hacked based on history of hacks. Php webapps are much, much, more likely to be hacked than those created in other languages.  The DNC server was running a php blog system. Hacked.

Or just use **sftp**, which is a secured, file transfer tool that requires authentication. sftp comes along with ssh, so this is a no brainer.  IMHO, ssh and sftp are basic needs for every Unix server.

Is this for internet or LAN use?

---

### Post by gordintoronto on 2017-01-07
Also, a 4 GB hard drive won't get you very far.

---

