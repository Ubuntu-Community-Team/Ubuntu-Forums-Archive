---
title: "need suggestions about upgrading ubuntu in an almost dead box"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by MadKAT on 2008-05-10
hello:

the monitor in my old PC died a couple of months ago. The CD-ROM died a year ago. Luckily for me i got openssh server installed before the monitor died so i still get to access my files and its internet connection is still working. webserver is still accessible,. so all in all it's still functioning as a file and web server.

but my question here is, the OS in it is getting old. it's running the 6.10 i think. so how do i get to upgrade it to the new version? or even change it to a server version. (or how to install without monitor and cd)

please dont suggest buying a new monitor hehe :D. i already know that but just not feasible right now. no cash :D and please dont suggest throwing it in the garbage, i still love the old bugger :D


thanks!

---

### Post by Xiong Chiamiov on 2008-05-10
I believe you can upgrade with something like
```

gksu update-manager -d

```

EDIT: Oh, nvm, that's a GUI command, duh.
```

sudo apt-get dist-upgrade

```

---

### Post by MadKAT on 2008-05-10
oh ok thanks! I'll give that a try later.

but how about something that will now remove the gui packages or at least not make them run at all.

Thanks!

---

