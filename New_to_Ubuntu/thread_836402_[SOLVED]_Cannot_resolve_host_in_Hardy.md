---
title: "[SOLVED] Cannot resolve host in Hardy"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by myotis on 2008-06-21
I am having an error of being unable to resolve host:

graham@Antec-Linux:~$ gpg --export --armor E2A11821 | sudo apt-key add -
sudo: unable to resolve host Antec-Linux
OK

By typing in terminal:

graham@Antec-Linux:~$ cat /etc/hosts

I get
127.0.0.1 localhost
127.0.1.1 Antec-Linux.MYOTIS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

If I  run graham@Antec-Linux:~$ gksudo gedit /etc/hosts

I get:

127.0.0.1 localhost
127.0.1.1 Antec-Linux.MYOTIS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have been browsing the forums and I think I need to edit the host file to remove the Domain "MYOTIS" so it is changed to:

127.0.0.1 localhost
127.0.1.1 Antec-Linux

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Can anyone confrim that this is what I should be doing.

Thanks,

Graham

---

### Post by avtolle on 2008-06-21
That would be my thought, to edit that file so it reads as you post. That seems to have resolved most nearly all the problems others have had.

---

### Post by myotis on 2008-06-21
> **avtolle said:**
> That would be my thought, to edit that file so it reads as you post. That seems to have resolved most nearly all the problems others have had.


Thanks, I will give that a try.


Graham

---

### Post by the_doc on 2008-06-21
Sounds good to me.

---

### Post by Oldsoldier2003 on 2008-06-21
> **myotis said:**
> I am having an error of being unable to resolve host:

graham@Antec-Linux:~$ gpg --export --armor E2A11821 | sudo apt-key add -
sudo: unable to resolve host Antec-Linux
OK

By typing in terminal:

graham@Antec-Linux:~$ cat /etc/hosts

I get
127.0.0.1 localhost
127.0.1.1 Antec-Linux.MYOTIS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

If I  run graham@Antec-Linux:~$ gksudo gedit /etc/hosts

I get:

127.0.0.1 localhost
127.0.1.1 Antec-Linux.MYOTIS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have been browsing the forums and I think I need to edit the host file to remove the Domain "MYOTIS" so it is changed to:

127.0.0.1 localhost
127.0.1.1 Antec-Linux

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Can anyone confrim that this is what I should be doing.

Thanks,

Graham

yep thats exactly what you need to do. Hardy has issues with the dotted suffix to the host name

---

### Post by myotis on 2008-06-21
Thanks all,  line now edited and seems to have fixed the problem.


Graham

---

