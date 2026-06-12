---
title: "Nothing working in one of my accounts HELP!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by tophatandy on 2008-07-20
Alright, 

so I switched over to Mac, but my mom is now using ubuntu.
She has been using it successfully for several months now (without switching back to windows).

It has been pretty much smooth sailing, until tonight.

My mom told me that she got a "trojan horse" after visiting a churches website.
A "box came up that said that she had been 'attacked' and she clicked 'ok' then boxes started to fly up on the screen that said that nautilus had failed (and a box for several other applications) and gave a more details option, and the more detail option revealed and error to the effect of 

"cannot add client to server list OMG.ORG/CORBA/COMM_FAILURE:1.0"

and the same error multiple times for different applications.

she has no menus, but I have created another account via the repair terminal listed in grub boot up.

she claims that she didn't download anything.

I have tried restarting gdm to no success, and deleting the ~/.gconfd/saved_state and whatnot (which also did not help at all).

What should I do?

-Andy

---

### Post by Dark_Stang on 2008-07-20
Dude... a higher power is angry at you, there is nothing you can do.

Just kidding...

If it was me I'd just make a new account, migrate her files over from the old account, then remove the old account and the old files. That is probably going to be the easiest way.

---

### Post by tophatandy on 2008-07-20
thats what I was considering,

but I just wanted to make sure that there wasn't an easier way first.

---

### Post by Sef on 2008-07-20
Here's one [solution]("http://ubuntuforums.org/archive/index.php/t-93314.html"):

> VanHammersly
January 27th, 2007, 10:30 PM
Hi. For those who come here for future reference, I had the same problem and deleting ~/.gconfd/saved_state and (if it exists) ~/.gconfd/saved_state.tmp fixed the problem.

[More Help]("http://ubuntuforums.org/showthread.php?t=693499")

---

### Post by tophatandy on 2008-07-20
I have tried everything listed in those threads (and the ones linking off of them), but nothing worked. 

thus far, I have set up a new user account, and have given it some of the most basic administrative privileges, is there any way for me to copy everything in the previous accounts home folder into the new accounts home folder?

---

### Post by Dark_Stang on 2008-07-20
The easiest way to do it would be open two windows in nautilus with root priveledges (just run sudo nautilus twice) and drag and drop her files. Then change the ownership of all the files to the new user. To change ownership of all the files at once in the new folder use this command...
```
sudo chown -R /home/newusername newusername
```
change "newusername" to whatever the new username is. Let me know if you get hung up.

---

