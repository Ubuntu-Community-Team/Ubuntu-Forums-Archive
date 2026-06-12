---
title: "nothing after login"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by Newb2Ubun2 on 2011-11-07
Hello all. My first encounter with Ubuntu is off to a bit of a rocky start. I'm hoping that the issues I'm facing are simple issues to work with. 

I've got a fairly new Dell Inspiron laptop (maybe 6 months old), with Windows 7 currently installed. I wanted to try the Wubi installer to run 11.10 side by side with 7 before making my mind up on which OS I prefer.

To my point, after completing the download a install process, I successfully arrived at the login screen. After I input my password, the pretty pinkish/purplish screen appears, but nothing else happens after this. I patiently sat for at least 15-20mins waiting, but nothing ever happened. I eventually gave up and had to power down and restart in Windows. An interesting thing happened when logging into windows. Somehow, my wireless adapter was now disabled. This has never happened since I've owned this computer.

Still thinking it was somehow my fault, I uninstalled Ubunto and tried going through the download/install process once again. The end result was exactly the same (including my wireless adapter becoming disabled when logging back into windows. 

Has anyone out there ran into this strange issue? I really would love to check out this OS, but I'm becoming a bit fearful. Any suggestions or ideas would be greatly appreciated! Thanks!

---

### Post by Mark Phelps on 2011-11-07
I can't think of any reason why a wubi-based install would disable your adapter any more than a regular install would.

But I did run into a similar situation with 10.10 when I first installed it on my desktop that behaved the same.  The wired connection would drop inside Ubuntu.  When I rebooted into win7, the connection was down. I had to run a Realtek LAN diagnostic utility to FORCE the connection to restart.

Every time I rebooted into Ubuntu, it was the same problem.

Since I was hibernating Win7, my guess is that had something to do with the LAN connection going down and staying down while Win7 was hibernated.  However, eventually, it fixed itself -- after a couple of LAN driver updates in Win7.  I'm still hibernating Win7, but the LAN connection is no longer going down.

When I later installed 11.04, that problem didn't happen any more, nor does it happen with 11.10.

---

