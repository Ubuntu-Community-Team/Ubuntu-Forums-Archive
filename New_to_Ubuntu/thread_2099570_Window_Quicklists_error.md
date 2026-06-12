---
title: "Window Quicklists error"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by davidavida on 2012-12-29
Good day guys

It is good to be posting on this forum, I wish I get the solution for my puzzle.

The Window Quicklists on Gnome 3 seems to be quite cool, so I followed instructions on this site <http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html> to get this feature.

1- WHAT HAS HAPPENED

I typed the following commands:
sudo apt-add-repository ppa:alanbell/unity sudo apt-get update sudo apt-get install unity-window-quicklists

It worked so far but as the autor says:
"There's a bug with the autostart .desktop file and Unity Window Quicklists doesn't start automatically on login, so let's fix it:"

So I typed:

sudo sed -i 's/OnlyShowIn=UNITY/OnlyShowIn=Unity/g' /etc/xdg/autostart/unity-window-quicklists.desktop

Now this one did not install.


After doing this I experienced weird things.
A- Window Quicklists is not working
B- When I start my laptop a window to repor a problem opens up, it says:
   -System program problem detected
   -Do you want to report the problem?
   -If I hit report problem another window will open asking for my root password, it says.
   -Please enter your password to access problem reports of system programs.
 I found it suspicious and I did not put the root password there.

I tried to remove the unity-window-quicklists 

I typed:
davi@Computer1:~$ sudo apt-get remove unity-window-quicklists
[sudo] password for davi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unity-window-quicklists

2- WHAT I AM AFTER

I would like either make this 'window quick list' work
OR
Remove it from my computer so I do not have do deal with any possible bugs.


3- MY SOFTWARE
Ubuntu 12.04 (precise pangolin) - only operational system
Gnome 3

4- HARDWARE
Toshiba Satelite L300


Thanks you guys in advance.

---

