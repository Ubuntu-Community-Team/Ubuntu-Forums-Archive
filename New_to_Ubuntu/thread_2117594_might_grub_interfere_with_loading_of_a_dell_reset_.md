---
title: "might grub interfere with loading of a dell reset to factory status utility"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by cutSn8 on 2013-02-18
Hi
Just wondering if grub might interfere with loading of a dell reset to factory status utility?  The utility is supposed to load (after pressing f8) on boot up but isn't at the moment.  I'm not actually wanting to use it right now but just want to confirm it is working ok (I accidentally deleted and then recovered the partition, so its also possible the utility isn't working because the recovery is imperfect).  Thanks

---

### Post by wildmanne39 on 2013-02-18
Hi, no grub does not interfere with the recovery unless you deleted the recovery partition as you stated.

---

### Post by cutSn8 on 2013-02-19
Thanks Wild Man

So is the partition cactus, or to really find out what is going on do I need to remove grub/ubuntu and investigate?

Kind regards

---

### Post by wildmanne39 on 2013-02-19
Hi, no you should not need to remove grub, it is likely that you are just not hitting the key fast or soon enough as the computer boots to make it go into recovery, a lot of computers including mine is very picky about going into recovery or the setup menu.

You can see the recovery partition from windows correct?

Do you also have recovery cd's?

Reboot your computer and as it goes off start tapping the f8 key until it goes into recovery or boots back up.

Also you may need to watch the screen and make sure it is f8 that puts it into recovery mode.

Entering recovery happens before the grub is even loaded so that is not the issue.
Thanks

---

