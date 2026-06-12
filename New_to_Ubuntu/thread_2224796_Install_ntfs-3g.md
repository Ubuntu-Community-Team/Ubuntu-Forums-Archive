---
title: "Install ntfs-3g"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by ak47jx on 2014-05-18
so I'm trying to install this: [http://www.tuxera.com/community/ntfs-3g-download/](http://www.tuxera.com/community/ntfs-3g-download/)

I'm following and typing what it says in the installation but doesn't work can someone help me please

---

### Post by The Cog on 2014-05-18
Is there any reason you dont want to use the version in the repositories? Unless you have a reason to do otherwise, the easiest install would be to simply run these two commands:
```
sudo apt-get update
sudo apt-get install ntfs3g
But I would have thought it is
``` installed by default anyway.

---

### Post by ak47jx on 2014-05-18
i get the follow when i write sudo apt-get install ntfs3g 
reading packages lists... done
Building dependency tree
Reading state information.. done
E: Unable to locate package ntfs3g

I'm running xubuntu

---

### Post by coffeecat on 2014-05-18
The package is ntfs-3g, not ntfs3g. But why are you trying to install it? As The Cog said, it is installed by default.

---

### Post by ak47jx on 2014-05-18
is it default installed on xubuntu 12.04????

---

### Post by coffeecat on 2014-05-18
I'd be very surprised if it isn't. To be sure it is installed in your system, run this terminal command and post the output:

```
dpkg --get-selections | grep ntfs
```

---

### Post by ak47jx on 2014-05-18
[COLOR=#ff0000][/COLOR]this is what i get[COLOR=#ff0000]
ntfs[/COLOR]-3g[COLOR=#ff0000][/COLOR]            install
[FONT=courier new][/FONT]

---

### Post by The Cog on 2014-05-18
> The package is ntfs-3g, not ntfs3g. 
Aaargh! Silly mistake. Sorry.

> this is what i get
ntfs-3g install
Sorry, I don't understand what you mean by that. Can you explain?

---

### Post by Elfy on 2014-05-18
> **The Cog said:**
> ...
Sorry, I don't understand what you mean by that. Can you explain?

It's installed already - no need to install it anymore.

Changing thread title.

---

### Post by ak47jx on 2014-05-18
when i type this in the terminal:
dpkg --get-selections | grep ntfs

i get this *ntfs-3g       install*

---

### Post by coffeecat on 2014-05-18
@ak47jx, you didn't explain why you thought you needed to install ntfs-3g. As Elfy said, it's already installed. Is there a problem that you need help with?

---

### Post by ak47jx on 2014-05-18
i have one more problem
I made 2 partitions on a usb and installed xubuntu on the first partition(fat32)
so then i boot from usb and I'm using xubuntu live i install true crypt and make a container on my second partition once thats all complete when i try to mount my volume on true crypt i get the following:

mount: you must specify the filesystem type


then after reading a bit someone said they resolved the issue by installing ntfs-3g 
btw the second partitions format is ntfs

sorry if I'm not explaining it clearly

---

### Post by Elfy on 2014-05-18
Given you've started another thread with the same post as #12 here and the ntfs-3g is dealt with I'll close this and mark it solved.

---

### Post by coffeecat on 2014-05-18
That's clear enough. A comment and then a suggestion.

The person who solved their problem by installing ntfs-3g must have uninstalled it beforehand, whether intentionally or unintentionally, so wherever you read that, it doesn't help you.

I don't have any experience with true crypt and it's better if you get advice from someone who does. It would be better if you start a fresh thread. Give it a meaningful title with truecrypt in the title in order to attract those who can best help you. Give as much relevant information as you can - at least everything you have included in your latest post.

Good luck.

**EDIT**: Posted a few moments after Elfy posted. I see the OP has started a new thread then.

---

