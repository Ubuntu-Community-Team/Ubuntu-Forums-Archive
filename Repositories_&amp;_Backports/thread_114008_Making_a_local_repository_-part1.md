---
title: "Making a local repository -part1"
date: 2006-01-07
forum: Repositories &amp; Backports
---

### Post by ShirishAg75 on 2006-01-07
[quote=https://wiki.ubuntu.com/AptMoveHowto]
```
sudo apt-get -d install xubuntu-desktop
``` This will put the packages in /var/cache/apt/archives.  Apt-move will look there by default.[/quote] 
This I've been doing from the last 3 days in sessions of 2-3 hrs. so now I have about 200 MB worth of repository. I do see all the packages in /var/cache/apt/archives in .deb format




[quote=https://wiki.ubuntu.com/AptMoveHowto]

Step three  Run apt move to create the archive structure
    Make sure you have enough disk space first. 
 ```
sudo apt-move get 
sudo apt-move move
``` [/quote] 
The first one 
```
apt-move get
``` went fine giving this output

updating from local package files....
All Done, exiting

The second however
```
apt-move move
``` gave the output 
Moving files .....
Skipping files ....
 gave the whole list of the files .deb which I've downloaded
& then gave
 All done, exiting.

Now my questions are :-

1. When it says updating from local package files what is it 
   updating? 
2. Should I run apt-get update before running the two apt-move 
   commands?
3. Is it normal for this skipping files or should it have given
   some other output?
             The wiki is silent as to what output should be given.
4. To have a verbose output should I just include
         ```
apt-move -v get
```or something different.

                   Looking for directions from all.

---

### Post by ShirishAg75 on 2006-01-08
Looking desperately for help guys, somebody plz. respond who has done this :)

---

### Post by az on 2006-01-11
[QUOTE=shirishag75]

1. When it says updating from local package files what is it 
   updating? [/QUOTE]
The local repository it is making in /mirrors.  This location is determined by /etc/apt-move.conf 

I will add this detail to the wiki page.


[QUOTE=shirishag75]

2. Should I run apt-get update before running the two apt-move 
   commands?
[/QUOTE]

It depends.  If you just installed the packages you want to include in your repo, the newest versions were just downloaded to /var/cache/apt/archive.  If you installed them a while ago and would like your local repo to have recent updates (assuming you have the breezy-updates and the breezy-security repositories active) then yes.
[QUOTE=shirishag75]

3. Is it normal for this skipping files or should it have given
   some other output?
             The wiki is silent as to what output should be given.
[/QUOTE]

"It would seem that some ubuntu packages are not inserted into the packages.gz file by apt-move. Is this because of some ubuntu-specific reposiitory structure?"  I don't know why it skips some packages, but that is why we need to throw away the packages.gz file and start over with dpkg-scanpackages.
[QUOTE=shirishag75]
4. To have a verbose output should I just include
         ```
apt-move -v get
```or something different.
[/QUOTE]
I don't know what you mean by this.


I made that wiki page after looking for a tool to make a custom cd repository.  I could not find one, so I used apt-move.  I am sure there are more elegant ways to get the job done, but this has worked for me.

---

### Post by GAJ on 2006-01-12
Hello folks,
May be this thread will help, I done my local repository as this : 
[http://ubuntuforums.org/showthread.php?p=633062#post633062](http://ubuntuforums.org/showthread.php?p=633062#post633062)

HTH,

---

### Post by GAJ on 2006-01-13
Hello again,

BTW, the commands : 
```

$ alien -d *.rpm
$ dpkg -i *.deb

``` seem to be very more productive than a local repository, as they prepare RPMs (if needed of course) and install deb packages correctly, then let Synaptic knowing and managing it without other hassle...

No more cents.

best regards,

---

