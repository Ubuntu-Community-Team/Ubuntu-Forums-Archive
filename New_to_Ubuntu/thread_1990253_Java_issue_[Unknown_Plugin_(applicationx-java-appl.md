---
title: "Java issue [Unknown Plugin (application/x-java-applet;jpi-version=1.6)]"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Underdog_RC on 2012-05-29
I'm trying to run a website that requires silverlight and java for work.  I can get around the silverlight issue by using the moonlight plugin, but Java just does not work.  

I've tried the icedtea plugin, openjre, etc.  I've tried following the steps in multiple posts to install 1.6.0_31 or 32 and tried just installing the latest version 1.7.0_04, but nothing works and i continue to get this error in Firefox:

No suitable plugins were found
Unknown Plugin (application/x-java-applet;jpi-version=1.6)

Is the x-java-applet that it's looking for tied to something else that i'm missing?  This is the only thing preventing me from moving 90% of my work to an Ubuntu machine.......which would be quite useful.  :-)

Thanks!

---

### Post by roton on 2012-05-29
Did you install icedtea on its own or as part of the unrestricted extras?
I just remember having trouble getting it working until I installed the extras (sudo apt-get install ubuntu-restricted-extras).

---

### Post by Underdog_RC on 2012-05-29
I installed it on it's own...but i'll try adding the extras now and update shortly.  Thanks!

---

### Post by Underdog_RC on 2012-05-29
No luck.  I definitely does not like the icedtea plugin it seems.  I can never get the Oracle Java one to show up in the list of plugins in Firefox either.

---

### Post by Curtis6767 on 2012-05-29
Here are two sites that you might find helpful. Look them both over before doing anything as there are a couple of steps missing from one but added to the other.

Before proceeding, you probably want to get rid of Icedtea, etc.

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

&

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Hope this helps

---

### Post by Underdog_RC on 2012-05-29
Thanks, i'll look through those to make sure they aren't the same as the other articles i've looked at and give them a shot.  I just got pulled into something else here at work though, so i may not get to try until tomorrow AM.

---

### Post by Underdog_RC on 2012-05-30
Ironically, the second link will not open because of a javascript issue:


Alert
Firefox doesn't know how to open this address because the protocol (javascript) isn't associated with any program.



....so, that's definitely at least part of the issue.  ;-)

---

### Post by Underdog_RC on 2012-05-30
Ok, I was able to get both links open (the second had the complete list of instructions).  I followed the steps to get the repository added and install Java...however, it's version 1.7.  It does show up as an add-on in Firefox, but I still get the same error referencing x-java-applet and 1.6.  I'm assuming I need to be able to get the 1.6 plugin to show up within Firefox to make this work. 
 
Help?

---

### Post by Underdog_RC on 2012-06-01
bump....anyone help?

---

