---
title: "PPA Question?"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by newbietwo on 2014-02-18
In general, should you remove PPA after installing something?  Or, is it best to leave in source list to maintain updates?

Thank you.

---

### Post by robin7 on 2014-02-18
I think it depends on what you installed using the PPA.  For instance if you used a PPA to install Xfce 4.10 in your Xubuntu 12.04, you'll probably want to keep it until / unless Xfce 4.10 reaches the Ubuntu 12.04 repositories.  You'll know when you get an "error" message about duplicate packages.  When you upgrade from 12.04, you find the newest version of Xfce already in the Ubuntu repositories so you can lose the "extra" PPA.

I like the Seamonkey browser, and it's not in the Ubuntu repositories, so I added the Ubuntuzilla PPA to install my favorite browser.  I'll keep Ubuntuzilla in my sources list to keep Seamonkey up to date, and Seamonkey is not offered in the Ubuntu repositories.

---

### Post by monkeybrain20122 on 2014-02-18
It depends. If it is an one off thing which you don't expect any upgrade then it doesn't matter. Sometimes you may just want to install a latest version of foo and foo is generally slow in upgrade. But if you expect upgrade then obviously you need to keep the ppa around.

Another thing to consider is that some dependencies may get pumped up,  if you remove the ppa you may run into conflicts with future normal upgrades and software install which would be hard to resolve, the error message would be something like "unmet dependencies: need to install libfoo.xxx.x but it is not going to be installed (since libbar version xxx.x+n is already installed from ppa and versions of libfoo and libbar have to match) Usually to fix this kind of problems you would simply need to reactivate the ppa so it can fetch a matching version of libfoo from the ppa (of course you can also purge the ppa, but assuming you want to keep what has already been installed/upgraded) If the ppa is removed and you don't remember which one (so you can add it back) you would have a hard time fixing the problem.

So I would just disable the ppa instead of removing it if I don't need it at the moment. In software source simply go to "Other Software" and uncheck the ppa's check box.

---

### Post by newbietwo on 2014-02-18
Thanks for your help.

Appreciate the feedback.

---

