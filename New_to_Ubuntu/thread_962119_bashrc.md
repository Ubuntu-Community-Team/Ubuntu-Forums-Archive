---
title: "bashrc"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by CVS on 2008-10-28
Hi, I was wondering if someone could tell me the purpose of the .bashrc file in /root?  The reason I ask is that I was attempting to change the color of the prompt to reflect root or not and finally succeeded by adding this to the .bashrc file in ~. 

# If I am root, set the prompt to bright red
if [ ${UID} -eq 0 ]; then

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\[\033[01;32m\]\h\[\033[01;37m\]:\[\033[01;36m\]\w\[\033[01;37m\]\$ '

fi

This works as I wanted, just changes the user name 'root' to red.

Any changes I made to the /root/.bashrc did not seem to have any effect.  Just curious.  Thanks,

---

### Post by redmk2 on 2008-10-29
The .bashrc file is read when the shell is invoked by a user.  When you (not root) login it reads the ~/.bashrc.  When you sudo or su you do not change the shell only the UID so the /root/.bashrc is not read.

---

