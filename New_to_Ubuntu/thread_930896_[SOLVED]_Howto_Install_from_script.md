---
title: "[SOLVED] Howto Install from script"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by SBFree on 2008-09-26
Hi:
I would like to build a rig to read email to my Mom who recently went blind. I found a site offering a script and software, LinuxSpeaks [http://www.joekamphaus.net/]("http://www.joekamphaus.net/"), but I do not know enough about Linux and Ubuntu to install the tarball. I can download it and extract the files but cannot figure out how to run the script called 'install.sh' . In the graphic environment I get a spoken message that I must be root and trying to run the script in the terminal using 'sh install.sh' generates an error "40:Syntax error "}" unexpected. Any help would be appreciated. Thanks.
Scott

---

### Post by nkri on 2008-09-26
Open up a Terminal (Applications>Accessories>Terminal), and find the directory in which you put the folder (for example, the desktop).

In the terminal, type
```
cd *directory*
```

For example, if it's on the desktop, you would type
```
cd /home/*username*/LinuxSpeaks-alpha-1.10
```

You would then type
```
sh install.sh
```
to run the install script.

If it says something about insufficient privileges, type
```
sudo sh install.sh
```
(it will ask for your password...it won't show anything, so just type it in and hit enter)

This should do it.  If you have any questions, don't be afraid to ask!

Good luck!
-nkri

---

### Post by twitch2197 on 2008-09-26
try cd'ing to that folder and typing ```
sudo sh install.sh
```
that's what i think it'd be.

EDIT: oops, too late. listen to the person before me.

---

### Post by SBFree on 2008-09-26
Thank you, it looks like I was on the right track and have an error in the script.

---

### Post by twitch2197 on 2008-09-26
yeah, i've gotten a few install scripts that were messed up. frustrated me too :lolflag:

---

### Post by SBFree on 2008-09-28
So I got the install script to run. This is really embarrassing, how do I start and top the program it installed? The readme file isn't helpful. It is a text based front end that 'speaks' it's output for use by the blind. There is a Uninstall script that removes a few directories, one of which is named 'Linuxspeaks'. Does that sound like the place to look? What should I look for to execute the program? Thanks.
Scott

---

