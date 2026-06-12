---
title: "Installing text editor"
date: 2007-09-14
forum: Programming Talk
---

### Post by Ken Iovino on 2007-09-14
Hey everyone, i just finsihed installing Ubuntu 7.04 on my dv6000 laptop and everything worked flawlessly. This is my first time switching to a Linux distro and I would like to know how to install some programs I need. 

I'm trying to install Bluefish: [http://bluefish.openoffice.nl/download.html](http://bluefish.openoffice.nl/download.html) and it says:

> 
Debian and Ubuntu users just run apt-get install bluefish and Bluefish will be downloaded, configured and installed on your system.


I tried typing "apt-get install bluefish" in the terminal, but I get the following error message.

```

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

What do I need to do to get this installed? Sorry if this is a noob question. Thanks! :)

---

### Post by kerry_s on 2007-09-14
**sudo apt-get install bluefish**
you can also use the gui front end "synaptic" under adminastration.

make sure you have all the repos turned on.

---

### Post by Ken Iovino on 2007-09-14
Kerry, thank you for that. Worked like a charm. :)

---

### Post by ddrichardson on 2007-09-14
Just to expand - the initial command needs to been run as sudo - the standard user account does not have permission to install software - hence why synaptic asked for the password.

---

