---
title: "SSH key refused"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-09
For what possible reasons (other than not being the same) would a Putty-Ubuntu connection refuse the key?

---

### Post by ahsile on 2008-10-09
Is your public key installed in the **$HOME/.ssh/authorized_keys** file?

---

### Post by spiderbatdad on 2008-10-09
the public and private key generated on the computer you want to login to...the private key stored on the computer you want to log in from.

---

### Post by Konstabel on 2008-10-10
How do I add my new key to the authorized_keys file?

---

### Post by Konstabel on 2008-10-10
Maybe this might help;

[I]Oct 10 10:29:28 server sshd[8052]: Failed none for user from x.x.x.x port 3786 ssh2
Oct 10 10:29:28 server sshd[8052]: Authentication refused: bad ownership or modes for directory /home/user/.ssh
Oct 10 10:29:28 server sshd[8052]: Authentication refused: bad ownership or modes for directory /home/user/.ssh
Oct 10 10:29:28 server sshd[8052]: Failed publickey for user from x.x.x.x port 3786 ssh2
[/I]

I got it from the auth.log file.

---

### Post by hyper_ch on 2008-10-10
The first part here is about using ssh-key (on two linux computers) but I'm sure you'll manage to make it work with putty: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by spiderbatdad on 2008-10-10
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

my permissions are 700 for .ssh, and 644 for /.ssh/authorized_keys

---

