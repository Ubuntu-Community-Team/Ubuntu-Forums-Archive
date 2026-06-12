---
title: "[SOLVED] samba package version differences"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by W4JKA on 2008-08-24
I've been playing with Wubi HH 8.04 about a month and have a problem I can now describe well enough to ask for help - 

I have used both the Symantic Package Manager and command line method in an attempt to install samba server package.

It seems that the issue is with the samba-common (3.0.28a-1ubuntu4.5) program. All the other samba progs except samba-common are 3.0.28a-1ubuntu4.4.

Error Message:
===========================
root@owner-laptop:/home/owner# apt-get install samba
Reading package lists...Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.

The following information may help to resolve the situation:
The following packages have unmet dependencies:
samba: Depends: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.5 is to be installed
E: Broken packages root@owner-laptop:/home/owner# 
============================

So, how can I get resolve this?
----------
Tkx, John

[http://xkcd.com/456/](http://xkcd.com/456/)

---

### Post by Partyboi2 on 2008-08-24
Have you tried to use the older version of that package if it is available? You can do this by opening up synaptic package manager and doing a search for samba-common then highlight it and select "package" then "force version" and select the 3.0.28a-1ubuntu4.4 version.

---

### Post by W4JKA on 2008-08-24
> **Partyboi2 said:**
> Have you tried to use the older version of that package if it is available? You can do this by opening up synaptic package manager and doing a search for samba-common then highlight it and select "package" then "force version" and select the 3.0.28a-1ubuntu4.4 version.

Thanks for the push.... What I ended up doing was removing samba-common 4.5, (which was installed by default from the wubi site), then reinstalling it through the package manger (all ver 4.4).  One issue is that removing samba-common also removed ubuntu-desktop.

I blithely removed ubuntu-desktop, then reinstalled it.  Next I installed the complete samba package with no apparent problem.  Since my windows network name is not the default WORKGROUP, I changed the workgroup name line in samba.conf.

Now my network shows the ubuntu machine, as well as the windows machines

Many thanks.

John

---

### Post by IntuitiveNipple on 2008-08-28
I just experienced the same issue with Hardy i386 8.04.1, on a system that is almost untouched in terms of additional package installs.

I fixed it by forcibly removing smbclient and samba-common and then forcibly installing samba, samba-common, and smbclient. This avoids removing the ubuntu-desktop virtual package:
```

sudo dpkg --force-all -r smbclient samba-common

sudo apt-get -f install samba samba-common smbclient

```

It is strange that [launchpad lists 3.0.28a-1ubuntu4.5](https://launchpad.net/ubuntu/hardy/i386/samba) as the current release but [packages.ubuntu.com lists (3.0.28a-1ubuntu4.4) [security]](http://packages.ubuntu.com/hardy/samba-common)

---

### Post by zivley on 2008-09-01
> **IntuitiveNipple said:**
> I just experienced the same issue with Hardy i386 8.04.1, on a system that is almost untouched in terms of additional package installs.

I fixed it by forcibly removing smbclient and samba-common and then forcibly installing samba, samba-common, and smbclient. This avoids removing the ubuntu-desktop virtual package:
```

sudo dpkg --force-all -r smbclient samba-common

sudo apt-get -f install samba samba-common smbclient

```

It is strange that [launchpad lists 3.0.28a-1ubuntu4.5](https://launchpad.net/ubuntu/hardy/i386/samba) as the current release but [packages.ubuntu.com lists (3.0.28a-1ubuntu4.4) [security]](http://packages.ubuntu.com/hardy/samba-common)

Thanks to nipple for his intuition! 
Your suggestion did the trick for me!

---

