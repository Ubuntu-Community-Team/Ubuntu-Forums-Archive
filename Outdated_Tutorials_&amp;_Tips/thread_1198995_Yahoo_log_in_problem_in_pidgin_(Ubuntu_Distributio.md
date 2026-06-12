---
title: "Yahoo log in problem in pidgin (Ubuntu Distribution)????"
date: 2009-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dipaish on 2009-06-28
Yahoo ! Inc practically blocked all the Linux IM clients like pidgin,kopete. We all thought it might be some problems that has disabled us to log in but the story behind it is different. Yahoo has changed its login method which has made Instant messenger clients for linux to connect with yahoo protocol.

Anyways to every problem there are solutions. Follow the following steps to make your pidgin work with ubuntu 8.04 or ubuntu 9.04

I assume that you have pidgin installed already. Incase not please install pidgin using your favourite package manager.

Step 1 : Save this  key  (Right click and then select save link as )

Step 2 : Go to system >> Administration >> Software sources >>
enter the password if asked and then go to "Third Party Software " Click on the "Add" button and pase the line below depending on your ubuntu distribution.

Ubuntu 9.10

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

Ubuntu 9.04

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main

Ubuntu 8.10

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) intrepid main

Step 4 : Go to  "Authentication," click the "Import Key File" (this file is the one which you saved it just before ). Navigate to the location where you saved this file.

Step 5 : Update your system . Go to terminal and then click on sudo apt-get update or
 go to system >> administration >> Update Manager

Step 6: Close pidgin (if its currently logged in ) and then sign in your yahoo account.

---

### Post by drdabbles on 2009-06-29
Thank you for your tip. Job well done.

As for Yahoo!, my response to the two latest issues of them making their protocol incompatible has been even simpler. I have stopped using Yahoo! Messenger, and all Yahoo! products. It was much easer than I thought. :p

Too bad for them, really. I've become a real Google power user, and Yahoo! needs people like us to promote them to our less technical friends. Oh well.

Again, thank you for your help to others on this issue!

---

### Post by Elep.Repu on 2009-06-29
Yeah, I remember this problem. 
It's not ubuntu, I don't believe.

---

### Post by eugen_nicoara on 2009-06-30
Try that: [http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/]("http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/")
It worked for me.

---

### Post by danbar on 2009-06-30
I followed the instructions as in [http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/comment-page-1/#comment-7667](http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/comment-page-1/#comment-7667)

But unfortunately I had this message.  (I'm using Ubuntu 8.10)


E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


How can I solve it?

---

