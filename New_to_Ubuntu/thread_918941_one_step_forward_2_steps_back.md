---
title: "one step forward 2 steps back"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by wayco1 on 2008-09-13
Why is it SOO difficult to watch original movies? (copies work fine)..
Why is it SOO difficult to copy movies with ubuntu?
Just try to download FREE nero and see what happens,,19.99 for a year!!
Try and download CODEX to watch movies ,, no luck
Shrink,decripter,fabdvd,nero,,,I can't get any on ubuntu !!!
This switch to ubuntu was nice,,cool and I thought would be a step forward, but if I can't do what I like to do, I probably will return to XP..
Any thoughts or comments?

---

### Post by SunnyRabbiera on 2008-09-13
Huh?
Can you give us more details on your issue?
We cant help unless you give us info.

---

### Post by Ub1476 on 2008-09-13
To install "normal" plugins and codecs, install the package "ubuntu-restricted-extras" from terminal or add/remove or Synaptic.

To watch DVDs some hacking is required..


Write the following codes in the terminal:

```
 sudo apt-get install libdvdread3
 sudo /usr/share/doc/libdvdread3/install-css.sh
```

You can now watch DVDs :)

See [here]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs") on how to ripp (copy?) DVDs.

---

### Post by mikewhatever on 2008-09-13
Perhaps it is SOO difficult because, for no apparent reason, you are stuck with nero.

---

### Post by Tatty on 2008-09-13
Well your first problem is you are thinking in terms of windows software, have a look through the repos to see what linux software exists.  VLC is a highly recommended media player which has many codecs built in.

In short, Ubuntu does not ship with support for many multimedia technologies out of the box because there is often a legal grey area over these things.

However, there are many ways of enabling this support easily via the community.  Have a read through this page and follow the links and it should get you set up with almost anything you want

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

---

### Post by wayco1 on 2008-09-14
To Sunny Rabbiera,,Tatty,,and especially UB1476 I am now watching movies. thanks to all 3 of you.

---

