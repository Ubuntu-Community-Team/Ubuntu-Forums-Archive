---
title: "help with user control and sudo, locked myself out"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by jroddog on 2013-09-30
Hello I was messing with the account permisions and accidently made myself a standard user and i am not able to install programs and run sudo is there any way i can fix this

---

### Post by Impavidus on 2013-09-30
Boot into the recovery console, mount the file system rw and re-add yourself to the sudo group. You can follow this tutorial until (not including) the passwd command (I assume you haven't lost the password): [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). Then use```
adduser yourusername sudo
``` to add your name to the sudo group. Type **exit** and resume booting, or just reboot.

@slickymaster: Missed that one. It exactly tells what I wrote.

---

### Post by slickymaster on 2013-09-30
Just follow this tutorial: [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo") and you'll have everything fixed.

---

### Post by Francisco Cardoso on 2013-09-30
You can try to "sudo passwd root"
If you can pass it, you can type "su -" and get the root access to fix it.

---

### Post by jroddog on 2013-09-30
thank you i have fixed it

---

