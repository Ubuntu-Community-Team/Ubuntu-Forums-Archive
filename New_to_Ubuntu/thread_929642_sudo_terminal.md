---
title: "sudo terminal"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by ja660k on 2008-09-25
hey guys, 
i'm using Eterm... if that makes a difference

my problem is im working in var/www/ directory and everytime i want to edit somehting i need to write sudo vim, or sudo gedit... 

and most of the time i forget to do sudo and its quite annoying, is there a way i can make the terminal admin, so everything i open is admin...?

---

### Post by eeeandrew on 2008-09-25
> sudo -s

will temporarily log you in as root. every command you give after that will be sudo'd. you should note that the terminal header changes from username@computer to root@computer. after your finished you need to exit twice.

hope this helps,
Andrew

---

### Post by Nepherte on 2008-09-25
To become root in a terminal:
```
sudo -i
```
Don't forget to switch back to normal user when you're finished.

---

### Post by ja660k on 2008-09-25
thanks, they both work fine
but...
> after your finished you need to exit twice.

how do you mean... exit twice?


and uhh how would i switch back to normal mode when im finished?

---

### Post by kpkeerthi on 2008-09-25
Type exit <enter>
And then exit <enter>

or <Ctrl> + D twice

---

### Post by WWSmith36 on 2008-09-25
Another option might be use natilus as root and just double click to edit

```
gksu nautilus
```

---

### Post by ja660k on 2008-09-25
oh right.... derr
thanks :)

---

### Post by eeeandrew on 2008-09-25
Should that not be

> gksudo nautilus

this should give you a browser logged in as root so you should be able to navigate through the directories in a GUI.

hope this helps,
andrew

---

### Post by eentonig on 2008-09-25
There's another, smarter one might say, way to achieve the same goal. And in my personal opinion, less likely to allow you to screw your system by accident.

If you need to change those files in /var/www/ that often, give yourself the permissions to do so.

Most likely, they are all owned by the user "www-data" (and some by root by now)

First things first.

Make sure all files are owned by www-data again (verify if ww-data is indeed your apache2 user)
> chown -cR www-data:www-data *

Then add yourself to the group www-data
> usermod -a -G www-data ja660k

This way, you don't need root privileges to change those files.

---

### Post by ja660k on 2008-09-25
oh that works good =D 

i use the cmd at uni alot and its becoming faster and faster to use 
just still have alot to learn 

thanks alot guys

---

