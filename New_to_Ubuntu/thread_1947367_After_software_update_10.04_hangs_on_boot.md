---
title: "After software update 10.04 hangs on boot"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by Stingray88 on 2012-03-26
Note: This has been crossposted from General Help because it wasn't getting any response over there...

I've had Ubuntu 10.04 running on my desktop for a while without any issues. I went away for the weekend, and when I came back there were software updates available, so I ran them, and they required a reboot. So I clicked "restart now". Now Ubuntu fails to boot past the Ubuntu splash screen.

I have no backup, as that was my task for this week to make one. Great timing.

I'm not really sure where I should begin to start diagnosing my issue, so any suggestions are appreciated. My installation is pretty close to stock 10.04 I'd say, so I'm hoping I can possibly perform some sort of "repair" on my installation with a live cd, not sure if that is possible.

I have tried to boot into recovery, however pressing 'esc' anytime during boot does nothing.

Anyways, thanks for any help you guys can give me. I'm really just looking for the quickest and easiest way to get myself back to where I was. I am not interested in upgrading past 10.04 right now.

---

### Post by nazar91 on 2012-03-26
Maybe your file system is corrupted. 
Try boot from livecd. Unmount your hd and run fschk on it.

---

### Post by Stingray88 on 2012-03-26
> **nazar91 said:**
> Maybe your file system is corrupted. 
Try boot from livecd. Unmount your hd and run fschk on it.

Do you mean fsck? fschk returned as no command found, and suggested fsck.

From there, it replies with:

/dev/sda1: clean, 319065/9691136 file, 13085542/38751488 blocks

---

### Post by Jesse Tustin on 2012-03-26
Did you save your LiveCD ? If you did, then reinstall Ubuntu. If not, have a friend make a LiveCD for you. If he or she's not that good at it, help them do it. I really hope this helps.

---

### Post by Stingray88 on 2012-03-26
> **Jesse Tustin said:**
> Did you save your LiveCD ? If you did, then reinstall Ubuntu. If not, have a friend make a LiveCD for you. If he or she's not that good at it, help them do it. I really hope this helps.

I have a liveCD, but why would I want to reinstall Ubuntu and lose everything?

That doesn't sound like a great idea.



NEVERMIND about this post. I don't have the time or patience for this OS any longer.

---

