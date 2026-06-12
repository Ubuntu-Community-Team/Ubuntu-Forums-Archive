---
title: "Partial upgrade"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by huu2011 on 2012-06-13
Hello all,
I have got this problem here.it makes me cannt install or upgrade.
please any help

```



sudo dpkg --configure -a 
 Setting up libgmp3c2 (2:4.3.2+dfsg-2ubuntu1) ... 
 Setting up getdeb-repository (0.1-1~getdeb1) ... 
 --2012-06-13 19:34:56--  http://archive.getdeb.net/getdeb-archive.key 
 Resolving archive.getdeb.net... 107.09.200.127 
 Connecting to archive.getdeb.net|107.09.200.127|:80...



```.
It seems it cannot get connect through internet,and would like to remove it.
thank you
huu

---

### Post by wilee-nilee on 2012-06-13
Post all the text from running a update in a terminal, including the command.

When you paste this to a reply wrap it as well in code tags.

---

### Post by josephmills on 2012-06-13
in terminal try 
```
sudo apt-get -f install 
```
then ```
sudo apt-get update
```
then ```
sudo apt-get install figlet 
```
then ```
figlet "MY Name is $USER"
```
did figlet install ? 
if so you can now remove 
```
sudo apt-get --purge remove figlet
```

---

### Post by huu2011 on 2012-06-13
Hi Josephmils;
Here is the output.
```

  **sudo apt-get -f install **
  Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded. 
 2 not fully installed or removed. 
 After this operation, 0 B of additional disk space will be used. 
 Setting up libc-bin (2.13-20ubuntu5.1) ... 
 Setting up getdeb-repository (0.1-1~getdeb1) ... 
 --2012-06-13 23:15:47--  http://archive.getdeb.net/getdeb-archive.key 
 Resolving archive.getdeb.net... IP
 Connecting to archive.getdeb.net| IP ** &#8220;Fail to connect&#8221; ** 

```

  ```

 **sudo apt-get update**
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
  
```

```

 **sudo apt-get install figlet **
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
  

```
The problem still there,any help?

---

