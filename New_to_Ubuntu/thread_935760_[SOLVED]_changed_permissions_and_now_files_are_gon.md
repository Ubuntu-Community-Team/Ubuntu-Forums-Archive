---
title: "[SOLVED] changed permissions and now files are gone"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by radiantarchon on 2008-10-02
earlier i had changed permissions to home/(username) to 777 for recovery purposes. (which later i changed to another plan). but then when i logged in it said that others should not have write access to .dmrc and to the home folder. i changed this and then i realized the files in the folder in there such as files in my documents and examples are gone. can i get them back somehow or did they just disappear

---

### Post by radiantarchon on 2008-10-02
bump

---

### Post by rybaxs on 2008-10-02
try Ctrl+H

---

### Post by radiantarchon on 2008-10-02
nope they were not hidden

---

### Post by nothingspecial on 2008-10-02
Type ```
df
``` in the terminal. Does it look like your stuff has gone or that you can`t access it.  

It will give you a percentage of disk space used.

---

### Post by ciaramitaro on 2008-10-02
[http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/](http://www.ubuntuproductivity.com/journal/ubuntu/08/2008/fix-ubuntu-dmrc-permissions-error-on-login/)

this worked for me
for changing permission not recovery of .dmrc my apologizes:oops:

---

### Post by radiantarchon on 2008-10-02
i fixed it using ```
sudo nautilus
``` and then changed all the permissions myself. all the files are back now and everything works fine

---

