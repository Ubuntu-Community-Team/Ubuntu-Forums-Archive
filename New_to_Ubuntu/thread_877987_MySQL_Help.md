---
title: "MySQL Help"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Houli on 2008-08-02
I tried installing the mysql-server package and now it is configuring it but it says

Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.2) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
$Mounting securityfs on /sys/kernel/security: done.
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

Help

---

### Post by eightmillion on 2008-08-02
Try this:

```

sudo apt-get autoremove --purge mysql-server mysql-server-5.0
sudo apt-get install mysql-server

```

---

### Post by Houli on 2008-08-02
I can't do anything it tells me to dpkg --configure -a because it is trying to configure it and then I close it because it is doing nothing and when I try removing while it is configuring it tells me dpkg is locked.

Help!

---

### Post by eightmillion on 2008-08-02
```

sudo pkill dpkg
sudo dpkg --configure -a
sudo apt-get -f install

```
Then run the commands I gave above.

---

### Post by Houli on 2008-08-02
When i type in sudo dpkg --configure -a it leaves me with that error so I have to close terminal but when i tried pkill and then i tried the -f command it told me i had to do dpkg --configure -a but then I try that and it still hangs on me.

---

### Post by Houli on 2008-08-02
Really I don't care if I can't get MySQL going now if it won't let me get anything else. I justed wanted it as a test. How do I tell it to stop trying.

---

### Post by eightmillion on 2008-08-02
Could you please post the exact outputs of all your error messages?

---

### Post by Houli on 2008-08-02
Ok I fixed it. I opened the system monitor as root. Opened a new terminal and used it to run the --configure command and then in system monitor I ended the mysql-server process and then in the terminal it came up with the processing triggers stuff and now I can remove it and install other stuff!

---

