---
title: "password-less ssh isn't working :("
date: 2014-08-13
forum: New to Ubuntu
---

### Post by engineer2 on 2014-08-13
[SIZE=4]**Hello guyes**[/SIZE] 
[SIZE=4][B]I'm having problem with setting up a  password-less ssh connection between two laptops that having Ubuntu  14.04 LTS and Ubuntu 12.04 LTS installed. I generate the rsa keys on  both sides and copy the id_rsa.pub on the authorized_keys on both sides  then ssh using (ssh root@ <ip address> )  and this was the output  when i tried to copy the key using scp before i copy it manually into  the authorized keys :

[/B][/SIZE]```
 root@gridmaster:~# ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): 
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
e0:5a:39:3a:b3:0d:fc:a9:87:b9:d7:e7:27:47:b5:70 root@gridmaster
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|      .          |
|     . o    . E  |
|      = S    + . |
|   . + .    . .  |
|    Bo .   .     |
|    oBo.. o o    |
|    +=+  o.+     |
+-----------------+
root@gridmaster:~# chmod 600 .ssh/id_rsa
root@gridmaster:~# scp .ssh/id_rsa.pub root@192.168.10.70:
The authenticity of host '192.168.10.70 (192.168.10.70)' can't be established.
ECDSA key fingerprint is c6:db:30:93:c0:39:5c:0a:dc:86:b2:e2:04:4e:e8:68.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.10.70' (ECDSA) to the list of known hosts.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied (publickey,password).
lost connection
root@gridmaster:~# 
root@gridmaster:~# 
root@gridmaster:~# 
root@gridmaster:~# scp .ssh/id_rsa.pub root@192.168.10.70:
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied (publickey,password).
lost connection


```

 **[SIZE=4]and this is the output after the manual copy of the id into the authorized keys:[/SIZE]**

```
root@gridmaster:~# chmod 700 .ssh
root@gridmaster:~# 
root@gridmaster:~# 
root@gridmaster:~# ssh root@192.168.10.70
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied (publickey,password).


```


**[SIZE=5][SIZE=4]Please help :sad::sad::sad::sad:[/SIZE][/SIZE]**

---

### Post by Lars Noodén on 2014-08-13
It's generally a bad idea to do remote logins as root.  What task are you trying to accomplish?  

Also with 'passwordless' keys, it is a very good idea to tie them to a specific program or script on the server side.  That's easy to do.  

That said, the default settings for LTS won't allow you to remotely login as root using passwords, [only keys](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html).  So to get the public key to the server, you will have to log in as another user and then transfer the public key to the server's root account using sudo.

---

### Post by nerdtron on 2014-08-13
Login as root is really not recommended but you can accomplish what you want using this.

On your local machine after generating keys:
```
root@gridmaster:~# cat /root/.ssh/id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA1fja8tGZ62lMO5QZ5F9by0QubxKbXxi9awZuKPDo+NVUKt2fEydWfgndIV05n6XkCPApG79SD0HJaaQxFa/JDhBM/NWL+9S65Rs+RxeBw3KT1VsCDo2EaAem/tI5j6EpPS8B3JE5FS2COydmcey6s3gcFFXunqhMiuBZeTN3XBYakjlpvBt15ee00drisBvpMMabfRq1+WIcnIrq0Dk5aiudjyQKH6dytKEuasdfasdfasdfasdfasdfUYD8vPuwRIa3UBasdfasdfasdfasdfasdfasdfasdfasdfsafdasdf == root@gridmaster
```

Copy this output line.

Login on the 192.168.10.70 computer and paste the key:
```
root@192.168.10.70:~# echo 'ssh-rsa  AAAAB3NzaC1yc2EAAAABIwAAAQEA1fja8tGZ62lMO5QZ5F9by0QubxKbXxi9awZuKPDo+NVUKt2fEydWfgndIV05n6XkCPApG79SD0HJaaQxFa/JDhBM/NWL+9S65Rs+RxeBw3KT1VsCDo2EaAe/tI5j6EpPS8B3JE5FS2COydmcey6s3gcFFXunqhMiuBZeTN3XBYakjlpvBt15ee00drisBvpMMabfRq1+WIcnIrq0Dk5aiudjyQKH6dytKEuasdfasdfasdfasdfasdfUYD8vPuwRIa3UBasdfasdfasdfasdfasdfasdfasdfasdfsafdasdf  == root@gridmaster' >> /root/.ssh/authorized.keys
```

Now go back to your machine and try to login to 192.168.10.70
```
 root@gridmaster:~# ssh -i /root/.ssh/id_rsa.pub root@192.168.10.70 
```

---

### Post by engineer2 on 2014-08-13
I'm trying to install grid engine software which have a grid master that need to have a ssh access to all other grid clients at the same time  in order to be able to access them directly and install the necessary components 
in this case 192.168.10.60 supposed to be the master and 192.168.10.70 is a grid client. 
but i supposed to get the password-less access ready before installing the grid master software which will manage the installation of the clients software through the ssh access.

so i need to be a root in the master and the clients for the later installation of the software which needs  root privileges

---

### Post by engineer2 on 2014-08-13
[B][SIZE=4]Hello nerdtron 
i tried your way but i was unable to login to 192.168.10.70 in order to echo the rsa key

this is the output :
[/SIZE][/B]
```
root@gridmaster:~# cat /root/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDPyrmcAD6v/TcmfGnXHTIbdR759WKWPI0TbmiH+UeIwqvOwEiJIcnf+iy+Fn/dnzrzCw/ahBaEgFHYn0HKz9FIIA01ARJDUWrGjr4SbN8IPxWX8bGWj4/QjmeqBVwhe7txsqEGHJPa7OOPaRHx9D9DjjS0YklUvG8Kze/XtqbK7HWvEJJqrcWZD/JYB8FlIT05UONjfLawSluzb5XxqEwof8mpDnvl92YMFPxjGfNsvAoke02IbxQdH/ZokvkPhQ920W0baI+XrK6sO/7q9aNN/vXy8B2gBG5sBvE1X+y7U1p+JiD6ycXjILZNga3WFz0OUpFatQbniY7fTBcId1a5 root@gridmaster
root@gridmaster:~# 
root@gridmaster:~# 
root@gridmaster:~# ssh root@192.168.10.70
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied (publickey,password).
root@gridmaster:~# 


```

---

### Post by Lars Noodén on 2014-08-13
Until you set up the public key over on .70 you'll have to log in as someone other than root.

```

root@gridmaster:~# ssh engineer2@192.168.10.70

```

Once you're in, then you can use sudo to put the key into root's authorized_keys

---

### Post by nerdtron on 2014-08-13
> **engineer2 said:**
> [B][SIZE=4]Hello nerdtron 
i tried your way but i was unable to login to 192.168.10.70 in order to echo the rsa key

this is the output :
[/SIZE][/B]
```
root@gridmaster:~# cat /root/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDPyrmcAD6v/TcmfGnXHTIbdR759WKWPI0TbmiH+UeIwqvOwEiJIcnf+iy+Fn/dnzrzCw/ahBaEgFHYn0HKz9FIIA01ARJDUWrGjr4SbN8IPxWX8bGWj4/QjmeqBVwhe7txsqEGHJPa7OOPaRHx9D9DjjS0YklUvG8Kze/XtqbK7HWvEJJqrcWZD/JYB8FlIT05UONjfLawSluzb5XxqEwof8mpDnvl92YMFPxjGfNsvAoke02IbxQdH/ZokvkPhQ920W0baI+XrK6sO/7q9aNN/vXy8B2gBG5sBvE1X+y7U1p+JiD6ycXjILZNga3WFz0OUpFatQbniY7fTBcId1a5 root@gridmaster
root@gridmaster:~# 
root@gridmaster:~# 
root@gridmaster:~# ssh root@192.168.10.70
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied, please try again.
root@192.168.10.70's password: 
Permission denied (publickey,password).
root@gridmaster:~# 


```

Please follow the instruction:
**Login on the 192.168.10.70 either by directly going to the machine itself** or login remotely as a different user.

---

