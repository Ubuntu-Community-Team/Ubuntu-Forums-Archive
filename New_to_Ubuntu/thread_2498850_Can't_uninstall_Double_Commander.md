---
title: "Can't uninstall Double Commander"
date: 2024-07-01
forum: New to Ubuntu
---

### Post by snudgeo on 2024-07-01
Having installed DC I find it is not suitable for my needs and wish to uninstall it. Apparently it can't be uninstalled, due to it being constituted using many packages from different sources. I found an old post here by someone who solved the problem using Aptitude and have tried to understand the information here: [https://ubuntu.com/server/docs/package-management](https://ubuntu.com/server/docs/package-management). I have made several attempts using command lines, all to no avail.
I am at a loss as to what to do. I never expected Linux to be so complicated. Please help and thanks in advance.

---

### Post by ajgreeny on 2024-07-01
How did you install DC, doublecmd-qt, doublecmd-gtk, doublecmd-common or some other method?

---

### Post by vanadium on 2024-07-01
If you installed according to one of the standard methods, i.e., using Software, then it can be removed equally easy. If you installed it in your own way, then, yes, linux can be complicated. The same applies for other operating systems, though. So yes, to get help, you will need to indicate first how the application was installed.

---

### Post by snudgeo on 2024-07-01
Oh dear. It was from one of those sites offering the best file managers, but I can't remember which one. Perhaps there is a log, still on my machine. I just don't know. Is there anything I can do? No doubt situations like this crop up all the time from us ex Windows newbies.

---

### Post by ActionParsnip on 2024-07-01
What is the output of 
```

dpkg -l | grep -i double 

```
Thanks

---

### Post by yancek on 2024-07-01
Why do you want it?  Did you check to see if there was any similar software available in the Ubuntu repositories?  If you go to the site at the link below, is that where you downloaded it from and if so, which one?  If you are downloading from 3rd party sources the standard methods of removing software do not apply.

[https://sourceforge.net/p/doublecmd/wiki/Download/](https://sourceforge.net/p/doublecmd/wiki/Download/)

I don't have any interest in this software but I would suggest you try an online search for deleting/removing double commander from ubuntu (include release version in search).

---

### Post by Impavidus on 2024-07-02
If it was installed as a deb package, that must have left a trace in the log files: /var/log/dpkg.log. But if you installed it some other way, it may not be that easy.

Yes, a lot of newbies take their Windows habits with them and get in trouble that way. Linux is really different. But once you get used to it, Linux makes a lot of sense.

---

### Post by snudgeo on 2024-07-03
I have looked in the dpkg log, but can't find any reference to DC, so I reckon I'm stuck with it. Also, I can't update several programmes, for instance Bleachbit. The system tells me the repository doesn't have a release file and is disabled.
 Clearly I have made a mess of my first foray into Linux. I'm thinking of starting again from scratch, in the hope of not having quite so much trouble next time.
Thanks to those who took the time to respond here.

---

### Post by yancek on 2024-07-03
> I have made several attempts using command lines, all to no avail. 

The above quote is from your initial post.  I suggest in the future you keep notes as to what commands you use and what you intend to do and what actually happens.  This will be helpful in troubleshooting later and in posting for help at a forum.

With regard to the error you report about the repository lacking a release file, which release version of Ubuntu are you using?  That is always significant information which should be posted in any thread.

---

### Post by Rubi1200 on 2024-07-03
There was no output at all from the command **ActionParsnip **asked you to run?

Not sure why you think you need Bleachbit. On Linux there are commands that can be run to clean the system without needing additional software. You can even create a bash script and cronjob to run them on a regular basis.

What version of Ubuntu do you have installed?

Listen, we have all been there. You would laugh if I told you how many times I messed up an install and had to reinstall.

Don't be discouraged. Learn from it and you will gain a sense of satisfaction as you learn to master the systems you install.

---

