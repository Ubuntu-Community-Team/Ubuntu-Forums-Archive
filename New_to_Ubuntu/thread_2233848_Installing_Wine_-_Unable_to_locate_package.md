---
title: "Installing Wine - Unable to locate package"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by shalom3 on 2014-07-11
when i use terminal to install wine (to use windows programs) i get an error message

**E: unable to locate package wine**

how to fix this? please refer to the screen shot too.
thank you

---

### Post by deadflowr on 2014-07-11
What does
```
sudo apt-get update
```
say?

---

### Post by shalom3 on 2014-07-11
screen shot attached.

i have disabled automatic updates. does that have anything to do with it ?

---

### Post by ian-weisser on 2014-07-11
apt-get thinks another package manager is running.
You can run only one package manager at a time.
Quit the others before you run an apt-get command.

After the others are closed, run **sudo apt-get update** again.

Please cut-and-paste terminal output, and use [code] tags, instead of screenshots.
Screenshots make it harder for us to help you.

---

### Post by ibjsb4 on 2014-07-11
That usually means that you have another package manager open, like maybe the software center.  You can use only one PM at a time.

If this is not the case, you can remove the lock.
```
sudo rm /var/lib/dpkg/lock
```

Edit:  should of updated this post before I replied :)

---

### Post by grahammechanical on 2014-07-11
I do not think that you are using the correct method to install Wine. We should install Wine through the software centre. That will bring us the latest stable version. But if we want the latest, Beta version we install a PPA first. This is how the Wine developers say we should install wine.

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

If we click on the link to install the older, stable Wine 1.6 version it will open the Ubuntu Software Centre right at the Wine Windows Program Loader page with an Install button.

Regards.

---

### Post by sotiris2 on 2014-07-11
There's nothing wrong with this method apart from the fact that he is also using another package installer at the same time. Both methods will install the exact same version of wine unless he messes with the repositories. This method is included in the winehq page as well.

---

### Post by shalom3 on 2014-07-11
thank you. I made it

---

