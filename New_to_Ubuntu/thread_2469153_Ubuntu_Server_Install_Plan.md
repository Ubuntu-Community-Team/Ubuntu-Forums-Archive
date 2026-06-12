---
title: "Ubuntu Server Install Plan"
date: 2021-11-21
forum: New to Ubuntu
---

### Post by bolehill2 on 2021-11-21
Hello,

I've been a Windows user for many years, and have a home server which is running Windows 10 Pro (after Microsoft abandoned Windows Home Server).  The hardware is still 'good enough' but Windows isn't as 'snappy' as it ought to be, and a switch to Ubuntu Server seems to be the right way to move.

Almost all the devices that will be accessing the server are Windows 10/11.

The server has three drives, one for the OS and two for storage.

My installation plan is as follows:

1 - Back up the stored files (to a Netgear ReadyNAS)
2 - Check the back-up
3 - See 2
4 - Install Ubuntu server (from a live CD initally, just in case there are some hardware issues)
5 - Re-instate the back-up

The server is connected to the router via a cat 6 cable and the router handles DHCP.

After some research it seems that samba sorts out access to storage from Windows clients - this was the one thing I couldn't get my head around.

Does this look sensible, or have I overlooked something?  Aside from an old laptop running Lubuntu, I have pretty much no experience with Linux.

All advice appreciated.

Chris

---

### Post by ActionParsnip on 2021-11-21
Looks fine. Just use a Linux based file system for the storage and Samba will share it without issue. You could even use NFS or SFTP.

---

### Post by naxal on 2021-11-21
Hello,

Just a suggestion, since you are already running Windows 10 as make shift server on a "good hardware", why don't you give your entire linux setup idea a trial with a virtual machine?

No need to restore backup, just test out the configuration methods to see if its accessible and working the way you want it to. Once everything is fine and as per liking of yours, go ahead with the physical installation.

Secondly, server is better off with Static IP

Thirdly, I guess GUI snappy-ness isn't something one may want from a storage server. Front end Desktop environment snappy feel or lack of it won't make any difference with network performance.

Thanks.

---

### Post by bolehill2 on 2021-11-22
Many thanks guys,

1 - I'll stay with the 'out of the box' disc format suggested by Ubuntu (ext4 I guess)

2 - I'll allocate a static IP

3 - I was planning on installing Ubuntu server and manage that via the command line when required.  With Windows 10 there is no choice other than the GUI and I only ever logged in to manage updates.

4 - The idea of a trial in a VM has set me thinking.  I've used Virtual Box in the past when I've been tinkering, so I'll give it a try.

Thanks again for your advice, I'll keep you posted!

Chris

---

### Post by ActionParsnip on 2021-11-22
You can SSH to the system using powershell. It'd part of a default install so you don't need a GUI to install updates. Just SSH over and run
```

sudo apt update
sudo apt full-upgrade

```

---

### Post by yancek on 2021-11-22
>   I was planning on installing Ubuntu server and manage that via the command line when required 

It will be "required" as there is no GUI with an Ubuntu server, you would have to install it.

[https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu](https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu)

---

### Post by bolehill2 on 2021-11-23
Thanks for the link, good to have this in my back pocket 'just in case'!  I guess an unstated part of my plan is to become competent using the command line.  I was more than OK with DOS, but the advent of the GUI (whether Linux or Windows) has tended to simplify things to the point where competence is eroded over time.

---

### Post by LokiScarlet on 2021-11-24
Just my two cents since I'm a bit late to the party,

If you haven't messed with Ubuntu much yet, like the others have said, it's best to test your plan in a VM first. You might find something pleasant you'll want to add to your plan when you play around virtually. For example, Samba also handles Active Directory ever since version 4 came out.

It's a good thing you've backed up everything you need. I'd personally recommend completely backing up Windows before taking the plunge, something my former boss told me "don't get insolent" for mentioning. I still regret quitting that company, as I would have had so much fun at the helm of the IT department after his firing. But since it sounds like just a fileserver, you should be fine. Now if you were using Microsoft Exchange and you ever tried to restore that from anything from a full backup, I'd tell you the same thing I told my old boss - that it'll blow up in your face.

Once you've tested your virtual machine setup and recorded how you configured it to work, then play with the LiveCD on bare metal to make sure your hardware won't be a problem. Then you can install it directly on and repeat the steps you took to make the virtual machine operate the way you wanted.

---

### Post by bolehill2 on 2021-11-24
@ericthehax - thanks for the advice.  As per usual life has got in the way, so I haven't actually started on this yet.

Downloads are done, as is the back up.  It is essentially a fileserver as you correctly point out.  There is nothing special in the Windows installation, so I'm not planning on backing that up - to me it's just a wheel to drive the car with :-)

The idea of VM, then Live CD is great and progressively reduces risk in the process!

Chris

---

