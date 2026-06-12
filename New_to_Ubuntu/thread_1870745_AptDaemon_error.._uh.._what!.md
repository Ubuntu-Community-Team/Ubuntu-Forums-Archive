---
title: "AptDaemon error.. uh.. what?!"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Lildirt on 2011-10-27
Well, I installed Ubuntu about.. 3 weeks ago, and sometime yesterday it started reporting the error of:
"Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

What does this mean?
What do I have to do to fix it?
I can't seem to install ANYTHING from the Ubuntu Software Center, and this is quite critical to me, due to the fact I need it to keep my Oracle Virtual Machine updated, oh.. and install it in the first place.. :L
I installed the program 'PlayOnLinux' so I could run Steam last night, could that have done it?
I've tried rebooting it too, no luck.

P.S. I'm sorry if this is the wrong place to post.
I'm just really worried here, I don't want to have to re-do all of this.. let alone not be able to install anything!
 :(

---

### Post by decoherence on 2011-10-27
Yes, I would say that PlayOnLinux is probably the culprit. Steam requires Wine and Wine will want the ttf-mscorefonts-installer package the error refers to.

The generic 'cure all' for fixing problems related to the software centre is to open a terminal and run the following

```
sudo apt-get update && sudo apt-get -f install
```

It will ask for your password, then update the package database, then try to fix any broken packages. If you have a really slow internet connection, it might ask for your password again when it tries to fix the packages.

If that doesn't do it for you, please copy the output of the command and post it here. In my experience, there is no such thing as an unrecoverable error as far as package management goes -- it's just a question of what kind of juggling needs to be done to get things untangled.

---

### Post by Lildirt on 2011-10-28
Alright, I've done what you said.
Although, on MANY things I've installed, I keep getting a User Agreement output in terminal.
"Configuring ttf-mscorefonts-installer" is the header of the box.
It has "<OK>", but I can't click it or anything.
What do I do here? :L

Nevermind, 
After 30 mins of playing in Terminal, I figured it out! :P

---

