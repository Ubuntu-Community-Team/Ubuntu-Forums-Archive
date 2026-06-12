---
title: "Trouble with Wine installation enabling i386 arch"
date: 2021-01-15
forum: New to Ubuntu
---

### Post by andrewmarcapple on 2021-01-15
*I am having an issue with this as well.  I am entering:*

**sudo dpkg --add-architecture i386 **

*But I am getting this error:*

**pkg-config-dpkghook: warning: Architecture 1386 not defined in architecture tables, ignored**
[I]
You'll notice, I'm typing "i386," but the error says "1386."[/I]

---

### Post by Dennis N on 2021-01-15
> **andrewmarcapple said:**
> *I am having an issue with this as well.  I am entering:*

**sudo dpkg --add-architecture i386 **

*But I am getting this error:*

**pkg-config-dpkghook: warning: Architecture 1386 not defined in architecture tables, ignored**
[I]
You'll notice, I'm typing "i386," but the error says "1386."[/I]

You don't need to do this any longer. 32-bit support is already enabled. You can verify supported architectures with these commands:
Check the native architecture:
```
dmn@Sydney:~$ dpkg --print-architecture
amd64
```
Check for other architectures:
```
dmn@Sydney:~$ dpkg --print-foreign-architectures 
i386
```
These were run on Ubuntu 18.04 system

---

### Post by QIII on 2021-01-15
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2444661").

Please don't hijack the threads of others.  Your issue, while similar in symptoms, may not stem from the same root cause.  Hijacking threads quickly causes things to become confusing for those seeking help and those willing to offer.

If you find a thread with a problem similar to yours, please start your own thread rather than horning in.  You may refer to the other thread as I have done above.  This will ensure that the OP of the first thread and you get the individual support you need.

---

