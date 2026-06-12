---
title: "How to Install Brother Printers In Edgy"
date: 2007-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mlissner on 2007-01-13
So, after having gone through figuring out how to install my printer (a Brother 4800) about ten times now, I've decided to put it in writing for myself as much as the rest of you that may stumble onto this.

Here's the process for installing Brother Printers into CUPS...it worked for me, the usual caveats apply. If it fails, feel free to let me know. If it works, add to this thread to let others know...

OK. So here's what I did:
1. Update CUPS. For some reason, edgy doesn't come with the latest version of CUPS. Go to CUPS.org, get the lastest tar.gz, unpack it using archive manager (by double clicking it), and navigate to the newly unpacked directory in your terminal. Now that you're in there do this:
```
./configure
make
sudo make install
```
That *should* install it for you. I did a reboot afterwards to be sure, and I should mention two things about this at this point. One, in Fedora Core 6, CUPS 1.2.7 came by default, and when I plugged in my printer, it just worked, so I thought the upgrade might do it. Two: The upgrade didn't do it, so this whole step could be unnecessary, though I understand that CUPS 1.2.7 has some security ups vs 1.2.4, which is Edgy default.

OK. So the next step is to get the stuff for Brother printers. For that, go to [http://solutions.brother.com/linux]("http://solutions.brother.com/linux"), and navigate around until you have downloaded the lpr and cupswrapper modules for your printer model. 

Now, because Brother printers rely on lpr, which doesn't come installed on Edgy, go into Synaptic, and install it. Once that's installed, double click the lpr module you got from the Brother site to install it. When that's done, install the cupswrapper module the same way.

Shutdown. Plug in the printer. Boot up.

If the auto print configuration thing doesn't pop up on its own, go to System > Administration > Printing, and the wizard should be pretty obvious. You might need to fiddle a bit in [http://localhost:631](http://localhost:631) to make things work. I didn't, but printer installation is a black art.

Good luck. Don't hold me liable for these instructions, they're just what worked for me.

---

### Post by flmckinney on 2008-12-22
Thanks! This post got me on the right track and helped considerably. I was trying to install a Brother MFC490CW and was having no luck. Here is what I did.
I did not update the CUPS. I went to the Brother site and got the lpr and cupswrapper files. I installed lpr (not the one I just got but the one listed in Synaptic) through Synaptic and then installed the packages I got from Brother. I did all this with the printer off. I shutdown, turned on the printer and booted up. No wizard appeared! I went to System>Admin>printing and the printer was listed but would not print. I deleted the printer then ran the find printer wizard. It found the printer and (after hitting forward once or twice) offered to install it with the cups driver. Did the install and the printer works great. I have not tried to scan yet but suspect it will be a new problem that I can work on.
Hope this helps someone.

---

### Post by mlissner on 2008-12-22
Yeah, I've experimented with the scanner on mine. There's a scanning driver that you'll probably want to get from that same CUPS site, but I don't remember the installing technique. I think the software you'll want to use is called XSane Image Scanner.

---

