---
title: "Web Development and testing - Advice"
date: 2010-10-02
forum: Programming Talk
---

### Post by MaxVK on 2010-10-02
I'm a web developer working heavily with PHP and Javascript. Currently when testing I use a combination of browsers (Firefox, Chrome and Opera), and then reboot into an old XP installation to test with the ancient IE (version 6 something I think), or copy to a USB stick and copy across to a Vista laptop for a slightly more up to date IE test.

In all cases I have Xampp installed so I can run files locally.

Problem: Testing IE is becoming an increasing pain as new CSS and Javascript that works in everything else, fails dramatically in IE, and I am reaching the stage where I am considering moving my entire web development across to a Windows machine just so I can work more quickly. (After all, I can test ALL browsers in the same place then)

Iv considered using a VM of some nature to run Windows within Ubuntu and allow for testing but I'm not sure how Xampp would respond in such a case.

Id like any advice you'd like to give on this subject because I *really* have no desire to work in a Windows environment again (shudder).

Some things Iv been wondering:
* Would a VM work well?

* Is it possible to copy files across from my Ubuntu desktop to the VM?
(and if so does this work 'Live' - so I can edit a file, copy or transfer, then change to the VM and test?)

* Does anyone know if Xampp would be comfortable in a VM?

* Would it be better to just develop in Windows?

* Would it be better to develop in a Windows VM?

Any help would be much appreciated

Cheers

Max

---

### Post by Some Penguin on 2010-10-02
Hmm.  Have you tried running IE under Wine?

[http://appdb.winehq.org/appview.php?versionId=469]("http://appdb.winehq.org/appview.php?versionId=469")

If it works for you (and judging from the comments, I'm not entirely sure that it will...) it might save you some hassle.

---

### Post by SeijiSensei on 2010-10-02
You could use VirtualBox to create a virtual machine in Ubuntu then install Windows to it.  You'll need a valid license key, though.

I always install the proprietary version of VirtualBox from [s]Sun[/s], oops I meant Oracle.  Follow the instructions [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), and it should work for you.

---

### Post by worseisworser on 2010-10-02
Err, just continue to develop on Linux then use Windows+IE under VirtualBox to test the stuff running on your Linux server.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Just set networking to "bridge" when creating your VM; Windows running will just show as another machine on your local network then it can access your web-app on your Linux server.

---

### Post by worseisworser on 2010-10-02
Right hand side is Linux stuff; a Chrome window showing my active machines on my local network and another Chrome window showing my web server running on the same Linux machine (localhost; LAN IP is 192.168.1.111).
Left hand side is a window containing a Windows XP instance under VirtualBox under the same Linux machine.

192.168.1.102 is Windows running under VirtualBox on my Linux machine.
..and again 192.168.1.111 is my Linux machine.

[IMG]http://static.nostdal.org/~lnostdal/always-here/virtualbox-for-testing-in-ie-1.png[/IMG]

WinXP VM set to bridge mode:
[img]http://static.nostdal.org/~lnostdal/always-here/virtualbox-for-testing-in-ie-2.png[/img]

---

### Post by MaxVK on 2010-10-02
Hmm thanks people. Iv considered using WINE, but there seem to be far too many problems to make it viable.

It looks like the VM is the first way to go. I have copies of XP and Vista from other machine so disks and keys are no problem and since if the VM can connect to/share with localhost I don't mind if its sluggish.

Ill take a look and see how things go.

Cheers

Max

---

