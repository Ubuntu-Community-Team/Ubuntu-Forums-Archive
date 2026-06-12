---
title: "K3b leaving some KDE process behind!?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by d2btoo on 2011-11-19
Hello,

It seems k3b is leaving some kde process after closing down! (please see the screen-shot)

You see, I'm not used k3b for a while, (presently using gnomebaker) but if I remember correctly in earlier ubuntu's (8 & 9 series) k3b doesn't show this behavior.... but then I might have forgot! What happened is one of my friend asked me this.... and so then I installed k3b on my system (he uses the same version of ubuntu 10.04), and indeed k3b leaving behind those kde processes!

So my questions are:
(1) Is this normal?
(2) Normal and/or ab-normal how do I configure/tell the system to not to do that? I mean k3b should also kill/terminate kde processes when it's done.

Thanks!

[[IMG]http://img32.imageshack.us/img32/1959/k3bkde.th.png[/IMG]](http://imageshack.us/photo/my-images/32/k3bkde.png/)

---

### Post by d2btoo on 2011-11-20
no one knows.... :confused::confused: oo what to do now :(

---

### Post by jerrrys on 2011-11-20
been using k3b since 8o4 and never looked until now.  I see three kde processes left over after closing k3b.  it adds up to about 4M of memory; not much to be concerned about.

---

### Post by d2btoo on 2011-11-20
Thanks for confirming , so it seems normal for k3b to leave those processes, I agree it's not much about ~4mb, but anyway I don't like dormant processes, so to speak, so do you have any idea how can I kill them automatically once k3b close down? any way to, say, attach/run a shell script which will clear those left overs?

---

### Post by jerrrys on 2011-11-20
it is my understanding that sleeping processes will be replaced when memory is needed.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ram+cache&as_qdr=all&sa=Google+Search&lang=en#806](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ram+cache&as_qdr=all&sa=Google+Search&lang=en#806)

---

### Post by d2btoo on 2011-11-21
I end up with ...
```
$ kdeinit4 && k3b --nofork && kdeinit4_shutdown
```
...and no more left over process :D:D

Thread solved. :popcorn:

---

### Post by jerrrys on 2011-11-22
> **d2btoo said:**
> I end up with ...
```
$ kdeinit4 && k3b --nofork && kdeinit4_shutdown
```...and no more left over process :D:D

Thread solved. :popcorn:
thats wild.  this command actually added processes when i tried it.  anyhow, glad it worked for you

---

### Post by d2btoo on 2011-11-22
> **jerrrys said:**
> thats wild.  this command actually added processes when i tried it.  anyhow, glad it worked for you

hmm! interesting ... do you have any other kde apps running... can you post here the terminal output please.... also what are your kde service configuration?

```

$ kdeinit4 && systemsettings --nofork && kdeinit4_shutdown 
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
systemsettings(2836)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
klauncher: Exiting on signal 1

$ ps aux | grep kde
-- returns nothing --



```

and my kde service settings:

[[IMG]http://img802.imageshack.us/img802/4552/servicemanagersystemset.th.png[/IMG]](http://imageshack.us/photo/my-images/802/servicemanagersystemset.png/)

---

### Post by jerrrys on 2011-11-23
I do not have /usr/lib/libkdeinit4_[FONT=monospace]* installed on my system, only k3b, but thanks anyhow.
[/FONT]

---

