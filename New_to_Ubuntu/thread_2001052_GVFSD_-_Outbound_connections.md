---
title: "GVFSD - Outbound connections"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by roodypoo on 2012-06-10
I ran netstat -t to find outgoing connections being made without my permission. I'm not a big fan of programs "phoning home". Isn't that what spyware/malware/rootkits do?

After some looking, I found it to be GVFS. Is it possible to remove GVFS without removing Gnome or do I need to find a new WM?

I have to say I'm very aggravated by this.

---

### Post by mcduck on 2012-06-10
Now what makes you think it would be "phoning home"? :D Did you check *where* it's connecting to?

Anyway, that's just a result from a harmless bug: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/571970]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/571970")

(the sort and not-too-technical explanation is that gvfsd-http is used by many different programs for many different purposes, for example by Rhythmbox to download album art, and by web browsers when you drag&drop files to your desktop to save them on your computer. And it has a small bug that causes it to leave the connections in CLOSE_WAIT state instead of closing them properly. CLOSE_WAIT means that the actual connection to the server has already been closed, but the program that opened the network socket hasn't yet closed it. This causes no security issues, and shouldn't result in any issues with system resources on any normal use, which is probably why the upstream developers haven't fixed it yet.)

---

