---
title: "update manager"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by garrettstarnes on 2008-05-02
my update manager just keeps freezing up.  It won't let me install my updates.  I recently upgraded to ubuntu 8.04, and I've been trying for about an hour to do some more updates that it says i need.  Any suggestions?

---

### Post by Tatty on 2008-05-02
try it via the command line

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by MattBD on 2008-05-02
Try doing it from the command line as you'll normally get a better error message:
```
sudo apt-get update
sudo apt-get upgrade
```
If you run those two commands in the terminal and post any error messages here, that might give a better idea of what's going on.

---

### Post by garrettstarnes on 2008-05-02
sudo: unable to resolve host StarnesFamilyLaptop

---

### Post by Tatty on 2008-05-02
can you post the output of ```
cat /etc/hosts
```

---

### Post by garrettstarnes on 2008-05-02
127.0.0.1 localhost
127.0.1.1 StarnesFamilyLaptop.[www.yahoo.com](www.yahoo.com)

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
user@StarnesFamilyLaptop:~$

---

### Post by MattBD on 2008-05-02
Try these previous posts: [http://ubuntuforums.org/showthread.php?t=615579](http://ubuntuforums.org/showthread.php?t=615579) and [http://ubuntuforums.org/archive/index.php/t-613521.html](http://ubuntuforums.org/archive/index.php/t-613521.html) which were about the same kind of thing.

---

### Post by Oldsoldier2003 on 2008-05-02
> **garrettstarnes said:**
> sudo: unable to resolve host StarnesFamilyLaptop

your /etc/hosts file needs to be fixed. reboot to recovery mode and edit /etc/hosts removing any .suffixes to the 127.0.1.1 entry. it needs to match the name that is in /etc/hostname

after you've done that reboot normally and sudo should work.

---

### Post by Tatty on 2008-05-02
> **garrettstarnes said:**
> 127.0.0.1 localhost
127.0.1.1 StarnesFamilyLaptop.[www.yahoo.com](www.yahoo.com)

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
user@StarnesFamilyLaptop:~$

Thats odd, im sure you shouldnt have .[www.yahoo.com](www.yahoo.com) on the end of that line.  Back up your hosts just in case:

```
sudo cp /etc/hosts /etc/hosts.backup
```

Then:

```
gksu gedit /etc/hosts
```

and edit the line "127.0.1.1 StarnesFamilyLaptop.www.yahoo.com", and change it to "127.0.1.1 StarnesFamilyLaptop"  (without the quotes obviously)

then try again.  Although you might need to restart some service first, i am not sure, so if it might be worth rebooting if it doesnt work straight off.

---

### Post by bigtel on 2008-05-03
I have had the same problem after upgrading and found the word 'MSHOME' after my host name. I have now deleted this and the problem has been solved.

I used the code... 

gksu gedit /etc/hosts

...in the terminal window to edit the file required.

---

### Post by garrettstarnes on 2008-05-04
That did it!! Thanks you guys.

---

