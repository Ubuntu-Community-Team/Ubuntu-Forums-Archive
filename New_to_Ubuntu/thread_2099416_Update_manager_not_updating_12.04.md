---
title: "Update manager not updating 12.04"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Yash Pal on 2012-12-29
OS -12.04 dual boot with windows 7
Laptop - Dell M5010

When I run the Update manager, the message is:[INDENT][SIZE=2][I][COLOR=Blue]The package information was last updated 64 days ago[/COLOR]. (It started with 4 days and has progressed)
[/I][/SIZE][SIZE=2][COLOR=Blue]*Press the 'Check' button below to check for new software updates.*[/COLOR][/SIZE]
[/INDENT]                                  
[SIZE=2]After pressing the 'Check' button, [SIZE=2]t[/SIZE]his is the message:[/SIZE]
 

                                 [SIZE=2][COLOR=Blue]*Failed             to download repository information*[/COLOR][/SIZE]
[COLOR=Blue]             [/COLOR][SIZE=2][COLOR=Blue]*Check your Internet connection.*[/COLOR][/SIZE]
                

                                       [SIZE=2]And these are the details: [/SIZE] 
 [SIZE=2][COLOR=Blue]*W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'main'/source/Sources' in Release file (Wrong sources.list entry or malformed file)*[/COLOR][/SIZE]
[COLOR=Blue]
[/COLOR] 
[SIZE=2][COLOR=Blue]*, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'main'/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)*[/COLOR][/SIZE]
[COLOR=Blue]
[/COLOR] 
[SIZE=2][COLOR=Blue]*, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'main'/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)*[/COLOR][/SIZE]
[COLOR=Blue]
[/COLOR] 
[SIZE=2][COLOR=Blue]*, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'main'/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)*[/COLOR][/SIZE]
[COLOR=Blue]
[/COLOR] 
[SIZE=2][COLOR=Blue]*, E:Some index files failed to download. They have been ignored, or old ones used instead.*[/COLOR][/SIZE]


[SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2]H[/SIZE]owever, sometimes the update manager also shows that some updates are t[SIZE=2]here, along with the messages above and [SIZE=2]t[/SIZE]hose updates can be installed. Could anyone tell me why the update manager is behaving like this (Downgrade manager?) and if there is any remedy.[/SIZE][/SIZE][/COLOR][/COLOR][/SIZE]


[SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2][SIZE=2]The same errors are shown wh[/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2][SIZE=2][SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2][SIZE=2]en I[/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE] use terminal and [SIZE=2]"[/SIZE][COLOR=Blue]sudo ap[/COLOR][/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2][SIZE=2][SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2][SIZE=2][SIZE=2][COLOR=Blue]t-get update && sudo apt-get upgrade"[/COLOR]
[/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE]

---

### Post by ibjsb4 on 2012-12-29
Please post the output of:

```
cat -n /etc/apt/sources.list
```

---

### Post by grahammechanical on 2012-12-29
There is a command you can try.

```
sudo rm /var/lib/apt/lists/* -rf
```

follow that with

```
sudo apt-get update
```

The first command removes/deletes all the sources scripts/files in the lists folder.

The second command will replace those scripts. This works. I had to do it some months ago when I was unable to update because one of those files had a missing header.

The scripts in the lists folder contain information about all the packages installed. Update Manager compares the information in those scripts with the information in the repositories to work out which packages on the machine can be updated.

It seems that if there is something wrong with those scripts then Update Manager will not update.

Another reason for this problem could be at the other end, in the repositories themselves. When that happens it usually get put right in a couple of days.

Regards.

---

### Post by Yash Pal on 2012-12-29
Thanks for guiding me

I first tried suggestion of[COLOR=Blue] 'grahammechanical', [COLOR=Black]after:[/COLOR][/COLOR][SIZE=2]

*[COLOR=Blue]sudo rm /var/lib/apt/lists/* -rf[SIZE=2]  [/SIZE][/COLOR]*[SIZE=2]and entering password for sudo, there was nothing, [SIZE=2]as generally linux works silently.

[SIZE=2][SIZE=2]T[/SIZE]hen [COLOR=Blue]sudo apt-get update [COLOR=Black]was entered and after 45 to 50 lines of messages, ([COLOR=Blue]fetched.... in... seconds[/COLOR] at end) the same error message was displayed:

[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][COLOR=Blue][COLOR=Black]   	 	 	 	 	 	   [/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][COLOR=Blue]*W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'main'/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)*[/COLOR][/SIZE]
[COLOR=Blue]   ...........
..............
..................
............[/COLOR]
  	 	 	 	 	 	   [SIZE=2][COLOR=Blue]*E: Some index files failed to download. They have been ignored, or old ones used instead.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR][SIZE=2][COLOR=Blue]*yashpal@yashpal-Inspiron-M5010:~$ ^C*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR][SIZE=2][COLOR=Blue][I]yashpal@yashpal-Inspiron-M5010:~$ 
[/I][/COLOR][/SIZE]


[SIZE=2][COLOR=Blue][SIZE=2][COLOR=Black]The output of command[/COLOR][/SIZE][/COLOR][/SIZE]
[SIZE=2][COLOR=Blue][SIZE=2][COLOR=Black]   	 	 	 	 	 	   [/COLOR][/SIZE][/COLOR][/SIZE]
cat -n /etc/apt/sources.list   is given below in separate reply

---

### Post by Yash Pal on 2012-12-29
As per suggestion of [COLOR=Blue]'ibjsb4' [/COLOR], the output of
cat -n /etc/apt/sources.list
is given below:
  	 	 	 	 	 	   [SIZE=2][COLOR=Blue]*yashpal@yashpal-Inspiron-M5010:~$ sudo cat -n /etc/apt/sources.list*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*1	# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*2	# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*3	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*4	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*5	# newer versions of the distribution.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*6	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*7	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*8	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]     [SIZE=2][COLOR=Blue]*9	## Major bug fix updates produced after the final release of the*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*10	## distribution.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*11	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates restricted main main'*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*12	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*13	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*15	## team. Also, please note that software in universe WILL NOT receive any*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*16	## review or updates from the Ubuntu security team.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*17	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*18	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*19	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*20	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*21	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*22	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu *[/COLOR][/SIZE] 
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*23	## team, and may not be under a free licence. Please satisfy yourself as to *[/COLOR][/SIZE] 
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*24	## your rights to use the software. Also, please note that software in *[/COLOR][/SIZE] 
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*25	## multiverse WILL NOT receive any review or updates from the Ubuntu*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*26	## security team.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*27	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*28	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*29	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*30	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*31	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*32	## N.B. software from this repository may not have been tested as*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*33	## extensively as that contained in the main release, although it includes*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*34	## newer versions of some applications which may provide useful features.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*35	## Also, please note that software in backports WILL NOT receive any review*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*36	## or updates from the Ubuntu security team.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*37	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports restricted main' main multiverse universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*38	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*39	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*40	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*41	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security main restricted*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*42	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*43	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*44	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*45	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security multiverse*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*46	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*47	## Uncomment the following two lines to add software from Canonical's*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*48	## 'partner' repository.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*49	## This software is not part of Ubuntu, but is offered by Canonical and the*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*50	## respective vendors as a service to Ubuntu users.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*51	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*52	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*53	*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*54	## This software is not part of Ubuntu, but is offered by third-party*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*55	## developers who want to ship their latest software.*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*56	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*57	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*58	# deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*59	deb-src [http://archive.canonical.com/](http://archive.canonical.com/) natty partner*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*60	deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main'*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*61	deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main'*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR]    [SIZE=2][COLOR=Blue]*62	deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security restricted main' main multiverse universe*[/COLOR][/SIZE]
[COLOR=Blue] [/COLOR][COLOR=Blue] [/COLOR][SIZE=2][COLOR=Blue][I]yashpal@yashpal-Inspiron-M5010:~$ 
[/I][/COLOR][/SIZE]
[SIZE=2][COLOR=Blue][COLOR=Black][SIZE=2]Password for sudo was not asked as both the above suggestions were completed in about 5 minutes[/SIZE][/COLOR]
[/COLOR][/SIZE]

---

### Post by ibjsb4 on 2012-12-29
52 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
57 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
58 # deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner
59 deb-src [http://archive.canonical.com/](http://archive.canonical.com/) natty partner

These four lines need to be removed, they are not part of precise 12.04 sources.  So again open a terminal and enter:

```
gksudo gedit /etc/apt/sources.list
```Remove them then try another update.

Also please use code tags in the future, its easier on the eyes.  Just highlight what you want in code tags and #.

```
yashpal@yashpal-Inspiron-M5010:~$ sudo cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
     2    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
     3    
     4    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5    # newer versions of the distribution.
     6    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
     7    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates restricted main main'
    12    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    13    
    14    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15    ## team. Also, please note that software in universe WILL NOT receive any
    16    ## review or updates from the Ubuntu security team.
    17    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
    18    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
    19    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
    20    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
    21    
    22    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
    23    ## team, and may not be under a free licence. Please satisfy yourself as to  
    24    ## your rights to use the software. Also, please note that software in  
    25    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    26    ## security team.
    27    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
    28    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
    29    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    31    
    32    ## N.B. software from this repository may not have been tested as
    33    ## extensively as that contained in the main release, although it includes
    34    ## newer versions of some applications which may provide useful features.
    35    ## Also, please note that software in backports WILL NOT receive any review
    36    ## or updates from the Ubuntu security team.
    37    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports restricted main' main multiverse universe
    38    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    39    
    40    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security main restricted
    41    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security main restricted
    42    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security universe
    43    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security universe
    44    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security multiverse
    45    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-security multiverse
    46    
    47    ## Uncomment the following two lines to add software from Canonical's
    48    ## 'partner' repository.
    49    ## This software is not part of Ubuntu, but is offered by Canonical and the
    50    ## respective vendors as a service to Ubuntu users.
    51    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    53    
    54    ## This software is not part of Ubuntu, but is offered by third-party
    55    ## developers who want to ship their latest software.
    56    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    57    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    58    # deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner
    59    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) natty partner
    60    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main'
    61    deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main'
    62    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security restricted main' main multiverse universe
yashpal@yashpal-Inspiron-M5010:~$ 
```[ATTACH]229322[/ATTACH]

---

### Post by Yash Pal on 2012-12-30
Thanks [COLOR=Blue]ibjsb4[/COLOR]
I do not know how to remove those 4 lines from the file; in fact I do not know how to enter the OS files. (though I was using Ctrl+ Alt +F1 to F7 about 10 - 12yrs back)
Anyway, it is not your headache and I will try to find out how to carry out the task.
I am also thankful for telling me how to[SIZE=1] [SIZE=2]use code tags[/SIZE][/SIZE][SIZE=2] (I did not know this).
[SIZE=2]As use of Linux [/SIZE] [/SIZE][SIZE=2][/SIZE]spreads among the population at large (Non IT people),  99% of users  will be  like me. ( who cannot edit/ modify system files.)
Since the system has not broken down, I will do a DVD install of 12.10 or 13.04 when required.
Thanks once again.

---

### Post by ibjsb4 on 2012-12-30
You came here looking for a fix and the fix is not that hard.  Why not finish what you started and fix it?  If my instructions are not clear, please ask questions.

---

### Post by Yash Pal on 2012-12-31
[COLOR=Navy]ibjsb4
[COLOR=Black]Please do not take my remarks amiss. I have already said that I will keep learning how to enter the system files. It may not be difficult but there is no environment here (in my place) for learning Linux,  unlike for Windows - for which you will find a fellow at each street corner.  Whatever I know is totally  self taught; in the process I have also sent into oblivion one PC already.

If I had not joined any forum, I don't think I could have learnt anything substantial. I have copied the  procedure you gave. Please keep helping others. [/COLOR]
[/COLOR]

---

### Post by Yash Pal on 2012-12-31
[COLOR=Navy]ibjsb4
[COLOR=Black]Please do not take my remarks amiss. I have already said that I will keep learning how to enter the system files. It may not be difficult but there is no environment here (in my place) for learning Linux,  unlike for Windows - for which you will find a fellow at every street corner.  Whatever I know is totally  self taught; in the process I have also sent into oblivion one PC already.

If I had not joined any forum, I don't think I could have learnt anything substantial. I have copied the  procedure you gave. Please keep helping others. People from halfway round the world have been helping. Not every body would be like me.[/COLOR]
[/COLOR]

---

### Post by ibjsb4 on 2012-12-31
ok

---

### Post by SunfireSSR on 2013-01-01
Having the same problem about updating.

Ran  sudo rm /var/lib/apt/lists/* -rf

Then ran sudo apt-get update. This helped a little.

Still get a lot of Ign. http and unable to fetch lines.

Ran cat -n /etc/apt/sources.list and this was the results.


 1	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    57	
    58	##Transmission BitTorrent
    59	deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) precise main
    60	deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) precise main
    61	
    62	##Ubuntu Tweak
    63	deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main
    64	deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) precise main
    65	
    66	##Medibuntu free/non-free
    67	##deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free
    68	##deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free
    69	##deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise non-free
    70	##deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise non-free
    71

---

### Post by SunfireSSR on 2013-01-01
BTW, update Manager gives me these errors:

Failed to Dowload repository Information.
Please check your internet connection.

Then I get this:

W:Failed to fetch [http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Update Manager will not update at all...

And there is nothing wrong with the internet connection since I did download some updates from the sudo apt-get update command, and firefox is working good.

---

### Post by NikTh on 2013-01-01
> **SunfireSSR said:**
> BTW, update Manager gives me these errors:

Failed to Dowload repository Information.
Please check your internet connection.

Then I get this:

W:Failed to fetch [http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/lavie-alexis/compiz-precise+placepluginfixed/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Update Manager will not update at all...

Hi ,

This is a specific problem with the specific PPA. You can remove this PPA to correct the problem. 
Run this command ```
gksudo software-properties-gtk
``` at the opened window goto "Other Software" and remove the PPA named : lavie-alexis

Thanks

---

