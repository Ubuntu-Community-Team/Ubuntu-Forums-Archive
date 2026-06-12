---
title: "Hardy on ReiserFS"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-04-24
Yesterday I read a post on planet ubuntu and the conclusion was that reiserfs was a very fast file system.

Would it be advised to install hardy on reiserfs?

Would would be the negative aspects on using reiserfs instead of ext3?

---

### Post by Michael.Godawski on 2008-04-24
I do not have an exact answer to your question but from a quick look at the different file systems, there is much reading before I say something on this topic :)

[LIST]
[*][http://wiki.novell.com/index.php/Linux_Data_Management](http://wiki.novell.com/index.php/Linux_Data_Management)
[*][http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
[/LIST]

---

### Post by billgoldberg on 2008-04-24
That's a lot of reading.

I would also like some feedback of people that used the FS on gutsy or another ubuntu distro.

Are there any problems ubuntu has with reiserfs?

---

### Post by PmDematagoda on 2008-04-24
> **billgoldberg said:**
> That's a lot of reading.

I would also like some feedback of people that used the FS on gutsy or another ubuntu distro.

Are there any problems ubuntu has with reiserfs?

I've used Hardy on ReiserFS since Alpha1 and it was(and still is) reliable and is also rather fast.

---

### Post by dada1958 on 2008-04-24
I use reiserfs since Ubuntu 5.10.

---

### Post by billgoldberg on 2008-04-24
Thanks, I'll use reiserfs than instead of ext3.

---

### Post by twright on 2008-04-24
xfs is also fast

---

### Post by milosz.galazka on 2008-04-24
I use xfs too but I think that I will not feel any difference between xfs or reiserfs on home computer.

---

### Post by kellemes on 2008-04-24
A common difference you may notice is that it's takes more time to mount a ReiserFS formatted disk.
At least that's what I notice.

---

### Post by Zill on 2008-04-24
When I started using Mandrake Linux I used ext3.  However, after a few power outages, immediately followed by my futile attempts to repair my broken file system, I changed over to reiserfs.  I continued with reiserfs when I moved over to Ubuntu with Breezy.

Several years and power outages later, reiserfs has performed faultlessly on all our three PCs :-)

ps.  I never did quite figure out what I was supposed to do with ext3 "lost+found" data - fortunately reiserfs does not have this peculiar directory!

---

