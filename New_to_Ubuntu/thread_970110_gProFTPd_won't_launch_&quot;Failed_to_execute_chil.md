---
title: "gProFTPd won't launch: &quot;Failed to execute child process &quot;su-to-root&quot;"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by alecwh on 2008-11-03
Hello,

I'm trying to set up an FTP server on my Ibex desktop, and after reading a tutorial, I was suggested to install "gproftpd" and "proftpd". After doing so, a menu item was installed under "System Tools" called "GADMIN-PROFTPD". 

I clicked on it, and I am presented with an error message: "Could not launch menu item: Failed to execute child process "su-to-root" (No such file or directory)".

What's wrong, and how do I fix it?

---

### Post by downhillgames on 2008-11-03
> **alecwh said:**
> "Could not launch menu item: Failed to execute child process "su-to-root" (No such file or directory)".

What's wrong, and how do I fix it?
Well, you're missing some kind of command which is probably in another package.

Try this in a terminal (yeah, sorry...) and see if anything pops up:
```

sudo apt-get install apt-file && sudo apt-file update && apt-file search bin/su-to-root

```

EDIT: I bet you're missing gksu or something.

---

### Post by alecwh on 2008-11-03
Can't get [http://archive.canonical.com/ubuntu/dists/intrepid/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/intrepid/Contents-i386.gz)
menu: /usr/bin/su-to-root
menu: /usr/sbin/su-to-root

Anyway, problem is still there. =(

---

### Post by downhillgames on 2008-11-03
> **alecwh said:**
> Can't get [http://archive.canonical.com/ubuntu/dists/intrepid/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/intrepid/Contents-i386.gz)
menu: /usr/bin/su-to-root
menu: /usr/sbin/su-to-root

Anyway, problem is still there. =(

Ok, all you need to do is open your package manager and install the "menu" package. Should work then. Hope so, anyway :D

---

### Post by alecwh on 2008-11-03
Thanks! Now it launches, only to crash a few seconds later. When I run it in the terminal is says: "Segmentation fault."

Know what's wrong? Thanks for your help so far.

---

### Post by downhillgames on 2008-11-03
I'm not sure about the segfault :( sorry.

Yeah, well, all for naught it seems heh :(

As a side note, have you ever used Webmin? [http://www.webmin.com/](http://www.webmin.com/) Grab the Debian package if you want to try it out. It's been so long since I've set up FTP...

On Windows I used to use um, what was it called... WS_FTP Server. Linux really needs something as easy to use as that :/

---

### Post by Björn Felten on 2008-11-05
> **downhillgames said:**
> Ok, all you need to do is open your package manager and install the "menu" package.
WOW! Thanks a million, downhill! This solved my problem with WiFiRadar. After I upgraded to 8.10 I got the very same su-to-root error message. After I installed the menu package all is well and working again.

Yeezzz, ain't internet great? :)

---

### Post by SINZAR on 2008-11-07
I'm having the same issue. After installing the menu package it crashes after starting. This is what I see in the syslog

Nov  7 10:31:05 ubuntubox kernel: [  600.313970] gadmin-proftpd[6134]: segfault at 200401 ip b786f5c8 sp bfa42720 error 4 in libgobject-2.0.so.0.1800.2[b7846000+3c000]
Nov  7 10:31:49 ubuntubox kernel: [  644.195226] gadmin-proftpd[6155]: segfault at 200401 ip b78ed5c8 sp bfbc1010 error 4 in libgobject-2.0.so.0.1800.2[b78c4000+3c000]
Nov  7 10:40:01 ubuntubox /USR/SBIN/CRON[6195]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  7 10:45:29 ubuntubox kernel: [ 1464.313571] gadmin-proftpd[6446]: segfault at 616c756d ip b78a65c8 sp bfe782c0 error 4 in libgobject-2.0.so.0.1800.2[b787d000+3c000]

If I have to uninstall/reinstall gproftpd what files should be backed up so I don't loose all my settings?

---

### Post by nossifer on 2008-12-05
i dont know whats wrong.  i pasted the shortcut command into a terminal:

~$ su-to-root -X -c /usr/sbin/gadmin-proftpd
<<nothing happened>>

~$ sudo -X -c /usr/sbin/gadmin-proftpd
sudo: illegal option `-X'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
~$ sudo -c /usr/sbin/gadmin-proftpd
sudo: illegal option `-c'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
~$ sudo /usr/sbin/gadmin-proftpd
Segmentation fault
~$

---

### Post by nossifer on 2008-12-05
i have to go to work now, but someone can try this:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=991644](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=991644)

~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                           [ OK ] 
 * Starting ftp server proftpd                                                   - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 52 of '/etc/proftpd/proftpd.conf'
                                                                         [fail]

---

### Post by pneedleman on 2008-12-10
if you goto [http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/](http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/) and download version gadmin-proftpd_0.3.5-2_i386.deb for 386 or 	gadmin-proftpd_0.3.5-2_amd64.deb for 64bit it should work. Hope this helps.

---

### Post by nossifer on 2008-12-10
> **pneedleman said:**
> if you goto [http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/](http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/) and download version gadmin-proftpd_0.3.5-2_i386.deb for 386 or 	gadmin-proftpd_0.3.5-2_amd64.deb for 64bit it should work. Hope this helps.

looks good.  thanks a lot my friend.  it will take me a couple days to really get to this, but the file launches.  if i dont come back in a few days, mark this Solved. :)

---

### Post by diiphantom on 2008-12-30
> **pneedleman said:**
> if you goto [http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/](http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/) and download version gadmin-proftpd_0.3.5-2_i386.deb for 386 or 	gadmin-proftpd_0.3.5-2_amd64.deb for 64bit it should work. Hope this helps.

Yes i was about to answer when i saw your post pneedleman. For those having this issue with GPROFTPD, I fixed it like this:

I completely removed proftpd, deleted the folder /etc/proftpd, to generate new proftpd.conf
Reinstalled it

and installed this version of GPROFTPD:

gadmin-proftpd_0.3.5-2_i386.deb

you can read about the issues with ubuntu here: 
[http://mange.dynalias.org/linux/misc/Intrepid_Ibex_errors.txt](http://mange.dynalias.org/linux/misc/Intrepid_Ibex_errors.txt)

---

### Post by chuycastillo on 2009-04-20
> **pneedleman said:**
> if you goto [http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/](http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/) and download version gadmin-proftpd_0.3.5-2_i386.deb for 386 or 	gadmin-proftpd_0.3.5-2_amd64.deb for 64bit it should work. Hope this helps.



It was the solution. I installed that version and it works!  thank you very much.

---

