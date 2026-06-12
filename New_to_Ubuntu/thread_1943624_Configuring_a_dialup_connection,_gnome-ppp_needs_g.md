---
title: "Configuring a dialup connection, gnome-ppp needs gksudo"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by gigi1234 on 2012-03-19
Hi, I am trying to get an analog modem connection going via gnome-ppp. Works fine if I gksudo, but not if I directly launch the program. How can I fix this issue? It's been awhile since I fooled around with stuff like this and I am a bit rusty. 

Thanks in advance!

---

### Post by varunendra on 2012-03-20
Try adding yourself to the '**dip**' user group.

To see which groups you are currently a member of:
```
groups <your user id>
```
for example:
**groups varun**
where 'varun' is my login user id.

To add yourself to the 'dip' user group :
```
sudo adduser <your user id> dip
```
for example:
**sudo adduser varun dip**


**_PS_:**
To remove a user from a group:
```
sudo deluser <user id> group
```
for example:
**sudo deluser varun dip**

---

### Post by gigi1234 on 2012-12-02
I am still having trouble with this issue. Adding the users did not help. Can anyone help?

---

