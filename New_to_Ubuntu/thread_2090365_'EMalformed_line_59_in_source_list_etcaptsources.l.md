---
title: "'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by compost1 on 2012-12-02
Hi all,
Not sure if this is the right place for this thread...
Pretty new to reporting here.  
Fresh install with an external dvd drive of 12.04 on an asus eeepc 1005PEB with maxed 2gig memory.
Problem is an error message:

Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

Is there any way possible to correct this problem?  Any help would greatly be appreciated.  

Thankyou

---

### Post by Cheesemill on 2012-12-02
Can you post the output of:
```
cat -n /etc/apt/sources.list
```

---

### Post by 3rdalbum on 2012-12-02
> **compost1 said:**
> 'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

Is there any way possible to correct this problem?  Any help would greatly be appreciated.  

Thankyou

There's a file at the location "/etc/apt/sources.list" (i.e. the "sources.list" file inside the "apt" folder inside the "etc" folder) that contains information about software repositories available to the system, to allow easy downloading and updating of software.

Some people edit this file directly, by hand. Sometimes people give directions about how to install a piece of software, involving editing this file. If you've followed any of these instructions, you may have followed them incorrectly and now the system doesn't understand what's on line 59 of the file.

You can edit the file as root:

```
gksudo gedit /etc/apt/sources.list
```

and either put a # at the start of the malformed line to disable that line, or fix the problem if it's obvious how to fix it.

Save your changes, then run this command:

```
sudo apt-get update
```

which will re-read the repositories list.

In future, add repositories to your system using the Software Sources program, or the add-apt-repository command as they will refuse to add any lines that are malformed.

---

### Post by ibjsb4 on 2012-12-02
For line numbers in gedit.  Go to Edit>Preferences>View

[ATTACH]228088[/ATTACH]

---

### Post by compost1 on 2012-12-02
As asked by Cheesemill..

blah@blah-blah:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5    
     6    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7    # newer versions of the distribution.
     8    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     9    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    14    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    20    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    21    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    22    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    30    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    31    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    32    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    40    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    41    
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    43    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    44    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    45    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    46    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    47    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    54    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    59    deb [http://archive.canonicalcom/precise](http://archive.canonicalcom/precise) partner
    60    deb-src [http://archive.canonicalcom/precise](http://archive.canonicalcom/precise) partner
    61    deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    62    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    63    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by arochester on 2012-12-02
Mistake...

Is: deb [http://archive.canonicalcom/precise](http://archive.canonicalcom/precise) partner

Should be: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

---

### Post by ibjsb4 on 2012-12-02
Line #60 is also malformed and need to be corrected.

However line #60 is for source code and something you will not use unless you are a developer.  You can remove all deb-scr sources simply by unchecking "source code" in "Software Sources".

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Cheesemill on 2012-12-02
Lines 59 and 60 are incorrect (you don't have a space before precise). Instead of fixing them you can delete these 2 lines as they are repeated correctly in lines 61 and 62.

To do this just edit the files with root privileges by hitting ALT+F2 and typing:
```
gksudo gedit /etc/apt/sources.list
```

Then go to Edit > Preferences > View and enable line numbers (thanks ibjsb4).
Delete lines 59 and 60 then you can save the file and exit gedit.

To check everything has worked open a terminal and type:
```
sudo apt-get update
```
If everything is OK you wont get any errors.

---

### Post by compost1 on 2012-12-02
Thank you all, that did the trick.

______________________________________________________________
Iligitamy noncarberundum = Don't let the bastards let you down
**[]("http://www.google.com/url?sa=t&rct=j&q=iligitamy%20noncarberundum&source=web&cd=1&cad=rja&ved=0CDMQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FIllegitimi_non_carborundum&ei=3Ji7ULHwIYK_igKU64HYCg&usg=AFQjCNEWjzRkiI_o7ak9nMURS9-hLQYz2w")**

---

### Post by ibjsb4 on 2012-12-02
On behalf of the WWW

Welcome  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by davejm73 on 2012-12-06
Hi there

I apologise for posting this now, but please help before I re-install 10.04.4 LTS. I was trying to install Skype!!!!

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

I have the same issue..can anyone tell me where or how I can fix this. Here is my text: 

# deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

---

### Post by ibjsb4 on 2012-12-06
Remove the last line:
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

And next to last line:
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
Edit it to read:
deb [http://archive.canonical.com/](http://archive.canonical.com/) ubuntu lucid partner
[https://help.ubuntu.com/community/Repositories/Ubuntu#Editing_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Editing_Repositories)

---

