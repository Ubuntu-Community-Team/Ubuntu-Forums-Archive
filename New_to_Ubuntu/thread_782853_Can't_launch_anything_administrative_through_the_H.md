---
title: "Can't launch anything administrative through the HH GUI"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by blue_comet on 2008-05-05
I'm running 8.04 on a generic single-processor pentium with 2 GB of RAM and 260 GB of HD. The machine is a simple file server on a small LAN serving 5 or 6 users. Over the weekend, I upgraded 7.04 to 7.10 and then to 8.04 online. All went well. I set up Samba as best I could with the rather clunky interface(s) and it worked to a point. Whenever I tried to use "Samba," I got a crash. Eventually, I installed GSAMBAD and was able to do some stuff but I had to edit smb.conf before it did what I needed it to. (It's a pity about the shares tab.) I have several users set up on the box and these all feature happily in GSAMBAD. Two of the users have administrator privileges. I was able to test access and controls with my MAC and all seemed well.

Then, this morning, I ran the update and it installed 67 packages. Thereafter, I moved the box from my home LAN (using iBurst) with an auto DHCP config to the office LAN (using Telkom ADSL) with a manual IP setting. The IP is fine - I have trouble-free connectivity, as far as that's possible with Telkom.  I mention it because it is the only real variable apart from the update. I can access the box remotely with my Mac but have not been able to do so with Windows, yet - but that's not unusual.

The problem is that, since the move, I can get nothing administrative to launch in Gnome, in either of the users with administrative privileges. Desktop apps and monitors will launch quite happily but anything that requires admin privileges (i.e. just about everything under "System") will not start. The launch starts and the notifications appear in the taskbar but then it all goes dead and I'm left looking at an empty desktop. (However, I do *not* get crash notifications, which is  another interesting development).

Whilst I can do some basic stuff at the command line, I'm not really very knowledgeable there and am still pretty dependent on the GUI, especially when it comes to the black magic bits of systems admin.

Can anyone suggest what might have gone wrong and how to correct it?

I apologise if this is not unique - I did a search on the threads and didn't see anything like it. If this problem has been raised already, pleased point me to the thread.

---

### Post by blue_comet on 2008-05-05
OK, this was solved for me by forestpixie who was dealing with someone's host name resolution problem. It dawned on me that the hostname was "overqualified." I edited it down to its simplest form in /etc/hosts and the problem went away. I still don't really understand the connection between the hostname and the GUI but I guess it's some sort of inter-server relationship.

Thanks, forestpixie. :)

---

