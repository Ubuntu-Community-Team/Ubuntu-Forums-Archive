---
title: "Ubutnu software center and Synaptic manager dont work...."
date: 2012-02-13
forum: New to Ubuntu
---

### Post by ethanzh on 2012-02-13
Ok so whenever I start ubuntu software center, there is a tab below saying that it is starting, but that dissapears after about 110 seconds.

I was told to use Synaptic Package manager, but I recieve this rror upon startup:

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I booted and Installed ubuntu from a usb drive (E:)

Any help woul be appreicated..

---

### Post by oldos2er on 2012-02-13
Can you run ```
cat /etc/apt/sources.list
``` in a terminal, and post the output here?

---

### Post by ethanzh on 2012-02-14
I get this,

ethanzh@ethanzh-HP-Mini-110-1100:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
ethanzh@ethanzh-HP-Mini-110-1100:~$


So im guessing those are my repositories?

---

### Post by HiImTye on 2012-02-14
make sure software center is properly closed
```
killall  -9 software-center
```now reload your package information
```
 sudo apt-get update
```

---

### Post by cortman on 2012-02-14
The lucid "partner" repository is added twice on sources.list (see the error message dpkg returned). Why this is I don't know, but you can open sources.list with a text editor like gedit-

```
gksu gedit /etc/apt/sources.list
```

And remove the duplicate 

```
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

lines.

To be honest, I'm not sure why you'd need the lucid partner repositories anyway, if you're running maverick, and have the maverick partner repos enabled (as you do). You could remove all reference to lucid partner repos.

---

### Post by ethanzh on 2012-02-14
> **HiImTye said:**
> make sure software center is properly closed
```
killall  -9 software-center
```now reload your package information
```
 sudo apt-get update
```

I get this:

ethanzh@ethanzh-HP-Mini-110-1100:~$ killall -9 software-center
software-center: no process found
ethanzh@ethanzh-HP-Mini-110-1100:~$ sudo apt-get update
[sudo] password for ethanzh: 
E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
ethanzh@ethanzh-HP-Mini-110-1100:~$

---

### Post by ethanzh on 2012-02-14
I still don't get how an of this is keeping the software center from even STARTING?

---

### Post by ethanzh on 2012-02-14
Just to note: whenever I goto the update manager iu get this error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)'

---

### Post by cortman on 2012-02-14
> **ethanzh said:**
> Just to note: whenever I goto the update manager iu get this error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)'

Have you tried my suggestion?

---

### Post by oldos2er on 2012-02-14
> **ethanzh said:**
> I still don't get how an of this is keeping the software center from even STARTING?

None of the package manager front-ends will work with a borked sources.list file. Cortman posted the answer to your problem in post #5.

---

### Post by jerrrys on 2012-02-14
I risk sounding picky, but would you run:

cat -n /etc/apt/sources.list

and post

---

### Post by ethanzh on 2012-02-14
When I do the first command cortman said, it opens a blank text file named sources. He also gave two more lines of code. Do those go into the document or into the terminal?

---

### Post by cortman on 2012-02-14
> **ethanzh said:**
> When I do the first command cortman said, it opens a blank text file named sources. He also gave two more lines of code. Do those go into the document or into the terminal?

It's "sources.list" not just plain "sources". It's probably a good idea to copy/paste the code into the terminal rather than type it, for accuracy.
The two lines are the ones you need to delete from sources.list.

---

### Post by ethanzh on 2012-02-14
> **cortman said:**
> It's "sources.list" not just plain "sources". It's probably a good idea to copy/paste the code into the terminal rather than type it, for accuracy.
The two lines are the ones you need to delete from sources.list.
The sources.listhas all my repos in it. about your other two commands, where do those go?  (the 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by ethanzh on 2012-02-14
> **jerrrys said:**
> I risk sounding picky, but would you run:

cat -n /etc/apt/sources.list

and post
I get this 

ethanzh@ethanzh-HP-Mini-110-1100:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick main restricted
     6    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
    11    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick universe
    17    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick universe
    18    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates universe
    19    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick multiverse
    27    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick multiverse
    28    deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
    29    deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
    30    
    31    ## Uncomment the following two lines to add software from the 'backports'
    32    ## repository.
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    39    # deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    46    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
    47    
    48    ## Uncomment the following two lines to add software from Ubuntu's
    49    ## 'extras' repository.
    50    ## This software is not part of Ubuntu, but is offered by third-party
    51    ## developers who want to ship their latest software.
    52    # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
    53    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
    54    
    55    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
    56    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
    57    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
    58    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
    59    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
    60    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
    61    deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
    62    deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
    63    deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
    64    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
ethanzh@ethanzh-HP-Mini-110-1100:~$

---

### Post by jerrrys on 2012-02-14
It stopped at 61 so comment out (#) 61.  But then i expect to stop at 62 and do the same thing.  So to get running again be prepared comment out 61 to 64.

In terminal enter:

gksudo gedit /etc/apt/sources.list

and make your list look like this:

#deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
    #deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
    #deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
#deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

and save

---

### Post by oldos2er on 2012-02-14
> **ethanzh said:**
> The sources.listhas all my repos in it. about your other two commands, where do those go?  (the 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

Those aren't commands. You need to *remove* the last four lines of that file (the ones with "lucid"), save it, exit, and run ```
sudo apt-get update
```

---

### Post by ethanzh on 2012-02-15
> **oldos2er said:**
> Those aren't commands. You need to *remove* the last four lines of that file (the ones with "lucid"), save it, exit, and run ```
sudo apt-get update
```
OH my god thank you so much it is working now!!!!!!!!!

---

### Post by oldos2er on 2012-02-15
Glad to hear it. Could you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

