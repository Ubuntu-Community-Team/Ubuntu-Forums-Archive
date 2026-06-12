---
title: "[SOLVED] Ubuntu Antivirus"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by peterjakey on 2008-08-17
Hi, I was wondering how important it is to have an antivirus and firewall on ubuntu

---

### Post by Paqman on 2008-08-17
> **peterjakey said:**
> Hi, I was wondering how important it is to have an antivirus and firewall on ubuntu

Not important at all. Ubuntu doesn't get it's security from adding extra layers of software, it has it built in.

The best protection against malware is to simply stay current with security updates. If you are then you're protected against all known threats.

As for firewalls, the default configuration is already secure. If you don't install any server software (eg: Apache, Samba) then you shouldn't need to do anything. If you do, there are a few different tools (such as ufw for the command line, and the GUI-based Firestarter) that you can use to control access. These aren't firewalls, they're just tools to configure the built-in firewall system.

---

### Post by aheckler on 2008-08-17
A firewall is already installed and configured on all Ubuntu systems, so there's no need to worry about that. And there's almost zero chance of getting a virus with a Linux-based system, so you really don't need to worry about antivirus either.

Read [this]("http://www.psychocats.net/ubuntu/security#firewallantivirus") for more information. It's a bit outdated, but essentially correct.

---

### Post by peterjakey on 2008-08-17
> **Paqman said:**
> Not important at all. Ubuntu doesn't get it's security from adding extra layers of software, it has it built in.

The best protection against malware is to simply stay current with security updates. If you are then you're protected against all known threats.

As for firewalls, the default configuration is already secure. If you don't install any server software (eg: Apache, Samba) then you shouldn't need to do anything. If you do, there are a few different tools (such as ufw for the command line, and the GUI-based Firestarter) that you can use to control access. These aren't firewalls, they're just tools to configure the built-in firewall system.

thanks for the info :)

---

### Post by billgoldberg on 2008-08-17
I must add that an anti-virus scanner in Ubuntu (linux in general) can be usefull if:

- you have a shared hdd in you pc that you share with a windows partition
- have a fileserver running that get's accessed with windows
- copy lots of files and pass them to windows users (usb, dvd, ...)

Now, I wouldn't install a anti-virus scanner for the last point. A clamav live cd is better for that.

[https://launchpad.net/clamav-livecd](https://launchpad.net/clamav-livecd)

For the first two point it all depends on how much you care about passing on viruses.

Note that linux viruses scanners scan for windows viruses, so if you don't use windows on your pc or have a server that gets accessed from windows, it is completely useless.

---

### Post by cybrsaylr on 2008-08-17
Here's a good read on [Ubuntu 8.04 Security]("http://ubuntutip.googlepages.com/security").

---

