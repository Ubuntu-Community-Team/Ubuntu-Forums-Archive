---
title: "Why is Facebook not working on chrome and firefox!!!"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by AEllerbrock on 2012-01-17
Hei everyone! every single website is working except for facebook. i don't know how to fix it. i cleared the browsing data and it works for like 5 minutes. i tried to reinstall google chrome and it doesn't change anything. i can't uninstall it neither because it says "Virtual packages like 'google-chrome' can't be removed
"
i tried with 
sudo apt-get purge google-chrome
sdo dpkg -r googl-chrome

i cannot find it in the software center.


what can i do?!!!

---

### Post by ubudog on 2012-01-18
What exactly is happening (after five minutes)?

---

### Post by muteXe on 2012-01-18
If every single website is working except fb, that suggests to me that something's up with fb rather than your browser.

---

### Post by wolfen69 on 2012-01-18
Isn't today the internet blackout day where some sites choose to be down? But yeah, it sounds like a facebook issue, not browser.

---

### Post by muteXe on 2012-01-18
yep you're right wolfen. wikipedia's down - there are people in my office wondering around like lost souls now they have nothing to look at :)

---

### Post by ubudog on 2012-01-18
That might be it.  Have you tried Facebook before (like yesterday)?

---

### Post by mvpereira on 2013-04-14
> **AEllerbrock said:**
> Hei everyone! every single website is working except for facebook. i don't know how to fix it. i cleared the browsing data and it works for like 5 minutes. i tried to reinstall google chrome and it doesn't change anything. i can't uninstall it neither because it says "Virtual packages like 'google-chrome' can't be removed
"
i tried with 
sudo apt-get purge google-chrome
sdo dpkg -r googl-chrome

i cannot find it in the software center.


what can i do?!!!

Changing MTU to 1464 solved the problem to me, like suggestes here: [http://ubuntuforums.org/showthread.php?t=2110129&p=12480983#post12480983](http://ubuntuforums.org/showthread.php?t=2110129&p=12480983#post12480983)

---

### Post by overdrank on 2013-04-14
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

