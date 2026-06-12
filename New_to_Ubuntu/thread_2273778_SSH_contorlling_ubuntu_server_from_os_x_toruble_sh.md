---
title: "SSH: contorlling ubuntu server from os x toruble shooting"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by con2 on 2015-04-15
I am working on a project for school involving a small web server I've made (Dell GX520 running Ubuntu) and I want to be able to work in the terminal via SSH from my mac in class. Basically, I feel like I've run through every SSH tutorial/toruble shooting tip and I am still getting "Permission denied (publickey)." - even when I try to connect to a non-existent user like fakeuser@[ip address], I get the same message.

I just don't know what to try anymore. Can anyone help me trouble shoot?

---

### Post by tgalati4 on 2015-04-15
You can log in with passwords or RSA keys (public key and private key).  If you set up your ssh client and server correctly to use keys, then you don't need a password to log in.  This can be tricky to set up correctly.

Open a terminal and post the following from both the Ubuntu machine and the Mac.

```
cat /etc/ssh/ssh_config
```

Then delete ~/.ssh/known_hosts and try again.  If you have static IP addresses for both the Mac and the Ubuntu server, make sure they are specified in /etc/hosts.

---

### Post by mastablasta on 2015-04-16
I followed Debian's and Ubuntu's instructions. make sure keys are setup properly and in the right place. If you named it (key) differently then I think you need to specify that key's name on login:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

[https://wiki.debian.org/SSH](https://wiki.debian.org/SSH)

---

### Post by nerdtron on 2015-04-16
Be sure that the user you are connecting to is existent on the ubuntu server and that the password is set to that user.

Try it on your mac:
ssh -p 22 username@[ipaddress]

---

