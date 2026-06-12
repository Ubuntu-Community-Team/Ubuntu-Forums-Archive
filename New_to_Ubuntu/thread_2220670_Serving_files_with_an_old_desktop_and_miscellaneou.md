---
title: "Serving files with an old desktop and miscellaneous storage media"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2014-04-28
I have an old low-spec desktop someone gave me,
a very low spec laptop from 2004,
my current higher spec laptop from 2007,
4 external hard drives, 
2 hard drives from older computers, 
3 flash drives,
3 smart phones,
and easily 7+ TB of data between them all. 

Currently, I only access these devices through USB and my best computer only has 3 USB 2.0 ports.
Also, I'm anticipating needing to expand my storage capacity by at least 8 TB in the near future. 

When I had less data, it was very easy to organize my files on one external HDD.... Currently, I'm having to stow it wherever there's space and I have no backups. 


I want to use the old desktop to create a makeshift file server because it has the most USB ports. 
I was planning on connecting as many of the above devices to it, mounting them to one location, and then sharing that mount point via some form of secure FTP with my good computer.

I was looking into NAS4Free and Lubuntu, but would prefer to use some type of minimal ubuntu on the makeshift server. 


I've never done this before and will need to conduct some trials. 
Any advice and pointers would be greatly appreciated.

---

### Post by papibe on 2014-04-29
Hi YQ002lc2.

Been there, done that. I'd recommend Ubuntu Server: no gui so more resources to services ;)

Having external USB hard drives connected to a server works, but it is a barely OK situation. Most of the external USB hard drives I had have some sort of power saving feature. These produces some inconveniences.

For instance:
[LIST]
[*]It makes NFS shares 'stale' very often. Not an critical situation, but not ideal.
[*]Rebooting or powering on the machine may take longer than usual. In same cases, you may need to connect a monitor and keyboard to resolve booting issues. Again, not a big NO-NO in a server that is mostly 24x7, but an inconvenience nevertheless.
[*]In my experience, not all USB external drivers are recognized as in "plug-and-play" (as in the desktop version). You may need to reboot if you want to connect one.
[/LIST]
Having said all that, if you already have the drives, as I did once, the best way to share them and have them available to all your devices is to actually connected to a server ;)

I hope that helps. Let us know how it goes.
Regards.

---

### Post by YQ002lc2 on 2014-12-20
Thank you papibe for your reply!

My laptop has only 3 USB ports on it which is a real problem with all my external HDDs and USB peripherals. 

I installed ssh on my laptop.
I have an old desktop with lubuntu desktop but no Wifi antenna. 
I used [http://askubuntu.com/questions/359856/share-wireless-internet-connection-through-ethernet](http://askubuntu.com/questions/359856/share-wireless-internet-connection-through-ethernet) to connect my two computers via ethernet. 
I was able to update the desktop and install ssh. 
I setup an ssh server on the old desktop and made sure I could connect on my laptop. 

Now, I simply ssh into my server's IP address and then use nautilus to "connect to server".

All my external HDDs connect to the "server" desktop and I connect them to my laptop through the ethernet cable. 

I essentially went from 3 USB ports to 11. 

This solution worked for me.

The only problem I have is that sometimes my videos won't play on the laptop through the ethernet, but will on the desktop. 

I hope that helps someone and let me know if you have any suggestions about the video issue. 

Thanks again! 

Regards,

YQ002lc2

---

