---
title: "Can't log in as root in hardy???!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dresman on 2008-04-30
I just switched to 8.04 and it doesn't seem that I can log in as root from the login screen.  I don't know how else to log in as root which is a big problem for me.

---

### Post by V-600 on 2008-04-30
What distro were you using before. I have missed out a few ubuntu releases but you shouldn't need to log in as root as you can use sudo instead.

If you have a lot to do, in a terminal I believe you can use "sudo su" to become root. Not sure how to login as root from gdm though.

---

### Post by scragar on 2008-04-30
that's the way it's supposed to be, ubuntu subscribes to the "sudo" method of gaining root permitions, if you truely need root access you can run```
sudo -i
```or```
sudo su
```to gain temp root perms in a terminal, if you know what to do as root this is the way to do it, if not then you should be using sudo anyway, since root is too powerful to play around with.



EDITED according to post 6's guidelines, I should read manual on it :P

---

### Post by bilal.17 on 2008-04-30
By default you cannot login as root from the login screen, but you can change that. If you want to login as root from the login screen, you can navigate to System->Administration->Login Window, then click on the security tab, and check the box that says Allow system administrator login. That should allow you to login as root.

---

### Post by scragar on 2008-04-30
@ bilal.17 -- read: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

> Policy
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

---

### Post by Joeb454 on 2008-04-30
> **scragar said:**
> if you truely need root access you can run```
sudo -s
```or```
sudo su
```to gain temp root perms in a terminal

Actually using ```
sudo -i
``` is preferable. For reasons I won't bother to explain here (permissions issues basically). Just so you're aware :)

---

### Post by master5o1 on 2008-04-30
Ubuntu has a disabled root system. Instead of using root in the GUI and login in from GDM you just use 'sudo' and 'gksu' or 'kdesu' infront of commands that require root access.

If you require a root session in terminal use 'sudo -i',
if you DO require a 100% root access GUI then I would ctrl+alt+F1 and login there, then do sudo -i there, then type startx.


**UNRECOMMENDED:** If you do want to enable the root account, I believe it is:

```
user@ubuntu:~$ sudo passwd root
Enter new UNIX password: <enter password>
```

---

### Post by bilal.17 on 2008-04-30
> **scragar said:**
> @ bilal.17 -- read: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

I'm sorry, I didnt realize I couldnt do that. Is it possible for a moderator, to remove my post or something simillar along those lines.

---

### Post by aysiu on 2008-04-30
> **bilal.17 said:**
> I'm sorry, I didnt realize I couldnt do that. Is it possible for a moderator, to remove my post or something simillar along those lines.
Done.

---

### Post by scorp123 on 2008-04-30
> **bilal.17 said:**
>  Is it possible for a moderator, to remove my post or something simillar along those lines. You can edit your own postings. Just remove anything that you think should be removed and mark it like that (e.g. by writing "EDIT: " into your posting) so others understand that you did change your post.

---

