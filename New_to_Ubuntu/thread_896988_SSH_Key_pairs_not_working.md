---
title: "SSH Key pairs not working"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by know-it-some on 2008-08-21
I am having trouble getting key based authentication to work on my new server.  Whats most odd is that I use this method for all of my other linux (all redhat/fedora) servers but for some reason this time it is not working.  

Here is my process:

   1.  `ssh-keygen -t rsa` is used to generate the key but just hit enter for the password (twice). Accept the default location for the ID and the public key, *.ssh/id_rsa and .ssh/id_rsa.pub, and then rename the .pub key with the name of the machine you are on, example: `mv id_rsa.pub thegiantsdrink.pub`
   2. scp the newly created .pub file to the /root/.ssh directory of the machine you'd like to ssh into.
   3. ssh into the remote machine and cd into /root/.ssh
   4. `more thegiantsdrink.pub >> authorized_keys` This appends the contents of the public key file to the .ssh/authorized_keys file of the remote server. 

After this I should be able to ssh into the remote system without being prompted for a password.  Unfortunately this is not the case with my ubuntu server.  Any ideas?

---

### Post by spiderbatdad on 2008-08-21
Add your keys to seahorse?
Applications>>Accessories>>Passwords and Encryptions...on my system.

---

### Post by know-it-some on 2008-08-21
Thats a good idea, but my servers are commandline only. No GUI.  Is there a way to do this without a gui component?

---

### Post by spiderbatdad on 2008-08-21
you should have a file calles .ssh/authorized_keys, add your key to the bottom of the file.
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by know-it-some on 2008-08-21
> **spiderbatdad said:**
> you should have a file calles .ssh/authorized_keys, add your key to the bottom of the file.
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Indeed, as I posted above that is one of the steps in my current process.  However, I actually figured this out.  I tailed /var/log/auth.log and saw a line in there something like:

COMPROMISED: 2048 d2.......... admin@thegiantsdrink

So I wiped out my keys and regenerated them after doing a: 'apt-get dist-upgrade' and re-scp'd them to the servers and now all is working as it should.  So the take away is this:

If your key based auth isn't working as you think it should be then tail your auth.log and see whats up.

Thanks!

---

### Post by ptn107 on 2008-08-21
make sure 'PubkeyAuthentication yes' and 'PasswordAuthentication no' are present in your sshd_config file

---

### Post by ilrudie on 2008-08-22
Also why are you trying to put them into root's .ssh folder?  Unless you meant to login as root you should put them in your .ssh folder in the authorized_keys file.

---

