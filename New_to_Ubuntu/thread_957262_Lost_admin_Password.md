---
title: "Lost admin Password"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by equanimous1 on 2008-10-24
Hi 
Ok, I know its a classic, I have forgotten my admin password for Ubuntu, any way to recover or reset , without a reinstall ?

Regards
Paul

---

### Post by eternalnewbee on 2008-10-24
Take a look here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
( Tip from Iaculallad )

---

### Post by melojo on 2008-10-24
You could boot from live CD and edit your /etc/sudoers config file to add your user to the sudoers list. Then boot again from hard drive and try to set new root password.
You can also use chroot when booted from live CD and change you root password.
The third way is to edit directly the /etc/shadow file when booted from live CD and set the same password for root the same as your user has or delete the password for root.

I think the most comfortable is boot from live CD, mount the root partition from hard drive for example to /mnt/disc and use "chroot /mnt/disc" and then "passwd" and change your root password. Tha last step is reboot. I would do it like this;)

---

### Post by starcannon on 2008-10-24
+1 to [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
I have successfully used that guide.

---

