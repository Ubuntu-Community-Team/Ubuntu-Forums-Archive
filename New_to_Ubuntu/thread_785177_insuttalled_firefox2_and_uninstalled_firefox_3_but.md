---
title: "insuttalled firefox2 and uninstalled firefox 3 but"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by singetak on 2008-05-07
I have a problem with adding Addons the browser says that there is an unexpected error in the installation
Any idea.

---

### Post by Biggy on 2008-05-07
go to synaptic manager and mark for complete removal firefox3 and mark for install firefox2. ( remove from application > internet firefox3 icon)

---

### Post by singetak on 2008-05-07
still the same problem

---

### Post by Biggy on 2008-05-07
uninstall firefox2 + 3 and remove firefox folder from your system.

install firefox2 from applications > add/remove or synaptic package

---

### Post by rjmoerland on 2008-05-07
This link could be of help:[http://ubuntuforums.org/showpost.php?p=4745743&postcount=1]("http://ubuntuforums.org/showpost.php?p=4745743&postcount=1")

---

### Post by Biggy on 2008-05-07
from terminal :

> sudo apt-get purge firefox
sudo rm -r ~/.mozilla
sudo apt-get install firefox-2

---

### Post by singetak on 2008-05-07
Thanks for the help.i Solved it.just deleted the .mozilla folder from my user

---

