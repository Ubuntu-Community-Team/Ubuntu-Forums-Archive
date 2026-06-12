---
title: "malformed line 59 in source list /etc/apt/sources.list (dist parse)"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by chappymonya1231 on 2014-03-19
Hey all, extremely new to ubuntu. I used to do a lot of funky things on mdos but this terminal is a whole new beast. I keep getting the above code when trying to add certain simple programs to my book. I appreciate the help guys and gals. Thanks

---

### Post by westie457 on 2014-03-19
Welcom chappymonya1231.
Let us see what the problem is. Copy and paste this into a terminal ```
cat -n /etc/apt/sources.list
```
Highlight all of the output in the terminal > right-click and select copy

In an 'Adv Reply'  here click on the # in the icons just above the text pane and paste between the [code] brackets. This will preserve the formatting of the text and make it easier to read.

---

### Post by Iowan on 2014-03-19
You can use the **nano** editor to list the file. **nano +58,1 /etc/apt/sources.list ** should open the file and place the cursor on line 58 (column 1)... in case it was the culprit that caused line 59 to be malformed. Otherwise, check or post that section of the file.

---

### Post by chappymonya1231 on 2014-03-19
```
chapman@chapman-X200CA:~$ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130801-07:00]/ precise main


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/precise partner
deb-src http://archive.canonical.com/precise partner
chapman@chapman-X200CA:~$ cat -n /ect/apt/sources.list
cat: /ect/apt/sources.list: No such file or directory
```

---

### Post by chappymonya1231 on 2014-03-19
I did that **n****ano **and the last two lines are different both in color and they do not begin with #

---

### Post by chappymonya1231 on 2014-03-19
```
chapman@chapman-X200CA:~$ cat -n /etc/apt/sources.list     1	# deb cdrom:[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130801-07:00]/ precise main
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6	deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17	deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27	deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41	deb http://security.ubuntu.com/ubuntu precise-security universe
    42	deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43	deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu precise partner
    51	# deb-src http://archive.canonical.com/ubuntu precise partner
    52	
    53	## Uncomment the following two lines to add software from Ubuntu's
    54	## 'extras' repository.
    55	## This software is not part of Ubuntu, but is offered by third-party
    56	## developers who want to ship their latest software.
    57	# deb http://extras.ubuntu.com/ubuntu precise main
    58	# deb-src http://extras.ubuntu.com/ubuntu precise main
    59	deb http://archive.canonical.com/precise partner
    60	deb-src http://archive.canonical.com/precise partner
chapman@chapman-X200CA:~$ 



```

---

### Post by westie457 on 2014-03-19
> deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Edit lines 59 +60 ```
gksudo gedit /etc/apt/sources.list
```
to make them like these.
deb [http://archive.canonical.com/](http://archive.canonical.com/)[COLOR=#ff0000]ubuntu [/COLOR]precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/)[COLOR=#ff0000]ubuntu [/COLOR]precise partner

Proof read, save the file and close gedit

Then ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chappymonya1231 on 2014-03-19
Fantastic. Thank you kindly.

---

