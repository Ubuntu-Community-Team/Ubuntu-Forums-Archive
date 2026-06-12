---
title: "Hardy Low Sound Quality"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by RequinB4 on 2008-06-07
Was very pleased when sound worked in hardy on my Toshiba p105, but the sound quality is so low the audio is almost unrecognizable.  (Incidentally, was also very happily suprised that the potential sound volume has almost doubled (A problem I thought was due to hardware)

Sound works after a kernel patch in gutsy/feisty (note [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469))

lspci | grep Audio
```
 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
```

Hopefully, this isn't a new bug.  I doubt it is, considering many have this laptop and its been a while since hardy release.  Any help would be much appreciated.

SOLVED - for googling reference - you need to turn PCM down to a comfertable level in alsamixer.  Don't I feel smart.

---

### Post by RequinB4 on 2008-06-07
Bump - This is probably better suited for the sound sub-forum because its more technical - Can a moderator please move this there?  Thanks much.

---

