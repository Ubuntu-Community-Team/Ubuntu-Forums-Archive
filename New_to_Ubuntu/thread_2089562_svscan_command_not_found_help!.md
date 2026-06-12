---
title: "svscan: command not found help!"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by ggole on 2012-11-29
Hi all,

I was just installing the latest version of PHP on my server. It all went well and so I did a reboot of the server. However, when it came back up, I noticed I could no longer access my site via it's domain name. Long story short, the reason is because svscan is no longer running tinydns. 

I then tried to get svscan to restart my services but everytime I try to do so it says:

svscan: command not found. 

I checked in /commands/svscanboot and the file is there but when I try to execute it, it says:

/command/svscanboot: No such file or directory. 

Even though I can see the executable is there when I type ls to list the files. 

So I'm not sure how to restart it or if the daemontools has just suddenly broken or what. Any help here would be great and I would really appreciate any advice to tracking down this error. 

What I did: 
downloaded latest version of php (5.4.9)
configured it
ran make clean
make
make install
restarted apache
site came back up.
rebooted
svscan not working.

I also noticed that when I type php -v it says I have php version 5.4.5 installed which seems wrong :S

---

