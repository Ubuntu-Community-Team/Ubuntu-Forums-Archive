---
title: "Disable Unity Launcher"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by makitso on 2011-09-16
Is there a way to prevent the left launcher from showing completely aka turn it off?  Removing the unity plugin is not the solution.  I have fiddled around with the CompizConfig Setting Manager Edge Reveal Timeout but that does not seem to do it.  Reveal mode of None doe not eliminate it.  If you create a folder on the desktop and them move it the launcher again shows.

---

### Post by lucazade on 2011-09-16
with unity-2d you can remove executable bit from launcher
```
sudo chmod -x /usr/bin/unity-2d-launcher

```then kill the launcher or logout/login

with unity-3d I have no idea.. there are not separate processes like in 2d version.

---

### Post by makitso on 2011-09-16
I am running in 3d.  I use the Avant app launcher so the Unity launcher is unnecessary.  I do like the Dash however.  What happens is that if you have a window open and move it around the screen then the launcher shows up.

Its kind of interesting, with the Gnome 3 shell, the launcher is off by default.

---

### Post by mc4man on 2011-09-16
If you want to use unity 3d then you'll need to live w/ the launcher expose on cursor grab & move. Did file a 'wishlist' type bug in 11.04 that that feature should be optional, - don't see that happening though..
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/776669](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/776669)

---

### Post by NCLI on 2011-09-16
> **makitso said:**
> I am running in 3d.  I use the Avant app launcher so the Unity launcher is unnecessary.  I do like the Dash however.  What happens is that if you have a window open and move it around the screen then the launcher shows up.

Its kind of interesting, with the Gnome 3 shell, the launcher is off by default.
Gnome shell doesn't use the Unity panel at all, so of course the launcher doesn't show.

In Unity 3D launcher, Dash and panel are all one, so for you to disable part of it, an option would need to be added.

---

### Post by cariboo on 2011-09-16
If you don't want to run Unity, why not try one of the other members of he Ubuntu family. Xubuntu, Lubuntu and Kubuntu, all work very well.

---

### Post by makitso on 2011-09-19
Thanks for the response.  Actually, I have run Ubuntu unity/Gnome 3, Fedora 15, Xubunu and Kubunu in Virtualbox.    

However, my goal is to run Unity shell if possible.  This is with the assumption that Unity can be configured to my needs.  At this point the Gnome 3 shell and a is a bit closer to what I need since the "Dock" is not on by default.

---

### Post by sixthwheel on 2011-09-19
Unity knows what you need, even if you don't.
Let Unity make the decisions for you. After all, this is what Linux is all about, isn't it? :lolflag:
You should be happy that you can still change the wallpaper.

---

### Post by cariboo on 2011-09-19
@makitso, if you set the launcher to autohide, it only comes out when you press your mouse cursor against the left side.

@sixthwheel, if you don't like Unity, why not tell us what's on your mind in the [Unity Mega thread.]("http://ubuntuforums.org/showthread.php?t=1695432")

---

### Post by Is Mise on 2011-09-19
> **cariboo907 said:**
> @makitso, if you set the launcher to autohide, it only comes out when you press your mouse cursor against the left side.

And if you set Reveal Mode to None, it won't even appear then.

---

### Post by mc4man on 2011-09-19
The Op doesn't like the the cursor grab & move exposes launcher feature, that can't be prevented
(I find it handy other than that for some reason it's been decided to always light the home folder icon no matter what file type is grabbed, makes no immediate sense here to me..

---

### Post by Is Mise on 2011-09-20
> **mc4man said:**
> The Op doesn't like the the cursor grab & move exposes launcher feature, that can't be prevented
(I find it handy other than that for some reason it's been decided to always light the home folder icon no matter what file type is grabbed, makes no immediate sense here to me..

Because a folder can accept any type of file?

---

