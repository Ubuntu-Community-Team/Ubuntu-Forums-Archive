---
title: "New Hard Drive problems"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Spoken on 2008-08-22
alright, so i just had a hard drive fail on me, luckily i was still under warrenty with dell and they shipped me a new one.  for some reason they didnt load ubuntu 7.04 on it like the original one had.

this one has NOTHING on it.  i have the 7.04 live cd. but when i boot from it, i get this error

can't access tty, job control turned off.
(initramfs)


i would like to reconfigure xserver or something to get it to detect my screen but the commands are limited from this screen.  is there anyway i can get to a command line?  or what do i need to do?:confused:

---

### Post by Gannon8 on 2008-08-22
This problem has nothing to do with the hard drive. I think someone else had this problem before, try searching posts.

---

### Post by LowSky on 2008-08-22
may I suugest that you download and try a 8.04 Live CD? or prefeable a Alternate install CD

---

### Post by Spoken on 2008-08-22
kk, i will try to find a computer to do that on.  im posting off my colleges computers and they are not capable of doing such tasks.  any other suggestions besides burning a cd?

---

### Post by bobnutfield on 2008-08-22
I recently encountered the same issue, but with a Slackware kernel.  In my case, it was a bad initrd file to boot the kernel with.  However, that is unlikely from a live CD.  You might want to take a look at this:

[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error]("http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error")

---

