---
title: "Network Manager 0.7.0 SVN! How to go back to official repository (from third party)"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Kosimo on 2008-07-02
Hello guys, I'm testing Network Manager 0.7 SVN.  It looks great and it have lots of amazing new features.

But my question regards about how to "downgrade"

In order to test this new svn NM-0.7 I had to add a third party repository:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

At the moment I'm gonna keep using it, as it works perfectly and I want to help testing it. 

But, 
How can I go back to my previous state?  If I just remove this repositories, and update/upgrade my system, it'll go back to the official one? Or as this SVN one has a bigger number 0.7.0>0.6.6 (from official hardy repos) then it'll keep using this new one?

Thank you guys!

---

### Post by nowshining on 2008-07-02
remove the repo. update/reload in synaptic or in terminal sudo apt-get update & sudo apt-get clean and ur pw won't show as you type.

Close down any open instances of the Network Manager you are running:

Completely remove the installed one.

close and re-open synaptic - download the one from the ubuntu repos. - logout and backin if needbe.

---

### Post by Kosimo on 2008-07-02
> **nowshining said:**
> remove the repo. update/reload in synaptic or in terminal sudo apt-get update & sudo apt-get clean and ur pw won't show as you type.

Close down any open instances of the Network Manager you are running:

Completely remove the installed one.

close and re-open synaptic - download the one from the ubuntu repos. - logout and backin if needbe.

WoW!!   

It should be a bit easier to stop using some third party specific version and going back to official repos.  

Can't it be used the option (Force Version) from synaptic?

---

### Post by nowshining on 2008-07-02
lol forgot about that one - more than likely yes :P

---

### Post by Kosimo on 2008-07-02
> **nowshining said:**
> lol forgot about that one - more than likely yes :P

lol ! ;)

Thank you anyway for the answer dude

---

### Post by nowshining on 2008-07-02
ur welcome.

---

