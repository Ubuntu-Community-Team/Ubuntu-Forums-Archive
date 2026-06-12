---
title: "How do you sync ubuntu laptop with ubuntu desktop?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by uglowp on 2008-05-02
One of the opportunities for the linux community is to post more information on connecting and sync'ing with linux machines.  There seems to be a lot of information about how to sync and mount shared windows directories on ubuntu, and nothing on ubuntu to ubuntu.

Hence my issue,

I have an ubuntu 7.10 laptop that I want to sync with my ubuntu 7.10 desktop.

What is the best way to do that?

rsync seems to be the way to go, however I can't figure out the command to access my laptop (192.168.0.6).

Or Grsync? (Can't figure out how to connect the laptop over the lan)

Or should I mount my laptop drive on the desktop?  If so how do you do that? (Same connection issue over the lan)

Any help is greatly appreciated.

Thank you!

Phil

---

### Post by bjm1904 on 2008-05-02
The syntax is:

rsync /source /destination

There are plenty of other options you can add, but they only apply if you're doing a remote backup or updating a webserver and want to avoid snoopers - syncing between devices should only need a command as simple as that. You can also save this in a .sh file and call it from the commandline via ./file.sh

---

### Post by bjm1904 on 2008-05-02
A little addition - you can add IP Addresses into the address path (just to clarify) - just make sure they're hooked up!

(I suggest you go with the post below, as it's more reliable over a network - I know that my suggestion tends to work locally)

---

### Post by Monicker on 2008-05-02
Are you talking about just syncing a set of files from one machine to the other?  You can do that using rsync over ssh.  The destination machine will need to have the openssh-server package installed and running.

```
rsync -ave ssh /local/dir/ username@192.168.0.6:/remote/dir
```

You can use -avze to compress the transfer, this may speed up the transfer quite a bit.

---

