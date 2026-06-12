---
title: "Wine &amp; Windows Apps"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by drenard on 2008-09-23
Good Day,

I hoping someone might be able to explain to me if this is possible and maybe have link to show some pointers.  If using
Ubuntu 8.x with Wine, How do you setup to handle legacy applications such Office 97 or with Applications that require a physical drive mapping like "T:" - I would love to use Ubuntu but get held up at this point and cant find a clear answer because unlike windows you can simply do a net use to point to the shared drive - "Net use T: \\server\tdrive"

I see how you can connect to a Microsoft server from Ubuntu but not how you establish the drive mapping to allow the legacy application to run. 

Any info would be great.

---

### Post by HittingSmoke on 2008-09-23
To do legacy apps there is an option in Wine to set what version of Windows you want it to emulate.

Cant help with network drives, sorry.

---

### Post by jemate18 on 2008-09-23
First check the wine application db if your software is listed.. Make sure to choose platinum and gold since they are the ones tested to work.

> [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Tatty on 2008-09-23
I believe winecfg allows you to map windows drive letters to your actual linux mount.

So you would first need to mount your network share in ubuntu,  Then assign T: to that mount point using winecfg.

---

### Post by drenard on 2008-09-24
Thanks for the input. I have been reading about Wine and have posted a message there to see about the actual drive mapping. 
If I should find the answer I will post it back here.

---

