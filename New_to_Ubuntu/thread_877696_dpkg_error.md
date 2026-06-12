---
title: "dpkg error"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by simonlugi on 2008-08-02
When I try and open Synaptic I get the following error message

E:dpkg was interrupted, you must manually run 'dpkg-configure-a' to correct the problem
E:-cach->open() failed, please report

Can someone in simple instruction tell me what I need to do.
Simon

---

### Post by cpetercarter on 2008-08-02
Open a terminal and enter:
```
sudo dpkg --configure -a
```
Enter your password at the prompt.

---

### Post by simonlugi on 2008-08-02
Thanks
I get an error saying that I have one broken filter.
Can you let men know what to do next

---

### Post by iaculallad on 2008-08-02
> **simonlugi said:**
> Thanks
I get an error saying that I have one broken filter.
Can you let men know what to do next

Try fixing it with:

```
sudo apt-get install -f
```

or if that fails, try the other option below:

Navigate to System->Administration->Synaptics Package Manager, click on the "Edit" menu and select "Fix Broken Packages".

---

### Post by simonlugi on 2008-08-02
Thanks the first suggestion appears to have worked.
Thanks Simon

---

### Post by MofroShow on 2008-08-08
This helped me alot also. Thanks alot.
Mofro

---

### Post by meitetsuman on 2008-08-10
I was trying to install java and I got the same error message. 

E:dpkg was interrupted, you must manually run 'dpkg-configure-a' to correct the problem
E:-cach->open() failed, please report

 I tried:

owner@owner-desktop:~$ sudo dpkg --configure -a
[sudo] password for owner: 
dpkg: status database area is locked by another process

Any suggestions?

---

### Post by Joeb454 on 2008-08-10
Close all package managers etc. you have running.

For example Synaptic or Add/Remove etc. And then try again

---

### Post by Joeb454 on 2008-08-10
Close all package managers etc. you have running.

For example Synaptic or Add/Remove etc. And then try again

---

### Post by meitetsuman on 2008-08-10
And then:

owner@owner-desktop:~$ sudo apt-get install -f
[sudo] password for owner: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by meitetsuman on 2008-08-11
Thanks for the tip!  Forgot to mention, I didn't see anything open, so I restarted the computer and tried again, and then it worked.

---

