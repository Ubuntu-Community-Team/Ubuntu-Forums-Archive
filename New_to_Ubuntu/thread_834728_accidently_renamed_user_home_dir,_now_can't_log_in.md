---
title: "accidently renamed user home dir, now can't log in"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by flowerchild on 2008-06-19
Hi,

can anyone direct me what to do?
I was actually trying to change just my login name & got a bit carried away and changed my directory name (as in changed from /home/smith to /home/bob) to match my new log in name. (yes, I know, not the smartest thing to do).

Anyway so then I re-booted my computer but now of course I can't log in because I can't link to all my files (due to manually changing the name).

I found another post (really old -2006) where someone had done the same but there was no real answer of how to correct this on it.

Any help/links would be really really appreciated.

thanks.

---

### Post by bodhi.zazen on 2008-06-19
boot to recovery mode

You will be at a root shell

mv /home/old_name /home/new_name

chown user.user -R /home/new_name

where new_name == user == you log in name

reboot

(or init 2)

---

### Post by Delever on 2008-06-19
Can you boot from CD? If you can, you could open terminal in cd, type

gksudo nautilus

to get nautilus with full access to file system, and rename them back. That's the most user-friendly way i can think of :)

EDIT: better do how bodhi.zazen said.

---

### Post by tjwoosta on 2008-06-19
either way would work fine (as long as you could acess the filesystem)

---

### Post by flowerchild on 2008-06-19
> **bodhi.zazen said:**
> boot to recovery mode

You will be at a root shell

mv /home/old_name /home/new_name

chown user.user -R /home/new_name

where new_name == user == you log in name

reboot

(or init 2)

Hiya, thanks for your speedy reply. I booted to recovery mode then I typed:
mv /home/smith /home/bob (hit enter)
chown bob.bob -R /home/bob (hit enter)
It told be bob.bob was invalid user. what am I supposed to write for 'user' (did try the actual word user but it didn't work).

Sorry - I feel a bit silly, don't know much bout Ubuntu commands which is probably why I'm not understanding completely.

Thanks for your help

---

### Post by flowerchild on 2008-06-19
> **Delever said:**
> Can you boot from CD? If you can, you could open terminal in cd, type

gksudo nautilus

to get nautilus with full access to file system, and rename them back. That's the most user-friendly way i can think of :)

EDIT: better do how bodhi.zazen said.

Hi, did this but once I got to nautilus couldn't find the file with 'bob' (new name)on it to rename. Could find file with 'smith' (old name) on it but wasn't sure if I was meant to change it to 'bob' of if by doing that I would ruin things more than they already are??

thanks for your help :)

---

### Post by bodhi.zazen on 2008-06-19
flowerchild, did you change your username ? If so, what to ?

use the commands I gave you with your new username ...

Also I outlined "how to" change your user name in this post :

[http://ubuntuforums.org/showpost.php?p=4968235&postcount=3](http://ubuntuforums.org/showpost.php?p=4968235&postcount=3)

There are other helpful posts on that thread as well :twisted:

FYI : you can do all this from a live CD if you like, I find it is just as easy in "recovery mode"

---

### Post by flowerchild on 2008-06-19
> **bodhi.zazen said:**
> flowerchild, did you change your username ? If so, what to ?

use the commands I gave you with your new username ...

Also I outlined "how to" change your user name in this post :

[http://ubuntuforums.org/showpost.php?p=4968235&postcount=3](http://ubuntuforums.org/showpost.php?p=4968235&postcount=3)

There are other helpful posts on that thread as well :twisted:

FYI : you can do all this from a live CD if you like, I find it is just as easy in "recovery mode"

Hi, yeah - changed user name from smith to bob. then looked in the other tabs and changed the directory from /home/bob to /home/smith. So I'm not really trying to change my actual user name back (I don't think) just trying to make it so I can actually start up the computer normally so thought all I had to do was just correct the directory.

As I said before, I know next to nothing about all this stuff. If I can't fix it I think I'll just wipe everything and reinstall ubuntu..

ta for your replies

---

### Post by tjwoosta on 2008-06-19
> Hi, did this but once I got to nautilus couldn't find the file with 'bob' (new name)on it to rename. Could find file with 'smith' (old name) on it but wasn't sure if I was meant to change it to 'bob' of if by doing that I would ruin things more than they already are??

thanks for your help 

in nautilus you have to go to Computer then to the drive that says blahblah VOLUME (example 67GB VOLUME) that is your ubuntu install

(otherwise you would be looking at the live cd's filesystem, which would explain why you cant see your user directory)

---

### Post by bodhi.zazen on 2008-06-19
> **flowerchild said:**
> Hi, yeah - changed user name from smith to bob. then looked in the other tabs and changed the directory from /home/bob to /home/smith. So I'm not really trying to change my actual user name back (I don't think) just trying to make it so I can actually start up the computer normally so thought all I had to do was just correct the directory.

As I said before, I know next to nothing about all this stuff. If I can't fix it I think I'll just wipe everything and reinstall ubuntu..

ta for your replies

The link I gave you will walk you through how to fix the problem.

If you have trouble feel free to ask, lots of people willing to help.

Be sure to tell us if you are working from recovery mode or from the live CD and what step you need help with.

---

### Post by flowerchild on 2008-06-19
Hi, seem to have managed to change user name over - back to what it was(check with 'id smith' and all the right stuff came up) - but it's not letting me log in at all now saying my username or password is invalid.
I think I give up!!!

---

### Post by bodhi.zazen on 2008-06-20
Hard to say without more information ...

You can always make a new user ... (no need to re-install).

To sort it out you need to look at /etc/passwd /etc/shadow and /etc/group

Make sure your user is listed in those files.

If so -> reboot

you did not mention if you are working from recovery mode or live CD.

---

