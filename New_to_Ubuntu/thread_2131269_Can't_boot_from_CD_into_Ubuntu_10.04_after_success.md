---
title: "Can't boot from CD into Ubuntu 10.04 after successful installation of Ubuntu 12.04"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by skitnik on 2013-04-01
Hi everybody!

I successfully installed Ubuntu 12.04 (64 bit), so I can boot it and use it without problems. However, due to compatibility issues with Matlab R2012, I'd like to replace it by Ubuntu 10.04. I downloaded an .iso-image of 10.04.4 LTS amd64 and burned it on a DVD. However, when I restart the machine boots directly into 12.04 instead of booting from CD. I modified BIOS such that the CD drive has the highest boot precedence but the problem remains unsolved. Any ideas?

---

### Post by robsablah on 2013-04-01
This is a good one, spent 15 mins thinking about this....
Can you try booting into a live boot like puppy linux and using gparted to format the drive?

in other words, a different os not going to be recognised as ubuntu?

---

### Post by skitnik on 2013-04-01
Hi & thanks.
I already tried to boot into Lubuntu 12.04 from a CD but it didn't work: same thing. Is lubuntu 'remote' enough to answer your question? Currently downloading puppy linux... to be continued.

---

### Post by robsablah on 2013-04-01
Mmmm, yeah, maybe needs to be a bit more remote.
I'm off to bed now so I'll check tomorrow and see how you go!!!

---

### Post by skitnik on 2013-04-01
Same problem with Puppy linux, so, I guess, it was not the OS. However, the problem is solved now.
I googled the options for manually choosing the boot medium upon startup and followed them: 

Restart > press ESC > press F9 (Booting options) > ATAPI CD-ROM > hit ENTER to choose this option

In this way I booted directly from the 10.04 CD and replaced 12.04 with it.

I suppose the problem was in the BIOS settings but have no idea just what went wrong and why assigning the highest boot precedence to CD-ROM from BIOS settings did not work right away, i.e. why I had to choose manually chose the CD ROM during boot.

---

