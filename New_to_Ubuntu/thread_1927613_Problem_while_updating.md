---
title: "Problem while updating"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-02-18
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by howefield on 2012-02-18
Perhaps you are running more than one package manager, eg synaptic package manager, ubuntu software centre, update manager, ect.

If so, close all except the one you are trying to use and try again.

---

### Post by raja.genupula on 2012-02-18
> **rishiar4 said:**
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

+1 to above post .

another thing is if you close any apt thing then you will get that . 

```
sudo rm -rf /var/lib/dpkg/lock
```

do that in terminal and try again what you wanna do, if its give something similar to that but with another location then do the above command with the new location .

```
sudo rm -rf <place the new location>
```

if you have any doubt please post the terminal output .
All the best

---

### Post by rishiar4 on 2012-02-18
i closed everything but still im getting the same error :(

---

### Post by raja.genupula on 2012-02-18
> **rishiar4 said:**
> i closed everything but still im getting the same error :(

yeah if you close or stop any update/upgrade/installation you gonna get that issue . try what i have given and let us know what you got . all the best . but dont forget providing terminal output . :D

---

### Post by rishiar4 on 2012-02-18
Actually im trying  to install chromium .....
after doing sudo rm -rf  <address> 3 or 4 times 
finally I got this error 

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

then i tried 
sudo rm -rf /usr/bin/dpkg

still getting the same error sir!!!

exact  output:Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium-browser is already the newest version.
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

---

### Post by raja.genupula on 2012-02-18
```
sudo rm -rf /var/cache/debconf/config.dat
sudo apt-get update

```

and try again and always wrap the terminal code and output in code tags , you can get them by click at # in this window . 


all the best , let us know what you got .


EDIT : tags

---

### Post by rishiar4 on 2012-02-18
now this error at the end...
```

```
OUTPUT:
Fetched 396 B in 2s (152 B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by raja.genupula on 2012-02-18
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update


```

do it , it will fix your issue . if anything comes up , let us know ,.

all the best .

---

### Post by rishiar4 on 2012-02-18
It got updated successfully .....
but when i typed    sudo apt-get install chromium-browser
i got 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium-browser is already the newest version.
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

---

### Post by raja.genupula on 2012-02-18
give a restart to your PC and  try again .

---

### Post by wildmanne39 on 2012-02-18
Hi, I just wanted to add that this command:```
sudo rm -rf
```is very dangerous and it always needs a warning statement with it.

Please make sure you know what files you are removing and what they do because if you type the wrong path with that command you can wipe out ubuntu completely.
Thanks

---

### Post by raja.genupula on 2012-02-18
hey wildmanne39 , how are you ?:o

+1 to this post . 

@wilmanne39 thats why only i have mentioned him , if you have any doubt give me terminal out put .

so that i can provide the next command . 

i have seen that thread regarding rm rf , that explains rm -rf .  
                                  
@op so whats came up now ?

---

### Post by wildmanne39 on 2012-02-18
Hi, I am good.

A warning will help keep you out of trouble because people will see this thread and start running commands without asking questions and they will destroy there system.

Also most of the time you can dropped of the -rf and it will not be so damaging unless the wild card is used.

---

### Post by rishiar4 on 2012-02-18
no change same output..........

---

### Post by raja.genupula on 2012-02-18
> **wildmanne39 said:**
> Hi, I am good.

A warning will help keep you out of trouble because people will see this thread and start running commands without asking questions and they will destroy there system.

Also most of the time you can dropped of the -rf and it will not be so damaging unless the wild card is used.


yeah ! i agree  .:)

---

### Post by raja.genupula on 2012-02-18
> **rishiar4 said:**
> no change same output..........
  
Ok , 
```
sudo -i
fuser -v /var/cache/debconf/passwords.dat
fuser -v /var/cache/debconf/templates.dat
```
look at what process are using them and kill them .

---

### Post by rishiar4 on 2012-02-18
> **raja.genupula said:**
> Ok , 
```
sudo -i
fuser -v /var/cache/debconf/passwords.dat
fuser -v /var/cache/debconf/templates.dat
```look at what process are using them and kill them .

still the same output............

---

