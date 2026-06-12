---
title: "unable to do password less ssh"
date: 2018-09-02
forum: New to Ubuntu
---

### Post by gnaneswarreddyk on 2018-09-02
Hello,
I am unable to do password less ssh in ubuntu 18.04. Here are the steps i followed.
1. Created user1 on 2 virtual servers.
2. Did ssh-keygen on server1 with user1. Copied it to server2 using shh-copy-id.
3. From server1 when i do ssh user1@server2
    It asks for password. If i give password ssh is successful. (But i need password less)

4. Edited /etc/ssh/sshd_config file with root on server2 with below change
    From  #PubkeyAuthentication yes
    To PubkeyAuthentication no
5. Restarted ssh
6. now When i do ssh user1@server2, I was asked to do enter password. Even though i give correct password, i get permission denied.

What do i need to do for password less ssh?

---

### Post by The Cog on 2018-09-02
To start with, you need to re-enable PubkeyAuthentication.

Then check the permissions of the .ssh directories and files in them (at both client and server). 
the .ssh directory must be usable only by the owner (-rwx------)
The client private key file must be readable only by the owner (-rw-------)

My guess is that something somewhere is too pyblic and ssh doesn't like it.
[https://superuser.com/questions/215504/permissions-on-private-key-in-ssh-folder](https://superuser.com/questions/215504/permissions-on-private-key-in-ssh-folder)

You couls also look at authorized_keys on the server and make sure the client private key is in there.

---

### Post by gnaneswarreddyk on 2018-09-02
Thanks for reply. After i change permissions for .ssh directory, i get new error.
$ ssh user1@192.168.133.129
user1@192.168.133.129: Permission denied (publickey).

---

### Post by sporksrule on 2018-09-04
If you want turn off password authentication you need:
PubkeyAuthentication yes
PasswordAuthentication no

Then:
Make  sure the server you are trying to SSh into has your public key inside  the ~/.ssh/authorized_keys folder, and that that folder is owned and  readable by the a user on that server (i.e. the one you are SSHing in  with).

---

