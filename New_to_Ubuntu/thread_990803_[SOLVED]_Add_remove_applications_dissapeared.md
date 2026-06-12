---
title: "[SOLVED] Add remove applications dissapeared"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by jon555 on 2008-11-23
Under programs there was box Add remove applications, now it's gone. I don't know how it happened, but I want it back.

---

### Post by Michael.Godawski on 2008-11-23
Run the command

```
sudo alacarte
```

Click on Applications on the side bar.

Scroll down to the bottom and check Add/Remove.

---

### Post by Nepherte on 2008-11-23
The prefix sudo isn't necessary and might mess things up in this case.

---

### Post by Michael.Godawski on 2008-11-23
thx Nepherte you are right... 
had long break, correct me so that I get into the Ubuntu flow again :)

---

### Post by Paqman on 2008-11-23
> **jon555 said:**
> Under programs there was box Add remove applications, now it's gone. I don't know how it happened, but I want it back.

Are you using a different account from before? If so, make sure that the account has admin rights. Go to System > Admin > Users & Groups and make sure "administer the system" is checked for that user.

---

### Post by jon555 on 2008-11-24
I used  alacarte, a window opened and I putted a checker in box by add remove programs, but after second it unchecked itself.
And yes, I'm using my default account - jon.
In day before I had this problem I made three changes. 1. forcemounted 1 partition, 2. installed virtualbox and tried to make me a user in virtualbox group or something. 3. Installed accessability futures for reading text aloud. Then after restart I had lost add remove programs.

Now I somehow managed to make add remove program shortcut on desktop. But it doesn't allow me to do anything, says I'm not sudoer. How can I make me sudoer.

---

### Post by jon555 on 2008-11-24
Yesterday it all was OK, but today, I'm not sudouser any more, what to do. I can't add remove programs. Any script with sudo gets turned down. 
jon is not in the sudoers file.  This incident will be reported.
I guess I damaged it while trieing to add me to virtualbox users.  I can't open sudoers file or access users and groups.

---

### Post by aysiu on 2008-11-24
Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by sisco311 on 2008-11-24
Reboot in recovery mode.
In the root shell add your user to the admin group:
```
adduser *your-login-name* admin
```
```
reboot
```

---

### Post by jon555 on 2008-11-24
> **sisco311 said:**
> Reboot in recovery mode.
In the root shell add your user to the admin group:
```
adduser *your-login-name* admin
```
```
reboot
```
It worked! THNX!

---

### Post by jon555 on 2008-11-24
While in recovery mode  command  adduser jon admin   solved everything.

---

