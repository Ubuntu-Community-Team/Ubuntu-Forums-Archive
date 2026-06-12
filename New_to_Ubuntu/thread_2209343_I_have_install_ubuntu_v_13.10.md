---
title: "I have install ubuntu v 13.10"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by cosmin-georgescu on 2014-03-05
I'm noob in this platform so i need some help ...

After the instalation try to install othe aplication with Ubuntu Software Center and i cant install nothing....
Also i have try to install chromiun browser using terminal commands :
cd /tmp
sudo dpkg -i package.deb
after i insert the password i receive this msg
dpkg status databese is locked by another process

So my question is how to install other apps in the ubuntu?

And second question is how to upgrade ubuntu 13.10 to ubuntu 14?

Thx you all for your help.
With respects,
Cosmin

---

### Post by bluefrog on 2014-03-05
a good chance is that the computer was working in the background while you were trying to update/install things manually.

Install directly the new version. it will save you some time
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by westie457 on 2014-03-05
Welcome [[COLOR=#000000]cosmin-georgescu[/COLOR]]("http://ubuntuforums.org/member.php?u=1908937")

> [COLOR=#000000]second question is how to upgrade ubuntu 13.10 to ubuntu 14?[/COLOR]

IMHO this is the more important question, so answered first.
14.04 Trusty is still under development and should not be installed unless you have some ability and knowledge to repair the system when things break.

Install 13.10 and upgrade when 'Update-Manager' says it is available. This will be a few weeks after the initial release to allow the devs to fix most of the issues found.


> [COLOR=#000000]dpkg status databese is locked by another process[/COLOR]

This happens when another process is using 'Apt' at the same time, Software Center being open and the Update Manager being open at the same time are well known culprits.
Check that neither of these is running and try in the terminal ```
sudo apt-get install chromium-browser
```

If there is any errors post them back here for another look at the problem.

---

