---
title: "How to install .deb?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-11
How do I install a .deb file I DLed? Do I need to do that through Synaptic or Add/Remove, or is there a terminal command  can use?

Thanks!

---

### Post by lswest on 2008-05-11
you can either double-click it and choose "install program" or do this in the terminal:
```
sudo dpkg -i /path/to/file/[name of package].deb
```

---

### Post by SunnyRabbiera on 2008-05-11
well ubuntu has a built in tool just for this called gdebi, you should be able to just click on the debian package you downloaded and gdebi should fire up automatically.
where did you get this package from might i ask?

---

### Post by chadwit on 2008-05-11
Got it from some website...It was a while ago so I don't remember exacly where. Does that matter?

---

### Post by SunnyRabbiera on 2008-05-11
> **chadwit said:**
> Got it from some website...It was a while ago so I don't remember exacly where. Does that matter?

well just in case there are issues, but it should be able to install nonetheless.

---

### Post by chadwit on 2008-05-11
The gdebi thing worked fine. Thanks Sunny!

---

### Post by SIXAXIS on 2008-05-11
Normally for .deb files, you would just double-click it and then press install. Maybe it's not actually a deb file, maybe it's another type like tar.gz or something and someone just renamed it to deb?

**EDIT:** Never mind.

---

### Post by nynoah on 2008-05-11
If you got it from some website a while ago, I would go back there and redownload it.  There may be a more up to date version for you to use.  downloading things as a Deb package does not mean you will get the updates to the program.  You only will if you download it from snyaptic or have a repository added to your computer that supports that program.

---

### Post by chadwit on 2008-05-11
ok this should not be this difficult...
In Windows, I was using Nero Express. I could just drag,drop,burn - done. I DLed the trial version of Linux Nero, but I still can't figure this out. (There is no Nero Express for Linux.)  I just want to burn .AVIs as they are - not as ISOs, vob, bin, cue - none of that. Just a straight plain data burn. Also, when I insert a blank DVD, it insists on seeing it as a CD (says I have 650mb free). Please help!

---

### Post by SunnyRabbiera on 2008-05-11
nero for linux isnt that great anyhow, if you dont like brasero pre installed with ubuntu you can try k3b... k3b is our answer to nero for sure, in fact its better then nero in my opinion.

---

### Post by blithen on 2008-05-11
Becareful you don't download a deb unless you know where you are downloading it from and trust the site it could have malicious code in it.

---

### Post by indiecast on 2008-05-11
u should be able to just double click on it. a deb utility will pop up and you just click install. 

if it says you need to install other packages, install those first. (it wont let you install unless the dependencies are first)

---

