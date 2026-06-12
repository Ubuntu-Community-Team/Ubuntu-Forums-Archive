---
title: "[SOLVED] 8.10 installation problem"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Narshada on 2008-11-03
Hi all, I'm having an issue trying to install 8.10 onto my laptop. I did do a search around the forums to see if anyone had posted similar but couldn't see anything, so forgive me if this is a repeat and direct me on my way.

I downloaded 8.10 and burned it to a CD - my first mistake might have been to burn at whatever speed was the default. I couldn't see an MD5SUM (which I since found,) so I skipped that part. (I know, I know...)

My hardware is a Dell Inspiron Laptop
80GB HDD
1024MB RAM
Dual core Centrino CPU running at approx 1.8 GHZ (sorry not got my laptop to hand.)
ATI Mobility Radeon

I ran it from the CD an it worked beautifully - my external HDD was there, my wireless worked once I'd put in the WPA2 key, Firefox worked fine and the desktop looked great and everything seemed to work fine apart from the obvious lag involved in running it from a CD but either way, I was converted. 

I did some shell scripting in Linux at university, which involved me using a free distro (I forget which, it was about 10 years ago,) and dual booting. The Linux was horrible - I ended up with a 16 colour display and very little worked. It was enough for doing shell scripting but it put me off Linux for a while.

Anyway, I installed from CD and it all went smoothly at first - I put in my location details etc and used the default partition selection.

Then part way through it went from the GUI back to a text screen, with various checks on it (I remember the last one was 'Checking Memory - OK') and then went to another screen telling me "the display server has been restarted up to 6 times in the last 90 seconds, which usually means something bad has happened. Waiting 2 minutes before trying again..." something, something. I apologise for not having the unabridged error text, but I'm going from memory. I may be able to fill in more tonight.
I clicked OK and it went back to the previous screen (checking memory - OK).

This happened a few times before it just hung on the text screen and seemed to do nothing. The keyboard was still responsive as hitting Enter took me to a new line.

I closed down and tried again, this time checking the integrity of the CD (which came back fine,) and the same thing happened. I waited a lot longer for anything to happen but nothing did.
I'm downloading 8.10 again to burn slower this time and also 8.04.1 LTS Hardy Heron in case installing and upgrading works.

Obviously I've lost Windows, (no biggie, I have my old install disk as a last resort,) and I backed up my files, but I really want to get this working.

If anyone knows of anything that might be causing this, I'd appreciate any help, but despite having done a little shell scripting and previously worked for a company that used proprietry servers based on FreeBSD, I am pretty much a *nix N00b, so may require some explanation.

Thanks very much.

---

### Post by Peter09 on 2008-11-03
Some sections of the install can take a while - are you sure you waited long enough? This is especially the case for partitioning a large drive.

If you cannot get through the display driver problems then download the alternate CD. This does an install without using the graphics card to any extent and will normally work. You can then fix any driver problems from there.

Also - does your system boot now - or attempt to boot onto Ubuntu?

---

### Post by Narshada on 2008-11-03
I think I gave it about an hour and came back to it and nothing had happened. Maybe I didn't wait long enough? To be honest I haven't tried booting without booting from CD as I assumed that it hadn't finished installing.
I'm currently doing an MD5SUM check on 8.10 before burning it again on a slow speed and I'll try again tonight with that (it can do it's thing while I go to a pub quiz! ;)) and if that doesn't work I'll try the alternate CD, which I'll download and check now.
Thanks. :)

---

### Post by Narshada on 2008-11-03
New CD worked. Posting from Intrepid Ibex now. :D

---

