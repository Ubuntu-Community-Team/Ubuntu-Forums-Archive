---
title: "[SOLVED] FF3 beta 5 not upgrading"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by SuzanneSmith on 2008-07-02
Hi,

I'm fairly new to Ubuntu, so go easy on me!

My system did the automatic upgrade to Hardy Heron, and with it to FF3b5 - all well and good.

What has not happened though is the upgrade to FF3.0.  I may have messed up the automatic upgrade by downloading it manually, and then not knowing what to do from there.....  

If I open up the applications->add/remove, it has FF ticked.  If I try to uninstall it, it says it can't due to dependencies.  The update manager hasn't mentioned FF3 at all.

I'm a bit stuck on how to get FF3 up and running - any help appreciated!!

Thanks,

Suzanne

---

### Post by eapache on 2008-07-02
In the terminal, type```
firefox
```This will run the firefox version that came with Ubuntu, rather than any you downloaded/installed from the mozilla website.

EDIT -- make sure no other instances of firefox are running when you do this. Go to System->Admin->System Monitor->Processes Tab and make sure there is nothing there named firefox.

If the Help->About menu still says FF3b5, run```
sudo apt-get update
sudo apt-get upgrade
```The first line updates the database of available programs, the second upgrades to the latest version of every program available.

If you still end up with FF3b5, something is peculiar...

---

### Post by SuzanneSmith on 2008-07-02
Thanks for getting back to me.

It would appear that something peculiar is going on then!

I ran ff from the command line, and the version was FF3b5.

I ran the 2 commands to refresh and upgrade.  The upgrade one had nothing to report.  Just to double check, FF still has version 3b5.

Any other ideas are gratefully recieved!!

Suzanne

---

### Post by gandaran on 2008-07-02
check if you have the first two update channels enabled (recommended updates and security updates) in system » administration » applications sources » update tab.

---

### Post by SuzanneSmith on 2008-07-03
Thank you!!!  

The recommended updates option wasn't ticked.  I ticked it and off it went and sorted everything out.  I am now the proud 'owner' of FF3 - thanks!!

Suzanne

---

### Post by eapache on 2008-07-04
Since the thread is solved, please mark it with the "thread tools" menu. 

This lets people with the same problem know that there is a possible solution while searching the forums, and lets people looking to help know that they can skip it.

---

