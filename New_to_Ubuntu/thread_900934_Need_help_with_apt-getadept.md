---
title: "Need help with apt-get/adept"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by DFord425 on 2008-08-25
How do i unlock the packaging system database for the adept manager or to use apt-get. For some reason mine is locked and i do not know why.

---

### Post by iaculallad on 2008-08-25
> **DFord425 said:**
> How do i unlock the packaging system database for the adept manager or to use apt-get. For some reason mine is locked and i do not know why.

On your terminal:

```
sudo apt-get -f install
sudo dpkg --configure -a
```

then try accessing your Adept Manager.

---

### Post by DFord425 on 2008-08-25
it didnt work, i ran the commands, here is the output:
```
dford@DMoney:~$ sudo apt-get -f install
[sudo] password for dford:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dford@DMoney:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

```
Then when i went to adept manager, it gave me the same error, database is locked.

---

### Post by iaculallad on 2008-08-25
> **DFord425 said:**
> it didnt work, i ran the commands, here is the output:
```
dford@DMoney:~$ sudo apt-get -f install
[sudo] password for dford:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dford@DMoney:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

```
Then when i went to adept manager, it gave me the same error, database is locked.

On your terminal:

```
sudo rm /var/lib/dpkg/lock
```

then:
```

sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by DFord425 on 2008-08-26
ok i ran those commands, and here is what i got:
```
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
```
Any ideas on how to fix this?

---

### Post by jgrabham on 2008-08-26
> **DFord425 said:**
> ok i ran those commands, and here is what i got:
```
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
```
Any ideas on how to fix this?

ahh, sounds like a botched java install, run ```
sudo apt-get install sun-java6-bin
``` IIRC adept doesn't like installing java.

---

### Post by DFord425 on 2008-08-26
Thanks for that reply, seems that i have found another problem. It seems that i cant get this to work.
```
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```
How do i lock the download directory?

---

### Post by benerivo on 2008-08-26
Have you tried what iaculallad said above.

---

### Post by DFord425 on 2008-08-26
> **benerivo said:**
> Have you tried what iaculallad said above.

yes i did

---

### Post by benerivo on 2008-08-26
Try```
sudo rm /var/cache/apt/archives/lock
```then```
sudo dpkg --configure -a
```or maybe just a restart if you haven't tried one.

---

### Post by DFord425 on 2008-08-26
Thanks, that worked to unlock adept. But it still gives me an error when i use adept and i got an error when installing java. But when i go into adept manager and click "review changes" nothing shows up, which it did before when java wasnt getting installed. Any ideas?
```
Preparing to replace sun-java6-bin 6-06-0ubuntu1 (using .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java6-jre 6-06-0ubuntu1 (using .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb
 /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by benerivo on 2008-08-26
Well, you've got a lot of 'lock' problems. This isn't something i've had myself, but i would look to remove the files that are locked, then restart and try again. So to begin i would do```
sudo rm /var/cache/debconf/config.dat
```

---

### Post by DFord425 on 2008-08-26
> **benerivo said:**
> Well, you've got a lot of 'lock' problems. This isn't something i've had myself, but i would look to remove the files that are locked, then restart and try again. So to begin i would do```
sudo rm /var/cache/debconf/config.dat
```

Thanks, i ran that command then i ran ```
sudo apt-get -f install
``` and now it seems to be working. When i did the ```
sudo apt-get -f install
``` it removed the java packages that were gving me trouble. 

Thanks for you help everyone.

---

