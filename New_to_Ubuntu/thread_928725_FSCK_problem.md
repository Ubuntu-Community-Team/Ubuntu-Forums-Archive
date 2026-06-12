---
title: "FSCK problem"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by kj4860 on 2008-09-24
I have a bit of a problem:

When i booted for the 20th time, FSCK kicked on. It got up to 61% then went into terminal mode with a ton of errors and asking if i wanted to fix/change them by pressing Y(Yes). I sat there for about an hour holding down Y until i gave up and restarted to see if anything changed. 

On restart, it stopped again at 61%. I rebooted and manually ran FCSK...no good. I booted into the install disc and ran it manually, no good. I finally ran the Partition Manager in check/repair mode on it(went on for 9 hours)...no good. 

I can get past FSCK by pressing escape at boot but i REALLY would rather not have this issue and have it boot normally. Can anyone be of some assistance please? :confused:

---

### Post by Orange_and_Green on 2008-09-24
Hello kj ;)

If I were you, before trying anything else I would make a full backup of all your data ASAP as it seems to me your hard drive is about to meet its maker...

(if it's still on warranty, that is ;))

---

### Post by jrothwell97 on 2008-09-24
Short answer: use Partition Manager to convert it into an ext3 partition. That *may* work if you're using a spinning hard disk as opposed to a solid-state disk.

---

### Post by kj4860 on 2008-09-24
ugh...seriously?

It runs any other OS fine with no apparent HDD errors on check.

This exact same problem happened about a year ago with Gutsy. That was the sole reason i left Ubuntu originally.:(

---

### Post by kj4860 on 2008-09-24
> **jrothwell97 said:**
> Short answer: use Partition Manager to convert it into an ext3 partition. That *may* work if you're using a spinning hard disk as opposed to a solid-state disk.

could i convert it w/o losing data?

I will still backup my apps + such but just wondering.

---

### Post by Orange_and_Green on 2008-09-24
Well, obviously I can't tell you for sure...
But better safe than sorry don't you think?

In my experience, hard disks failing checks have seldom lasted long...

---

### Post by kj4860 on 2008-09-24
> **Orange_and_Green said:**
> Well, obviously I can't tell you for sure...
But better safe than sorry don't you think?


Ofcourse!

I most definatly will backup all my stuff as of recently. I already have the apps backed up on disc. Now i will move my personal stuff over just incase as well.

All of this done regardless of the possible outcome. 

Before i attempt converting the partition, any other plausible ideas/solutions?

---

