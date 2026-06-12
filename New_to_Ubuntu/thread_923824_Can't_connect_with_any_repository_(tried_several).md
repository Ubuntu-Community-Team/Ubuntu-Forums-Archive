---
title: "Can't connect with any repository (tried several)"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by gasull on 2008-09-18
Hi.

I cannot connect with any repository.  I've tried changing the repository using the "Select Best Server" button.  I always get the same problem when updating the software sources:

```
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://ppa.launchpad.net/rockwalrus/ubuntu/dists/hardy/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://ppa.launchpad.net/rockwalrus/ubuntu/dists/hardy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Could anybody tell me where the problem might be?

TIA.

EDIT:

[LIST]
[*]Yes, I get Internet connection, and I can access the repositories with Firefox.
[*]I'm not using a proxy.
[*]This problem happens with my laptop wherever I am: from home, from a cafe with wifi, etc.
[*]I've been using Linux for years.  I might be missing something obvious, but I think it can be some of the software I have installed: moblock, dnsmasq, etc.
[/LIST]

---

### Post by Sef on 2008-09-19
moved to absolute beginners.

---

### Post by Paqman on 2008-09-19
Have you got a working internet connection?

---

### Post by Gone fishing on 2008-09-19
Do you connect through a proxy? 

If so you need need to add the proxy settings in Synaptic
Synaptic > settings > Preferences > Network

---

### Post by gasull on 2008-09-19
I should had said this from the beginning:

[LIST]
[*]Yes, I get Internet connection, and I can access the repositories with Firefox.
[*]I'm not using a proxy.
[*]This problem happens with my laptop whenever I am: from home, from a cafe with wifi, etc.
[*]I've been using Linux for years.  I might be missing something obvious, but I think it can be some of the software I have installed: moblock, dnsmasq, etc.
[/LIST]

---

### Post by jre on 2008-09-19
Because of this message "502 Disconnected operation" I doubt that it is MoBlock.

But to verify this, in case Moblock is blocking it for ftp (although you can access it with firefox), do a "tail -f /var/log/moblock.log" in the console. Then you can see live any blocks by Moblock.

---

### Post by gasull on 2008-09-19
> **jre said:**
> Because of this message "502 Disconnected operation" I doubt that it is MoBlock.

But to verify this, in case Moblock is blocking it for ftp (although you can access it with firefox), do a "tail -f /var/log/moblock.log" in the console.

You are right.  It isn't Moblock.

What else can it be?  How can I debug the problem?

---

### Post by philinux on 2008-09-19
[http://www.checkupdown.com/status/E502.html](http://www.checkupdown.com/status/E502.html)

[http://pcsupport.about.com/od/findbyerrormessage/a/502error.htm](http://pcsupport.about.com/od/findbyerrormessage/a/502error.htm)

---

### Post by gasull on 2008-09-20
I'm trying to narrow the problem.

I went to System -> Administration -> Software sources -> Ubuntu Software -> Download from -> Main server

Then I got these errors:

```

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://ppa.launchpad.net/rockwalrus/ubuntu/dists/hardy/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://ppa.launchpad.net/rockwalrus/ubuntu/dists/hardy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  502 Disconnected operation and object not in cache
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  502 Disconnected operation and object not in cache
Some index files failed to download, they have been ignored, or old ones used instead.

```

But if I try once of the URLs with several methods it works:

1) Firefox (no proxy) to [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binaroy-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binaroy-i386/Packages.gz) -> It works
2) wget [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz) -> It works.
3) Galeon with no proxy -> It works.
4) wget [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz) -> It works.

So the problem is exclusively with aptitude, apt-get, Synaptic, etc.  Synaptic is configured with direct access to the Internet, so it is the system proxy in System -> Preferences -> Network Proxy

What can it be?  Maybe a variable in my bashrc or in some file in /etc/?

TIA.

---

### Post by gasull on 2008-09-21
Solved.

It had Polipo proxy installed, although I thought no app was using it because http_proxy and HTTP_PROXY are not set.

Restarted Polipo and it works now.

---

