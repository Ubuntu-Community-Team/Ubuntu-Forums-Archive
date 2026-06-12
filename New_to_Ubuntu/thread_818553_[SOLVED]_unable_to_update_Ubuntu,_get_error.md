---
title: "[SOLVED] unable to update Ubuntu, get error"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Alavai on 2008-06-04
Hello all,

I was doing an update from the update manager, however I get an error that will not allow me to complete the update.

The error is:
-----------
An error occured.
The following details are provided:

E: /var/cache/apt/archives/bash_3.2-0ubuntu18_i386.deb: files list file for package `cupsys' is missing final newline
------------

I don't know what this means.

Later another window appears. I click on details and it has the following:
---
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/bash_3.2-0ubuntu18_i386.deb (--unpack):
 files list file for package `cupsys' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/bash_3.2-0ubuntu18_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
---

I'm currently using ubuntu 8.04.

I've been running Ubuntu since 7.10 without such a hitch. The only thing that has occurred recently was failing RAM. I didn't realize till I tried copying files in Ubuntu from my WinXP partition to my Ubuntu partition and my system would crash. WinXP would go BSD. Then I ran memtest from GRUB and saw the 70k+ errors............... :(

Anyway I got new RAM now and ran through memtest. The new RAM is fine.

Could my using of the bad RAM have corrupted Ubuntu installation? 

Thanks for your time.

---

### Post by wpshooter on 2008-06-04
Did you try switching to another server under software sources ?

---

### Post by robertchahine on 2008-06-04
did you try
```

sudo apt-get install -f 
```

---

### Post by Alavai on 2008-06-04
I switched to 2 other servers and both times they yielded the same errors. The files were downloaded, but then when it went to install the updates, it would show the error.

I tried the command:

sudo apt-get install -f 

and it yielded:
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.

---

### Post by bapoumba on 2008-06-04
Probably the list file for cupsys is corrupt (for some unknown reason). One way to solve this is described [here]("http://ubuntuforums.org/showpost.php?p=1635843&postcount=9") and another one [there]("https://answers.launchpad.net/ubuntu/+question/2591"). Adapt the commands for cupsys.list.

---

### Post by Alavai on 2008-06-04
bapoumba I think that did the trick... the first link you suggested:[http://ubuntuforums.org/showpost.php?p=1635843&postcount=9]("http://ubuntuforums.org/showpost.php?p=1635843&postcount=9")

From the post I did:

1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.

I searched for 'cupsys' and saw 'Package: cupsys' . I deleted the whole entry for cupsys(everything from 'Package: cupsys' to the blank line before the next package) and saved the file. 

4. apt-get update, apt-get -f install

I ran apt-get update and then I ran apt-get -f install

it saw the a problem with the dependency and downloaded cupsys from the server. I then ran the update manager and I was able to install all the updates without problem.

Thanks.

---

### Post by bapoumba on 2008-06-04
Congratulations! Glad to see you got it to work :)

---

