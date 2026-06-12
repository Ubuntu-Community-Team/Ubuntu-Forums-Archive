---
title: "Serious Problem:Lost adminstartive Powere"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pardesi on 2008-04-26
when i start my newly installed KDE 4.0 there comes a dialog telling me that i have lost i don't have adminstrative powers and that i can't do any marked changes.
Also those files which i delete due to this limitation return back on my next log in

---

### Post by Michael.Godawski on 2008-04-26
Run in terminal:
```
 sudo adduser $user admin
```
, where you replace $user with your acount name.

---

### Post by pardesi on 2008-04-26
the reply is 
```
The user 'pardesi' is already a member of 'admin'
```

---

### Post by Michael.Godawski on 2008-04-26
Can you please post your sudoers file:

```
sudo cat /etc/sudoers
```

---

### Post by pardesi on 2008-04-26
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by Michael.Godawski on 2008-04-26
I have also found this on launchpad. Your sudoers file is fine.

[https://answers.launchpad.net/ubuntu/+question/3333](https://answers.launchpad.net/ubuntu/+question/3333)

I think it is worth a try. But when you say you are already in the admnin group... weird. What version of Ubuntu do you use?

---

### Post by pardesi on 2008-04-26
i use 8.04 the problem is though i can download any file using synaptic but the omp is not able to apply them:mad:

---

### Post by daranz on 2008-04-26
Can you do something simple with sudo, like "sudo ls" in terminal? I'm making a wild guess here, but maybe something is wrong with your kdesudo. Also, try doing "sudo -l" which should list all the commands you're allowed to execute via sudo (what you want here is ALL).

---

### Post by pardesi on 2008-04-26
```
sudo -l
```
gives
```
User pardesi may run the following commands on this host:
    (ALL) ALL

```

But i do think there is something wrong with my kdesudo because that's the pop-up i receive on starting which tells me i can't **apply** an changes all i can do is just download them

---

### Post by daranz on 2008-04-26
You can always try starting your package manager with sudo. I don't use kubuntu, so I'm not sure what its GUI package manager is these days, but basically, you should be able to do "sudo synaptic" or "sudo adept" from terminal. If sudo is working right, you should be able to apply your updates from that. If you still have kde updates pending, installing them might help. Otherwise, check if your kdesudo package is installed.

---

### Post by pardesi on 2008-04-26
see the attachment this is what i get when i start

---

### Post by daranz on 2008-04-26
Yep. It looks like there's a mangled command being executed. It's supposed to run synaptic through kdesudo. Instead, it runs kdesudo without arguments and then runs synaptic without elevating priviledges to superuser.

Try doing what I suggested before, or even "kdesudo synaptic" from terminal, and then finishing the updates.

---

### Post by pardesi on 2008-04-26
can u please tell me in detail and step by step what to do i am semi-noob to all these

---

### Post by daranz on 2008-04-26
Basically what you should do is open a terminal window (konsole), and type in ```
sudo synaptic
```Sudo will ask for your current account password. After that, synaptic should come up. Click refresh. Then, click Mark All Upgrades. Then, click Apply.

Alternatively, you can do the following two commands directly from terminal:

```

sudo apt-get update
sudo apt-get upgrade

```


This may or may not solve your issue, but it's worth a shot. It should bring all your packages up to date, which is something you haven't been able to do while running synaptic without sudo.

---

