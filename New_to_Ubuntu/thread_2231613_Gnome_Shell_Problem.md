---
title: "Gnome Shell Problem?"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by 1099 on 2014-06-26
Hello Everyone!

I am new to Ubuntu, yet I already spent some time using it and enjoyed it* a lot*. The forum helped me greatly whenever I had doubts. Unfortunetely, three days ago or so something went really bad and I don't think it is something I can diagnose and fix myself anymore.
[COLOR=#000080]Please, hear my pray[/COLOR].

On my netbook I use Ubuntu 12.04 with Gnome Classic view. From what I recall, last thing I did was updating everything through Update Manager. Since then, my top-bar is entirely black, icons on the right (Bluetooth, Network) are different and lame, with sound icon missing. In general, all icons on the computer are replaced with Blank Sheet Icon except very few, windows are grey, Softwere Center is missing from the [Places] menu. Choosing Displays or System Settings from the top-bar does nothing.

I assumed it's a Gnome Shell related problem, so I decided to try and re-install it. And then it struck me.

```
sudo apt-get install --reinstall gnome-shell
sudo: apt-get: command not found
```

I researched it - in general, not founding apt-get was a result of misspelling, not of a more serious problem I believe I have.
Any suggestions?

P.S. This is my first post here and the issue seems to be pretty heavy-duty one. I am sorry, if the title is misleading - in fact, I just don't know where the problem originates and where to turn to. Please, help! 

Sending my Best Regards!

---

### Post by grahammechanical on 2014-06-26
I do not think that installing Gnome classic in 12.04 brought in Gnome shell but Gnome panel. Gnome 3 Shell is the user interface that is used in Ubuntu Gnome 14.04 instead of Unity. It does have a Classic Extension.

What theme are you using? Is it one of the two default themes or is it a theme that you have installed from a website? What is the situation when you log into Unity?

Regards.

---

### Post by collisionystm on 2014-06-26
apt-get not found?

Can you try

sudo apt-get update

Will that work?

---

### Post by 1099 on 2014-07-03
[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"): I probably should have been more precise. I never downloaded any Gnome additionally, what I am using on my 12.04 system is Gnome Classic view, no effects. When I try on Unity, it all loads awfully slow and the top panel is just black and still lacks some icons. It seems that the issue goes beyond the theme. 

[**[COLOR=#000000]collisionystm[/COLOR]**]("http://ubuntuforums.org/member.php?u=1249225"): I tried and it reveals the very depth of my problem! /apt-get: command not found/ is what I get after entering my sudo password. The disability of my terminal is something that accompanies all the things bad things going on with my computer. What can it mean?

Regards Guys, thanks for the advice. Are there any other suggestions? I will try anything.

---

