---
title: "How can I access music files on my Windows machine from my Linux machine?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-11-17
I have all of my music files on a machine running Ubuntu Server.  
I have a separate machine with Windows installed, which has iTunes.
These machines are both connected to the same router on the same network.  
I'd like to figure out the most efficient way to get the music files from my linux machine imported into iTunes on my Windows machine so I can update my iPod.  Any help would be appreciated.


(Yes, I know there are iTunes alternatives for Linux but this is how I'd like things to work :) )  Thanks again!

---

### Post by akelsall on 2008-11-17
From the limited knowledge I have of Linux (been running it for about a month now), I'd say the best route for you would be to check out a program called Samba. It makes you're Linux box look like a Windows PC and allows you to set up shares between "real" Windows machines and your Linux box. It may take some time on your part to figure out how to set it up, but learning is part of th fun, right? :) 

[http://de.samba.org/](http://de.samba.org/)

Oh, and don't do what I just did. I entered [www.samba.com](www.samba.com) and wound up on an Arabic site. Might have Homeland Security knocking on my door soon. :lolflag:

---

### Post by TMcKSmith on 2008-11-17
I will also add that the drive on my linux server that contains the music files I need is formatted in NTFS

---

### Post by boaterrob on 2008-11-17
it won't matter that your Windows box if formated to NTFS.  Ubuntu will still be able to read the files.  You might have to download viewers for Windows to look at your ext3 drives however.

---

### Post by TMcKSmith on 2008-11-17
no, I'm trying to access my files on the linux box from my windows machine...

---

### Post by bennachie on 2008-11-17
Try [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by spiderbatdad on 2008-11-17
lol. It's almost too easy. Right click a folder you want to share and select sharing options, then try to share the folder. You will be prompted to install some software. Install the software by agreeing. Then go back to step one.

I  apologise. I just re-read your original post. If you are running a server, it should be pretty easy to access the files you want. What type of server are you running? Maybe consider apache, then just use indexing as an option for the appropriate folder...or use  openssh and install putty on your windows machine.

---

