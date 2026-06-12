---
title: "uninstalling wine"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by srharri9 on 2012-03-19
I'm looking to uninstall wine to install 1.4.  I tried this command:

sudo apt-get remove wine

But it says that I don't have wine installed.  I don't recall how I installed it.  

So, first of all, how might I go about uninstalling it?  Or, can I update it from 1.3 to 1.4 without going through this trouble?

---

### Post by Bucky Ball on 2012-03-19
Try looking:

[http://au.search.yahoo.com/yhs/search?p=uninstall+wine+ubuntu&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=uninstall+wine+ubuntu&fr=altavista&fr2=sfp&iscqry=)

Wine uninstall is not easy and leaves bits lying about. Generally, don't bother. If you're not using it isn't making any difference.

> I'm looking to uninstall wine to install 1.4. Uninstall Wine to install Wine version 1.4, you mean? If so can't you just upgrade it?

[http://au.search.yahoo.com/yhs/search?p=upgrade+wine+ubuntu&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=upgrade+wine+ubuntu&fr=altavista&fr2=sfp&iscqry=)

---

### Post by srharri9 on 2012-03-19
I don't know, can I?  I do intend to uninstall 1.3 and install 1.4.  I don't know how to just upgrade.  I am brand new to Linux, and I'm still trying to figure all this out.

Thanks for any help.

---

### Post by Bucky Ball on 2012-03-19
> **srharri9 said:**
> I don't know, can I? ...  I don't know how to just upgrade. 

That's why I provided the link at the bottom of my last post. Look there.

---

### Post by srharri9 on 2012-03-19
Haha, whoops!  I completely missed that.  Thanks a bunch!

---

### Post by critin on 2012-03-19
> **srharri9 said:**
> I don't know, can I?  I do intend to uninstall 1.3 and install 1.4.  I don't know how to just upgrade.  I am brand new to Linux, and I'm still trying to figure all this out.

Thanks for any help.

If you don't have Synaptic Package Manager installed, go to the Software Center and install it.  After installing  find it under the Administration/System menu depending on your version of ubuntu.  Get acquainted with all the tools it offers to Install and Uninstall apps.  It really comes in handy.  It should pick up most of the pieces when uninstalling, and will find all the extra dependencies when installing something.

Spending time there is not being wasted.

---

### Post by srharri9 on 2012-03-19
Cool, I'll check that out.

---

### Post by Bucky Ball on 2012-03-19
Your other option is via the terminal (if your comfy with that). Open a terminal and paste in these commands one at a time:

```
sudo apt-get update
sudo apt-get upgrade
```

The upgrade command will NOT upgrade your release but will upgrade any packages you have installed that need to be upgraded. ;)

---

### Post by sleash78 on 2012-03-20
sudo apt-get purge wine && sudo apt-get --yes autoremove ; sudo apt-get --yes autoclean

---

### Post by sleash78 on 2012-03-20
if you're having problems you can try something like this mv .wine .wine_old

---

