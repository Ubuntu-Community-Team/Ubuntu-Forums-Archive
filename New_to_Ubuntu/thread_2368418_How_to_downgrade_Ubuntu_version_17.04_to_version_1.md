---
title: "How to downgrade Ubuntu version 17.04 to version 16.10"
date: 2017-08-10
forum: New to Ubuntu
---

### Post by badhri on 2017-08-10
I have recently installed ubuntu version 17.04, later i found out lots of issues in it and the softwares i want to try support only for 16.10. Please help me in downgrading it.

Thanks in advance

---

### Post by QIII on 2017-08-10
Hello!

Unfortunately there is no downgrade path except by reinstalling.  Do you know how to preserve your important data and /home partition?  If not, just ask.

16.10 is no longer supported, would be a poor choice and would be a struggle in any case. If going back, 16.04.2 would be better.

---

### Post by Autodave on 2017-08-10
Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by badhri on 2017-08-11
Thanks all. I installed Ubuntu 16.04 and all looks great now.:cool::cool:

---

### Post by metalbiker on 2017-08-11
another option to do instead of downgrading, which is by and large absolutely ok to do so (to go back to a previous release), but what you could is to also report anything to launchpad as a bug report. any issues you come across in any version can be submitted and reviewed along with supporting video/pics from you in regards to the issues you're experiencing. I'm currently doing the shakedown of ubuntu 17.10 and I've already had to file some bug reports of my own because of the hardware inside of my laptop, which is the whole point to do so to flush out any issues and get them corrected.

in order to file a bug report, you'll need a launchpad account, so go to launchpad.net and get one setup for yourself and then after that, you can file a bug report in this manner:

1. open terminal and type in this: ubuntu-bug *issue area*

*issue area* will be wherever you suspect the problem to be such as graphical. so if it is graphical, you can label it as graphics so the terminal input will look something like this: ubuntu-bug graphical, without the asterisks. 

for an example from my own bug reports, i submitted one like this "ubuntu-bug gnome-shell" and it gathered all relevant information from my computer and took me to launchpad.net.

from there, I was able to expand on the description of the symptoms and provided supporting screen pics and videos to show what was going on. 

pretty simple really just takes a bit of work to get it all done. 

that'd be what I'd do if I were having problems with 17.04 but you do what you feel is necessary for you.

---

