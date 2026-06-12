---
title: "command help"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-02
brain fart - please correct this command i know it is wrong 

sudo dpkg-reconfigure -a
need to reconfigure 

tks

---

### Post by NikTh on 2012-11-02
Reconfigure what ? This command 
```
sudo dpkg-reconfigure -a
``` will reconfigure -a(all) the packages 
```
man dpkg-reconfigure
```

---

### Post by rburkartjo on 2012-11-02
ni tks that is what i was looking for but didnt help my problem here is the error message i am trying to correct


THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo dpkg-reconfigure -a
[sudo] password for ray: 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by rburkartjo on 2012-11-02
and just have an error spm etc is also not open when trying to correct

---

### Post by rburkartjo on 2012-11-02
and have no broken packages according to spm

---

### Post by NikTh on 2012-11-02
> **rburkartjo said:**
> 
```
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo dpkg-reconfigure -a
[sudo] password for ray: 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
ray@ray-GC660AA-ABA-SR5123WM:~$
```

I think this message means you have 2 or more package managers open at the same time or you want to use 2 or more package managers at th same time. 

Try to close all applications (smp included) or reboot and run again the command. 

Thanks

---

### Post by rburkartjo on 2012-11-02
ni tks will give that a try

---

### Post by rburkartjo on 2012-11-02
did work still same error message

---

### Post by NikTh on 2012-11-02
Give the results of this command 

```
fuser -v /var/cache/debconf/config.dat
```

Thanks

---

### Post by rburkartjo on 2012-11-02
ni it returns with nothing 

would i mess up my system if i just became root and navigated to

/var/cache/debconf

and deleted these files
config.data and config.data-old

or could i just delete all the files in the folder and not just the aforementioned
there is also these files in /var/cache/debconf
password.data
templetes.data
templetes.data-old

---

### Post by NikTh on 2012-11-02
> **rburkartjo said:**
> ni it returns with nothing 

would i mess up my system if i just became root and navigated to

/var/cache/debconf

and deleted these files
config.data and config.data-old

or could i just delete all the files in the folder and not just the aforementioned
there is also these files in /var/cache/debconf
password.data
templetes.data
templetes.data-old

Probably Yes. I just deleted the folder (in VB of course) and I can not dpkg-reconfigure anything , the results are
```
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
```**EDIT: **Just tried again and I saw that there is no problem if you manually re-create the folder. ```
sudo mkdir /var/cache/debconf/
```So , first backup the folder 
```
sudo cp -R /var/cache/debconf ~/
```then remove and create the folder again 
```
sudo rm -r /var/cache/debconf
sudo mkdir /var/cache/debconf
```and then try again
```
sudo dpkg --configure -a
sudo dpkg-reconfigure -a
```
If any problem occurs you can restore (the backed up debconf) with 
```
sudo cp -R debconf /var/cache/
```
Thanks

---

### Post by rburkartjo on 2012-11-03
ni tks for all your help got it working just backed up folder. then deleted and remade as you suggested

---

### Post by NikTh on 2012-11-03
> **rburkartjo said:**
> ni tks for all your help got it working just backed up folder. then deleted and remade as you suggested

:)

Then I guess you can mark the thread as solved. Click on "thread tools" above. 

Thanks

---

