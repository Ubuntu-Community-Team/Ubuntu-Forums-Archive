---
title: "Where to get help with individual services."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-11-21
Hello!

I am starting to go through the services that are activated, but I'm struggling a bit.  I can't seem to find any one place online that explains what each service does (so I can tell if I need it or not).

For instance, Account Information Resolver is active, but I don't know what it is or what it does, and a search both here and on Google has turned up with nothing.

Is there any one place I can go to learn about each service?

(I am running Intrepid :)

Thank you!

~Nix

---

### Post by lswb on 2008-11-21
Are you finding these service names from the Main Menu/System/Admin/Services application? I'm not using Intrepid at the moment so I can't check, but in hardy the name of the actual program for the service is displayed for most of the listed services if you resize the window enough horizontally. Once you have that, you can type "man program-name" in a terminal, or do a google search.

Many of these services are started at boot by the scripts that are found in /etc/init.d and linked to from the /etc/rc2.d. Also, you can use the "man -k keyword" command to get a list of topics that refer to "keyword" For instance with your example, "man -k resolver" returns a list of items that you can then run "man item" on. (Unfortunately probably not a good example; I don't think "Account Information Resolver" actually has anything to do with what "man -k resolver" suggests.)

---

