---
title: "I changed the owner group of my root directory"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by FastLearner on 2011-10-21
Hello ,
I managed to change the usergroup of my root directory.
As a result I am not able to run any administrative commands.I am not even able to access the sudoers file. Every time I prefix a  command with sudo , I get a message "The group Id of sudoers is 1609 , It should be 0" and then it exits.

The command that i ran which resulted in this problem was :
sudo chgrp -R mysql /

I was supposed to run 
sudo chgrp -R mysql .

The account mysql is nonloggable by the way.

Is there any way I can salvage the situation.

---

### Post by cavh on 2011-10-21
Try booting from a LiveCD and running sudo from a terminal there. I think (but am not entirely sure) that you just hit the Enter key when prompted for the sudo password.

---

### Post by ArgusVision on 2011-10-21
I'm with cavh. Get a live CD and mount the file-system. It gets a litte ugly though... You still have to change the ownership of the subdirectories to their defaults. If you "chgrp root /" then the group ownership of the entire system will be 'root'. This can be a problem. For example your home directory needs to be owned by your user our you may not be able to login. Certain files on the system (I can't remember a specific list) should be owned by the system daemons and/or 'nobody'.

At least it appears you only did chgrp and not chown...

Hmmm. It's only group ownership, so the primary ownership of the files should be intact... It may not affect your login.

---

