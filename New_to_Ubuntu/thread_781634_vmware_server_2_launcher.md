---
title: "vmware server 2 launcher"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-04
i just installed vmware server 2 beta 2 on ubuntu 8.04- does anyone know where the launcher icon resides after it installs?  i always resided under Applications/System Tools with Workstation and Server 1.5, but does not show up there now.  any ideas?  thanks.

---

### Post by javaguy78 on 2008-09-24
vmware server 2 does not have a gtk interface like vmware server 1, it has a web front.  After you've installed it, you can access the management console by going to [https://localhost:8333/ui/#](https://localhost:8333/ui/#)

If you didn't setup a user when you ran vmware-config.pl, then re run it and when it asks "The current administrative user for VMWare Server is 'root', would you like to specify a different administrator?" Answer "Yes" and specify your account, then login using your username and password.

---

### Post by mavenjohnson on 2008-11-29
try these /usr/lib/vmware/share/icons/.  hicolor/scalable/actions/vm-tools-install.svg is decent to use.  using the command "vmware" in a launcher should trigger the browser interface.

---

### Post by briandu on 2008-11-29
I have also installed the 64bit of vmware server.

When I go to the [http://localhost](http://localhost) it asks me for a UID and PWD. :confused:

What is this? I have tried my own and the root UID/PWD combination and no result.

What do I do now?

---

### Post by briandu on 2008-11-29
Solved  when administrator prompt pops up say yes and set urself as administrator  - solved

---

