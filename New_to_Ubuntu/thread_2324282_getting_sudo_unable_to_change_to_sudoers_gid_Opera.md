---
title: "getting sudo: unable to change to sudoers gid: Operation not permitted"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by Megh_Tripathy on 2016-05-12
Hi,

I moved /home directory to /home.bak and restarted machine, since then I am unable to login to the account.
when I log in using guest user log in and trying to 

mv /home.bak /home I am getting  the below error

sudo: unable to change to sudoers gid: Operation not permitted

Please suggest the solution.

Thanks,
Megh

---

### Post by sotiris2 on 2016-05-12
Instead of loggin in as guest (who can't use sudo) can you switch to tty1 via alt+ctrl+F1 and login there as your normal user? It should work even though you don't have a home folder and you can use the command to move home back.

---

### Post by yetimon_64 on 2016-05-12
> **sotiris2 said:**
> Instead of loggin in as guest (who can't use sudo) can you switch to tty1 via alt+ctrl+F1 and login there as your normal user? It should work even though you don't have a home folder and you can use the command to move home back.  The tty log in may still need a working home folder, the prompt there defaults to the users home folder. **If** it fails as well there, a root recovery prompt may be needed. The home folder for root will not have been affected by moving the home folder, it is at /root not /home like the user account.  

@ OP, try out a tty terminal first, but if you can't get a log in there go to the advanced menu of the grub boot screen, boot a recovery kernel and drop to a root prompt from the menu system it loads. 
Take care what you do on the root prompt, it is easy to trash an install if you aren't careful. The root account defaults to /root for its home not the /home folder like a normal user. You don't need to use the sudo command at all from the root prompt on the recovery panel when issuing mv commands etc. I just hope the tty terminal does work, use a recovery root prompt only as a last resort in such circumstances.

---

