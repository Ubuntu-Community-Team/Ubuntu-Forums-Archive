---
title: "How To: Setting up numlock on start up (only for Edy Eft 6.10)"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Pawel on 2006-11-01
Hello!

Few days ago i was updated my dapper to edgy.
Some of configurations variable doesn't work so i try to set in by my own.
Numlock problem is one of them.

Normally script which is located in /etc/init.d/console-setup should enable numlock in consoles. Usually it works but not in my case with edgy.

This little howto describes how to enable numlock in every console druning startup only for Edy Eft. For previous versions of Ubuntu you should look here:
[http://ubuntuforums.org/showthread.php?t=14930](http://ubuntuforums.org/showthread.php?t=14930)

I was write simple script that provides install and uninstall all files made by install.

Just download one of 2 attachments (one is for Polish speaking users //cnumlock-pl.sh.tar.bz2//, 2nd is for english speaking users //cnumlock-en.sh.tar.bz2//).

Download it, unpack and go into your terminal:
1. login as root
2. change current dir do sciript dir (e.g. cd Desktop)
3. run script:
for Polish users or
```
./cnumlock.sh
``` 
for English users
```
./cnumlock-en.sh
``` 
4. Follow the instructions in script.
----------------------------------------

Notes: Script is simple so it may includes little bugs but it works (tested  on my and my Brothers computer with edgy installed). It consist of code which is grabbed form older versions of init scripts.
License: GPL of course :)
Author: Pawe&#322; W.

> This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

**What scripts really do?**
In short:
In install (1)
1. It makes little startup script in /etc/init.d/ directory called setleds.sh
2. Next it makes symbolic links for properly startup in diffrent init state.
---------
In uninstall (0)
1. Uninstall all files created druning install.
---------

Please fell free to post your comments here :)

Best regards
Pawel

---

### Post by gschoper on 2006-11-06
This didn't work for me. Running a fresh install of Edgy.

gschoper

---

### Post by stalefries on 2006-11-06
I don't know if this is specific to just me and my laptop, but turning on Num Lock will make it seem as if I am holding down the Fn key. So, instead of "i", it'll type 5. This is annoying because, among other reasons, some of the characters in my various passwords use keys that have alternate, Fn-keys that are valid characters.

---

### Post by Crashmaxx on 2006-11-07
Didn't work for me. Looked like it was gonna, but didn't by the time it finished booting.

---

### Post by Pawel on 2006-11-09
Hello!

try to open gedit and paste into:

> #!/bin/sh   
for i in `seq 1 12` 
do
setleds +num < /dev/tty$i
done
exit 0

Then save as cnumlock.sh eg. on your Desktop.




Next give it right permissions to execute:
```
chmod a+x cnumlock.sh
```
 
login in terminal as root:
```
sudo su
```

next:
```
./cnumlock.sh
```
**not** sh cnumlock.sh.

Switch to console e.g. 2
numlock should be turn on (only to reebot ;-) )
tell me if that works.

Also please tell me what exactly are you do. Step by step.
you may attach what script shows terminal. thats important!


best regards
Pawel

---

