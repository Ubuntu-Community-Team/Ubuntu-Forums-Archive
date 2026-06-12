---
title: "Beep on Shutdown"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by johnnylong on 2011-09-10
Ladies & Gentle,
    Run Ubuntu Remix on a Asus 1000h netbook. Everything runs just fine except for an unexplainable glitch. Every time I shut down the computer I get a beep. What's up with that. If anyone can enlighten me on the possible cause I be very much appreciative.

                  johnnylong

---

### Post by snip3r8 on 2011-09-10
Is the beep really that bad? Are there any other problems?

---

### Post by _d_ on 2011-09-10
What motherboard do you have, and can you elaborate on what kind of "beep" it is? Is it short beep, long beep, multiple beeps?

Mostly a computer will only send out a beep if there is something wrong.

---

### Post by ajgreeny on 2011-09-10
Which version of ubuntu, your user CP says 9.04, which is no longer supported.  However, aside from this I seem to remember a shutdown beep which was a bug in a previous version of ubuntu, maybe 9.04, but I can't remember which.

I have just remembered that I made a txt file to remind myself of the bug's solution, which is this:-

Stop Anoying Shutdown Beep!
the file system in jaunty has changed slightly and the command will manually add "blacklist pcspkr" to the file /etc/modprobe.d/blacklist.conf ```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist.conf
``` It worked for me and many others

---

