---
title: "Flash for Ubuntu 11.04 installation probs?"
date: 2011-10-11
forum: North Carolina Team - US
---

### Post by naragam on 2011-10-11
Hi,

I am a new user of Ubuntu desktop and am trying to install a new flash player for my Firefox 7.0.1. It looks like nothing happens or the antivirus s/w may be preventing the download and/or installs. How do I disable any antivirus running on this version 11.04 of Ubuntu? Any help?

TiA, Nash

---

### Post by ubudog on 2011-10-11
Hey there!  

First off, there is no antivirus that comes with Ubuntu (it's just not needed).  Everything however, is locked down and secure by default.  This won't interfere with downloads though.

So, what I would do to install flash:
1. Close all open instances of Firefox
2. Open a terminal
3. Type this:
```
sudo apt-get -y install ubuntu-restricted-extras
```
4. Wait for it to download (you might have to type your password)
5. Type exit
6. Start Firefox, enjoy flash!

---

### Post by naragam on 2011-10-11
Thanks for you help, but something is frozen right now....I am not getting out of some MS font loading or install....it's hung perhaps waiting for me to accept some legal junk....I lost my input cursor on the terminal and I have no idea where this has hung....it did seem to indicate that it was going to install a bunch of new app pkgs. Is there anyway I can check the status?

I am under sudo...so I am not sure what to look for in my process table??

Any further help?

Thanks much,

Nash

---

### Post by ubudog on 2011-10-11
Just close the terminal.  Something better for your situation would be:
```
sudo apt-get -y install flashplugin-installer
```

That'll install an installer for the Flash plugin.  It should guide you through everything.

(press tab to select 'Yes' or 'No' on the legal agreements, space to apply)

---

### Post by naragam on 2011-10-13
Well, there are a lot of unknowns with this 11.04 version I have...

Your last suggestion create bizarre 'lock' errors...

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I can't see anybody else using it...soooo....now what?

Nash

---

### Post by naragam on 2011-10-13
Okay...I got it installed....I guess I need to get familiar with some of these new features working as root in Ubuntu....Thanks much for the help.

Nash

---

### Post by ubudog on 2011-10-13
> **naragam said:**
> Okay...I got it installed....I guess I need to get familiar with some of these new features working as root in Ubuntu....Thanks much for the help.

Nash

Great!

The lock error was probably because you still had apt running - either the Software Center was running, Synaptic, or another terminal window with apt.

Glad you got it working!

---

