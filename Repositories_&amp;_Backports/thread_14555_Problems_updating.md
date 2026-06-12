---
title: "Problems updating"
date: 2005-02-08
forum: Repositories &amp; Backports
---

### Post by dan1928 on 2005-02-08
I recently install Ubuntu and so far love it. I got Samba up and running through the posted help files. My problem is that now whenever I try to update (for example firefox through Synaptic), i get a samba failed error. I'm not sure how to copy the terminal output to text (otherwise I'd post it directly), but it always fails at: 

*Starting Samba daemons...                          [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure);

there's more, but I'm not sure how much is pertinent. When I opened up firefox it had updated to 1.0, but the end of the terminal stated:

Errors were encountered while processing:
samba

Failed to apply all changes! Scroll in this buffer to see what went wrong


Anyone know where I can start. Obviously the update worked for Firefox, but I'd like to get that error taken care of as it seems to happen for any update. Any help is greatly appreciated!

-Dan

---

### Post by mendicant on 2005-02-08
You can try running the daemons manually, enabling the debugging.  For samba, look in /etc/init.d/samba.  You'll notice that the start) entry starts nmbd and smbd.  Try running nmbd:

% sudo nmbd -d 1
% sudo smbd -d 1

If you get errors that you can figure out, you're done.  If no errors, then up the debug level (goes up to 10).  You can also post the output here.

---

