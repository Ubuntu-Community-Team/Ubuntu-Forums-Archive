---
title: "deleted wine and cannot get it back."
date: 2011-09-09
forum: New to Ubuntu
---

### Post by kingnug on 2011-09-09
Hello, and thank you for helping. I am using Ubuntu hardy heroin... i was running wine for a while but was having a problem deleting old programs from the menu so i deleted wine hoping to get rid of all the old programs off my computer. now i am trying to get it back on my computer through add/remove and it tells me "You are about to install software that can't be authenticated! doing this could allow a malicious individual to damage or take control of your system." If you can help me out i would very much appreciate it.

---

### Post by Frogs Hair on 2011-09-09
Running sudo apt-get update in the terminal often clears this problem . I don't know if it would work with an unsupported version of Ubuntu .

---

### Post by kingnug on 2011-09-09
thank you for your quick response. i tryed that and after showing a bunch of web addresses it said: W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

any thing els i can try?? i had wine running just fine before i deleted it... thank you

---

### Post by ajgreeny on 2011-09-09
What do you mean by "deleted wine"?  Did you uninstall the wine package, and can not now get it back, or did you remove the hidden **/home/username/.wine** folder from your home, or perhaps both?

Your problem having removed it is now that the normal repos for updating etc etc, are gone, hardy no longer being supported.

It would be advisable for you to reinstall, and I suggest Lucid, 10.04, which is supported for almost 2 more years, but if you want to try to keep hardy, you can manually edit your sources.list to include:-
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
``` and remove the current dead ones.  That will give you a very old version of wine, however, so I recommend you update your distro and not try to meddle together an old ubuntu version.

---

### Post by kingnug on 2011-09-09
this was about a month ago so i can't remember exactly what i did but i'm pretty sure i uninstalled, unsuccessfully, then using old posts on this forum, i used the synaptic package manager to remove. i think i am just not good enough with this program and may have removed stuff i needed. i believe i will try to upgrade to lucid now...  i have a very old dell computer, that is why i haven't upgraded yet. i think it only has a 14 Gig hard drive. would lucid be much bigger than hardy??i really like this O.S. and the amazing community that comes along with it. thank you for all of your help.

---

### Post by BlinkinCat on 2011-09-09
Hi,

You could give Xubuntu a go! - :)

I find 11.04 is fine -

---

