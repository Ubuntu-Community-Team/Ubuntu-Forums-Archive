---
title: "hostname"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-24
Hi,

i tried to change my hostname-

sudo nano /etc/hostname(edited the new hostname 'server')
sudo /etc/init.d/hostname.sh start(restarted)

however when i try sudo  nano /etc/resolv.copnf

it gives me 'sudo : unable to resolve host server
n it still shows the old hostname at the prompt
 'davis@fh-78serv:$

only thing thats changed is when i type $hostname,it shows server...

whats goin wrong here?

---

### Post by gtdaqua on 2008-06-24
To change your hostname:

```

sudo echo servername > /etc/hostname

```

Then edit your 'hosts' file:

```

sudo nano /etc/hosts

```

The content should look like this:

```

127.0.0.1       localhost
192.168.0.101   servername

```

Change the IP address and servername accordingly. Restart your server.

Check now:

```

hostname
hostname -f

```

Both should return your new servername.

---

### Post by ub007 on 2008-06-24
the sudo command doesnt work anymore..

it reads sudo:unable to resolve host server

---

### Post by gtdaqua on 2008-06-24
thats may be because your hostname is messed up

Type 'su' and become root. Then type those commands without 'sudo'.

---

### Post by sujoy on 2008-06-24
you can also set hostname simply by

# hostname new_name

---

### Post by ub007 on 2008-06-24
i type su:
password:

n then it gives Authentification failure...

strange,cz i',m certain the password is right

---

### Post by ukripper on 2008-06-24
you may want to use ```
sudo su
``` to become root

---

### Post by ukripper on 2008-06-24
> **sujoy said:**
> you can also set hostname simply by

# hostname new_name

you can but it won't stay there after reboot.

---

### Post by ub007 on 2008-06-24
hostname new_name...can try that but need to be root...

at the moment i cant get to be root...
sudo -s -H -sudo doesnt work
error msg:sudo:unable to resolve host server

tried sudo su...same error

tried su:
asks password..i key in the correct one but guves me authentication failure....

---

### Post by sujoy on 2008-06-24
try logging in through the recovery console

---

### Post by nick_h on 2008-06-25
> **sujoy said:**
> you can also set hostname simply by

# hostname new_name

You should also be able to change the hostname in System->Administration->Network

---

### Post by ub007 on 2008-06-27
didnt try the recovery console....but nothing else mentioned worked,so had to perform a fresh install :(thanks

---

