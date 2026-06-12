---
title: "Users in ssh"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by lbunbuntu on 2013-05-26
Hi

I have a server runing ubuntu and I have several computers arround the world. I need to make backup from these computers to my ubuntu server via ssh.

My question is : "should I create a different user in ubuntu server for each computer and store the backups files in each home folder, or can I do it in other way?"

Thanks in advance

---

### Post by prodigy_ on 2013-05-26
You can have multiple SSH connections under the same user name simultaneously. So it's easier to have one user and (probably) add a subfolder for each PC. Something like **/home/backup/remote_pc1**, **/home/backup/remote_pc2**, etc.

---

### Post by lethall1 on 2013-05-26
what kind of backup you want to do? 
If it would be one tar file, you are able to name it like "server1-$Date" and put it on server.
You can make 1 different user on server whithout sudo group.
Don't you like "bacula"?

---

### Post by lbunbuntu on 2013-05-26
Thanks for all your answers. I use Duplicati software. I don't knew "bacula". 

If use the same user and later if must break the access to one of those computers , how can I do this?

---

### Post by prodigy_ on 2013-05-26
> **lbunbuntu said:**
> If use the same user and later if must break the access to one of those computers , how can I do this?
If you need SSH only for backups, you could withhold the account password and generate RSA (DSA) keys - one for each computer. Then, if you need to revoke a key, you just remove it from they **authorized_keys** file.
More info here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

This still implies a certain level of trust though. If you're not sure the other side will play nicely, then you need to create a separate user account (or, even better, a separate VM or chroot) for every remote host.

---

