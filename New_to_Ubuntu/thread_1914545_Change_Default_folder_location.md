---
title: "Change Default folder location"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by DrGreenBean on 2012-01-24
Hi
 I want to change my Documents and Picture folder from /home/cp/Documents to a mapped drive I created. /media/data/Users/CP/Documents and /media/data/Users/Pictures. The map works fine.
 

 I have tried editing the *user-dirs.dirs with XDG_DOCUMENTS_DIR="$HOME/media/data/Users/CP/Documents" save it close it and then run “killall nautilus” no change to the folder location*
 

 *I also tried it with Ubuntu Tweak. I am running Ubuntu 11.04, Unity is off and using Gnome*
 

 *The files are located on a Windows server, I want to move from Windows to Linux so starting by switching from Win 7 to Ubuntu*
[I]Thanks
[/I]

---

### Post by Cheesemill on 2012-01-24
First delete the directory's that you have created at /home/cp/Documents and /home/cp/Pictures (making sure that any contents have been backed up).

Then create a couple of symlinks:
```
ln -s /media/data/Users/CP/Documents /home/cp/Documents
ln -s /media/data/Users/Pictures /home/cp/Pictures
```Take a look at:
```
man ln
```for more info.

---

### Post by Double.J on 2012-01-24
Hi there, you could create a softlink?

```

ln -s /path/to/destination /path/to/current/directory.
```

For example - say I wanted to link my pictures directory, to my My Pictures directory on /media:
```

ln -s /media/My\ Pictures /Pictures
``` If im in my home directory. 

Hope it helps. type
> 
man ln
 for more info ;) 

(BTW ln is lowwer case LN)

---

### Post by Double.J on 2012-01-24
> **Cheesemill said:**
> First delete the directory's that you have created at /home/cp/Documents and /home/cp/Pictures (making sure that any contents have been backed up).

Then create a couple of symlinks:
```
ln -s /media/data/Users/CP/Documents /home/cp/Documents
ln -s /media/data/Users/CP/Pictures /home/cp/Pictures
```

Take a look at:
```
man ln
```
for more info.

beet me to it ;)

---

### Post by DrGreenBean on 2012-01-25
Cool it seems to have worked for Documents Thanks
I struggled with doing the My Pictures and My Documents then found the I had to do My\ Pictures

So its not like Windows where you would change the location of the My Documents folder

---

