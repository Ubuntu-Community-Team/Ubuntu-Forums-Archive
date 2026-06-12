---
title: "If I`m using Wine to run a &quot;Windows&quot; program do I now need any Antivirus program"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by cliveT on 2012-02-18
Hi Guys

I`ve installed wine to run a windows only program  -which is running great by the way,my question is do I now need an anti virus program now or not?

Regards

Clive

---

### Post by mcduck on 2012-02-18
> **cliveT said:**
> Hi Guys

I`ve installed wine to run a windows only program  -which is running great by the way,my question is do I now need an anti virus program now or not?

Regards

Clive

No, you shouldn't need one. Especially if the program in question is not an old windows version of a web browser or anything like that.

Wine isn't fully windows-compatible, so viruses are unlikely to run on it successfully. And even if the program would somehow get a virus on your system, it would only affect applications installed through Wine (simply because for the virus to get access outside of the fake directory structure Wine uses, the virus would have to know that it's running in Wine, and be designed to access the Linux directories outside of the Wine directory tree...)

edit: Here's a quite funny old blog post about trying to run Windows viruses on Wine (on purpose): [http://jadmadi.net/2005/01/27/linux-wine-how-to-running-windows-viruses-with-wine/]("http://jadmadi.net/2005/01/27/linux-wine-how-to-running-windows-viruses-with-wine/"). Most likely Wine has improved a lot since then, but actually gettign avirus to run on Wine is still not likely, and what the virus could possibly do even if it worked perfectly would still not be anything nearly as abd as it would be on Windows. Of course you still use common sense wth Wine and avoid running things you don't trust to be safe...

---

### Post by BlouBlou on 2012-02-18
No, you don't need it, because wine emulates windows, but it is not. If a virus wants to shutdown your computer, it would need root privileges, or at least more privileges. They're made for windows, not for Linux. Remember, wine is not windows, and doesn't emulate it. Wine just adds a compatibility-layer.

---

### Post by cliveT on 2012-02-18
Thanks guys for your swift answers and have a good weekend!

---

### Post by silvama11 on 2012-02-18
Oi
Did  you encounter virus problems with the program when run in Windows? If not I doubt it. But running an antivirus may be a prudent action if in doubt.just find one with small footprint and minimal resource usage. I think other posters maybe better informed on what is a good av to use .

---

### Post by Gone fishing on 2012-02-18
I'm going to disagree with mcduck - I think it would be prudent to run an AV. 

Here's what Wine say 

[http://wiki.winehq.org/FAQ#head-](http://wiki.winehq.org/FAQ#head-)
3cb8f054b33a63be30f98a1b6225d74e305a0459

and here's a link 

[http://ubuntuforums.org/showthread.php?t=72598&page=2](http://ubuntuforums.org/showthread.php?t=72598&page=2)

However, the virus would not be able to effect Ubuntu as a whole unless you ran Wine as root or gksu and your not going to do that. Potentially it could damage your /home although probably more likely just the .wine folder. It is also worth saying that many viruses will not run properly under wine.

It would be safer to run an AV and check Windows files before you ran them under wine, you could use clam AV. Obviously the main protection is using your brain before you click and most Linux users probably do this more than many Windows users.

---

### Post by cliveT on 2012-02-18
> **Gone fishing said:**
> I'm going to disagree with mcduck - I think it would be prudent to run an AV. 

Here's what Wine say 

[http://wiki.winehq.org/FAQ#head-](http://wiki.winehq.org/FAQ#head-)
3cb8f054b33a63be30f98a1b6225d74e305a0459

and here's a link 

[http://ubuntuforums.org/showthread.php?t=72598&page=2](http://ubuntuforums.org/showthread.php?t=72598&page=2)

However, the virus would not be able to effect Ubuntu as a whole unless you ran Wine as root or gksu and your not going to do that. Potentially it could damage your /home although probably more likely just the .wine folder. It is also worth saying that many viruses will not run properly under wine.

**It would be safer to run an AV and check Windows files before you ran them under wine, you could use clam AV. Obviously the main protection is using your brain before you click and most Linux users probably do this more than many Windows users.**

OK agreed and thanks for the update.:)

---

