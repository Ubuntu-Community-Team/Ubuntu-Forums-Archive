---
title: "server connection issue"
date: 2017-04-09
forum: New to Ubuntu
---

### Post by dpen2 on 2017-04-09
Hello Everyone,

completely new in this world of Ubuntu but fascinated by the potential.

I recently installed 16.04LTS on  my laptop, i have a AIRPORT EXTREME router to which i connect a hard drive for file sharing.

The problem is that i keep having issues connecting to it. Sometimes it works great for a few minutes then i get a "connection timeout" error message, sometimes it is very slow to work with.

Since I'm totally new and have zero experience, the online research of this problem gave me no results (or at least that i could understand).

Can anyone drive me trough this?

thanks a lot in advance!!

---

### Post by TheFu on 2017-04-10
How are you connected - wired or wireless?

Do other, non-storage things, work?

Does it work from other devices on the same network, as expected?

We cannot tell if this is a network issue, a CIFS issue or some failing router issue.

BTW, connecting storage to any WAN router probably isn't good for security of those files.  Router vendors make mistakes all the time which effectively make storage available to the internet.  It has been a known issue on many routers. Apple tends to take great care to do things well, but it should still be a concern. Everyone makes mistakes.

---

### Post by dpen2 on 2017-04-10
Hello TheFu,

thank you for your reply.
How are you connected - wired or wireless?  WIRELESS
Does it work from other devices on the same network, as expected? YES IT WORKS PERFECTLY FROM MY WIFE'S LAPTOP (MAC)

What should i do to verify where the issues is?

thanks a lot

---

### Post by TheFu on 2017-04-11
So an Apple laptop connects to an Apple router. Nothing surprising there, but at least we know it is working from other devices.  That reduces the chances it is a router problem.  

Can you plug into the router using ethernet? Does that work from the Ubuntu machine?  This would eliminate some other possible issues.

I don't use wifi much - there's a wifi-info script commonly referenced in these forums. Find it. Run it. Post the URL for the generated output.  Please.

---

### Post by dpen2 on 2017-04-11
ok, so i connected my laptop harwired to the router and it is even worst..........i can't access my shared HD at all.

I run the wifi-info script and here the result:All your help is much appreciated!

[http://paste.ubuntu.com/24361367/](http://paste.ubuntu.com/24361367/)

---

### Post by TheFu on 2017-04-11
3 things.
* the wrong wired ethernet driver appears to have been installed and setup.  Go through the info to find the correct wired ethernet chip, then google for "ubuntu 16.04 {insert that chip}" - and see what comes up. Follow those instructions.
* the wifi signal quality seems really low (39/70). How far away from the AP are you? Move closer. Does that fix it?
* It might be a driver thing with the wifi too. Go through the info to find the correct wifi chip used, then google for "ubuntu 16.04 {insert that chip}" - and see what comes up. Follow those instructions.

As for wifi signal strength - I'm about 20 ft away from the wifi here - going through an internior wall. It is a N-300 router only using 2.4Ghz - the quality is 70/70 and Signal level=-40 dBm.  There is a wifi signal that I'm seeing 39/70 quality from - it is at least 1 house away with a level of -71 dBm.

Just trying to teach you to fish for yourself. If you need more help, ask.

---

