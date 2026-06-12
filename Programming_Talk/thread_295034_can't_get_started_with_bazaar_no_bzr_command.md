---
title: "can't get started with bazaar: no bzr command"
date: 2006-11-07
forum: Programming Talk
---

### Post by jnoreiko on 2006-11-07
I've just used Synaptic to install bazaar.
I'm now looking at the documentation: [http://bazaar-vcs.org/QuickHackingWithBzr](http://bazaar-vcs.org/QuickHackingWithBzr)

The first and pretty major problem is that there's no 'bzr' command on my system:

```
joachim@ubuntu:~$ bzr
bash: bzr: command not found

```

A check in Synaptic's list of installed files shows a 'baz'. On a long shot, I've tried this...

```
joachim@ubuntu:~$ baz whoami
baz: unrecognized command (whoami)
  (try ' baz help')

``` 

Have I installed the wrong package?

---

### Post by marianom on 2006-11-07
Hi there. I'm planning to start using bazaar today so I'm kinda with the same doubts as you.
For starters, I'm checking [http://bazaar-vcs.org/releases/debs/](http://bazaar-vcs.org/releases/debs/) to find the .deb since that's what [http://bazaar-vcs.org/DistroDownloads](http://bazaar-vcs.org/DistroDownloads) suggests (I'm in Dapper).

Anyway, there's lot of packages so I'm in doubt, deciding what's next. In the meantime: I don't see a "baz" package in Synaptic, I see a "bzr", if you ask me that's the one you should install.

Let me know how it's going, maybe we can work this out together.

---

### Post by marianom on 2006-11-07
Yeap, confirmed. I have it running. 
You need to download bzr (I still don't know what the other package "bazaar" does but checking the .debs in the url I posted before, it's a long time since somebody did something with it).

---

### Post by jnoreiko on 2006-11-09
Aha! Now I've got it installed, thanks.

What sort of work are going hoping to do with bazaar?
I've come to it because I want to do some work on the xchat-gnome manual, and there's a bazaar branch for it on launchpad:
[http://bazaar.launchpad.net/~vcs-imports/xchat-gnome/trunk](http://bazaar.launchpad.net/~vcs-imports/xchat-gnome/trunk)

I'm now scratching my head trying to figure out what to do next.

Any idea how to get just part of the tree checked out? Working on docs, I only want the help/ folder out of the trunk, not all of the source.

---

### Post by marianom on 2006-11-09
Am I wrong or you finally did it? Cause I was searching the launchpad to see what I can suggest and I saw
[https://launchpad.net/people/jnoreiko/+branch/xchat-gnome/docs](https://launchpad.net/people/jnoreiko/+branch/xchat-gnome/docs)

I assume you are Joachim.

With a coworker of mine we are practising in our server with bazaar (you know: testing branches, messing files, merging, etc, etc) to see if we like it and we can use on our daily work. Basically, learning.

---

### Post by jnoreiko on 2006-11-09
Yup, I've done it!

Took a very long time, both to check out and to push the branch.
Turns out there's no way currently to checkout only part of a hierachy. :(

I've just made a commit to my branch, next step is figuring out how to make that appear on Launchpad!

---

