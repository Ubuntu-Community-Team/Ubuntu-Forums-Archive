---
title: "Eclipse Error when compiling Java programs"
date: 2007-03-29
forum: Programming Talk
---

### Post by harmonizedchaos on 2007-03-29
what does this mean and what do I do to fix it? Any and all ideas are much appreciated!

"ERROR: JDWP Unable to get JNI 1.2 environment, jvm->GetEnv() return code = -2
JDWP exit error AGENT_ERROR_NO_JNI_ENV(183): [../../../src/share/back/util.c:820]"

Thanks in advance!

---

### Post by smokey edgy on 2007-03-29
Are you using Sun's JDK or the stock GNU Java compiler (gcj) that comes with Ubuntu? If you have the GNU Java compiler, I would suggest using Sun's JDK. Personally, I've never had much luck with GCJ; then again I haven't spent much trying to get it going. :)

---

### Post by smokey edgy on 2007-03-29
bah, sorry. Sent the message twice.

---

### Post by harmonizedchaos on 2007-03-29
nope, am using Sun's JDK. Although if I just ignore the error, it seems like the program will run fine..the error doesn't really affect it I guess. :)

---

### Post by smokey edgy on 2007-03-29
Oh so the error shows up in the terminal window while your working in the IDE?

---

### Post by Nebulus on 2007-04-12
> **harmonizedchaos said:**
> what does this mean and what do I do to fix it? Any and all ideas are much appreciated!

"ERROR: JDWP Unable to get JNI 1.2 environment, jvm->GetEnv() return code = -2
JDWP exit error AGENT_ERROR_NO_JNI_ENV(183): [../../../src/share/back/util.c:820]"

Thanks in advance!

This is known bug in Java 1.6 and it only appears when debugging.

More info on Suns site:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6476706]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6476706")

---

