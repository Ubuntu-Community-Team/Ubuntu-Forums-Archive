---
title: "Unable to fix broken packages"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by lolwhites on 2008-05-08
The update manager tells me I have 20 updates to install. However, when I try, I get the message:
> 
Could not apply changes!
Fix broken packages first.

I've tried doing this through Synaptic, every time it tells me it's fixed any dependency problems, yet I still get the same message from the update manager.

---

### Post by phidia on 2008-05-08
Maybe logging out and back in again will clear that.
If not a reboot is worth a try too, and refreshing synaptic also.

---

### Post by lolwhites on 2008-05-08
Afraid not. Have logged out and in, rebooted and refreshed Synaptic, allto no avail. I did manage to install 9 of the 20 though.

---

### Post by drs305 on 2008-05-08
In synaptic, if you click on the Custom Filters tab (lower left) there is a filter for Broken packages. Can you determine which one(s) are creating the problem by looking there, and if so, omitting them during the update?

---

### Post by lolwhites on 2008-05-08
Synaptic seems to think there aren't any broken packages that need fixing, but through trail and error I've managed to get all but two of the updates.

Now a new problem has emerged: Update manager has found even more updates, but doesn't install them. When I click on "Install Updates" it just reads the package information and goes back to the start without installing anything. I tried doing it in a terminal with apt-get update apt-get upgrade and just got a stack of 404 errors and "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

---

### Post by unutbu on 2008-05-08
Edit: It appears others have had the same problem:

[http://osdir.com/ml/agnula.general/2005-07/msg00224.html](http://osdir.com/ml/agnula.general/2005-07/msg00224.html)
[http://ubuntuforums.org/showthread.php?t=212101](http://ubuntuforums.org/showthread.php?t=212101)

According to those posts the problem is on the server side. The problem seems to go away if you wait, or maybe try a different repository mirror.

---

### Post by lolwhites on 2008-05-10
I tried a different mirror, which seemed to resolve the issue, but it's copme back. I can only update via the terminal and the "broken packages" that refuse to update are the same. They are all libqt-4-something.

---

### Post by Xiong Chiamiov on 2008-05-10
The qt4 packages just came out today - at least in the mass of repos I've got enabled.
Try
```

sudo aptitude -f

```

---

### Post by lolwhites on 2008-05-10
Cheers, aptitude seems to have done the trick!

---

### Post by Xiong Chiamiov on 2008-05-10
I'm sure you can do it with apt-get as well, but after reading [this]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/") today, I'm thinking of switching to using aptitude instead.

---

### Post by zvacet on 2008-05-10
```
sudo apt-get update && sudo apt-get upgrade
```

You should see broken packages listed.Try to fix them manualy with 

```
sudo dpkg --configure package_name
```

or 

```
sudo apt-get -f package_name
```

---

### Post by RealG187 on 2008-09-25
I am trying to install Samba on 8.04 and get that message.

Synaptics reports no broken packages and I tried
```
sudo apt-get autoremove
```

---

