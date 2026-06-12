---
title: "How do I remove User Account?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by opm595 on 2008-11-28
Hi Guys,
I created a new user on Unbuntu earlier via [System / Administration / Users and Groups ] etc, and now no longer want it on my system. I've deleted the access from another user account (via users & groups) but I really wish to delete the whole profile from my system. I'm guessing Terminal and Sudo something right? Any takers?
Thanx in advance,
Rob

---

### Post by Dj Melik on 2008-11-28
sudo userdel -r <nameofuser>

---

### Post by doas777 on 2008-11-28
check out this thread: [http://ubuntuforums.org/showthread.php?t=358403](http://ubuntuforums.org/showthread.php?t=358403)
it should answer your question. the instructions given are terminal commands. 

you can also delete a user in the System -> Administration -> Users and groups GUI. 

either way, if after removal the user home directory still exists (it's at /home/<username>) by default. you can remove it by hitting alt + F2, and entering ```
gksu nautilus
```. then just go to /home and delete the folder. be careful though; gksu is like sudo, and gives you the ability to do potentially dangerous things in that shell.

good luck,
franklin

---

