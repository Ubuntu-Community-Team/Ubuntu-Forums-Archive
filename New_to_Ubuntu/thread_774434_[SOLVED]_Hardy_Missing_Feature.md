---
title: "[SOLVED] Hardy Missing Feature?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by renfrew on 2008-04-29
I'm posting this from work (Windoze 2000) and am having a bit of a brain freeze.  In Gutsy, if I typed in say fglrxinfo on the command line I'd get a message saying it wasn't installed and tell me what package to install.  

In Hardy Beta that feature was working great.  

I did a complete refresh on the 24th and installed Hardy stable, now I don't seem to have that feature... I just get a msg saying it can't find flgrxinfo, for example... but i get no message about what package to install to get fglrxinfo...

What package do I need to get that functionality back?

BTW, I know what package I need to install to get fglrxinfo, I want to know what package tells you about missing packages...  

and while I'm at it, apport seems to be broken, it's not actively capturing program crashes like when flash loses it while trying to watch an flv from within firefox

---

### Post by OffAxis on 2008-04-29
works on mine (7.10 and a fresh 8.04) from the command line...
```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
-bash: fglrxinfo: command not found

```
It's a function of the shell, so I think it's enabled by default.

maybe you misspelled it?
what's the exact error message?

---

### Post by renfrew on 2008-04-29
Thanks for the quick response.  That's just it, I don't get an error message as such, it's as if I did a 'find' and got no results...  can't find fglrxinfo...

I'm using the default Bash shell for what its worth, I didn't know it was a function of shell. I always assumed it was a separate program/process...  In either case, it's busted on my install.  

One thing worth noting is that I saved all the packages I had installed while running beta as a list and used that list from within Synaptic to recover my installed progs (stuff like celestia, boincmanager, bitchx, stellarium, some games like wesnoth and glest, etc), after I did the Hardy stable Live CD install...  I don't have any forced versions from what I can see, everything is normal, update manager is happy, etc, etc

Far as I can tell I'm missing something... 
maybe I should dpkg-reconfigure the whole works...

btw:  I'm just using fglrxinfo as an example, it's happened with a couple of things

---

### Post by renfrew on 2008-04-29
I ended up doing the dpkg-reconfigure after all... and it works fine.

Either I fixed it with dpkg-reconfigure or I'm not as good a typist as I'd like to think...  thanks to OffAxis for suggesting that it might be my (lack of) spelling ability and not Hardy :D

---

