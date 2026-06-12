---
title: "[SOLVED] Programs don't appear in Applications"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-29
Hi Gang

I've been trying out a few Financial programs, but one I found in Synaptic Package Manager that is highly rated does not appear in Applications.
Probably because it uses the Apache Server?  It's called SQL Ledger!
When I downloaded it, it brought with it numerous other programs I assume it's dependent upon.  Like Apache2 was one of them.

Our of curiosity, when I uninstalled it, ONLY a single package uninstalled.  So I put it back, reinstalled it again.

NOW, how do I get to it to try it out, or is that over my head too?

TTUL
Gary

---

### Post by rockerphil on 2008-10-29
well typically a program will install the program binaries to /usr/bin so i'd personally look there and see if there's a program that looks like the one you're looking for, if so you can either run that in terminal to launch the program or you can simply run it by clicking the binary file. also, with most WMs you can edit the menu file and add the program to your menus in the event it doesn't add it to your menus for some reason (at least i know i can with Fluxbox) which normally would be found in the home folder (i.e. mine is /home/phil/fluxbox/menu) it shouldn't bee too difficult to add the entry, just do some google searches. to adress the issue of only the program package itself being uninstalled you can simply run this code in the terminal to uninstall all the dependency packages that was installed and are no longer needed:

```
sudo apt-get autoremove
```

hope this info helps,

Phil

---

### Post by Kellemora on 2008-10-29
Hi Phil

Well, I tried that!  Not my place to be either, hi hi....
I tried double clicking and then opening each of the three programs that looked like they might be it.  Nothing happened, SO I tried Speaker Test right above it, now that works, and each time I clicked it, the speakers got louder and louder, the only way out was to reboot.
Now my entire LAN is down!
Not because of that, probably installing SQL Ledger and all it's associated files.

Hope I get THAT fixed before the employees get here in the morning or I'll be paying to have them sit around twiddling their thumbs until I do.

TTUL
Gary

---

