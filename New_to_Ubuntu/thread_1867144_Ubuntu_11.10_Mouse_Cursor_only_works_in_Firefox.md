---
title: "Ubuntu 11.10 Mouse Cursor only works in Firefox"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by slayner117 on 2011-10-22
I have already downloaded and extracted the Cursor Theme into my icons folder, and the Icon *will work, however only in Firefox. Outside of that, IE: desktop folders etc, I am back to the simple white cursor. Please help me out here, thank you in advance.

---

### Post by slayner117 on 2011-10-22
bump

---

### Post by slayner117 on 2011-10-22
buuuump

---

### Post by Silent Warrior on 2011-10-22
Welcome to the wonderful world of the bulletin board: It's not an instant messenger, nor is it real time IRC.

As for your question, have you tried logging out and back in, or rebooted? (I think the terminology is 'update icon cache', or summat. You could do that instead, if you find out how. I've never gone looking, myself.) Also, what desktop environment are you using? GNOME and Unity (XFCE, LXDE?) use settings from one place, KDE from another. Since, I believe, Firefox is a GTK+ application, changing cursor settings native to KDE will do bugger all for Firefox (and other GTK+ things).

---

### Post by slayner117 on 2011-10-22
Sorry about that, Anyway I am using Unity Gnome I believe. The cursor is made for the version I am using. And yes, I have tried rebooting.

---

### Post by Silent Warrior on 2011-10-22
Hey, now I notice that it does this for me as well! [CONFIRMED, then]

That is a bit strange... Maybe... the 'proper' setting is in gnome-tweak-tool, but the desktop/Nautilus (file manager) read their cursor setting from somewhere else, like GConf, due to modifications? Older Gnome 2 preferences? Doesn't sound right, but that's the only theory I have. My efforts at finding a configuration entry for this have turned up nothing at all.

---

### Post by velcom on 2012-02-04
same here!
Ubuntu 12.04
cursor theme only works within firefox

---

### Post by sffvba[e0rt on 2012-02-04
I just got a fix for this an hour ago while changing my mouse cursor theme - [http://www.ubuntugeek.com/reset-system-wide-cursor-theme.html](http://www.ubuntugeek.com/reset-system-wide-cursor-theme.html)


Cheers
404

---

### Post by joetait on 2012-02-04
> **not found said:**
> I just got a fix for this an hour ago while changing my mouse cursor theme - [http://www.ubuntugeek.com/reset-system-wide-cursor-theme.html](http://www.ubuntugeek.com/reset-system-wide-cursor-theme.html)


Cheers
404

That does solve it on Unity, but not on Gnome for some reason :(
Oh well, a small price

---

### Post by Dennis N on 2012-02-04
> **joetait said:**
> That does solve it on Unity, but not on Gnome for some reason :(
Oh well, a small price

After you set the Unity Mouse cursor, you need to set the Gnome Mouse cursor with Gnome Tweak (Advanced Settings) to be the same. It will change instantly. I think Ubuntu Tweak will do it also.

---

### Post by joetait on 2012-02-06
> **Dennis N said:**
> After you set the Unity Mouse cursor, you need to set the Gnome Mouse cursor with Gnome Tweak (Advanced Settings) to be the same. It will change instantly. I think Ubuntu Tweak will do it also.

I just realised that it did work, but only after a reboot. Also, what is Ubuntu tweak as opposed to Gnome tweak - I can only find the latter?

---

### Post by Dennis N on 2012-02-06
> **joetait said:**
> I just realised that it did work, but only after a reboot. Also, what is Ubuntu tweak as opposed to Gnome tweak - I can only find the latter?

Here is a story that explains a bit about it:
 
[http://www.omgubuntu.co.uk/2011/12/new-version-of-ubuntu-tweak-released/](http://www.omgubuntu.co.uk/2011/12/new-version-of-ubuntu-tweak-released/)

I would install from Ubuntu Tweak Stable PPA so you get updates afterwards. There is a link on that page.

---

### Post by joetait on 2012-02-06
Looks really good, thanks very much :)

---

### Post by laserator on 2012-04-04
It does that on mine too. Except its not just firefox its any application, but wont show in the normal desktop. I have unity gnome.

---

### Post by cottfcfan on 2012-04-04
What I always have to do is edit the file usr/share/icons/default/index.theme.
```
sudo gedit /usr/share/icons/default/index.theme
```
And change the line inherits= to the name of your cursor. eg
inherits=Ecliz
which is mine. Be careful it has to be exact & is case sensitive.
Once done save the file, exit, then logout/in.
Should be sorted.

---

### Post by linkingeek on 2012-05-05
For all users working on gnome 3 remove compiz which will eventually also remove unity, otherwise you will see only a black cursor

---

### Post by cottfcfan on 2012-05-05
> **linkingeek said:**
> For all users working on gnome 3 remove compiz which will eventually also remove unity, otherwise you will see only a black cursor

Not sure that is the answer??
Ive used custom Cursors in 11.10 & now 12.04 with no problem.

---

### Post by ClyN3il on 2013-02-01
Oh for the love of god, is this still not fixed? :evil::evil::evil:

---

