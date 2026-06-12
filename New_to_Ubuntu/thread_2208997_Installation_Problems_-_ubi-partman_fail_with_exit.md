---
title: "Installation Problems - ubi-partman fail with exit code 10"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by Dave.B on 2014-03-03
i am trying to install ubuntu on a Dell 9150 with 2 gig of memory and Pentium D processor
i get to the Preparing to install screen and check the install updates and then press continue 
i then get a ubi-partman fail with exit code 10

and one one help

Thanks
Dave

---

### Post by grahammechanical on 2014-03-03
I have found these two references

[http://nixsos.com/ubi-partman-failed-with-exit-code-10-error/](http://nixsos.com/ubi-partman-failed-with-exit-code-10-error/)

[http://askubuntu.com/questions/248500/ubi-partman-failed-with-exit-code-10-during-12-10-fresh-install](http://askubuntu.com/questions/248500/ubi-partman-failed-with-exit-code-10-during-12-10-fresh-install)

Regards.

---

### Post by hardyp3 on 2014-04-24
I found those two threads today when I got the same ubi-partman crash with exit code 10 during an install of 12.04.4 on a Dell Inspiron 1200 from a USB drive.  Neither was applicable in my case.  I finally took the advice of the dialog box, found xterm, opened up /var/log/syslog, searched for ubi-partman, and **voila**!! success! partman was simply running out of disk space.  I had used a 1G thumbdrive I had laying around, afterall Ubuntu.iso fit ok with about 50MB to spare.  Unfortunately that was enough to try out Ubuntu but not enough to install.  I fixed the problem by using a proper 8GB thumbdrive.It's up and running after a successful install now.  BTW, I disconnected internet access during the install and it only took about 15 min to install, it finished while I was reading a Ubuntu security article on the Wiki. After I rebooted from the hard drive I started the network and began the update process.  It takes quite awhile.
Bottom line, check your /var/log/syslog file after partman crash and you should get some helpful hints.

---

