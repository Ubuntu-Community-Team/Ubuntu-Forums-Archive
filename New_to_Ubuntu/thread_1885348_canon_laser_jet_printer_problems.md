---
title: "canon laser jet printer problems"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by krishnan t s k on 2011-11-23
i had recently installed oneiric ocelet in my system and tried to configure my printer canon LBP 2900....i followed the instructions  from  [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) and managed to set my my printer without a hitch
but after configuring my printer, i am unable to print the test page.... the printer state shows Idle - ccp send_data error, exit
i have been breaking my head over this problem for over a week without making any progress
thank you in advance for your help :):)

---

### Post by BC59 on 2011-11-23
Canon has usually problems with Linux installations.

Just check here:

[http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux](http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux)

---

### Post by krishnan t s k on 2011-11-23
tried that too....it dosent work on 11.10 :( :(

---

### Post by krishnan t s k on 2011-11-27
i was unable to install my printer in ubuntu 11.10 so i ran the wubi installer in one of my computers to determine the cause.....wubi installed the amd64 version of ubuntu 11.10 in my computer and i once again followed the steps provided in   [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) this time pausing and observing every little step..... after fiddling around for 2 days, i seem to have made some progress..... i have been able to add my printer and get the two numbers that i should get for the ccpd status
however, the captstatusui shows the error message Check the Device Path of /etc/ccpd.conf and upon typing 
lsmod | grep usblp it outputs as follows
usblp                  18239  0
now it says in the link mentioned above that in case it outputs nothing,then we should load the module and restart ccpd
but in my case, there is an output..... i even tried changing the device uri by replacing ccp with parallel but with no success
what should i do now?
thanks in advance :) :)

---

### Post by 94ostry on 2012-11-26
Hello :) I have the same problem with Ubuntu 12.04 64 bit and Canon LBP 2900. Do you found any solution for this problem? Thank you for answer :)

---

### Post by pdc on 2012-11-27
can you please start a new thread: the forum moderators will say you should

.........meanwhile..............

have a careful read at post #2

[http://ubuntuforums.org/showthread.php?p=12332260#post12332260](http://ubuntuforums.org/showthread.php?p=12332260#post12332260)

........ and after doing it, start a new thread telling us how you are doing..

---

### Post by wildmanne39 on 2012-11-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

