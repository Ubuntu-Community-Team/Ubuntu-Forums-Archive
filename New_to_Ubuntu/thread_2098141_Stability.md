---
title: "Stability?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-25
Is there a way to check that Ubuntu is stable & not breaking up?

Thanks.

---

### Post by snowpine on 2012-12-25
Can you give more details on the problem? Specific error messages, for example?

---

### Post by MishaX2 on 2012-12-25
If you mean for example a stress test you can install stress:
> sudo apt-get install stress

A usage example:
> stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s

You can check in the manual whichever settings you would like to use:
[http://manpages.ubuntu.com/manpages/precise/man1/stress.1.html](http://manpages.ubuntu.com/manpages/precise/man1/stress.1.html)

---

### Post by Kirk Schnable on 2012-12-25
> **Yezinki said:**
> Is there a way to check that Ubuntu is stable & not breaking up?

Thanks.

If you're talking about files, looking for corrupted data, etc, you could run fsck...
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

