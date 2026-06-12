---
title: "Abandoned Linux as a home server option"
date: 2015-08-24
forum: New to Ubuntu
---

### Post by john-geroitos on 2015-08-24
I decided to run a home file/print server with Ubuntu on my old laptop. Setting up the share was easy, only problem was while upload speeds (lan) were fine, download speeds were horrific.

After some googling, I've found thats a common(?)/known Ubuntu problem with no easy solution, so 2 hours of unsuccessful troubleshooting later, I tried other distros.

One afternoon later of troubleshooting sambas whims, I ditched the "linux" part of the project.

Sadly, it's not the only time a linux project has gone south for me. This is not a "linux sucks" post, just expressed frustration that I'm sure is shared among many new users.

---

### Post by SeijiSensei on 2015-08-24
Are you asking for help?  I've used Samba for years and have never had a problem with transfer speeds.

When you say "download speeds," are you referring to copying files from the Ubuntu server, or something else?

---

### Post by john-geroitos on 2015-08-24
Copying files from the server is really slow. The other way around is ok

---

### Post by ian-weisser on 2015-08-24
Hmm. My Linux-based print and file server seems plenty fast.
Perhaps your settings? or Network?
What 'known issue'? Is there a bug report open on it? A link would help...

---

### Post by john-geroitos on 2015-08-24
Everything else works fine in the network and as I said, its a known issue with Ubuntu...

---

### Post by QIII on 2015-08-24
Unknown to me.  My home server and web server both run Ubuntu.

Perhaps we could help if you would care to have us try.

---

### Post by john-geroitos on 2015-08-24
Gonna sleep on it since its late here and maybe give it a shot tomorrow... Thnx for listening me ppl

---

### Post by bab1 on 2015-08-24
> **john-geroitos said:**
> .. and as I said, its a known issue with Ubuntu...
I have no problems with Samba on my network.  It would be nice for you to document this "known issue".  There [s]can be[/s] is lot's of belly aching on various forums, but that does not make the problem well known or even true.

As @ SeijiSensei said  "Do you want help fixing this?"

---

### Post by cariboo on 2015-08-24
I'd like to know what you consider slow upload speeds. I use a combination of samba,NFS and sftp to transfer files, it all depends on how I feel that particular day :). All 3 protocols transfer at the maximum network speeds on my network.

**Note:** My networks consists of mostly Ubuntu powered system, with very occasional windows usage on a laptop and one desktop system.

---

### Post by MartyBuntu on 2015-08-24
Wireless?

---

### Post by john-geroitos on 2015-08-25
This community is indeed warm and welcoming, I'll give it a go when I get home and give you all the info you need.

The laptop is an old asus, connected through Ethernet cable (100). The usb disk is  3TB USB 3, connected to a USB 2 port.

Slow is ~300kb/s. Fast is ~9Mb/s.

I'll write a full summary when I get home...

---

### Post by HermanAB on 2015-08-25
Hmm, in general, finding a problem is the hard part.  The fix is usually very simple.  As for SAMBA, it should operate at the same speed both ways if all is working properly.  My guess is that you have a network or authentication problem - something is waiting and waiting, falling back and trying different modes and eventually giving you the file.

The proper way to debug SAMBA is with the 'smbclient' program.  It provides very clear error messages.  You cannot successfully debug SAMBA with a GUI tool - doing so is a waste of time - since you cannot see what is actually happening.

---

### Post by john-geroitos on 2015-08-25
Alright... some proper description and new-found data.

Asus laptop A6ja, Ubuntu 14.04 LTS installed, connected to a 100Mbps LAN network via cable.

3TB USB hdd connected and shared with  Samba version 4.1.6., no security.

Windows 10 client downloads data from the HDD at speeds around 100 kb/s, while it uploads to the HDD around 9 Mb/s (not "ideal" but normal LAN speed).

UPDATE
If I connect through WiFi, the speeds are normal. So I'm thinking ethernet driver problem?

---

### Post by john-geroitos on 2015-08-25
UPDATE
It looks like it really WAS a driver problem that got fixed thnx to this guy:
[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

Everything now works fine, including the printer.

After trying a few distros while doing this, the samba part was indeed a lot easier in Ubuntu. 

cheers

---

