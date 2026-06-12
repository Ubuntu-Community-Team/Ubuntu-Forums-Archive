---
title: "ubuntu server startup program (perl)"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by tsocratis on 2013-03-09
Hey I am new with linux,

I have the file

 /home/fs/dir/filename.pl

I want this file to start when my computer boots.
I have make a new file on /etc/init.d/Runfile

Runfile
########################
#!/bin/bash
perl /home/fs/dir/filename.pl &
########################

and then I execute this
sudo chmod +x /etc/init.d/filename
sudo update-rc.d /etc/init.d/filename defaults

but isn't working. :(

and which command shows me the startup programs ?

---

### Post by tsocratis on 2013-03-10
I found the answer.
One of my friends told me that I must do this :

Runfile
########################
#!/bin/bash
perl -I /home/fs/dir/ /home/fs/dir/filename.pl
########################

that's it

---

