---
title: "stupid question.. about safe downloading"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-27
which is the safest way to download:ftp or http or it just doesn't matter?
and some explaining would be nice also :)

---

### Post by sayakb on 2008-05-27
Generally, http uses port 80 and ftp uses port 21. Unless any other connection is being made to any other port, you should be safe with either case. You might install a firewall configuration utility like Firestarter
```
sudo apt-get install firestarter
```
At first, firestarter blocks everything. You might have to individually allow inbound services on specific ports (which is not a very tough job though). That would provide an extremely solid protection to your system.

---

### Post by Monicker on 2008-05-27
Depends on what you mean by "safe".  Ftp and http are both cleartext protocols, so any unencrypted traffic would be visible if it were intercepted.

What do you think you need to be "safe" from?

---

### Post by lisati on 2008-05-27
There's always "common sense" to guide you when it comes to deciding WHAT to download - do you trust the source? If not, be extra cautious.

---

### Post by niteshifter on 2008-05-27
Hi,

It depends upon what you mean by "safe". If you're asking if downloads via http / ftp are safe from prying eyes, the answer is no, and with ftp the username and password you send to the site are sent unencrypted. 

If you're asking if downloads by these methods are safe in the sense that the data will arrive complete and correct the answer is probably, with ftp being somewhat better than http (also slightly faster). Very large downloads - think multi-GB sizes - there is a small chance that some bit errors can creep in. If the site offers a checksum or a file of checksums, get it and check your download against their checksum.

If a site offers a torrent file, use it (bittorrent) for transfers, it's error free, even on huge downloads.

---

### Post by lunaluna on 2008-05-29
could you provide some more info for the protocols?

---

### Post by jcsteele on 2008-05-29
[http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)

[http://en.wikipedia.org/wiki/Ftp](http://en.wikipedia.org/wiki/Ftp)

---

### Post by Joeb454 on 2008-05-29
Ahh wikipedia ;)

I can tell you in short that - often - ftp is used for larger files, such as dvd iso files ;) Though http can still be used for files of this size.

Personally I prefer torrents for large files (you may not want to know, but I'll tell you anyway) because it checks the file as it goes along, so you know you have the correct file when it's downloaded :)

---

### Post by theophiles on 2008-05-29
> **lunaluna said:**
> could you provide some more info for the protocols?

Hyper Text Transfer Protocol was originally designed with text, specifically Hypertext, in mind. These files, even if they are pretty marked up with links and frames, are really pretty small. That was the design but we use it for all kinds of things now.

File Transfer Protocol was originally designed to move larger files than simple text files. I remember back in the early nineties waiting an hour for a picture to download. Http did not exist yet then, but even after it came out a couple years later, we wouldn't have dreamed of just putting pictures willy-nilly into the frames (like you see on this page). That would have taken forever to download!

Somethings remain the same. FTP is still used mostly for data that you are going to use outside your browser when it is finished. HTTP is used mostly for data that you are going to view inside your browser when it is downloaded. These are not hard and fast rules.

---

### Post by lunaluna on 2008-05-29
is there a possibility for someone to change the some of the  packets while the download is in progress or its impossible? 
just asking from curiosity?

---

### Post by jcsteele on 2008-05-30
your going outside of http/ftp/etc. and more into tcp/ip...I suggest googling for "TCP/IP" and read what you can if your interested...the topic is vast though so be forewarned...

tcp/ip checksum might be what you are referring to (when a packet gets corrupted, etc.) so you might want to google for it specifically...I am sure you will find lots of information, i believe CISCO still has alot of information on their sites, and a google came up with [http://www.cisco.com/warp/public/535/4.html](http://www.cisco.com/warp/public/535/4.html) for me real quick...might be a good starting point.  I can also recommend the oreilly book on the subject as well.

---

