---
title: "Ubuntu wants a password to unlock sda5_crypt disk. HELP"
date: 2017-06-09
forum: New to Ubuntu
---

### Post by mor.eckert on 2017-06-09
Hi;

It has been awhile since I installed Ubuntu on my old Dell laptop. I attempted to install the newest version with a complete wipe of my hard drive, but I somehow messed something up. The computer starts up but then goes to a password screen to unlock sda5_cyrpt ****? I have tried every password I can think of. Is there a way to start over? I have attempted to re-install Ubuntu, but had no success. IT continues to go to the password screen. anyone know what I can do before I send it into a shop? 

Thanks

---

### Post by RobGoss on 2017-06-09
Hello and welcome to the forums, Are you saying you forgot the password for this machine which has Ubuntu installed?

---

### Post by deadflowr on 2017-06-09
You've got it set for full-disk-encryption, in which case there is nothing anyone can do to help you to recover the password for it.
Not really sure what you're trying in regards to reinstalling that brings up the same screen.
As a proper reinstall should wipe that out and then allow you to install and boot into a system properly.

---

### Post by mor.eckert on 2017-06-13
I did not set it up for disk encryption when I did a full install. So I am guessing I should just buy a new hard drive and start from scratch?

Thanks

---

### Post by RobGoss on 2017-06-13
If you are trying to just Install Ubuntu on this hard drive as a stand alone OS you should be able to boot from a **USB** or **DVD** with the Ubuntu ISO file and choose to use the **entire disk **for your installation. I my self have never used encryption so I'm not much help with that

---

### Post by deadflowr on 2017-06-13
Double checking it seems that it's the /dev/sda5 partition, which normally would be the swap partition, in which case it's possible that it an encrypted swap partition.
What you can do is run the installation media and at boot up choose 'Try Ubuntu'.
This will run a live session.
In the live session click on the top icon in the launcher and type 'gparted'
If need be post a screenshot of the layout it shows for the hard drive.

If my assessment is right, you can try the method of disabling it from here:
[https://askubuntu.com/questions/34519/how-to-disable-cryptswap]("https://askubuntu.com/questions/34519/how-to-disable-cryptswap")
(actually passing through that link to this link:
[https://www.logilab.org/blogentry/29155]("https://www.logilab.org/blogentry/29155"))

---

