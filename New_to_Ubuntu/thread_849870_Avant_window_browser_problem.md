---
title: "Avant window browser problem"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-07-04
I use avant and it had an update yesterday and after the update when i launch it it freezes. I need help please.

---

### Post by ChameleonDave on 2008-07-04
> **DarkSaga70 said:**
> I use avant and it had an update yesterday and after the update when i launch it it freezes. I need help please.

It's not a browser.  It's called "Avant Window Navigator".  Incorrect titles make it harder for people to find information on the forums.

If the current version of this experimental software fails, then go back to the version that worked.

You probably have archives of the old installers.  Enter this at the command line:

```

cd /var/cache/apt/archives
ls avant*  awn*

```

---

### Post by DarkSaga70 on 2008-07-04
> **ChameleonDave said:**
> It's not a browser.  It's called "Avant Window Navigator".  Incorrect titles make it harder for people to find information on the forums.

If the current version of this experimental software fails, then go back to the version that worked.

You probably have archives of the old installers.  Enter this at the command line:

```

cd /var/cache/apt/archives
ls avant*  awn*

```


ok after i enter those  i get this msg "
avant-window-navigator_0.2.1-0ubuntu2.1_i386.deb
awn-manager_0.2.1-0ubuntu2.1_all.deb"

now what do I do?

---

### Post by ChameleonDave on 2008-07-04
> **DarkSaga70 said:**
> ok after i enter those  i get this msg "
avant-window-navigator_0.2.1-0ubuntu2.1_i386.deb
awn-manager_0.2.1-0ubuntu2.1_all.deb"

now what do I do?

Hmm.  That's probably just the version you currently have.

It looks like Synaptic is not keeping archives for you.  If you go into the Preferences in Synaptic, you can choose to keep the packages you download.  That makes it easier to go back to previous versions.

I'm not quite sure where you can get hold of an older copy.  Perhaps you could Google for one.

Otherwise, you could try just completely removing the program and reinstalling it.

---

### Post by DarkSaga70 on 2008-07-05
I dunno what i did but i un installed it and turned off the xperimental crap and now i have it working again thanks a bunch. :guitar:

---

### Post by webabun on 2008-07-05
> **DarkSaga70 said:**
> I dunno what i did but i un installed it and turned off the xperimental crap and now i have it working again thanks a bunch. :guitar:

I do have same problem, pls tell me what "xperimental crap" is so I can switch it off as well.
Removing avant + avn-manager using synaptic didn't work for me AND no older version are kept on system.(which is strange as it's my default option for synaptic).

---

### Post by moonbeam on 2008-07-05
Please see:

[http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=849005&highlight=avant+window+navigator)

and

[https://bugs.launchpad.net/awn/+bug/245448](https://bugs.launchpad.net/awn/+bug/245448)

The awn package in -proposed is broken.

---

