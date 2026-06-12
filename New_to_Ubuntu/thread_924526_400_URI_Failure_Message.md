---
title: "400 URI Failure Message"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by imalberto2012 on 2008-09-19
When I attempt to update from the terminal I get this message:
E:Method Gave Invalid 400 URI Failure Message.
How can I correct this, how can I get the update command to work???
imalberto2012

First I typed, "sudo nano /etc/apt/sources.list" Then tried to update; nothing.
Just a minute ago I typed in "cat /etc/apt/sources.list". Then, "sudo apt-get udate". And again the same error message was displayed.

The output after the command, "cat /etc/apt/sources.list" is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by halitech on 2008-09-19
can you post the output of the following command from the terminal please

```
cat /etc/apt/sources.list
```

---

### Post by imalberto2012 on 2008-09-20
> **halitech said:**
> can you post the output of the following command from the terminal please

```
cat /etc/apt/sources.list
```
First I typed, "sudo nano /etc/apt/sources.list" Then tried to update; nothing.
Just a minute ago I typed in "cat /etc/apt/sources.list". Then, "sudo apt-get udate". And again the same error message was displayed.

I'm completely new to this forum stuff also, and since I didn't know how to post the result of the command you gave me. I pasted them in my original post.

Since I wasn't getting no responses, I now am posting it this way.  Hope this is the correct way!
imalberto2012

The output after the command, "cat /etc/apt/sources.list" is:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by halitech on 2008-09-20
you have one messed up sources.list file

here is mine as an example
```
daryl@ubuntu:~$ cat /etc/apt/sources.list
#

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-security universe


# Remastersys
deb http://www.remastersys.klikit.org/repository remastersys/

##Virtual Box Repository
# deb http://www.virtualbox.org/debian gutsy non-free

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports restricted main universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy commercial
# deb-src http://archive.canonical.com/ubuntu gutsy commercial

daryl@ubuntu:~$ 


```

Maybe try removing all the extra stuff in yours
```
gksu gedit /etc/apt/sources.list
```
this will open it in gedit where it will be easier to clean up the file. Once done, then do the ```
sudo apt-get update
``` and see what happens

Edit: oh, btw, cat /etc/apt/sources.list is simply a command to tell the terminal to show the file contents in the terminal so you can view them, it doesn't make any changes

---

### Post by Mornedhel on 2008-09-20
What's messed up about his sources.list ? As far as I can see, it's all default entries. Yours looks like it has (a bit) more cruft.

---

### Post by halitech on 2008-09-20
whats messed up? the fact that most of the enteries couldn't be verified. 

and I'm not sure what "cruft" is but the only added repos I have are for virtual box (not active) and remastersys, everything else is standard.

---

### Post by Mornedhel on 2008-09-20
> **halitech said:**
> whats messed up? the fact that most of the enteries couldn't be verified. 

and I'm not sure what "cruft" is but the only added repos I have are for virtual box (not active) and remastersys, everything else is standard.

Standard ? It's Canadian. Hardly standard :)

Well the installer will add those lines if it can't contact the repositories during the installation, for example if there is not net access at this point. Which will be the case if, say, the only way for him to get online is by wireless. This does not mean they won't be contacted later on ; for instance, if the installer installs the wireless drivers. Used to happen to me every time until I finally got an RJ45 cable.

"cruft" is another word for "clutter". It's not very widely used in the real world, I think.

On the other hand, after having taken a closer look to his sources.list, I do notice that several repositories have been mentioned twice. He's using both us.archive and archive for universe, for instance.

imalberto2012 : you should use halitech's sources.list if you don't mind having an extra repository in there.

---

### Post by halitech on 2008-09-20
> **Mornedhel said:**
> Standard ? It's Canadian. Hardly standard :)

standard for me, I'm Canadian :D

> Well the installer will add those lines if it can't contact the repositories during the installation, for example if there is not net access at this point. Which will be the case if, say, the only way for him to get online is by wireless. This does not mean they won't be contacted later on ; for instance, if the installer installs the wireless drivers. Used to happen to me every time until I finally got an RJ45 cable.

never had that problem, always made sure I had a  working internet connection before I tried to install anything

> "cruft" is another word for "clutter". It's not very widely used in the real world, I think.

I was thinking something along those lines

> On the other hand, after having taken a closer look to his sources.list, I do notice that several repositories have been mentioned twice. He's using both us.archive and archive for universe, for instance.

imalberto2012 : you should use halitech's sources.list if you don't mind having an extra repository in there.

just have the OP put a # in front of the line for remastersys although I'd say install it and then back up the system once everything is set up the way they want it :D

---

### Post by imalberto2012 on 2008-09-21
Well, I did what you suggested and I still get the same message.  I do have a wired network connection, I'm connected right now. I'm going to keep on experimenting until I solve this problem. When I do, I'll post it.  Thanks everybody!!!!    imalberto2012

---

### Post by angelot on 2008-10-05
Are you sure the only repos your loading is in the sources.list?

I got the same message, and after removing the playdeb repo from /etc/apt/sources.list.d/ the error did not show again.

In the sources.list.d directory all "non-standard" repos are listed. At my 8.04 at least. Like medibuntu and playdeb. Apt will load these repos as if they were a part of your sources.list...

Did that make any sence?

angelot

---

### Post by Mikolaj.Q on 2008-10-05
I had the same problem. In my case the playdeb repository was responsible for error message. I had a playdeb entry (deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/) in main source.list, not in folder /etc/apt/sources.list.d/  When I removed it error disappeared. So remove playdeb entry WHEREVER it is. I think this is playdeb-beta issue. They should fix it.

---

### Post by NewJack on 2008-10-18
Yep, just had the same problem myself.  Once I removed it from my sources.list, everything was back to normal.

---

### Post by jerome1232 on 2008-10-18
I think the problem is in order to use that playdeb repo you need to have this apturl refresh package installed.

It's on this page [http://www.playdeb.net/available_games.html](http://www.playdeb.net/available_games.html)

this a direct link to the deb file [http://www.playdeb.net/apturl_0.2.6-0~getdeb0_all.deb](http://www.playdeb.net/apturl_0.2.6-0~getdeb0_all.deb)


Might be something they added recently so the issue just kinda cropped up.

---

### Post by SLA_leandrin on 2008-10-25
Thanks angelot, I had the same problem.... solved now.

---

