---
title: "Firefox"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by manners2345 on 2008-08-08
I have seemed to have developed a problem with Firefox 3.0. I have removed it using s package manager, which apparently just removes from directories, but leaves it on the computer cached locally. I used gksudo, to remove every file I could find for firefox 3.0, downloaded it again and installed, still same problem. Something about not being able to implement security, something about profile(deleted all files I could find)

:confused:

manners2345

Thank you

---

### Post by Crafty Kisses on 2008-08-08
Have you tried downgrading to Firefox 2?

---

### Post by InfinityCircuit on 2008-08-08
You stated the attempted solutions but not the problem!  What is wrong with Firefox? :)

If you want to remove it all, then:
dpkg -L firefox-3.0 | xargs sudo dpkg -P
sudo dpkg -P --force-all firefox-3.0
sudo apt-get install -f
rm -rf ~.mozilla

---

### Post by pi.boy.travis on 2008-08-08
What exactly is your problem?  You really shouldn't totally uninstall Firefox, because it has lots of components that other Ubuntu features require, like the Gecko rendering engine.

---

### Post by manners2345 on 2008-08-08
I said the problem seemed to be with implementing security and profile, Click "OK" and firefox crashes

Thank You

---

### Post by pi.boy.travis on 2008-08-09
> **manners2345 said:**
> I said the problem seemed to be with implementing security and profile, Click "OK" and firefox crashes

Thank You

Are you getting an error message/window?  What security features are you trying to use that don't work?

---

### Post by bpowell2005 on 2008-08-09
> **manners2345 said:**
> I said the problem seemed to be with implementing security and profile, Click "OK" and firefox crashes

Thank You

Try running Firefox from the command prompt with "firefox -ProfileManager" this will load the profile manager, then create a new profile, and run firefix under that profile...see if this gets around the problem...if so, delete the corrupted profile.

---

