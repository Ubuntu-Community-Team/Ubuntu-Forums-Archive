---
title: "samba for Ubuntu to LUbuntu"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by ShermW0829 on 2013-06-27
Will the below link help me to establis remote login from the Ubuntu client to the LUbuntu client? I don't need all the windows stuff. Can I remove the Windows refernces from the smb.conf file?

[http://www.ehow.com/how_12192340_install-configure-samba-ubuntu.html](http://www.ehow.com/how_12192340_install-configure-samba-ubuntu.html)

Thank you;

Sherman

---

### Post by DeathByDenim on 2013-06-27
No, that link will help you set up file and printer sharing with Windows computers. If you want to log in remotely from Linux to Linux, you need to use SSH. Run this command on the computer you would like to remotely log into (let's call it A):
```
sudo apt-get install openssh-server
```
Then you should be able to remotely log into that computer using this command on the other computer (let's call it B)
```
ssh x.x.x.x
```
where you need to replace x.x.x.x with the IP address for A.

---

### Post by ShermW0829 on 2013-06-29
Thank you, DeathByDenim. I am on a password protected Belkin switch. Will SSH open my computers to the world or will the computers still be protected from outside visibility?

Edited to include the following:

I think I have found what I am looking for in the following links.
[http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/](http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/)
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[http://www.la-samhna.de/library/brutessh.html#3](http://www.la-samhna.de/library/brutessh.html#3)
[http://askubuntu.com/questions/32246/how-to-secure-ubuntu-server-from-bruteforce-ssh-attacks](http://askubuntu.com/questions/32246/how-to-secure-ubuntu-server-from-bruteforce-ssh-attacks)

I still have one other question. What do I run on the lbuntu host to allow logins? I assume that since I am installing SSH on the Ubuntu host then the Ubuntu host is considered the server.

Thank you;

Sherman

---

### Post by DeathByDenim on 2013-06-29
No, your computer will not be open to the world. You router will most likely be using NAT, which assigns your computer a local IP that cannot be accessed from the outside. To check, you can type
```
ifconfig
```
which will report your IP address. Local IP addresses either have the form 10.x.x.x or 192.168.x.x. If you have that, then you're ok.

On the host is where you install the openssh-server using the apt-get command mentioned above. You can then log into that host from all of the other computers using ssh, which should already be installed.

---

### Post by deadflowr on 2013-06-29
Look here for a quick rundown on ssh/openssh on Ubuntu
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

And look here to learn how to use keys instead of passwords.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by ShermW0829 on 2013-06-30
Thank you

---

