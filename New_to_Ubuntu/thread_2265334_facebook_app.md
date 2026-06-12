---
title: "facebook app"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by flex567 on 2015-02-14
Is there an app for ubuntu that shows facebook notifications(new message, friend request...) so you don't have to open a browser and login in facebook. It should probably run in tray.

---

### Post by ajgreeny on 2015-02-14
Maybe the package** friends-facebook** is what you want.

I steer clear of facebook entirely so I don't know what that package does or if it help you.

---

### Post by flex567 on 2015-02-14
after this 
```

sudo apt-get install friends-facebook

```

I get that: 

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by grahammechanical on 2015-02-14
Those errors usually mean that more than one utility/process is trying to use those directories. Is the software centre open? Is software updater running. As far as I know three processes that make changes to /var/lib/dpkg/ and they are apt-get, software centre and software updater. And each one will lock the file to prevent any other process from interfering.

Regards.

---

### Post by bashiergui on 2015-02-14
Looks like there is a third party app that does what you want. [http://www.noobslab.com/2013/07/fb-messenger-and-facebook-applications.html](http://www.noobslab.com/2013/07/fb-messenger-and-facebook-applications.html)

---

### Post by flex567 on 2015-02-14
when I try to install facebook messenger I get after this:

```

sudo apt-get install fbmessenger

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fbmessenger

```

I installed friends-facebook package, but how can I run it now?

---

### Post by newb85 on 2015-02-14
> **flex567 said:**
> when I try to install facebook messenger I get after this:

```

sudo apt-get install fbmessenger

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fbmessenger

```

That would be because the noobslab PPA only has fbmessenger for older releases (it's fbmessenger 0.1.2).  On the other hand, the webupd8 PPA has fbmessenger 0.2.0 available for 14.04.  You can switch with

```

sudo add-apt-repository --remove ppa:noobslab/apps
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install fbmessenger

```

*Note: that first line removes the noobslab PPA.  If you'd rather keep it, you can omit that line.*

---

### Post by flex567 on 2015-02-14
after I run the app I get this message

```

We're sorry, but we can no longer support Facebook Messenger for Windows, and it will stop working on March 3, 2014.

We really appreciate you using Messenger to reach your friends, and we want to make sure you know that you can keep chatting and view all your messages on http://www.facebook.com. Learn more.

```

---

### Post by nerdtron on 2015-02-15
Doesn't the friends app able to connect to facebook? I remember using it on my previous ubuntu 13.10 install.

search the software center for "friends-app" or from the command line:
```
sudo apt-get install friends-app
```

---

### Post by newb85 on 2015-02-15
> **flex567 said:**
> after I run the app I get this message

```

We're sorry, but we can no longer support Facebook Messenger for Windows, and it will stop working on March 3, 2014.

We really appreciate you using Messenger to reach your friends, and we want to make sure you know that you can keep chatting and view all your messages on http://www.facebook.com. Learn more.

```

I see.  I've never used the Messenger app, and the way things are looking, I won't bother starting.

---

### Post by newb85 on 2015-02-15
friends-app is the new Gwibber.  It will connect to Facebook.  Empathy (already installed by default in Ubuntu) will also connect to Facebook.  I don't know exactly what differences exist between their features.

---

### Post by flex567 on 2015-02-20
Gwibber is not actively developed I think and it doesn't have the functionality I need.

---

### Post by newb85 on 2015-02-22
...and Empathy?

---

### Post by flex567 on 2015-03-02
Empathy doesn't work and I think it doesn't have the funcionalities I need.

I don't think there is a facebook notifications app even for windows.

---

