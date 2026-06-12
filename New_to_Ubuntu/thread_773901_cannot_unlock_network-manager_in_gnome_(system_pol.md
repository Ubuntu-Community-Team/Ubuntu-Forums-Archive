---
title: "cannot unlock network-manager in gnome (system policy problem)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by oimon on 2008-04-29
hello
using hardy, i realised i couldn't scan for wireless networks. when i tried to manually configure the network settings, system policy manager asks for my password. however authentication always fails. i've tried changing my login password, also deleting the login.keyring (there is no default.keyring file), and also making a new user on the system, but no joy. 

Something seems to be corrupted that is blocking access. the "system policy prevents modifying the configuration" appears and i can't get any further- password is always rejected.

anyone else experience this?

---

### Post by oimon on 2008-04-29
i found a workaround to this by running polkit-gnome-authorization and allowing my user explicit authorisation under freedesktop-systemtoolsbackends-manage system configuration.

it's a security risk but until i find a fix, there's no other way!

---

### Post by richardkemp on 2008-05-22
Thanks for the workaround, I've found the problem too. Its a bad bug!!!

---

### Post by evilcydnar on 2009-05-03
I've got this problem to. It started after I had accepted 188 updates to UBUNTU and associated packages days after I bought the machine from dell a few weeks ago. Before those updates I could get access to network manager with my password. I have changed password using instructions on forums, but to no avail. I posted it on a UBUNTU forum and was told it was NOT A BUG but have been offered no solution other than resetting password which doesn't work. As this is my first experience of UBUNTU/UNIX how do you run polkit-gnome-authorization to allow explicit authorisation for my user under freedesktop-systemtoolsbackends-manage system configuration?

---

