---
title: "ttf-mscorefonts-installer"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by Davdrkr on 2011-11-02
I cant seem to run an update on Ubuntu 10.10 I keep receiving a 403 forbidden error when I attempt any upgrade or download via the terminal and when I enter the upgrade manager I am immediately greeted with this message "E: The package ttf-mscorefonts-installer needs to be re-installed. Of which it offers me a partial upgrade to repair any packages, but then I receive the error

"Remove package in bad state
The package 'ttf-mscorefonts-installer' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?" I say yes and the prompt closes without any further action.

I also got the error 

"E: Internal error opening cache" (1). Please report." 

I have tried to rid myself of 'ttf-mscorefonts-installer'

1.by running; "sudo apt-get remove ttf-mscorefonts-installer" 
and I recieve the error message 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
XXXXX@XXXXXXXXX:~$ " 

2. I tried purging ttf-mscorefonts-installer "sudo apt-get --purge ttf-mscorefonts-installer" only to receive another error; "E: Invalid operation ttf-mscorefonts-installer"

---

### Post by vicshrike on 2011-11-03
Is this what you are looking for?:

[http://packages.ubuntu.com/maverick-updates/ttf-mscorefonts-installer](http://packages.ubuntu.com/maverick-updates/ttf-mscorefonts-installer)

---

### Post by mörgæs on 2011-11-03
Changed the title to a more descriptive one.

---

### Post by drofart on 2011-11-03
> **Davdrkr said:**
> I cant seem to run an update on Ubuntu 10.10 I keep receiving a 403 forbidden error when I attempt any upgrade or download via the terminal and when I enter the upgrade manager I am immediately greeted with this message "E: The package ttf-mscorefonts-installer needs to be re-installed. Of which it offers me a partial upgrade to repair any packages, but then I receive the error

"Remove package in bad state
The package 'ttf-mscorefonts-installer' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?" I say yes and the prompt closes without any further action.

I also got the error 

"E: Internal error opening cache" (1). Please report." 

I have tried to rid myself of 'ttf-mscorefonts-installer'

1.by running; "sudo apt-get remove ttf-mscorefonts-installer" 
and I recieve the error message 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
XXXXX@XXXXXXXXX:~$ " 

2. I tried purging ttf-mscorefonts-installer "sudo apt-get --purge ttf-mscorefonts-installer" only to receive another error; "E: Invalid operation ttf-mscorefonts-installer"
Ok try [this link]("http://ubuntuforums.org/showthread.php?t=1522427")
Gud luck

Mrinal

---

