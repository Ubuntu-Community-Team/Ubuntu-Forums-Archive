---
title: "trouble updating 8.04"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by harryliddic on 2008-05-03
I am having trouble updating to Hardy 8.04. I follow all the steps of the Update Manager, a pop-up comes up and runs the package manager then it sits there over night in some cases with the saying " checking package". I have tried to load kubuntu thru adept manager but it says I need administrative permission which I have but it never gives me a chance to enter it. I have downloaded both versions to disk but read somewhere that you need more than 256 RAM which I don't have. Is this hanging because of a busy server?

---

### Post by MongooseCage on 2008-05-03
Yes, quite likely, however you might want to try upgrading your RAM, or simply do a fresh install. Usually fresh installs do better than upgrades. You also might want to try to use Xubuntu because your RAM is just about sufficient and doesn't allow much flexibility on Ubuntu.

---

### Post by harryliddic on 2008-05-03
I am going to increase RAM in a few months but since I have RAMBUS memory it cost much more. Is there a queue on the server? Is it to my advantage to leave the distribution manager up and running?

---

### Post by Dazed_75 on 2008-05-03
System requirements for Ubuntu Hardy Heron call for a minimum of 384MB of RAM for desktop CDs and 256MB for other install methods.  In other words, your 256 is the bare minimum and you likely have less if your system uses some of that as video ram.

You best bet would be to add RAM to the computer and it is extremely cheap to do if you do it yourself.  As an alternative, you could try xubuntu as it truly is intended for older computers with fewer resources.  I believe it can be installed on systems with 128MB.

As to the update manager saying you need admin priviledge I can only guess that you did not start it with such priviledge or that it ran a long time before checking the need because of doing a LOT of swapping to disk (due to only 256MB) and you ran past the time sudo remembered that you had such privilege.  I may be way off on this speculation, but if so I hope somone corrects me.

---

### Post by richbl on 2008-05-03
There is clearly some issue here, and it's not hardware-related.

I'm running a 2 GB core 2 duo box, and am currently running into some locking issues when attempting to access repos, either through Update Manager or Synaptic Package Manager.

On cli, I'm getting an "unable to resolve host ubuntu" error message when attempting a "sudo apt-get update", so it appears to be config-related.

Oddly, on occasion, I seem to have no problems whatsoever...

Initially, I suspected laggy servers, and I'm not convinced yet that isn't the issue, but clearly it is not related to minimal hardware requirements.

I'll provide more info when I find out more.

Best of luck.

---

### Post by richbl on 2008-05-03
> **richbl said:**
> There is clearly some issue here, and it's not hardware-related.

I'm running a 2 GB core 2 duo box, and am currently running into some locking issues when attempting to access repos, either through Update Manager or Synaptic Package Manager.

On cli, I'm getting an "unable to resolve host ubuntu" error message when attempting a "sudo apt-get update", so it appears to be config-related.

Oddly, on occasion, I seem to have no problems whatsoever...

Initially, I suspected laggy servers, and I'm not convinced yet that isn't the issue, but clearly it is not related to minimal hardware requirements.

I'll provide more info when I find out more.

Best of luck.

The issue turns out to be the result of some corruption in the hosts file (/etc/hosts).

Please see this thread for further details:

[http://ubuntuforums.org/showthread.php?t=779589&referrerid=23192](http://ubuntuforums.org/showthread.php?t=779589&referrerid=23192)

Best of luck.

---

### Post by richbl on 2008-05-04
> **richbl said:**
> The issue turns out to be the result of some corruption in the hosts file (/etc/hosts).

Please see this thread for further details:

[http://ubuntuforums.org/showthread.php?t=779589&referrerid=23192](http://ubuntuforums.org/showthread.php?t=779589&referrerid=23192)

Best of luck.

Well, after editing the errant host entry, as prescribed in the thread above, I've noticed that it's back (the 127.0.1.1 entry).

I've gone ahead and added my own machine's local ip address (not localhost) and alias, and I haven't yet had any problems with synaptic/update issues, so that appears to have solved the issue once and for all.

If anyone can shed any additional light on this situation, I'd be very interested in knowing more.

For completeness, my Hardy Heron install was a clean install.

---

