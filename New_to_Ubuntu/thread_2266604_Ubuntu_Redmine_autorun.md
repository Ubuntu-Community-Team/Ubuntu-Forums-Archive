---
title: "Ubuntu Redmine autorun"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by PavloP on 2015-02-24
I'm trying to start redmine automatically. 
Redmine and ruby are in my /home/%username% directory, gem bundle is complete.
I wrote script, made it executable and placed link to it in /etc/rc.local. Tested it from there - works.
But when I test it from /etc/init.d/rc.local , I receive an error
 
Could not find rake-10.3.2 in any of sources
Run `bundle install` to install missing gems

Need help

---

### Post by dino99 on 2015-02-24
is the /etc/rc.local path filled into bashrc ?

---

### Post by PavloP on 2015-02-24
In which one? Root or user?
As far as I understand on autorun scripts start as root
But, no, neither in /root/.bashrc nor in /home/%username/.bashrc

---

### Post by Holger_Gehrke on 2015-02-24
> **PavloP said:**
> 
Redmine and ruby are in my /home/%username% directory, gem bundle is complete.
I wrote script, made it executable and placed link to it in /etc/rc.local. Tested it from there - works.
But when I test it from /etc/init.d/rc.local , I receive an error
 
Could not find rake-10.3.2 in any of sources
Run `bundle install` to install missing gems


Is there a reason why you installed it that way instead of using the one in the repositories or from the ppa ? Putting software in your home directory is generally not a good idea, especially not for stuff that's going to run as a server.

---

### Post by PavloP on 2015-02-24
I'm not strong in Ruby, but Redmine requires it. So I just followed Redmine installation guide

---

### Post by dino99 on 2015-02-24
here is some help [http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_on_Ubuntu_step_by_step](http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_on_Ubuntu_step_by_step)
and an other older  [https://docs.oseems.com/general/web/redmine/install-in-ubuntu](https://docs.oseems.com/general/web/redmine/install-in-ubuntu)

---

### Post by Holger_Gehrke on 2015-02-24
Unless you want to hack on redmine or absolutely, positively need the latest features, you really should not try an install from outside of the repositories unless you're very experienced both with Linux and with ruby.

A simple ```
apt-get install redmine
``` should get you version 2.4.something if you're on Ubuntu 14.04 or 1.3.something if you're still on Ubuntu 12.04. For 14.04 there is a PPA that has version 2.5.1, which you can add to your repositories with ```
apt-add-repository ppa:ondrej/redmine
```

---

### Post by Habitual on 2015-02-24
> **PavloP said:**
> I'm trying to start redmine automatically. 
Redmine and ruby are in my /home/%username% directory, gem bundle is complete.
I wrote script, made it executable and placed link to it in /etc/rc.local. Tested it from there - works.

Show us the script.

---

### Post by sandyd on 2015-02-24
> **PavloP said:**
> I'm trying to start redmine automatically. 
Redmine and ruby are in my /home/%username% directory, gem bundle is complete.
I wrote script, made it executable and placed link to it in /etc/rc.local. Tested it from there - works.
But when I test it from /etc/init.d/rc.local , I receive an error
 
Could not find rake-10.3.2 in any of sources
Run `bundle install` to install missing gems

Need help

Likely wrong ruby env is used if you installed it into /home/%username%.

If you want an easier method of doing this, just install thin.

```
sudo apt-get install thin
sudo nano /etc/thin/redmine.conf

```

Stuff below text in, changing pid and log to where you want it to be.
Assuming your ruby environment is in  /home/%username%
```

pid: tmp/pids/thin.pid
log: log/thin.log
timeout: 30
max_conns: 1024
port: 3000
max_persistent_conns: 512
chdir:  /home/%username%
environment: production
servers: 3
socket: tmp/sockets/thin.sock
daemonize: true
```

You now have sockets in /home/%username%/tmp/sockets/thin*.sock

Use them with NGINX or similar

---

