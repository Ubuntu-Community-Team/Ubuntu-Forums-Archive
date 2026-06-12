---
title: "Update Removed Necessary Packages?"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-25
Well, my recent update (this morning) removed gnome-session, unity (both full and 2D), and ubuntu-desktop. Now, in the past, that was no big deal because I could just reinstall those after the upgrade; however, this morning I get this:
```


install gnome-session unity ubuntu-desktop
The following NEW packages will be installed:
  gnome-session libunity-2d-private0{ab} ubuntu-desktop unity{b} unity-2d unity-2d-launcher{a} unity-2d-panel{ab} 
  unity-2d-places{a} unity-2d-spread{a} 
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,576 kB of archives. After unpacking 5,186 kB will be used.
The following packages have unmet dependencies:
  unity: Depends: libnux-1.0-0 (< 1.2.4) but 1.4.0-0ubuntu1 is installed.
         Depends: libunity-core-4.0-4 (>= 4.8.0) but it is not going to be installed.
         Depends: libunity-core-4.0-4 (< 4.10.0) but it is not going to be installed.
  unity-2d-panel: Depends: libnux-1.0-0 (< 1.2.4) but 1.4.0-0ubuntu1 is installed.
                  Depends: libunity-core-4.0-4 (>= 4.8.0) but it is not going to be installed.
                  Depends: libunity-core-4.0-4 (< 4.10.0) but it is not going to be installed.
  libunity-2d-private0: Depends: libnux-1.0-0 (< 1.2.4) but 1.4.0-0ubuntu1 is installed.
                        Depends: libunity-core-4.0-4 (>= 4.8.0) but it is not going to be installed.
                        Depends: libunity-core-4.0-4 (< 4.10.0) but it is not going to be installed.
The following actions will resolve these dependencies:

     Install the following packages:                                            
1)     gnome-shell [3.1.3+git20110718.a012dd83-0ubuntu1~11.10~ricotz1 (oneiric)]

     Keep the following packages at their current version:                      
2)     libunity-2d-private0 [Not Installed]                                     
3)     ubuntu-desktop [Not Installed]                                           
4)     unity [Not Installed]                                                    
5)     unity-2d [Not Installed]                                                 
6)     unity-2d-launcher [Not Installed]                                        
7)     unity-2d-panel [Not Installed]                                           
8)     unity-2d-places [Not Installed]                                          
9)     unity-2d-spread [Not Installed]                                          



Accept this solution? [Y/n/q/?] q

```
Is anyone else seeing this problem? I'm sure a later update will rectify this, as I must have upgraded at *just* the "wrong" time, but I wanted to confirm...

---

### Post by fjgaude on 2011-08-25
It looks like we have to wait it out, for lots of things are broken. Unity-2D not permitted to be installed... okay, it's still Alpha.

---

### Post by moore.bryan on 2011-08-25
Yeah, just making sure I wasn't the only one! :-)

---

### Post by ventrical on 2011-08-25
whoops .. I just posted the same thing .. 'synapttic gone completely bananas'

apologies..

---

### Post by moore.bryan on 2011-08-25
:-)

Now we can only hope the fixes come fast and furious!

---

### Post by mc4man on 2011-08-25
There is a new unity avail. - 4.10 which can be installed but will remove unity-2d. Or you can wait a bit for unity-2d to be  re-built and then nothing will be removed 
(the new unity fixes some things, has a new ubuntu start icon and breaks some things even further..

Edit: the new unity-2d is now avail.

---

### Post by moore.bryan on 2011-08-25
> **mc4man said:**
> There is a new unity avail. - 4.10 which can be installed but will remove unity-2d. Or you can wait a bit for unity-2d to be  re-built and then nothing will be removed 
(the new unity fixes some things, has a new ubuntu start icon and breaks some things even further..

Not available for me... :-(
```

bryan@ubuntu:~$ install unity
[sudo] password for bryan: 
The following NEW packages will be installed:
  unity{b} 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 799 kB of archives. After unpacking 2,322 kB will be used.
The following packages have unmet dependencies:
  unity: Depends: libnux-1.0-0 (< 1.2.4) but 1.4.0-0ubuntu1 is installed.
         Depends: libunity-core-4.0-4 (>= 4.8.0) but it is not going to be installed.
         Depends: libunity-core-4.0-4 (< 4.10.0) but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     unity [Not Installed]                              



Accept this solution? [Y/n/q/?]

```

---

### Post by mc4man on 2011-08-25
All the new builds are in the 'main' repos, don't know about any other

---

### Post by moore.bryan on 2011-08-25
> **mc4man said:**
> All the new builds are in the 'main' repos, don't know about any other
I'm using the "main" repos... 

:-(

---

### Post by mc4man on 2011-08-25
Beats me? were/are all avail. here
screen shows all new unity* & unity-2d installed

edit: when first installed did get some severe crashes in unity, that was resolved by some bamf upgrades

---

### Post by moore.bryan on 2011-08-25
Hmm... 4.8.2-0ubuntu4 is all that shows-up for me.

Me=confused.

And packages.ubuntu.com shows my version is the latest. Are you a wizard? ;-)

---

### Post by jerrylamos on 2011-08-25
> **fjgaude said:**
> It looks like we have to wait it out, for lots of things are broken. Unity-2D not permitted to be installed... okay, it's still Alpha.

It might stay Alpha.  Hopefully a bunch of Launchpad bugs will be noticed.  Sometimes not, and the Alpha bugs are still there on release....

Jerry

---

### Post by cariboo on 2011-08-25
This has been said before, and will probably be repeated. If an update is going to remove packages that you use, it is best to wait a couple of hours and check again. I updated before reading any ot the threads here, everything updated as it should. The only thing that was removed on my system was skype, which I expected to happen due to the multiarch change.

The only reason skype was even on this system is because my 82 year old Dad was learning to use skype, and he wanted to call someone. :)

---

### Post by moore.bryan on 2011-08-25
@cariboo907... I'm not complaining, but wanted to see if others saw the same problem. My breakage was due to my own -y on the aptitude upgrade without thinking.

---

### Post by cariboo on 2011-08-25
> **moore.bryan said:**
> @cariboo907... I'm not complaining, but wanted to see if others saw the same problem. My breakage was due to my own -y on the aptitude upgrade without thinking.

My post wasn't aimed at you, as I know you've been around the block a time or two. :) It was more aimed at newer testers that happen upon this thread.

---

### Post by moore.bryan on 2011-08-25
Thanks for the vote of confidence... ;-) and thanks for the diligence for new users! We were all there once.

On a very related note, everything *finally* installed/reinstalled/updated and I've noticed three interesting things:
[LIST=1]
[*]I now how a username indicator next to the power button on the right side of the top panel.
[*]I have no icons in the Unity launcher.
[*]My "overlay"--when the Super_L is hit--is not purely transparent, but more a disgusting hue of unknown origin...
[/LIST]

---

### Post by jbicha on 2011-08-25
> **jerrylamos said:**
> It might stay Alpha.  Hopefully a bunch of Launchpad bugs will be noticed.  Sometimes not, and the Alpha bugs are still there on release....

Jerry

Ubuntu uses time-based releases (which Mozilla is using now too) so releases basically always happen when they say they will. That's why Beta Freeze hit today so any Critical bugs can be ironed out before Beta release next week, and then there are six more weeks to finish cleaning things up and fixing bugs before Final release.

The Release Manager does have GO/NOGO authority but don't expect the release to not happen on the scheduled date.

---

