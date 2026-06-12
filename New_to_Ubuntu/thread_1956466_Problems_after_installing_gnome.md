---
title: "Problems after installing gnome"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by AUGit on 2012-04-11
Hi all, let me first say I'm 2 weeks in to the vast world of linux. It's not all been smooth sailing but I'm still enjoying every bit of it. The reason for my post is that I think I've done something silly that I cant revert using my very limit skill set.

Having been playing with Ubutnu 11.10 I've been looking at various guides on tweaking certain areas etc etc. 
One such tweak saw me run.
sudo apt-get install gnome
when this installed I got a menu within terminal asking if I'd like to use GDK or DMLIGHT (I think) I choose GDK and after it has changed my login screen from the standard password and cog to pictures and password. Sorry if that doesn't make sense.
I've tried removing gnome and purging, then reinstalling to see if I have the selection again, but it's not giving me the same window. 
Any help I greatly appreciated :)

---

### Post by leecheroflife on 2012-04-11
What you're seeing is GDM, the gnome login manager, when you log in, are you getting onto unity fine? If so, you just need to change your login manager.

EDIT: 
sudo dpkg-reconfigure lightdm

Run that in a terminal and reboot, tell me if it works

---

### Post by AUGit on 2012-04-11
Hi and thanks for your response. initially unity didn't work at all until i reinstated. after trying your fix everything is back to how i like it. thank you very much.

---

### Post by leecheroflife on 2012-04-11
Your welcome:guitar:

---

