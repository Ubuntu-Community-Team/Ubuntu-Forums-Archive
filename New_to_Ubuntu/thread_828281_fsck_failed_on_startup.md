---
title: "fsck failed on startup"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-13
i just restarted my computer after using a Fedora 9 LiveCD and fsck was started on my filesystem automatically- the process got to almost 2% when it failed stating there were inconsistencies and i must run fsck manually- what command specifically should i run here?  i tried just running fsck and it prompted me with a message about 'imagic flag set. clear?(y)'

i don't know what this is so i don't want to proceed without knowing the proper process.

any help is greatly appreciated.

thanks.

---

### Post by The Cog on 2008-06-13
Don't know about the flag. I always run a live CD when I get fsck problems and do something like:
**sudo fsck.ext3 /dev/sda2**
which always seem to sort the issue out.

---

### Post by Hospadar on 2008-06-13
I'm not sure exactly what that is, but I know it's a flag in the inode (part of the file system which defines files)  Sounds like this flag got set for something it shouldn't have.  [This]("http://www.linuxquestions.org/questions/mandriva-30/ext3-integrity-issues-180304/") post claims it's a minor issue, and while they arn't very descriptive about what is actually going on, it sounds like the guy was able to fix his problem.

---

### Post by Matt26 on 2008-06-16
thanks, i used the live cd and used fsck from there and i just followed the prompts as they came up (there were SO many of them so it took awhile) but it worked, and my system is up and running again.

---

