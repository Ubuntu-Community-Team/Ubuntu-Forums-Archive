---
title: "X programming"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by sal55 on 2013-06-29
I'm a programmer (under Windows), but very new to Linux. I have a low-end flash-based Linux netbook, but can't get it to compile the simplest X-window test program which I found on line.

(My machine, according to on-line reviews, runs Ubuntu, uses a 32-bit ARM processor, and mentions Gnome. However it seems to be impossible to confirm those details via the 'user-friendly' GUI interface it comes with; there are no technical utilities listed, apparently no way that I can see for it to tell me anything about itself at all (just getting access to the file system is a challenge). So I assume it runs 'X', but have no idea if it does, or how to establish that fact.)

It does run Terminal, and I've installed (or it had) gcc, but apparently I need a package called libx11-dev to get started . So I tried this as suggested in a few places online:

sudo apt-get install libx11-dev

but it says: 'E: Couldn't find package libx11-dev'.

Should this have worked? Does such a package exist, and should there be one for ARM, or is it independent of the hardware?

---

### Post by Nr90 on 2013-06-29
for info on your hardware open a terminal and run sudo lshw

Ok I assume you've run sudo apt-get update before trying to install libx11-dev?

You would need a specific package for ARM.
Searching packages.ubuntu.com seems to only return a package for x86 architectures.

If you really need this package I suppose you could consider installing the debian version... But this is probably a bad idea :P

---

### Post by sanderj on 2013-06-29
1) AFAIK programming against X is old skool; something from the 80's. I would advice programming against Qt or some other higher level GUI framework
2) my Raspbian (Debian on ARM on Raspberry Pi) does have  libx11-dev. That does not say anything about Ubuntu on ARM, but maybe it helps.
3) [https://launchpad.net/ubuntu/precise/armel/libx11-dev](https://launchpad.net/ubuntu/precise/armel/libx11-dev) seems to suggest libx11-dev does exist for Ubuntu ARM / armel


pi@raspberrypi ~ $ sudo apt-get install  libx11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpthread-stubs0 libpthread-stubs0-dev libx11-6 libx11-doc libxau-dev libxcb1 libxcb1-dev libxdmcp-dev x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  libxcb-doc
The following NEW packages will be installed:
  libpthread-stubs0 libpthread-stubs0-dev libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev xorg-sgml-doctools xtrans-dev
The following packages will be upgraded:
  libx11-6 libxcb1
2 upgraded, 12 newly installed, 0 to remove and 28 not upgraded.
Need to get 6530 kB of archives.
After this operation, 17.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
pi@raspberrypi ~ $

---

### Post by sal55 on 2013-06-29
> **Nr90 said:**
> for info on your hardware open a terminal and run sudo lshw

Ok I assume you've run sudo apt-get update before trying to install libx11-dev?

You would need a specific package for ARM.
Searching packages.ubuntu.com seems to only return a package for x86 architectures.

If you really need this package I suppose you could consider installing the debian version... But this is probably a bad idea :P

lshw gives me info on cpu and networks. The 'apt-get update' just gives me a screenful of errors.

Yet, the machine does have graphics, and runs Firefox and so on; could these be using a proprietory graphics system? It seems odd; I thought X-windows was fairly standard.

I guess I'll give up that idea on this machine. (I also have a Raspberry Pi that has Debian; it appears to have X, and it uses ARM (slightly different version); I'll try it out on that later, but it's not practical as a development machine.)

---

### Post by sanderj on 2013-06-29
" The 'apt-get update' just gives me a screenful of errors." ... if so, solve that first. You can start by posting the errors here.

Oh, wait: which Ubuntu version are you using? Check with:

```
cat /etc/lsb-release
```

Post the output here. You might be using an Ubuntu version that's not supported anymore. That would explaing the update errors and not able to find the file.

---

### Post by sal55 on 2013-06-29
> **sanderj said:**
> " The 'apt-get update' just gives me a screenful of errors."

It must have been offline. Now it gives me a list of things I don't understand, eg:

"Hit [http://package.ecafe.hercules.com](http://package.ecafe.hercules.com) lucid Release.gpg ...."

Trying the install again, it still can't find the package.

> Oh, wait: which Ubuntu version are you using?

That gives (transcribing the output of cat /etc/lsb-release):

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

So at least I know I'm running Ubuntu! Checking on-line, that's about 3 years old (and 10.04 has an 'end-of-life' of 9-May-2013, whatever that means). My machine was second-hand; I suppose it just has an old version of the OS? I don't fancy upgrading even if it was possible, as the chances are it'll stop working altogether! That 'X' test wasn't that important...

---

### Post by sanderj on 2013-06-29
Ah: Ubuntu 10.04. That's not supported anymore. Therefore you can't update it anymore and you can't find/install any new software anymore.

Out of curiosity: what kind of hardware is it: brand name, product name, ...

---

### Post by Nr90 on 2013-06-29
You won't get any security updates or be able to install software.
Even your compilers will be out of date.
I'd upgrade to 12.04.

---

### Post by sal55 on 2013-06-29
> **sanderj said:**
> Ah: Ubuntu 10.04. That's not supported anymore. Therefore you can't update it anymore and you can't find/install any new software anymore.

Out of curiosity: what kind of hardware is it: brand name, product name, ...

It's one of these: [http://www.linux-netbook.com/hercules-ecaf%C3%A9-ex-hd](http://www.linux-netbook.com/hercules-ecaf%C3%A9-ex-hd) (ecafe ex hd hercules).

It was a cheap refurbished one. (And I wouldn't recommend it because half the things it ought to do don't work, and the rest are too slow. But command-line-based stuff seems OK.)

So I'll have to forget graphics programming for now and update my machine when I advance a bit further.

---

