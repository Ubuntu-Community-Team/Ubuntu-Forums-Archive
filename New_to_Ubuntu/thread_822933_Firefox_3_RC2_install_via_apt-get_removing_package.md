---
title: "Firefox 3 RC2 install via apt-get removing packages"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ThreeLies on 2008-06-08
Hello,

I just have a fresh install of Ubuntu 8.04 which comes with Firefox 3b5. The default package lists don't have the newest update Firefox 3 RC2 so I was able to find this page... [http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/)

After adding that source to the sources.list and doing "sudo apt-get update" and "sudo apt-get dist-upgrade". It says...
```
The following packages will be REMOVED:
  gnome-user-guide ubuntu-desktop ubuntu-docs yelp
```

Was wondering why it is removing all userguides and Ubuntu desktop? I didn't go through with it cause I am not sure if its gonna screw up my desktop.

---

### Post by Tom--d on 2008-06-08
Just enable the postponed updates and firefox will be updated.

System > Admin > Software sources > Updates > enable the postponed updates

---

### Post by knavarathna92 on 2008-06-08
I had this problem with RC1, what I did was delete the repo they gave from my sources, unistall firefox 3 and forced the beta 5 version of xulrunner 1.9 using the package menu in synaptic, then reinstaled firefox 3 to get back to beta.  I ended up hating the beta again and installing swiftweasel, which is much more friendly and up to 3.0 RC1 with RC2 under construction as we speak.  Hope this helps :-)

---

### Post by ThreeLies on 2008-06-08
Thank you for giving me the advice for using postponed updates. Sure enough new Firefox 3 is in there and many others.

---

### Post by Sef on 2008-06-08
> Just enable the postponed updates and firefox will be updated.

That is not quite correct.  It is proposed updates. They are updates that are not considered stable enough for the regular updates.  I have been using it, and so far, I have not had any problems with the proposed updates.  Firefox is RC1 there.

---

### Post by ThreeLies on 2008-06-08
> **Sef said:**
> That is not quite correct.  It is proposed updates. They are updates that are not considered stable enough for the regular updates.  I have been using it, and so far, I have not had any problems with the proposed updates.  Firefox is RC1 there.

Could you use the standard Firefox Check for Updates to update it to R2? I tried that with the current version and says No update.

---

### Post by krang on 2008-06-09
the check updates within the firefox is not working and as been said above: with the proposed updates I just can get RC1...
any other suggestion?

---

