---
title: "install 8 failed, no boot, what now?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Carcharoth on 2008-07-26
original OS, windows 2000 Pro. played with Ubuntu 7 live disk. made a dual boot system and was playing. IN THE GRUB LOADER, I had 3 choices for Ubuntu, only the first in the list worked. I assume that the others are old kernels.

downloading KompoZer, Ubuntu 8 was strongly recommended, so I went for it.

installation failed with 4 minutes to go in ( like ) the fourth option. the one right before removing old packages and clean up.

in the recover mode I get as far as
Generating locals
[INDENT]en_AU.UTF-8 .....[/INDENT]

and she hangs.

what next?

oh, I have been around computers since FORTRAN and windows 3.1
but forums are new to me. please consider faux pas in this light.

---

### Post by bumanie on 2008-07-26
Think I would format the partition/s used for the failed install with gparted and then try the alternate installation cd. It is text based and 99% of the time works when the live cd won't.

---

### Post by Carcharoth on 2008-07-26
I have not yet tried the live CD for Hardy, I am downloading the iso now. yes, I am prepared to wipe it out and start over. but I am kind of hoping I can just fix....

thanks.

---

### Post by bumanie on 2008-07-26
I must have got the gist of the post wrong. You must be talking about the kompozer installation hanging. Sorry, I thought you meant ubuntu 8.04. was hanging during installation. How did you install kompozer? Best idea would be to remove the offending program. In terminal> sudo aptitude remove <program name> Will get rid of anything to do with compozer and if you want it, try again once you have 8.04 installed.

---

### Post by Carcharoth on 2008-07-26
I wasn't watching closely enough. I think KompoZer installed correctly, but before I tried anything I was prompted to try 8.

I was definitely installing 8 when she hung up.

now I have burned a live CD for 8 - we shall see what happens.
( if I can find the time... )

---

