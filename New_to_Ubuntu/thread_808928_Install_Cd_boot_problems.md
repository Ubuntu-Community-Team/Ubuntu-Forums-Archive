---
title: "Install Cd boot problems"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-05-27
I am having trouble installing 8.04 from cd.  When I select "Install Ubuntu" rather than taking me through the installation process a busy box shell opens.

I also attempted to boot from gparted 0.3.4-11 and it gave me some more information
"Determining root device
Determining looptype
!!Invalid loop location /gparted.dat
Please export LOOP with a valid location, or reboot and pass a proper loop=...
!!Kernel command line

Busy box welcome msgs and all that jazz
/bin/ash:cant access tty; Job control turned off
#normal command prompt

I have a Dell Vostro 200

Any ideas?

---

### Post by dreadh3ad on 2008-05-27
Well guess what?

I just attempted to upgrade through 7.10 and now my system will not boot.

The ubuntu logo appears and an orange rectangle bounces from side to side of the black bar and does nothing else.

As a result I have been FORCED to use windows xp.

How the hell is the average user supposed to troubleshoot this kind of issue?

Although I think it has something to do with the problems stated in the post above.

---

### Post by dreadh3ad on 2008-05-27
Any suggestions?  I currently have one computer that has been rendered completely useless due to an upgrade and its inability to run a livecd.

---

### Post by sayakb on 2008-05-27
First check the Hardy (8.04) CD for defects (Select *Check CD for defects* at Ubuntu boot menu)
Then if it comes to be okay, select Text mode install.
If the CD has defects, check the MD5 sum of your Hardy image and burn it again at slow speed.

---

### Post by dreadh3ad on 2008-05-27
And what if the cd has no defects?  How do you check the MD5 sum?

---

### Post by sayakb on 2008-05-27
If the CD has no defects, simply select Text install.
As for MD5 sum:
[http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by dreadh3ad on 2008-05-27
I tried to do that and after about a minute of waiting I was dumped to the busy box shell again.

It seems like a lot of people are experiencing this problem...

---

