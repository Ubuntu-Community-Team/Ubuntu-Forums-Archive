---
title: "[SOLVED] Have I been hijacked?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by nkri on 2008-10-02
Ok, so I run chkrootkit and rkhunter every week or so, and when I ran rkhunter today, two warnings came up that I've never seen before.  I'm pretty spooked that it could be a rootkit, but am not sure.

Everything turned out OK except for these:
```
[18:06:20] /usr/bin/ldd                                      [ Warning ]
[18:06:20] Warning: The file properties have changed:
[18:06:20]          File: /usr/bin/ldd
[18:06:20]          Current inode: 1459333    Stored inode: 1459084
[18:06:20]          Current file modification time: 1221229932
[18:06:20]          Stored file modification time : 1207352282
[18:06:20] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

[18:06:22] /usr/bin/sudo                                     [ Warning ]
[18:06:22] Warning: The file properties have changed:
[18:06:22]          File: /usr/bin/sudo
[18:06:22]          Current hash: a8b8876a79185207726c1de99eefbc144516c18c
[18:06:22]          Stored hash : 0ed9a0d689ad891475eb13d02be7e34b4c104f6c
[18:06:22]          Current inode: 3768331    Stored inode: 1458214
[18:06:22]          Current file modification time: 1221069938
[18:06:22]          Stored file modification time : 1210812110
```

Should I not be using the sudo command?  Is there a way to replace these commands with the ones installed by default?  Should I even be worried?

Thanks!
-nkri

---

### Post by Madman6510 on 2008-10-02
You shouldn't be concerned about having a rootkit, as far as we know there are none in existance.

As long as it isn't causing problems, I wouldn't worry about it.

---

### Post by nkri on 2008-10-02
> **Madman6510 said:**
> You shouldn't be concerned about having a rootkit, as far as we know there are none in existance.

I don't think this is true.  Why do you think chkrootkit and rkhunter scan for *known* and unknown rootkits?

---

### Post by Orange_and_Green on 2008-10-02
A similar problem has been reported on launchpad...

[https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/271301](https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/271301)

Recently there has been an update for sudo, so I think that the update is much more likely to have caused rkhunter's warning, rather than a rootkit...

---

### Post by ayenack on 2008-10-02
sudo was updated recently so that could be the reason for the sudo. Have a look at this post.

[http://ubuntuforums.org/showthread.php?t=920962&highlight=ayenack](http://ubuntuforums.org/showthread.php?t=920962&highlight=ayenack)

If you feel the need do an md5sum and post it here.

In terminal:-

[B]md5sum /usr/bin/sudo (For sudo)
md5sum /usr/bin/ldd (For ldd)[/B]

These are the results I got an Ubuntu 8.04.1 32Bit.

$ md5sum /usr/bin/sudo
d7df1b53d2f1eeb86cc51bf5c29ec944 /usr/bin/sudo

md5sum /usr/bin/ldd
286f01dca16e31a03f12d24ef3755a30 /usr/bin/ldd

They should match.

---

### Post by nkri on 2008-10-02
> **ayenack said:**
> sudo was updated recently so that could be the reason for the sudo. Have a look at this post.

[http://ubuntuforums.org/showthread.php?t=920962&highlight=ayenack](http://ubuntuforums.org/showthread.php?t=920962&highlight=ayenack)

If you feel the need do an md5sum and post it here.

In terminal:-

[B]md5sum /usr/bin/sudo (For sudo)
md5sum /usr/bin/ldd[/B] (For ldd)

These are the results I got an Ubuntu 8.04.1 32Bit.

$ md5sum /usr/bin/sudo
d7df1b53d2f1eeb86cc51bf5c29ec944  /usr/bin/sudo

 md5sum /usr/bin/ldd
286f01dca16e31a03f12d24ef3755a30  /usr/bin/ldd

They should match.

Excellent, exactly what I needed.  The checksums matched fine so I'm not worried anymore:D

Thanks!
-nkri

---

### Post by ayenack on 2008-10-02
> **nkri said:**
> Excellent, exactly what I needed.  The checksums matched fine so I'm not worried anymore:D

Thanks!
-nkri

Cool I'll put the sudo back in my original post.

BTW If you run.

**sudo rkhunter --propupdate**

It'll stop the warning showing up every time you run rkhunter.

---

