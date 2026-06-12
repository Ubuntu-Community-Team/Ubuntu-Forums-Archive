---
title: "dev/mapper/cryptswap1 issue"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by apa2 on 2013-10-21
Not sure what's going on here, fresh installation of Ubuntu 12.04.3 LTS and get that message before login screen.. dev/mapper/cryptswap1 message? I tried 1st option from this thread and appears to be working right now: [http://ubuntuforums.org/showthread.php?t=1806762&p=11563270#post11563270](http://ubuntuforums.org/showthread.php?t=1806762&p=11563270#post11563270) 

Adding the "noauto" to the line: ```
/dev/mapper/cryptswap1 none swap sw,noauto 0  0
```

I noticed there was bug reported for this, but isn't there a definite fix or way to NOT get this issue at all on fresh installation? Lol! *tisk, tisk* Ubuntu devs. Another thing I should have done though, was dismount my 3 1/2 floppy drive as that's registering too, which I don't need anyway. I only have ONE hard drive on this tower, so not sure why this error above should be happening? I chose encrypt home during installation, should I just skip this step until AFTER it's installed? Because I had done an install on the other tower, along side Windows 7 OS.. and encrypted /home and didn't get this issue/error/warning at start up before login screen... Thanks in advanced, just a noob looking for tips,suggestions, help and etc

---

