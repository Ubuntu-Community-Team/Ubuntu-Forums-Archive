---
title: "Kubuntu 11.10 + LTSP - possible? If so, how?"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by doctorbighands on 2011-10-28
I just installed Kubuntu 11.10 on a server. I then went through the process described [here]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall"), under the section entitled, "Installing on top of an already running desktop system".

I PXE booted a thin client. It found the server, and began to boot. Then, the following happened:

*It gave me a purple "Ubuntu" boot splash screen (on top of a KDE install on server?)
*It gave me an "Ubuntu" GDM login screen (same one you get with a standard Gnome Ubuntu LTSP setup)
*I attempted to log in, and it kicked me back to the login screen. In other words, no desktop was loaded, in spite of typing my login credentials VERY carefully.

Is there something different that I need to do to create an LTSP thin client interface using Kubuntu?

Any help is very much appreciated. Thank you!

---

### Post by hansdown on 2011-10-28
Hi, doctorbighands.

The guide you are using, is for ubuntu.

I'm trying to give you the kubuntu link, but it keeps timing out.

I'll try later.

---

### Post by doctorbighands on 2011-10-28
Problem solved.

I don't know what was different, but I issued another
```
sudo ltsp-build-client --arch i386
```
and now my thin clients boot without issue.

I guess sometimes it's just a good old-fashioned "reboot" that fixes many problems!

Still weird that I get a purple "Ubuntu" boot splash, but I'm figuring that's probably something to do with the defaults in the LTSP packages. No big deal!

---

### Post by hansdown on 2011-10-28
Good, that you solved it, to your happiness,doctorbighands.

Hope all goes well.

---

