---
title: "new computer with 12.04 can see old computer (10.04) but not vice-versa"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2013-12-29
I installed 12.04 on a new (to me) computer.

I opened Places/Network on "newcomputer" but could not see "oldcomputer".

Found and ran this:

```
sudo apt-get install apache2.2-bin libapache2-mod-dnssd
```

I re-opened Places/Network on newcomputer and now can see oldcomputer.

Then went to oldcomputer, opened Places/Network but could not see newcomputer.

So ran the code above on oldcomputer, but still cannot see newcomputer.

Am able to ping newcomputer from oldcomputer.

Any suggestions?

---

### Post by newb85 on 2013-12-29
I had a similar situation.  (Actually, neither of my computers could see each other.)  My solution is probably not normally the most direct or optimal approach, but it fit well with other objectives I had.  I'll throw it out there just for information.

I set one of the machines (the desktop) with Samba.  (I wanted to use it as a file and print server, anyways.)  In the smb.conf file, I also set it up as a WINS server.  Then, in the other machine's (the laptop) smb.conf file, I told it to use the desktop as the WINS server.  (Of course, to do this I also had to set the router up to assign a static local IP to the server machine.)

---

### Post by Odyssey1942 on 2013-12-29
Newb85, Ermmm, Absolute Beginners Section here. Thanks for what I am sure is a very good solution, but I would not know where to start to implement. If you could walk me through maybe?

---

### Post by Odyssey1942 on 2013-12-29
Certainly don't want to appear impatient, but this is the first step in a series of problems with this install needing assistance and would very much like to get as much of the help that is likely to be at a peak of availability on a Sunday.

Therefore would like to get this issue sorted and move onto next step, so any thoughts greatly appreciated.

---

### Post by Iowan on 2013-12-29
40 minutes DOES seem impatient...  
[Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945") suggests waiting AT LEAST 24 hours before bumping.
Have you tried **smbtree** from each machine? Do you have a share (shared folder) on the new computer?

---

### Post by Odyssey1942 on 2013-12-29
Deep bow with sincere apologies to all. And thanks.

smbtree yields some interesting results. We also have 2 windows machines in our office in a workgroup "MSHOME". smbtree on oldcomputer shows itself listed under WORKGROUP, and below: the two windows computers in MSHOME. Neither WORKGROUP nor MSHOME are indented.

Oldcomputer shows out to the right of its name "(Samba, Ubuntu)" . Don't know if this is significant

Newcomputer does show WORKGROUP, but does not list itself under WORKGROUP, but does show the two windows computers in MSHOME.

First question is: Is WORKGROUP the functional equivalent of MSHOME, or is MSHOME simply one "group" under WORKGROUP?

If the former, how does one change the group name to MSHOME so that all four computers can be on the same network.

Finally, why does oldcomputer list itself, but newcomputer does not?

I am wondiering if this holds the answer to the failure to connect.

---

### Post by Odyssey1942 on 2013-12-29
OK, not sure how I did it, but through a combination of sharing options, network config and a restart, newcomputer can now see oldcomputer.

However oldcomputer still cannot see newcomputer, and any suggestions welcomed.

Would also still like to know if all the computers can be "combined" into the same workgroup on the lan, and I will start a new thread on this since it is not strictly speaking part of the original question?

Another deep bow and apology for my confusion. Am trying to cram a lot into a short space with not much experience.

---

### Post by damage3025 on 2013-12-30
Can OP explain why he/she installs "libapache2-mod-dnssd"?

Also, can OP show the result of "apt-cache policy samba" on both Ubuntu computer?

For MSHOME and WORKGROUP, these seem to be two default/conventional work group name on Windows.
To change work group name on Ubuntu, you'd change /etc/samba/smb.conf

---

### Post by Odyssey1942 on 2013-12-30
Yes, and by way of background, I use my computers heavily to get my various work done. I don't like Window's constant interruptions, elevated needs for security supplementation due to it's (security) weak nature, fallovers, etc, and so use linux. Ubuntu is the most friendly implementation I have found and for me, it is a real workhorse by comparison to Windows. To complicate this, I am not very computer software and o/s capable, and so rely heavily on the GUI to keep on going. Having said all this, I am interested in learning to use the terminal, but at my stage of experience, find it terribly intimidating. Finally, I am older than the hills so this stuff doesn't stick very well in my memory which is not as good as it never was.

So that will help you understand why I google for solutions that others have found that will solve my occasional problems. That command line was another's solution which I tried (without really understanding it). This "half-way" practice of implementing terminal commands which I don't fully understand usually works well for me, and I do this with the realization that it carries risks, especially unintended consequences. Apology for a much longer answer than you probably expected, but I wanted to explain my inexperience and to come clean on this.

Here are samba results:

oldcomputer:

> samba:
  Installed: 2:3.4.7~dfsg-1ubuntu3.13
  Candidate: 2:3.4.7~dfsg-1ubuntu3.13
  Version table:
 *** 2:3.4.7~dfsg-1ubuntu3.13 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
        100 /var/lib/dpkg/status
     2:3.4.7~dfsg-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages

newcomputer (have installed samba since my previous post)

> samba:
  Installed: 2:3.6.3-2ubuntu2.9
  Candidate: 2:3.6.3-2ubuntu2.9
  Version table:
 *** 2:3.6.3-2ubuntu2.9 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     2:3.6.3-2ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

To update, since installing samba on newcomputer, both can now see each other. During that install, I managed to also "add" my printer using samba on newcomputer and don't know how to remove it. So when I look at Places/Networks (viewed from oldcomputer), it shows me:

oldcomputer
newcomputer
user's public files on oldcomputer
user's public files on newcomputer
Windows Network

Clicking on lines 1 and 3 show the expected results, but:

If I click on line 2 above, it shows me the printer share on newcomputer and if I click on it, it shows me a "password required" signin screen.

If I click on line 4 above, it shows:

> Unable to mount location
DBus error
org.freedesktop.DBus.Error.No Reply:Message[PHP]
     did not receive a reply (timeout by message bus)
Mountpoint already registered

--
Moving over to newcomputer, when I look at Places/Networks, it shows me:

user's public files on newcomputer
user's public files on oldcomputer
Windows Network

If I click on line 1 or 2 above, it shows me an error screen:

> Unable to mount location
DBus error
org.freedesktop.DBus.Error.No Reply:Message[PHP]
     did not receive a reply (timeout by message bus)
Mountpoint already registered

However, if I click on line 3 above, it shows:

MSHOME
WORKGROUP

If I click on MSHOME, it shows me a blank screen.
If I click on WORKGROUP, it shows:

oldcomputer
newcomputer

If I click on oldcomputer, it allows me sign in and see:

desktop
print$
userhome

If I click on newcomputer, it shows only:

print$

--
Thanks for the guidance on work group names. One additional thought on changing. Would there be any advantages, security or otherwise, to keeping the linux computers under a different name from the Windows computers?

Apology for the length of this post, but hopefully it will show those who understand this, what is (not?) happening.

---

### Post by damage3025 on 2013-12-31
> **Odyssey1942 said:**
> So that will help you understand why I google for solutions that others have found that will solve my occasional problems. That command line was another's solution which I tried (without really understanding it). This "half-way" practice of implementing terminal commands which I don't fully understand usually works well for me, and I do this with the realization that it carries risks, especially unintended consequences. Apology for a much longer answer than you probably expected, but I wanted to explain my inexperience and to come clean on this.

If you do not quite understand a solution you found elsewehre and things do not seem to work using that solution, please provide the origin source if possible.
I guess you did quote the essential part of the solution you found, however, your intention was not very clear to me.

In particular, you were installing [Apache HTTP Server]("http://httpd.apache.org/") and a mod related to [Zeroconf]("http://en.wikipedia.org/wiki/Zero-configuration_networking").
I was not 100% sure that this is not a technology that can probably enable your computers to see each other.
It turns out that you want to connect your computers using [Windows-style network technology]("http://en.wikipedia.org/wiki/CIFS") in a mixed (Linux and Windows) environment.
It is a pretty common scenario, just that it was not clear enough.

> **Odyssey1942 said:**
> To update, since installing samba on newcomputer, both can now see each other. During that install, I managed to also "add" my printer using samba on newcomputer and don't know how to remove it.

I guess the during install stuff is [debconf]("http://en.wikipedia.org/wiki/Debconf_(software_package)").
To see that setup again, try
sudo dpkg-reconfigure samba

If you need a configuration reset, you may refer to:
[http://askubuntu.com/questions/21553/how-do-i-completely-reset-samba-to-the-shipped-defaults](http://askubuntu.com/questions/21553/how-do-i-completely-reset-samba-to-the-shipped-defaults)

> **Odyssey1942 said:**
> Thanks for the guidance on work group names. One additional thought on changing. Would there be any advantages, security or otherwise, to keeping the linux computers under a different name from the Windows computers?

I don't think there is.

For the errors you quoted, they are not informative enough; detailed reasons are not given.
You'd try some CLI clients probably with verbose mode enabled to find out the real reasons for error.
( Linux GUI is not very good at error reporting so far, unfortunately. )
I guess the most likely reason for errors would be different computer has different default security policy so they are not happy with each other.
I remember this kind of problem happened in Windows-only environments also.

I'm unfortunately not an expert of Samba.
IBM developerWorks has quite some articles for mixed environment, they may be helpful to you.
[http://www.ibm.com/developerworks/linux/library/l-lpic3-map/](http://www.ibm.com/developerworks/linux/library/l-lpic3-map/)

Also, once you got your problem narrowed down, I guess you can post in a more specialized zone so that you are more likely to get advise from relevant expert.

---

