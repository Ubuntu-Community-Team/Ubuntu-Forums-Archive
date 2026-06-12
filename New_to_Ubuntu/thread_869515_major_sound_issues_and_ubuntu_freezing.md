---
title: "major sound issues and ubuntu freezing"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by pikeman47 on 2008-07-24
Lately, i've been having issues with sound. It seems that only one program is sending out sound at a time. Let's say i have firefox and pidgin open. If i haven't made any noise with firefox (i.e. watched a vid on youtube, streamed a song) the IM noises from pidgin will sound. But as soon as i open up a video or something involving sound on firefox, my sound from pidgin goes away. Or vice versa
Another problem i've run into along the same lines is: pidgin sound not working, then firefox sound not working either, then if i try to open any other application ubuntu will freeze up and nothing is clickable.
Help, please. I'm not sure if it's something i've done or some settings i overlooked or what...

---

### Post by iaculallad on 2008-07-24
> **pikeman47 said:**
> Lately, i've been having issues with sound. It seems that only one program is sending out sound at a time. Let's say i have firefox and pidgin open. If i haven't made any noise with firefox (i.e. watched a vid on youtube, streamed a song) the IM noises from pidgin will sound. But as soon as i open up a video or something involving sound on firefox, my sound from pidgin goes away. Or vice versa
Another problem i've run into along the same lines is: pidgin sound not working, then firefox sound not working either, then if i try to open any other application ubuntu will freeze up and nothing is clickable.
Help, please. I'm not sure if it's something i've done or some settings i overlooked or what...

On your terminal:

```
sudo apt-get install libflashsupport
```

---

### Post by mikedemario17 on 2008-07-24
well i used to have a problem with this as well but on windows...if your pc is an old one then it might not have the ableity to run more then one app. useing sound...and when two are running it might just cut out all together...so try to run one at a time....and for linux freezing ...my linux 8.04 was freezing in firefox and when i downgraded back to 7.10 everything was good again

---

### Post by pikeman47 on 2008-07-24
Wow, that libflashsupport did the trick.
Thanks man, i had no idea the solution would be so simple.

---

### Post by iaculallad on 2008-07-24
> **pikeman47 said:**
> Wow, that libflashsupport did the trick.
Thanks man, i had no idea the solution would be so simple.

I'm glad that helped.  Go Ubuntu
That file is the audio support wrapper for non-free Flash plugin.

---

