---
title: "Apt-get Update repeat"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by penguin970 on 2014-04-17
I understand you guys get this a lot, and i know it's annoying

But i need a solution to this thing that keeps happening
And anything i try does not work

```
W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) raring-getdeb/games i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_raring-getdeb_games_binary-i386_Packages)W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) raring-getdeb/games i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_raring-getdeb_games_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) raring-getdeb/games i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_raring-getdeb_games_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) raring-getdeb/games i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_raring-getdeb_games_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) raring-getdeb/games i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_raring-getdeb_games_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



```

How exactly to remove the file?
I know how to access it, but when i try to delete the duplicate sources, BOOM there is like 50 million lines of damn code i hafta sort through
And finding does not work because the next line over it has the same words
So yea
If anyone knows anything about this, then please send help, and tell me how to tell this piece of code that is the damn duplicate list entry to ___ off
(Answers include A:Buzz B:Screw C:Get
 Or 
D:I SWEAR I WILL SUMMON ALL THE UNHOLY DEMONS OF MACINTOSH AND STEVE JOBS TO BURN YOUR ENTIRE FAMILY IF YOU DO NOT ___  OFF(insert a secondary answer choice here))

---

### Post by Bashing-om on 2014-04-17
penguin970; Hi ! Welcome to the forum.

Let's just take a look at the situation and see:
post pack - Between code tags - the out put of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

If it turns out that you are running 'raring' - release 13.04, well, that release is End Of Life. It is no longer supported and you need to upgrade to a current release.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by penguin970 on 2014-04-17
Nope, i'm running 12.04 Ubuntu

Wait, so you want me to show the code that came out with those commands in the post?
Ok

```
 root@foup-VGN-NS140E:~# cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release i386 (20140204)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41    deb http://security.ubuntu.com/ubuntu precise-security universe
    42    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu precise partner
    51    deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
root@foup-VGN-NS140E:~# cat /etc/apt/sources.list.d/*.list
deb http://archive.getdeb.net/ubuntu raring-getdeb games
deb http://archive.getdeb.net/ubuntu raring-getdeb games
deb http://archive.getdeb.net/ubuntu raring-getdeb games
deb http://archive.getdeb.net/ubuntu raring-getdeb games
deb http://archive.getdeb.net/ubuntu raring-getdeb games
deb http://archive.getdeb.net/ubuntu raring-getdeb games
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/shnatsel/zram/ubuntu precise main
deb-src http://ppa.launchpad.net/shnatsel/zram/ubuntu precise main
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam



```

---

### Post by grahammechanical on 2014-04-17
> raring.getdeb/games i386 packages

If you are running 12.04 how come we are seeing that? Have you installed any PPAs from that site and have you installed them more than once? 

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

[http://www.playdeb.net/updates/Ubuntu/13.04/](http://www.playdeb.net/updates/Ubuntu/13.04/)

I think that you installed one of getdebs 13.04 games and as 13.04 has reached End of Life the getdeb repository is also closed. Hence the error. You need to edit Software sources and remove those entries for getdeb.

Regards.

---

### Post by penguin970 on 2014-04-17
I did not download twice from either site, i do not think i have even seen those sites
But what do i know?

OK so i did what you said

...
And i love you so much, i thank you guys for what you guys did today, LET ALL THE LINUX USERS KNOW ALL YOUR CONTRIBUTIONS TO ONE MAN'S DREAM TO DOING RANDOM CRAP ON THEIR CRAP COMPUTER
THANK YOU ALL

---

