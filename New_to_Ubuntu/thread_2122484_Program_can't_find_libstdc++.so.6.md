---
title: "Program can't find libstdc++.so.6"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2013-03-05
I'm running a fresh install of Precise on a 64 bit HP G62 laptop. I'm trying to run a program called ChatScript ([http://sourceforge.net/projects/chatscript/](http://sourceforge.net/projects/chatscript/)) which ran fine on this machine on Precise before I wiped everything and did the fresh install. Now I'm getting:

```
./LinuxChatScript32 local./LinuxChatScript32: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

```

but the file is there:
```
locate libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16

```

Is this a path issue? I've run into those before, but never with this file. Not quite sure how to proceed and could use some guidance.

regards, Richard

---

### Post by steeldriver on 2013-03-05
The name LinuxChatScript**32** would suggest it's a 32-bit binary - so it won't work with your 64-bit /usr/lib/**x86_64**-linux-gnu/libstdc++.so.6 shared lib

If that's the case, you *may* be able to get it to work with ia32-libs if you can't find a 64-bit native version of the program

---

### Post by Robing Goodfellow on 2013-03-05
Damn! I knew I was forgetting something obvious. Thanks Steeldriver, that did the trick.

regards, Richard

---

### Post by Robing Goodfellow on 2013-03-05
I'd mark this as solved, but that functionality does not seem to have survived the upgrade.

---

