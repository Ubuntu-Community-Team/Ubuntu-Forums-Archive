---
title: "A couple error codes"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by raker t on 2008-06-04
What can I do about the following error messages? I'm thinking that I need to be in the directory where the package is that I was trying to install?
 What about the second one?
There's a reason I'm on this forum, I need every_little_thing spelled out. Thanks in advance.
 These error messages are showing up when I open synaptic package manager. I'm using V 7.04 Feisty.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Maestro23 on 2008-06-04
Try what it says first. In a terminal:

> sudo dpkg --configure -a

---

### Post by rraj.be on 2008-06-04
just open terminal from applications-->accesories-->terminal and then type

```
sudo dpkg --configure -a
```

it will sak for your password.

enter it and it will clear everything
then you can install anything

---

### Post by lisati on 2008-06-04
Go to the terminal (in Ubuntu, it's on the Applications->Accessories menu) and type:
```
sudo dpkg --configure -a
```
You will be asked for your password - type in the one you used for login. Don't worry if the password doesn't show on the screen, it will still be recognized.
Then when the command has done its stuff, try your installation again. Let us know how you get on!

---

### Post by raker t on 2008-06-04
I guess I didn't try sudo first...I'll reboot into the other HDD and see what happens. This is just a little part of going round and round trying to install an external modem that said Linux compatible. I'll come back with that bucket of sweat and tears a little at a time, but you guys are great, thanks again.

---

### Post by raker t on 2008-06-04
That was it! Thanks.

---

### Post by Maestro23 on 2008-06-04
Good deal man.

---

### Post by rraj.be on 2008-06-04
If solved mark it solved.

Just you can see at the top as

```
Thread tools
```

Click on it and select 

```
Mark this thread as solved
```

---

