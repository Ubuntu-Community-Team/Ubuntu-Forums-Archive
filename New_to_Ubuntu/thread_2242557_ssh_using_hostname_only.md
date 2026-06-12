---
title: "ssh using hostname only?"
date: 2014-09-02
forum: New to Ubuntu
---

### Post by engineer2 on 2014-09-02
Hello everyone

how i can possibly attach an ip address to a specfic name ?
meaning when i ssh  i want to write the hostname only (ex. ssh gcl7) without the need to write the ip address ( ex. ssh gc@ 192.168.10.70 OR ssh 192.168.10.70 )

here is the code :

```
root@gmstr:~# ssh gcl7
ssh: Could not resolve hostname gcl7: Name or service not known
root@gmstr:~# ssh 192.168.10.70
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Tue Sep  2 19:49:47 2014 from 192.168.10.60
root@gcl7:~# 
root@gcl7:~# 
root@gcl7:~# 

```

---

### Post by steeldriver on 2014-09-02
You can create a ~/.ssh/config file containing the host and user specifications - something like

```

Host gcl7
    HostName 192.168.10.70
    User gc

```

See man ssh_config for details and additional options e.g. you can also specify an IdentityFile (keyfile) for passwordless logins

---

### Post by JKyleOKC on 2014-09-02
In addition to, or in place of, steeldriver's suggestions, you can add a line to your /etc/hosts file that will let you do things such as ping the remote machine by name in addition to making the ssh connection. Just open a text editor such as gedit with the command "gksudo gedit /etc/hosts" and respond to the password prompt with your login password, then find the line that begins "127.0.1.1" and add a new line right below it that says "192.168.10.70 gcl7" with a tab character where I put a space. Then save the file and get out of gedit. That's all you have to do.

The /etc/hosts file does the conversion between name and address, just like a phone book or contact list works. If you have other machines on your local network, you can add their names the same way. I have duplicate hosts files on all my machines, except that the 127.0.1.1 line is different for each of them; this lets me treat them just like all other addresses without needing to remember actual IP address for each one.

Hope this helps!

---

### Post by engineer2 on 2014-09-03
Worked  for Me  
Thanks ^_^

---

