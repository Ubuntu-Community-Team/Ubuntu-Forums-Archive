---
title: "Problem about user access"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by abhik78 on 2011-10-14
Hi Everyone, 
I am trying to add a new user in an existing network of few systems. I have created a new user e.g. "abhik" in a computer e.g. "sys1". Now when I try to login in "sys1" from "sys1" as "abhik" I could log in, I could see the home directory in "sys1" (/home/sys1/abhik) from other system. Now I am trying to give access "abhik" in other computers e.g. "sys2". I updated the /etc/passwd file of "sys2" with the same line from sys1 i.e. 
abhik:x:2032:100::/home/sys1/abhik:/bin/bash
whenever now I try to ssh "sys2" as "abhik" from "sys1" i get the message "permission denied". How can I give access user "abhik" all other computer while "abhik" has home in "sys1".
I have all these systems mounted properly i.e. all other users have access to any computer despite where their home is. 

Thanking you all in advance for your time and cooperation. 
Regards, 
Abhik

---

### Post by achase79 on 2011-10-14
Are you trying to access the share on sys1 from sys2?
Or are you creating a share on sys2 identical to sys1?

You can mount a sftp (ssh) share using the FUSE sshfs userspace filesystem
if each computer can login to sys1 as abhik, then each can use this

check out [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

I used to do this, but due to high load it put on my server I switched to NFS instead

---

### Post by abhik78 on 2011-10-14
Thanks for your reply. 
I am trying to access the share on "sys1" from "sys2" since I have the home directory in "sys1". 
We have NFS system installed in our network. Sorry for not to mention this before. These are the few lines from my fstab file from "sys1"

###########		NFS		 ##############
sys2:/home/sys2		/home/sys2		nfs	bg,rw		
0 0

sys3:/home/sys3		/home/sys3		nfs	bg,rw		
0 0

I mounted the systems with "mount -a" after updating the passwd file. But still no luck. 

Thanks. 
Abhik

---

