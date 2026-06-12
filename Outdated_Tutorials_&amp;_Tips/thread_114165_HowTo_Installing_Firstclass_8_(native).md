---
title: "HowTo: Installing Firstclass 8 (native)"
date: 2006-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Nate53085 on 2006-01-08
**NEW**

I have a newer (and presumably less broken) deb at

[http://www.natebourgoin.com/files/fcc-8.047.deb](http://www.natebourgoin.com/files/fcc-8.047.deb)

simply download and

sudo dpkg -i fcc-8.047.deb

-type fcc to run


**OLD AND SOMEWHAT BROKEN**

This was ripped from a Hoary Howto and edited a little to fix a dependency.  Thank you krusbjorn for making the package, fixing the original dependency issues and hosting it.

> sudo apt-get install xlibs
wget [http://johannes.raftegard.se/fcc.deb](http://johannes.raftegard.se/fcc.deb)
sudo dpkg -i fcc.deb
sudo ln -s /opt/firstclass/fcc /usr/bin/fcc

Worked fine for me, but remember, YMMV.

---

### Post by Nate53085 on 2006-02-03
Note that the default applications are stored in a config file at :

/opt/firstclass/fcapps.

---

### Post by _linux_ on 2006-04-11
Didn't work. Got this (again):
jason@edubuntu:~$ fcc
fcc: Received signal 11 (aborting)...
Aborted

---

### Post by mucha on 2006-04-11
I didn't got it work either.

Errormessages:
> simon@mucha:~$ fcc
*** glibc detected *** double free or corruption (out): 0x085c0148 ***
Avbruten (SIGABRT)
simon@mucha:~$ sudo fcc
Creating link /root/.kde/socket-mucha.
can't create mcop directory

---

### Post by Third Thoughts on 2006-04-12
I know that this How-To is about installing firstclass native, but seeing as the only two people replying seem to be having trouble with it, I thought I'd redirect to this thread.
[http://www.ubuntuforums.org/showthread.php?p=909579#post909579](http://www.ubuntuforums.org/showthread.php?p=909579#post909579)

There you can download a tar that will allow you to run it under wine. 

~Andrew S.

---

### Post by Nate53085 on 2006-08-05
I have a newer (and presumably less broken) deb at

[http://www.natebourgoin.com/files/fcc-8.047.deb](http://www.natebourgoin.com/files/fcc-8.047.deb)

simply download and 

sudo dpkg -i fcc-8.047.deb

-type fcc to run

---

### Post by McDuff on 2006-08-05
the version provided at [http://reflex.at/files/fcc-8.090-1-Linux-i686.deb](http://reflex.at/files/fcc-8.090-1-Linux-i686.deb) might be even newer (8.090). i've been working with this version for some months now without having probs.

---

### Post by Third Thoughts on 2006-08-05
Yeah, I just started running it natively again yesterday because our school distributed the Linux client. It seems to be working great for me. One of my friends made a deb, and you can download it here. [http://webdrive.service.emory.edu/users/raswerl/Share/fcc_8.047-3_i386.deb](http://webdrive.service.emory.edu/users/raswerl/Share/fcc_8.047-3_i386.deb)

~Andrew S.

---

### Post by mimithebrain on 2006-08-07
I noticed that when I install anything that's part of KDE, it breaks. The reason is a arts library, I'm not sure which anymore.

---

### Post by slappy19 on 2007-08-07
> **Nate53085 said:**
> **NEW**

I have a newer (and presumably less broken) deb at

[http://www.natebourgoin.com/files/fcc-8.047.deb](http://www.natebourgoin.com/files/fcc-8.047.deb)

simply download and

sudo dpkg -i fcc-8.047.deb

-type fcc to run

This was AWESOME!  Thank you.  I have been trying to install FirstClass for 2 days and now I have it on.  I do know that this version is a little behind, does anyone know if anyone is working on an install for the latest package?  (8.3 I think)

**UPDATE**
I installed the Debian version from their website and it worked like a charm.  Now I have the latest version.

---

### Post by Shibby73 on 2007-10-06
[http://www.aptiris.com/ClientDownloads/8.3/FCC8315Linux](http://www.aptiris.com/ClientDownloads/8.3/FCC8315Linux)

Has the 8.3 with instructions.

Worked for me.

-Steve (Shibby73)

[www.stansgnosticus.net](www.stansgnosticus.net)

---

### Post by jay3712 on 2007-10-06
I just tried this and it appears to install, but when i put in my password in it gives me an error saying that the file 'local network.FCP' is missing. Any ideas?
Thanks

---

### Post by jay3712 on 2007-10-06
Nevermind, it just started working. Thanks guys, this is great.

---

