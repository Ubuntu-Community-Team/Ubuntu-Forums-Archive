---
title: "[SOLVED] Sources.list/Adept installer problem"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by WolvenSpectre on 2008-11-10
While I am not an absolutely new user, I have only puttered around in the Ubuntu pool, where others I have turned on to it are actually much further ahead than I because I have not had the time to do more than work with the GUIs and install a couple of apps, where as in the windows world I am much more versed to say the least.

This is what makes my problem especially frustrating at the moment.

I borked my Kubuntu 8.10 install.

After four failed installs on two bad install i386 desktop I finally got the OS to the point I was installing all the different repository goodness onto my PC and then I went and added an additional source to the Adept installer's sources and added the third party sources.

Adept froze and crashed.  I found the answer to the problem and it was I misentered the source address I added (I wanted to try out boxee) and that was keeping me from getting back into Adept and  fixing it.

I searched for help and found the file it is stored in, /etc/apt/sources.list. I could open it in Kate and fix it, but it wouldn't let me save it and the place that told me what to fix didn't tell me how.

I know I have to be root, but dropping into the terminal in or out of Kate and sudo su-ing doesn't help.

Could you please save me from my 5th install (not to mention the problems I had trying the last Release Candidate... thanks Lifehacker !  )

---

### Post by zvacet on 2008-11-10
```
kdesu kate /etc/apt/sources.list
```

should let you edit file and save changes.

---

### Post by WolvenSpectre on 2008-11-10
> **zvacet said:**
> ```
kdesu kate /etc/apt/sources.list
```

should let you edit file and save changes.

Didn't work in or out of kate. maybe because its Intrepid.

The error I get is:
```
bash: kdesu: command not found
```

---

### Post by Denestria on 2008-11-10
I think it might be
```
kdesu**do** kate /etc/apt/sources.list
```
or open a terminal and use
```
sudo nano /etc/apt/sources.list
```

---

### Post by WolvenSpectre on 2008-11-12
```
kdesudo kate /etc/apt/sources.list
```
That did the trick... and if I hadn't had three crisis going on at once I should have thought to try that.

Thanks!

---

