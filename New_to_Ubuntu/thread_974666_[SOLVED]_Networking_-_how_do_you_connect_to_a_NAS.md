---
title: "[SOLVED] Networking - how do you connect to a NAS?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by GB_Joe on 2008-11-07
Hi guys

I've just put Intrepid on to my old IBM T23 laptop. It's mostly going well, but I just can't figure out how to connect to my NAS. I can connect to my router with and without wires, and I can get to the NAS using the IP in Firefox, but I really need to be able to access the thing in a File Manager. The NAS is a Qnap TS109 ProII, I don't think there's anything wrong with the config that end.

I've been searching forums for a couple of days, and followed a couple of how-tos which have got me nowhere (except I think I've probably installed some kind of Samba stuff unnecessarily). There are a couple of unanswered threads here which look like similar problems... am I asking for the impossible? Should I go with some other distribution? I'm particularly keen on Xubuntu because the laptop is pretty low-powered, and I'm very impressed with it in general...

Any help or suggestions greatly appreciated!!!

Joe.

---

### Post by B34ST1Y on 2008-11-07
can you connect to it via smb?   ```
smb://_____________
```

---

### Post by Peter09 on 2008-11-07
What version of ubuntu are o#you running.

can you see the NAS using its ip address. 

If it shows as a windows share and you can get to it only by its ip address you will need to install winbind.

---

### Post by chrisod on 2008-11-07
I have all my music and pictures on a NAS drive- haven't had any major problems on Ubuntu 7.x or 8.04.

1) Create mount points in /mnt directory
2) Auto mount the drive at boot with an fstab entry

Mine looks like this
> 192.168.11.7:/shares/SimplePool/Music /mnt/music nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

I couldn't get it to resolve to the NAS server name so I worked around it by assigning static IP addresses to the server and mounting by IP

---

### Post by GB_Joe on 2008-11-14
Thanks for the quick replies guys!

I think your comments are referring to Ubuntu...? I'm running Xubuntu 8.10. As far as I can work out, Ubuntu has much better network support, but my T23 only has 256MB RAM, so I'm really liking the lightweight Xubuntu variant - I can actually open more than one thing at a time!

@ B34ST1Y
Sorry, I don't quite understand... where should I be typing that?!? A terminal window or web browser?!? :(

I can get to the NAS in Firefox using its IP address just fine. I bought the "Pro" version of the QNAP TS109 because it was supposed to be compatible with Linux... but bear in mind I'm a total noob, so I really don't know what I'm doing beyond Windows and DOS (sorry - I'm here to learn!). The drive is set up as NFS, which to my mind means that I shouldn't need to worry about any kind of Windows sharing, or Samba - am I right?

I moved away from static IPs a while back because it was causing me such a lot of grief elsewhere, so I'm fairly keen to keep it dynamic if possible - everything else works great with this! I have two other PCs running Win XP and 2000, if I can get my T23 running right then my plan is to move the XP machine to some flavour of Linux too, but one step at a time - it's not just me who has to use this stuff!

---

### Post by chrisod on 2008-11-14
Check in your router set up - you should be able to exclude a single IP from the dynamic IP pool and then assign that IP address to the NAS server. That is how my network is set up. Everything is DHCP except the NAS server.

---

### Post by Peter09 on 2008-11-15
Hi,
just to confirm your problem. You can use your NAS machine if you refer to it by IP address but not by name? This would mean that Name resolution is not working.

---

### Post by GB_Joe on 2008-11-15
chrisod - that sounds reasonable! I'll try that once I'm sure I've done everything I should with the current set up.

Peter09 - that's correct... but I don't really understand the implications of this! Is it not possible to mount a drive using its IP address? I guess I don't know how Thunar works at all, either...

---

### Post by Peter09 on 2008-11-15
Thats fine, if you want to mount it by name you will need to install winbind.

---

### Post by GB_Joe on 2008-11-17
Well, now I'm really confused...

I thought winbind was for Active Directories? I didn't think I needed any of that stuff for an NFS connection. I think the NAS does support AD, but that sounds (in my feeble layperson's terminology) like emulating Windows so I can emulate Linux on it...

However, now that I've thought about it, it seems pretty clear that I need to either fix the Name resolution or set the NAS to a fixed IP.

---

### Post by Peter09 on 2008-11-17
If your Nas is exporting its shares as windows shares then you will need winbind. However if its NFS shares, not sure. It should be resolved by your router via DHCP.

---

### Post by gn2 on 2008-11-17
There's a link in my sig that might help, network browsing with Thunar.

Another method is using pyNeighborhood which is in the repositories.

---

### Post by GB_Joe on 2008-11-18
Well, it really is supposed to be NFS, and I've ticked the box in the Qnap web interface that's supposed to make it happen... from what I've read, this is by far the fastest way to connect from a Linux box, so I'm quite keen to get this method working if at all possible.

@ gn2 - I've seen that thread before, and tried following it without much luck. Again, it seems very samba-orientated... but I think I know more now than I did then, so I'll give it another go this evening. pyNeighborhood looks like another samba/Windows thing to me... but I'll check it out, thanks!

It seems weird that there's so much written about connecting to Windows but so little for Linux-Linux... I can only assume I'm over-simplifying things due to my (not so) blissful ignorance of what the heck I'm doing...:)

---

### Post by GB_Joe on 2008-11-22
Well, I've figured it out... Huzzah!

Followed the instructions (client setup) here:
[http://dcteam.guru-mountain.com/howto/nfs03.html]("http://dcteam.guru-mountain.com/howto/nfs03.html")

With the exception of having to add "sudo" to the front of a couple of commands, this worked really well for me. What a relief!

This is especially significant as my newer laptop (on XP) has just frozen and refused to reboot, so I can (hopefully) set Thunderbird up to pick up my email from where it's stored on the NAS.

What did we find to do with our time before computers?!?:)

Thanks for all your help and suggestions everyone.

Joe.

---

