---
title: "Want to understand &amp; implement AptMove"
date: 2005-12-27
forum: Repositories &amp; Backports
---

### Post by ShirishAg75 on 2005-12-27
[LEFT]Hi all,
[/LEFT]
             Read the wiki at [https://wiki.ubuntu.com/AptMoveHowto]("https://wiki.ubuntu.com/AptMoveHowto") & installed the packages required.When I used the command :-
     [LEFT]
[/LEFT]
        ```
[LEFT]sudo apt-get -d install sysv-rc-conf[/LEFT]
   
```  it just downloaded the software, it's just an example.Now I wanna install this software but at the same time also wanna makea local repositery of stuff I've downloaded or will be downloading & as the space fills up would burn a CD as a backup so I don't have to re-download them again. 

Q1. So should I just download first all the packages that I need
    first & then burn them onthe cd & then install them?

Q2. What does these commands mean :-
     
```

     [LEFT]cd /mirrors/debian/dists/stable/main/binary-i386

sudo dpkg-scanpackages ../../../../pool/ /dev/null > Packages[/LEFT]
 
``` Q3. what is there in this binary-i386 by default? If I download 
    any/all of the packages which I want they have some kind of 
    backup or what. Can somebody explain this one?

Q4. The sudo dpkg-scanpackages have been given this ../../../pool/
    what is this command? Although would be reading the man of
    spkg-scanpackages but sometimes somebody explaining is better.
    the packages do they get installed or some kind of backup or what?

---

