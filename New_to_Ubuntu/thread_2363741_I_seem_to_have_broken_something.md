---
title: "I seem to have broken something"
date: 2017-06-13
forum: New to Ubuntu
---

### Post by MNKK on 2017-06-13
Playing around with various things tonight, and it seems at random times, if i type something in, i get the following issue. 

I typed:
sudo apt-get install numix-icon-theme-circle

After enter on the above line, this appears. 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by NoWayWin8 on 2017-06-13
Probably "Software Update" is using the apt process and needs to finish doing it's thing before apt commands can be accessible by another process. It does this automatically at system start and might take a while if the network is slow or there are lots of updates.

---

### Post by VMC on 2017-06-13
You haven't broke anything. Most likely auto updates are running.Read this article to unlock:
[https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

---

