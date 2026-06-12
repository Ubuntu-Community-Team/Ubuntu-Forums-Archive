---
title: "Installing Android SDK"
date: 2012-10-12
forum: Programming Talk
---

### Post by unibroker on 2012-10-12
I'm at the installation of the packages stage.  If I install only the most recent package recommended (currently 4.1) will I be able to work on earlier versions of Android (ie., Gingerbread)?

Thanks in advance.

---

### Post by mevun on 2012-10-12
> **unibroker said:**
> I'm at the installation of the packages stage.  If I install only the most recent package recommended (currently 4.1) will I be able to work on earlier versions of Android (ie., Gingerbread)?

Thanks in advance.

Yes, if you do not use features that are only available in 4.1.  There are also compatability libraries whose purpose is to allow a phone running 2.3.3 to use a feature in later releases.  Not everything is compatible and sometimes you have to write your code differently.

OTOH, you can always download older packages even after installation.  How you come up with an app building workflow that works for different targets is up to you in terms of how much code re-use, code repository strategy, etc.

If you're brand-new to Android development, I would suggest not worrying about compatability issues yet.  There's a whole lot of other stuff to learn.

---

### Post by unibroker on 2012-10-12
> **mevun said:**
> If you're brand-new to Android development, I would suggest not worrying about compatability issues yet.  There's a whole lot of other stuff to learn.

Thanks for your response.  That's a fact (the above) I realize but just wanted to start off on the right foot.

---

### Post by unibroker on 2012-10-12
I lost my internet connection while downloading the last package.  I have re-established it and haven't touched anything inside of SDK Manager.  Will it eventually pick up right where it left off?  75% of the package had downloaded by the time the connection was lost.

Update:  I ended up "cancel task", restarted SDK Manager and only had to install the last package again.

---

