---
title: "[SOLVED] Amarok not working after recent update"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by dwhitney67 on 2008-06-06
I am running Ubuntu 8.04 with the latest updates, which includes kernel version 2.6.24-18-generic.

I updated my system yesterday (2008-06-05), and since then, Amarok has either refused to play or plays one song (maybe two), then just stalls... literally.

Prior to the update, I was running kernel version 2.6.24-17-generic and everything worked fine.

When Amarok goes out to lunch, the only way I can terminate it is to use the command line to force it to exit (using the 'kill' command).

Could the issue with Amarok actually be an alsa library issue?  If so, what are the proper steps to update the alsa library?

Btw, as of the moment I am writing this post, I am running my system with the 2.6.24-17-generic kernel... and the problem with Amarok still persists.

Can someone advise me on how to fix this issue?

---

### Post by rburkartjo on 2008-06-06
dwhit, try this open a terminal type apt-get upgrade . note you might have to log in a root. my amarok in 8.04 and using the new kernel is working fine/cheesemaker

---

### Post by Otto-C on 2008-06-06
> **rburkartjo said:**
> dwhit, try this open a terminal type apt-get upgrade . note you might have to log in a root. my amarok in 8.04 and using the new kernel is working fine/cheesemaker

huh

---

### Post by dwhitney67 on 2008-06-06
Well, I finally solved the sound problem.  It was not an Amarok issue, but instead a system-wide issue with the sound card driver.

Apparently the system update I performed replaced my /etc/modprobe.d/options file with a lamer copy.  Thanks Canonical/Ubuntu for wasting my time today!  :-x

Anyhow, I added the following statement to the /etc/modprobe.d/options file:
```
options snd-hda-intel model=3stack
```

Then I performed a reboot, and everything started working.

---

