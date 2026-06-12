---
title: "unable to update"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by duruttye on 2008-04-30
Hello
Just reverted back to 7.10, so it is a fresh install.

I am unable to update, it seems that the internet connection is not working, although it is, 'cause I'm writing this as well...

Is there something wrong with the servers? I tried a few servers and they are all the same...

Here is an example:

[HTML]W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_amd64.deb
  


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb[/HTML]

This is for the restricted driver, but any install does the same, too.
Anybody else is having the same problem?

Another example:
[HTML]WARNING: The following packages cannot be authenticated!
  traceroute
Install these packages without verification [y/N]? Y
0% [Connecting to archive.ubuntu.com (91.189.88.31)]
[/HTML]
and it stays like that forever...
Any ideas??

---

### Post by AndThenWhat on 2008-04-30
Does your update manager work? If so you should make sure you are fully up-to-date because an update could possibly fix your problem.  If that does not work you could try a full restart which sometimes fixes weird problems in Ubuntu :confused:

---

### Post by duruttye on 2008-04-30
The update manager works all right, it just doesn't download anything at all, although it says that there are 220 updates...

It does download something, but the speed is like 300 B/sec, so it will time out after a while.

---

### Post by vishzilla on 2008-04-30
Try re-installing the update manager from Synaptic and check it again

---

### Post by vishzilla on 2008-04-30
I tried it myself and I get the same result as your 2nd example. Maybe the server is busy right now
```
Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
```

---

### Post by AndThenWhat on 2008-04-30
Is your internet running at a reasonable speed? If it is, you could just run a wget on those file addresses and install their .deb manually.  (I know the sites are up, because when I did a wget on the addresses they worked)

---

### Post by duruttye on 2008-04-30
Oh, that's great!

I mean I know now that the problem is not with my Ubuntu.
I installed for the third time because of this, I thought that something was very wrong...

Thanx anyway for your help :)

---

### Post by SunnyRabbiera on 2008-04-30
there is also the server overolad too to consider, it will be there for some time now.

---

### Post by duruttye on 2008-04-30
for AndThenWhat

I downloaded the cd in 20 minutes, so it's working good.

Never mind, I will just try it later.

---

### Post by duruttye on 2008-04-30
Hey, how can I mark the thread as solved???

---

### Post by vishzilla on 2008-04-30
That feature isn't updated to the new version of vbulletin. Probably ask the mod to mark it as solved!!!

---

