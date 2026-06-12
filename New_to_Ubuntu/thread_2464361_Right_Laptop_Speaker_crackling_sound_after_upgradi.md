---
title: "Right Laptop Speaker crackling sound after upgrading to Ubuntu 20"
date: 2021-06-30
forum: New to Ubuntu
---

### Post by ucalyptus on 2021-06-30
[B]> Upgraded from 18 to 20 LTS
> Right speaker crackling sound I noticed. Left one works fine.
> I make changes in /etc/pulse/default.pa adding the tsched=0 flag, no improvements
> I change the modprobe.d/alsa-base.conf, no improvements.
> I did killall pulseaudio and pulseaudio -k, no improvements.
> Me cries in corner since no improvements even after restarting computer multiple times.
[/B]:confused:

---

### Post by ActionParsnip on 2021-06-30
I'm guessing you mean Ubuntu 20.04. "Ubuntu 20" and "Ubuntu 18" aren't things. Please follow the below and when you get to step 3 please give the URL that the script creates.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Thanks

---

### Post by ucalyptus on 2021-07-02
Yep 20.04 Focal Fossa -- apologies for improper language.

---

### Post by ucalyptus on 2021-07-02
Hi ActionParsnip,

I am attaching the URL to the outputs from the troubleshooting steps you mentioned:
[https://gist.github.com/forkbabu/38bdfbe60b7fd0708a35364dcfff6842](https://gist.github.com/forkbabu/38bdfbe60b7fd0708a35364dcfff6842)

---

### Post by ucalyptus on 2021-07-02
I heard that dist-upgrade (thru Software Center) from 18.04 to 20.04 always breaks something (it's a classic Ubuntu bug).
Someone suggested me to rebuild alsa. How to do that?

---

### Post by tea for one on 2021-07-02
Sometimes in-situ version upgrades create a new difficulty but not always.

Anyway, in your position, I would download the current Ubuntu 20.04 iso, make a bootable USB stick and test sound.

If the Right Speaker still crackles - could be hardware?
If sound is OK - could be broken upgrade?

---

