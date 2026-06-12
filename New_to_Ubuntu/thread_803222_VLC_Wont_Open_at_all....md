---
title: "VLC Wont Open at all..."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Quaily on 2008-05-22
Hey, I am a complete beginner... Very inexperienced. 
I use VLC to play DVDs and avi files etc, but since yesterday the program wont open at all.

Every time I try to use it I get "VLC media player has encountered a problem and needs to close.  We are sorry for the inconvenience."

I really dont know what to do!
Can anyone help?

Thank you

---

### Post by HotShotDJ on 2008-05-22
> **Quaily said:**
> Every time I try to use it I get "VLC media player has encountered a problem and needs to close.  We are sorry for the inconvenience."Please open Applications --> Accessories --> Terminal and run:```
vlc
```Please post the error messages, if any.

---

### Post by NightwishFan on 2008-05-22
Beat me to it. Does it error like that in Ubuntu, I thought that was a windows thing.

---

### Post by HotShotDJ on 2008-05-22
> **NightwishFan said:**
> Beat me to it. Does it error like that in Ubuntu, I thought that was a windows thing.Nah.  If it were a windows error, it would look more like the attached image:

---

### Post by sharks on 2008-05-22
yes. i also thought that it would be a windows thing.

---

### Post by drs305 on 2008-05-22
Open synaptic, select 'search' and enter 'vlc'. Right click on each vlc entry and 'mark for reinstallation', then apply. If that doesn't fix it, write down all the entries, mark for removal, apply and then reinstall.

---

### Post by HotShotDJ on 2008-05-22
> **drs305 said:**
> Open synaptic, select 'search' and enter 'vlc'. Right click on each vlc entry and 'mark for reinstallation', then apply. If that doesn't fix it, write down all the entries, mark for removal, apply and then reinstall.Shouldn't we see if we can diagnose the problem before we perform surgery?

---

### Post by drs305 on 2008-05-22
> **HotShotDJ said:**
> Shouldn't we see if we can diagnose the problem before we perform surgery?

No, I don't think so. The package files will be reinstalled but the user files won't be affected using the first option. I just did what I suggested, reinstalling vlc, and my user files (vlcrc) in ~/.vlc were not changed.

---

