---
title: "dual-monitor, nvidia geforce 6800, display scrambled"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by altonbr on 2008-11-03
I know this the 'Absolute Beginner' forum and I'm using w3m to access this forum right now, but when it comes to X.org, I am a beginner.

I had my Dell 19" LCD setup perfectly in Intrepid (as since Breezy) using DVI but I recently plugged in a LG Flatron W1934S and rebooted, my display when fuzzy. 
The display was cloned until Ubuntu actually started and tried to interfere and then it went fuzzy.

Now, when I have my original Dell monitor, it still is fuzzy and hasn't reverted back to its normal settings.

I've ran ```
dpkg-reconfigure xserver-xorg
``` but X.org 1.4 (and 1.3) doesn't change the display, only the keyboard, etc.

I've tried looking at /etc/X11/xorg.conf but the file is extremelly generic and only contains three lines of settings.

How am I to either (a) Return my one monitor back to its normal settings or (b) Get this dual-monitor working with an nVidia GeForce 6800.

I'm in a command-line browser, so I will try to add my lspci and x.org files.

---

### Post by Alberstt on 2009-02-11
I just posted that I solved near similar problem. ([http://ubuntuforums.org/showthread.php?p=6717677#post6717677](http://ubuntuforums.org/showthread.php?p=6717677#post6717677)) After tweaking the configuration of the monitor resolutions I got my setup close but with one fuzzy monitor.

I read to run **gdmflexiserver** and that cleared up my second monitor problem.

Maybe this will work for you as well?  Also if it does and you understand why, maybe you can provide me some incite.  

= )

---

### Post by altonbr on 2009-02-12
I don't have dual-monitors anymore, but what worked for me was just using the proprietary nVidia driver (v177 I think).

Sad, as I like to use all open-source software when I can, but what can you do?

I submitted a bug report on launchpad but it has gone unnoticed.

---

