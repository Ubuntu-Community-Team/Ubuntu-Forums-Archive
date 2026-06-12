---
title: "Installed 8.10 - what happened to Cairo-Dock?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by m_ad on 2008-11-01
I loved Cairo-Dock on my last system, so one of the first things I did was 'sudo apt-get install cairo-dock'

For some reason, it's not acting right. It displays and launches the items on the dock correctly, but none of the options are available. For instance, under 'Views,' the only option I can choose is 'default' which is the 2D view. When I click preferences, nothing happens.

Same thing for 'Chose some useful accessories for your dock!.' Nothing is there when I expand this option.

What is going on?

---

### Post by celticbhoy on 2008-11-01
Seems to be a recuring problem as shown in this post :-

[http://ubuntuforums.org/showthread.php?t=965149&highlight=cairo+dock](http://ubuntuforums.org/showthread.php?t=965149&highlight=cairo+dock)

I dont know if a complete removal & re-install would work, will try later & post back.

---

### Post by m_ad on 2008-11-01
I just tried it..

'sudo apt-get remove --purge cairo-dock'
'sudo apt-get install cairo-dock'

here is the output from the terminal when trying to click "Preferences" under 'Views'

```
cairo_dock_configure_module: assertion `pModule != NULL' failed
```

---

### Post by detroit/zero on 2008-11-01
I always had the same problem under both Gutsy and Hardy, and it's always kept me from using Cairo Dock and stuck me with the less-feature-rich and buggier AWN.

---

### Post by m_ad on 2008-11-01
> **detroit/zero said:**
> I always had the same problem under both Gutsy and Hardy, and it's always kept me from using Cairo Dock and stuck me with the less-feature-rich and buggier AWN.

Weird, this was never a problem until today after I installed Ibex. I wonder if there is an older deb I can install, and get rid of the one that's in the repos?

---

### Post by celticbhoy on 2008-11-01
I just tried a new install on a pc which never had it before, and the same problem is showing.I am going to have a look at the home site to see if there is another version there.

---

### Post by m_ad on 2008-11-01
Trying 1.4.6.3 right now.

edit.. No luck :(

---

### Post by m_ad on 2008-11-01
This version of cairo-dock is worthless. So many bugs it's not even funny.


It's time to find a new dock.


EDIT: anytime I click on my desktop or anywhere for that matter something launches from the Cairo-Dock. This is pathetic.

---

### Post by m_ad on 2008-11-01
I've gotten so used to Cairo-Dock that I may have to reinstall 8.04.

---

### Post by TwiceOver on 2008-11-01
The basic dock features work fine for me but none of the preference buttons work so I can't customise much.

---

### Post by m_ad on 2008-11-01
Older versions don't work, so it must be something in Ibex :/

---

### Post by m_ad on 2008-11-01
ok, it's definitly not just Cairo-Dock. I just left my PC and came back after 5 min and I had 2 "untitled folder"'s opened. Menus continue to appear out of nowhere, folders are being created, etc..

It's either my PC or Ibex, and I don't think it's my PC since it's a brand new PC.

---

### Post by celticbhoy on 2008-11-01
You seem to be having a time of it. I just got the dock config problem that everyone else has. I think you might have another gremlin or two playing games in your box..

---

### Post by m_ad on 2008-11-01
I'll figure it out. How did you fix it?

---

### Post by celticbhoy on 2008-11-01
As I say only the Cairo problem & I will just grin & bear it for the mo. Just a little ugly, not un-useable

---

### Post by m_ad on 2008-11-01
I would be able to, but it's completely unfunctional for me.

I use the auto-hide feature, and when it's hidden it tends to float around the screen :lolflag:


Which causes random launchers to launch from the dock when I click my mouse.

---

### Post by KazukiFlame on 2008-11-01
happened to me too. i just completely removed the package, downloaded cairo-dock 1.6.3, installed that plus the plugin. worked like a charm.

---

### Post by Landara on 2008-11-02
This did nothing for me, I'm afraid. :( Still the same problem.

---

### Post by m_ad on 2008-11-02
> **KazukiFlame said:**
> happened to me too. i just completely removed the package, downloaded cairo-dock 1.6.3, installed that plus the plugin. worked like a charm.

I tried an even earlier version than that and it didn't work. I'll try 1.6.3.

Although I'm having many other problems with Ibex besides this, I may just go back to Hardy.

---

### Post by ruipalmeira on 2008-11-02
i think the problem with cairo-dock, is that it doesn't install the plugins, which are usefull if you want all the fancy stuff.

EDIT : Grrr, they updated the locations of the .config file...... i have too change my recently created 5 themes.. whatever..

---

### Post by Landara on 2008-11-02
> **ruipalmeira said:**
> i think the problem with cairo-dock, is that it doesn't install the plugins, which are usefull if you want all the fancy stuff.

EDIT : Grrr, they updated the locations of the .config file...... i have too change my recently created 5 themes.. whatever..

sadly that isn't the problems, i have downloaded the DEB for the plugins many times and installed it, the right version too, but nothing.

---

### Post by fabounet on 2008-11-03
be sure to completely remove the Ubuntu package before you install the 1.6.3 from the project's repos (or even Berlios)
this packae is a shame, so please don't use it until they fix it.

---

### Post by Landara on 2008-11-03
I went to the app manager and did a complete remove on the dock, data, plug-ins.  Then I downloaded the 1.6.3 dock and plug ins from the Cairo website, the DEBS, and installed form them. But it still has no plug ins :(

---

### Post by fabounet on 2008-11-03
well in this case, what are the messages in the terminal ?

---

### Post by jbg7474 on 2008-11-03
FYI--I'm running Cairo-Dock version 1.6.2.3 on Intrepid with no real issues to report.  I was also running Cairo-Dock in Hardy.  I performed an upgrade to Intrepid, and Cairo-Dock retained all my settings.

---

### Post by Landara on 2008-11-03
> **fabounet said:**
> well in this case, what are the messages in the terminal ?

What messages? The programs functions, it just has no plug-ins listed, even though I installed them. So I can't use Rendering. Or anything else. Im sorry but I am not sure which terminal messages you mean sir.  Im not very good at this stuff yet.

---

### Post by fabounet on 2008-11-04
type "cairo-dock" in a terminal, then copy-paste the output.
it may help to see the problem.
or try with the .deb on Berlios, current version is 1.6.3.

---

### Post by Landara on 2008-11-04
```
rob@rob-desktop:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
```

This is my terminal output.

Also, I did use the 1.6.3 cairo dock and plugins .DEBs from here:
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

When I run that version, it won't launch. It says this is Terminal:
```
rob@rob-desktop:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
rob@rob-desktop:~$ 


```
So I had to revert to the one in the Repo, which functions except I still I have no plugins listed, even though I do see them on my computer.

---

### Post by Landara on 2008-11-04
Here you see the file that it says isn't there.  It's pretty there.

[http://tinypic.com/view.php?pic=214a59i&s=4](http://tinypic.com/view.php?pic=214a59i&s=4)

---

### Post by fabounet on 2008-11-05
is it the only output ?
what gives cairo-dock -l debug ?
you should maybe try to install libglitz-glx (and its dev part just in case) to be able to get the 1.6.3

---

### Post by James_mtl on 2008-11-11
I just had the same problem.

I fixed it by doing complete uninstalling of cairo-dock in synaptic and deleting .cair-dock in my home folder.

After that I installed the cairo repo for intrepid in software sources :

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

and added the key ( paste in terminal ):

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

then :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install cairo-dock cairo-dock-plug-ins

Type cairo-dock in terminal and you should be back where used to be !
Worked for me hope it helps !!

---

### Post by xSauronx on 2008-11-12
> **James_mtl said:**
> I just had the same problem.

I fixed it by doing complete uninstalling of cairo-dock in synaptic and deleting .cair-dock in my home folder.

After that I installed the cairo repo for intrepid in software sources :

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

and added the key ( paste in terminal ):

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

then :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install cairo-dock cairo-dock-plug-ins

Type cairo-dock in terminal and you should be back where used to be !
Worked for me hope it helps !!

it struck me to check the repo itself by directory....no 64-bit packages :(

damnit.

---

### Post by James_mtl on 2008-11-12
As per their web page : [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en)

It's supposed to be for both 32 and 64 bits but I did not try it myself as I'm now running only 32 bits.

---

