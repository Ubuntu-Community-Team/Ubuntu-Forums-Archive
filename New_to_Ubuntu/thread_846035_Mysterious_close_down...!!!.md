---
title: "Mysterious close down...!!!"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-01
My machine has mysteriously closed down while I was out...I found this on my System log....does it mean anything?

Jul  1 21:34:00 xxxxx kernel: [26086.045153] Uhhuh. NMI received for unknown reason a0 on CPU 0.

---

### Post by brian_p on 2008-07-01
> **dunbrokin said:**
> My machine has mysteriously closed down while I was out...I found this on my System log....does it mean anything?

Jul  1 21:34:00 xxxxx kernel: [26086.045153] Uhhuh. NMI received for unknown reason a0 on CPU 0.

Google offers lots of reading when searched with "NMI received for unknown reason". Maybe there is a clue or two for you there.

---

### Post by dunbrokin on 2008-07-01
> **brian_p said:**
> Google offers lots of reading when searched with "NMI received for unknown reason". Maybe there is a clue or two for you there.


Hmmmm! you are right...there are a lot of errors like these....but nobody has a goddam idea why it is happening....so, back to square one....anybody got any ideas?

---

### Post by brian_p on 2008-07-01
> **dunbrokin said:**
> Hmmmm! you are right...there are a lot of errors like these....but nobody has a goddam idea why it is happening....so, back to square one....anybody got any ideas?

I wouldn't have quite put it like that myself but tracking down the cause of the syslog message would appear to come into the 'there is no quick fix' category. Bios setting, memory, motherboard, video card could be factors. And the the message in syslog might not be related to the machine closing down.

Run the machine. If the problem is a regular occurrence you are into trouble shooting the hardware and software. If not - be thankful.

---

