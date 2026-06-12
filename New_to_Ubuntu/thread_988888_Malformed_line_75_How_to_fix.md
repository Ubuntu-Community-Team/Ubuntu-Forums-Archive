---
title: "Malformed line 75: How to fix ?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by abooks on 2008-11-21
I was mucking about in kubuntu and buggered my APT.I'm told I have a malformed line 75 in source list /etc/apt/sources.list, and I have to remove #'s, but how do I get there to do it? sudo gedit and others don't seem to work

---

### Post by iaculallad on 2008-11-21
> **abooks said:**
> I was mucking about in kubuntu and buggered my APT.I'm told I have a malformed line 75 in source list /etc/apt/sources.list, and I have to remove #'s, but how do I get there to do it? sudo gedit and others don't seem to work

You can start editing your sources.list file by:

```
kdesu kedit /etc/apt/sources.list
```

Note:

gedit = Ubuntu
kedit = (k)Ubuntu

EDIT:

Yes, that should be **kdesu** and not **gksudo**.

---

### Post by Paqman on 2008-11-21
> **abooks said:**
> sudo gedit and others don't seem to work

Try:
```

kdesu kate /etc/apt/sources.list

```

"sudo gedit" won't work because gedit is a gnome app that you won't have installed. Incidentally, you should use kdesu (or gksu for Gnome) when launching graphical apps; sudo is just for the commmand line.

---

### Post by abooks on 2008-11-21
I tried gksudo, and was told I didn't have it, but could download it...but of course I couldn't because APT is sick (plus I can't connect to the net)
But I forgot to include "Our story thus far":

[sudo] password for walt:
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
walt@desktop:~$ list /etc/apt/sources.list
bash: list: command not found
walt@desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
walt@desktop:~$ sudo /etc/apt/sources.list
sudo: /etc/apt/sources.list: command not found
walt@desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/gutsy](http://archive.ubuntu.com/ubuntu/gutsy) main
walt@desktop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
walt@desktop:~$ ==>.sudo gedit /etc/apt/sources.list
bash: ==: command not found
walt@desktop:~$ edit etc/apt/sources.list
Warning: unknown mime-type for "etc/apt/sources.list" -- using "application/*"
Error: no write permission for file "etc/apt/sources.list"
walt@desktop:~$ sudo edit /etc/apt/sources.list
Warning: unknown mime-type for "/etc/apt/sources.list" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
walt@desktop:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
walt@desktop:~$ sudo apt-get install gksu
E: Malformed line 75 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
walt@desktop:~$    

But thanks for the kedit tip! This all started when I couldn't install KPPP on desktop in ubuntu to get my dongle working. I know, if I had a brain I'd take it out and play with it til I broke it. . .

Edit: OK, I got in with kate (though I got scolded: Error: /var/tmp/kdecache-walt" is owned by uid 1000 instead of uid 0 (and two others owned by uid 1000 instead of uid 0)

However, ## means commented out, right? which ones do I get rid of?

---

### Post by abooks on 2008-11-21
OK, I got rid of everything but one line: 

deb [http://archive.ubuntu.com/ubuntu/gutsy/main](http://archive.ubuntu.com/ubuntu/gutsy/main)

APT still doesn't work. . .do I get rid of this too?

---

### Post by oldos2er on 2008-11-21
Line 75 is the last line in the file, so add a # at the beginning of the line to comment it out.

---

### Post by jimreynold2nd on 2008-11-21
That sounds weird.... Can you please post your source.list file?

---

### Post by abooks on 2008-11-21
> **oldos2er said:**
> Line 75 is the last line in the file, so add a # at the beginning of the line to comment it out.

Disabling line 75 did it! But how did you know that was line 75? Is "line 75" always the last line in any file?

---

### Post by adult swim on 2008-11-22
nope!  if you count down every line from the top, including lines that have nothing on them, you can get the line number.

---

### Post by plucky on 2008-11-22
> **abooks said:**
> Disabling line 75 did it! But how did you know that was line 75? Is "line 75" always the last line in any file?

In gedit you can turn on line numbering **Edit > Preferences** and tick the box that says "Display line numbers".

---

### Post by oldos2er on 2008-11-22
> **abooks said:**
> Disabling line 75 did it! But how did you know that was line 75? Is "line 75" always the last line in any file?

 Um, no. I copied and pasted your sources.list into gedit, which can show line nos.

---

### Post by CatKiller on 2008-11-22
For what it's worth, you were missing a space. ```
deb http://archive.ubuntu.com/ubuntu/gutsy main
``` should be ```
deb http://archive.ubuntu.com/ubuntu/ gutsy main
``` like the others. It doesn't matter in this case, since the main Gutsy repository is included in the line above.

---

