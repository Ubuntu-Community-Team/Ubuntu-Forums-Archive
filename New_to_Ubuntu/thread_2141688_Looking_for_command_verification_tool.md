---
title: "Looking for command verification tool"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Nipplebeards on 2013-05-03
Hi All,

This may be a long shot.. I was talking to a guy from my local b&m tech store about some things with Ubuntu. He described an app that will check commands upon executing them and if they are going to cause major issues, will let you know or prevent them from being run on the real file system. 

He highly recommended it for newbies, told me the apt-get name and I forgot it. Does anyone know of this thing?

Thanks,
Nipplebeards

---

### Post by ibjsb4 on 2013-05-03
-s ?  --simulate ?

In terminal:

```
man apt-get
```

---

### Post by prodigy_ on 2013-05-03
> **Nipplebeards said:**
> apt-get name
Well, this is rather confusing. **apt-get** is a command line tool used to install/remove additional packages on Debian-based Linux distros (including Ubuntu). So there are two distinct possibilities:

1) The guy you talked to meant adding the **-s** switch to apt-get which results in running a simulation instead of actually performing the requested action. This works but applies only to apt-get (and several other command that support similar switches).

2) He meant there was actually a package that could verify syntax and potential harmful effects for arbitrary command. AFAIK, no such thing exists. And even if it existed I wouldn't trust it too much.

---

Generally, **man** is your friend because Linux command line manuals tend to be comprehensive (even in sometimes hard to navigate).

---

### Post by Nipplebeards on 2013-05-03
> **prodigy_ said:**
> 

2) He meant there was actually a package that could verify syntax and potential harmful effects for arbitrary command. AFAIK, no such thing exists. And even if it existed I wouldn't trust it too much.

---

Generally, **man** is your friend because Linux command line manuals tend to be comprehensive (even in sometimes hard to navigate).

Yeah #2 is more what he was describing. I will go talk to him again and update this thread with his reply. 

Thanks!

---

### Post by ibjsb4 on 2013-05-03
> Generally, **man** is your friend because Linux command line manuals tend to be comprehensive (even in sometimes hard to navigate). 						

Yep, was trying to point you to the -s option.  Guess I should of copy/paste for easier understanding :)

> -s, --simulate, --just-print, --dry-run, --recon, --no-act
           No action; perform a simulation of events that would occur but do
           not actually change the system. Configuration Item:
           APT::Get::Simulate.

           Simulation run as user will deactivate locking (Debug::NoLocking)
           automatic. Also a notice will be displayed indicating that this is
           only a simulation, if the option
           APT::Get::Show-User-Simulation-Note is set (Default: true). Neither
           NoLocking nor the notice will be triggered if run as root (root
           should know what he is doing without further warnings by apt-get).

           Simulate prints out a series of lines each one representing a dpkg
           operation, Configure (Conf), Remove (Remv), Unpack (Inst). Square
           brackets indicate broken packages and empty set of square brackets
           meaning breaks that are of no consequence (rare).

---

