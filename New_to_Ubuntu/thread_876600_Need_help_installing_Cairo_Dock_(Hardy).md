---
title: "Need help installing Cairo Dock (Hardy)"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by kanati on 2008-07-31
Hi,
  I wanted to give Cairo Dock a try so I downloaded and installed the following deb files from [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724).

cairo-dock_v1.6.1.2_i686.deb
and
cairo-dock-plug-ins_v1.6.1.2_i686.deb

I installed them in the order I've listed them.  But there's no launcher in the applications menu for Cairo Dock.  When I try to run it through the terminal i get the following:

```
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-powermanager.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-switcher.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-cpusage.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-dustbin.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-AlsaMixer.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-shortcuts.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-rame.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-rendering.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-gnome-integration-old.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-systray.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xmms.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-showDesklets.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-clock.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-compiz-icon.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-nVidia.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-netspeed.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-Cairo-Penguin.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-Dbus.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-showDesktop.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-gnome-integration.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-weather.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-Xgamma.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-logout.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-tomboy.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-wifi.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-terminal.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-rhythmbox.so' : (libglitz-glx.so.1: cannot open shared object file: No such file or directory)



```

The weird thing is, Cairo-Dock actually does launch this way, but it seems a little off and there aren't any themes in it except the default.

Any ideas what I did wrong?

Thanks,
Kanati

---

### Post by fabounet on 2008-08-01
seems you need to install glitz-glx.
available in Synaptic.

---

### Post by cjv8888 on 2008-08-01
I followed the instructions [here]("https://help.ubuntu.com/community/CairoDock")
and had no problems.

---

### Post by nbayiha on 2008-08-01
Follow this thread for easy candy desktop .

[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)

---

### Post by tuxxy on 2008-08-01
Is this on 64bit

---

### Post by kanati on 2008-08-01
After my first attempt failed I tried installing it the way listed here: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock).  But that didn't change anything.  Maybe I need to remove the broken install first? If so, how?

I searched for glitz-glx in synaptic and found two packages:
-libglitz-glx1
-libglitz-glx1-dev
Neither package is installed, should I install them both?

And I'm working with 32bit Ubuntu 8.04.

Thanks for help!

---

### Post by Aetherius on 2008-08-01
install the -dev package only if you are going to compile it from source, for debs the other package should be fine

---

### Post by kanati on 2008-08-01
okay, I've installed libglitz-glx1, now how do I get rid of the broken install of Cairo so I can install it again.  Or should I just try installing it again as is?

---

### Post by Aetherius on 2008-08-01
if installed from deb it should show up in synaptic, you can right click and select "completely remove"

or as I would prefer, from the command line

sudo apt-get remove --purge <package-name>

then reinstall

if it still doesn't work, purge it again and then add 

```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

to your sources list and run the following in the command line

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
sudo apt-get update  
sudo apt-get install cairo-dock cairo-dock-plug-ins
```


(as per the thread link above)

---Aeth

---

### Post by kanati on 2008-08-01
I completely removed it through synaptic and then followed your instructions to reinstall.  I'm still having the same problem though. It doesn't show in the applications menu (which isn't a big deal since I can always make it a launcher), and there are no themes available other then the default.  Also, only the default 2D view of the dock is available.  I've installed Cairo on my laptop and didn't have these problems, any ideas?

---

### Post by Aetherius on 2008-08-01
ok, have you tried the second method with extra repository?

I just tried it with a pretty much stock 8.04 and it has installed and run fine, even giving me a gui to select themes (which is a hell of a lot more than i got the last time i used cairo!).

I did get a lot of warnings too tho, but none seem to effect it.

---Aeth

---

### Post by Aetherius on 2008-08-01
if you have tried the repo method, then remove it again and then run the command

```

rm ~/.cairo-dock
```

and reinstall, after that I can't be sure without more information

---

### Post by cjv8888 on 2008-08-01
There is supposed to be a hidden file in your home folder which contains the Cairo-Dock configurations.
So open your home folder, enable viewing hidden files (Ctrl+H) and delete ".cairo-dock" and try re-installing again after that.

Good luck.

---

### Post by kanati on 2008-08-01
So here's where I am now. I completely removed cairo-dock through synaptics.  Then I deleted the .cairo-dock folder in my home folder and ran "rm ~/.cairo-dock" in the terminal (which is when I realized that they were the same thing).  Then I followed these instructions to reinstall it:
> 
 if it still doesn't work, purge it again and then add

Code:

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock

to your sources list and run the following in the command line

Code:

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -
sudo apt-get update  
sudo apt-get install cairo-dock cairo-dock-plug-ins

It still doesn't show in applications menu and there's still only 1 theme available (the snow flake theme).  But, now I can change the format of the dock (2d, 3d, rainbow etc.) which I couldn't the last couple of times I tried it.  Is there anything else I can try?  I can always just use AWN but I like my docks on the top.

---

### Post by kanati on 2008-08-01
Just checked my themes folder in the .cairo-dock folder, and sure enough it's empty.  Is there a place I can just download the themes and install them manually?

---

### Post by kd420 on 2008-08-10
Hi guys,
I installed Cairo-dock with no real problem, I used the compositing manager in metacity because my laptop's not great. Everything seems ok, except the dock can only go on the top or left of the screen.
Changing the drop down box in the configuration to "bottom" (which was default) keeps in at the top. Putting it at "right" keeps it on the left. Anyone know what is going on here? I've heard that you can <Alt> + drag it to where you want, but this doesn't work for me.

Edit: And putting the box on left/top keeps it where it should be. It can ONLY go in those two spots.

---

### Post by fabounet on 2008-08-11
which version are you using ?

---

### Post by kd420 on 2008-08-11
> **fabounet said:**
> which version are you using ?

I'm using Cairo-dock 1.6.1.2 on Hardy Heron. I've tried Metacity and xcompmgr for compositing, both seem to be fine.

---

### Post by fabounet on 2008-08-11
are you in "advanced mode" ? (9 tabs instead of 2)
if not, then try to switch to it.

otherwise, then you can try this hack :
```
gedit ~/.cairo-dock/current_theme/cairo-dock.conf
```
on the first line, change the version number to another (1.6.0 for exemple), then open the config panel of the dock, and make your changes, or just restart it.

if it still doesn't work, thanks to paste the result of
 ```
cat ~/.cairo-dock/current_theme/cairo-dock.conf | grep "Choose the screen border"
```

---

### Post by kd420 on 2008-08-11
> **fabounet said:**
> are you in "advanced mode" ? (9 tabs instead of 2)
if not, then try to switch to it.

otherwise, then you can try this hack :
```
gedit ~/.cairo-dock/current_theme/cairo-dock.conf
```on the first line, change the version number to another (1.6.0 for exemple), then open the config panel of the dock, and make your changes, or just restart it.

if it still doesn't work, thanks to paste the result of
 ```
cat ~/.cairo-dock/current_theme/cairo-dock.conf | grep "Choose the screen border"
```



Yes, I am in advanced mode, and I tried some stuff with the config file. The first hack didn't work, so I checked to see what was happening. Each time I opened Cairo-dock, any changes I made to config file were reverted to the original. I even put in a blank comment at the top "#######blah######" and it was removed when i restarted cairo-dock. The result of the second line of code is:

"#r-[bottom;top;right;left] Choose the screen border regarding to which the dock will place itself :"

which doesn't seem to have any value assigned to it, but i can't tell. Changing the value in the program doesn't change the line in the config file.

I'm going to try finding an older version and see if that will work for now.


EDIT: Installed the last two versions, removing all files in Home folder, same problem.

---

### Post by fabounet on 2008-08-12
under the line containing "Choose the screen border", what is the value of the parameter "screen border" ?
you can try to change it from 0 to 3 included, and restart your dock after the operation.
setting the value to 0 should put it on the bottom ...
did you try with another theme ? (save your current theme before)

---

### Post by kd420 on 2008-08-12
> **fabounet said:**
> under the line containing "Choose the screen border", what is the value of the parameter "screen border" ?
you can try to change it from 0 to 3 included, and restart your dock after the operation.
setting the value to 0 should put it on the bottom ...
did you try with another theme ? (save your current theme before)

Yes, the value is set at 0, going through 1,2 and 3, it only stays at the top left. It seems like it glitches  for a second when I change it from top to bottom, before going back to the top. Different themes have the same result. Changing other options seem to be fine, just this problem.

It might be something to do with my hardware maybe, I'm using an intergrated graphics card, not great specs. Thanks for your help anyways.

---

### Post by fabounet on 2008-08-12
no it doesn't matter which card you have, it's just a window placement issue. :-/

ultimately, you can 
```
mv ~/.cairo-dock ~/.cairo-dock.bak
```
and then restart the dock, and choose any theme (the default one for exemple)
if it's still on the top of your screen after that ..... rotate your screen ^_^;

---

### Post by williamson389 on 2008-08-12
i have a question about cairo dock.  i have installed it but once i close the terminal in which i installed it, the dock closes and i cant find it in accessories or anywhere. to open it again i just run cairo-dock in the terminal, but obviously this isnt very practical to have a terminal open all the time.
Is it installed wrong or will it not run with my specs, because awn wont either.

---

### Post by fabounet on 2008-08-13
use alt+F2
or launch it from the menu (System) if you installed it from the .deb, or at start-up

---

### Post by converted on 2008-08-15
> **kanati said:**
> 

It still doesn't show in applications menu and there's still only 1 theme available (the snow flake theme).  

Did you ever get this resolved?  I have the exact same symptoms...

It didn't look like you had posted again, so I'm hoping that means you figured it out and forgot about the thread... :-)

---

### Post by converted on 2008-08-15
Here's what I did.

I was trying to use the instructions posted at [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) , and ran into seemingly the same symptoms as mentioned earlier in this thread.  (Only default themes.  Themes missing.  No themes.  I'm trying to include all the keywords I used when googling for this problem.)

I attempted to use the repository as noted in the link above.

I followed the advice throughout this thread regarding fully removing cairo-dock, including checking that /usr/share/cairo-dock and /home/*username*/.cairo-dock were deleted.

I didn't document the entire process, because frankly I didn't expect it to work.  However, it's worth noting that I installed cairo-dock as present in the Ubuntu repositories *and* as present in the developer's repositories (not at the same time) during the course of my efforts.

In the end, only one thing ended up giving me more than the snowflake/default theme to choose from.

I purged everything one last time, then installed using the .deb files, as noted at the link above.

Then, since Synaptic kept wanting to upgrade two of the cairo-dock packages (which I tried once, and which failed, and which resulted in a broken package), I had to lock the version on both of them.

-Joe

---

