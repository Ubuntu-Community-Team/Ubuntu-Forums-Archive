---
title: "Unzip .uu"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by KylePhys on 2012-11-27
I have a file that i downloaded which has an extension .uu ( no idea what that means). It says "package in tarred,           gzipped, uuencoded form". how can I extract it in terminal?

Might it be that you know any good unzipper for ubuntu which is very graphical, like those on windows?

Thanks.

---

### Post by StinkySQL on 2012-11-27
You'll need a uudecode utility first. Most likely that will give you a tarball to work with. 

Nothing I've seen in the way of graphical interfaces for these. Terminal still rules.

---

### Post by steeldriver on 2012-11-27
uudecode is in the sharutils package I think - likely not installed by default

---

### Post by KylePhys on 2012-11-27
> **StinkySQL said:**
> You'll need a uudecode utility first. Most likely that will give you a tarball to work with. 

Nothing I've seen in the way of graphical interfaces for these. Terminal still rules.

I got it. Thank you. Installed sharutils

---

### Post by oldos2er on 2012-11-27
The package **sharutils** contains uudecode. As StinkySQL says, it's a CLI app.

---

