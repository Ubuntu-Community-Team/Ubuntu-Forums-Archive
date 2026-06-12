---
title: "HOW-TO: Fix Your Monitor Refresh Rate"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Samuel on 2005-10-15
This How-to is for people who want to change the refresh rate and/or resolution for their monitor

**i have only tried this on nvidia cards

**use this info at your own risk, i will take no responsibility for damaged hardware 

First we want to get the modeline for our desired resolution and refresh rate, to do this we head to [www.sh.nu/nvidia/gtf.php](www.sh.nu/nvidia/gtf.php) 

At the top of the page is a table, input the settings you want into it, for example, i want to run my monitor @ 1280x1024 85refresh rate, so i enter into the first box marked X: 1280 in the second box marked y: i enter 1024 and the 3rd box i enter 85 (my desired refresh rate)

then i click the Generate modeline button and the output is as follows:
# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync

open a new terminal and type the following:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

in the xorg.conf document find:

Section "Monitor"

and at the bottom of this section copy and paste the modeline you got from the website you visited, mine looks like this:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

now save the file and restart x by pressing ctrl alt and backspace

if it takes you to a command prompt just log in and type startx 

your monitor should now be running at your chosen settings 

note: this is my first how-to so i would appreciate any feedback on it from you experts, i am still a linux newb but this is a small problem i managed to figure out and hope it can help others like the community has helped me.

---

### Post by Synt4x_3rr0r on 2005-10-15
Thanx for this Howto!!
I already fixed this "problem" on my monitor though, but it was hard to find the correct vertsync and that for my monitor.

But in the future I will use this howto if i need it, and i probably will.

---

### Post by llama on 2005-10-15
if you have a Dell 2005FPW with the nvidia drivers that is refusing to work at 1680x1050 try this modeline:
```

ModeLine "1680x1050" 119.0 1680 1728 1760 1840 1050 1053 1059 1080
```

works great for me.

---

### Post by CDX74 on 2005-10-16
hmm, doesn't seem to do anything to mine...  :(

---

### Post by Veloci on 2005-10-16
I found a very simple method to change the resolution. All you need to do is open up the Terminal, and enter:
sudo gedit /etc/X11/xorg.conf

Then, find the section that says:

"Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"LJD 7VlrSB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"

.. And edit the one that says " Depth 24" I am assuming that's 24-bit colour depth. I just put in my resolution "1152x864" and saved the modifications. After I rebooted, it allowed me to select the resolution in the Resolution box. Hopefully this will help people who cannot get the above method working.:)

---

### Post by Marcos.Rufino on 2005-10-16
Thank you Samuel. Great howto!

---

### Post by Arathorn on 2005-10-16
Hi Veloci.

About your method, when I type *sudo gedit /etc/X11/xorg.conf* in the terminal I get this error:

> ** (gedit:8068): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi) ' failed

** (gedit:8068): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

** (gedit:8068): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8068): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8068): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

(gedit:8068): GLib-GObject-WARNING **: invalid uninstantiatable type `glong' in cast to `GObject'

(gedit:8068): GLib-GObject-WARNING **: instance of invalid non-instantiatable ty pe `glong'

(gedit:8068): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TY PE_CHECK_INSTANCE (instance)' failed

(gedit:8068): GLib-GObject-WARNING **: invalid uninstantiatable type `glong' in cast to `BonoboMDI'

** (gedit:8068): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (md i)' failed

(gedit:8068): GLib-GObject-WARNING **: invalid uninstantiatable type `glong' in cast to `BonoboMDI'

** (gedit:8068): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS _MDI (mdi)' failed

** (gedit:8068): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDO W (win)' failed

(gedit:8068): GLib-GObject-WARNING **: invalid uninstantiatable type `glong' in cast to `BonoboMDI'

** (gedit:8068): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS _MDI (mdi)' failed

** (gedit:8068): CRITICAL **: bonobo_window_flash: assertion `win != NULL' faile d

(gedit:8068): GLib-GObject-WARNING **: invalid uninstantiatable type `glong' in cast to `BonoboMDI'

** (gedit:8068): CRITICAL **: bonobo_mdi_add_views: assertion `BONOBO_IS_MDI (md i)' failed

** (gedit:8068): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi) ' failed

What is wrong?
I have an ATI card but the */xorg.conf* file does have the passage you mention.
I'm a Windows user just trying Linux, so please try to keep things simple. ;)

---

### Post by Samuel on 2005-10-16
Glad this has helped for you who have been able to use it.

Veloci your right for changing resolution but this is to fix your refresh rate ;) 

I wish i could help you guys having problems with this but im still a linux newb myself:confused:

---

### Post by phend-one on 2005-10-16
Doesn't seem to work for me...

Anyone know if the old way of editing the HorizSync and VertRefresh work?

---

### Post by wolfchri on 2005-10-18
It is close to comical that we need an how-to in the year 2005 in order to change the screen refresh rate. As much as I like Ubuntu, that is definitely a missing feature, especially since Ubuntu aims for contries in Africa etc. that do not have the latest LCD screens but old CRTs without plug and play capabilities. 

A tool to choose a monitor/screen/screen type is definitely needed, such as SaX or in the Mandriva Control Center. Why not just port one of these tools (I think, there is even one in the Debian installer) to Ubuntu - I am sure that would not be too difficult.

---

### Post by WetWilly on 2005-10-18
[QUOTE=wolfchri]It is close to comical that we need an how-to in the year 2005 in order to change the screen refresh rate. As much as I like Ubuntu, that is definitely a missing feature, especially since Ubuntu aims for contries in Africa etc. that do not have the latest LCD screens but old CRTs without plug and play capabilities. 

A tool to choose a monitor/screen/screen type is definitely needed, such as SaX or in the Mandriva Control Center. Why not just port one of these tools (I think, there is even one in the Debian installer) to Ubuntu - I am sure that would not be too difficult.[/QUOTE]


I would agree 100% with that post.

And this info from the wiki is what worked nice and simple for me :

[https://wiki.ubuntu.com//FixVideoResolutionHowto](https://wiki.ubuntu.com//FixVideoResolutionHowto)

---

### Post by Samuel on 2005-10-19
i agree too that it would be nice, even if in the system>prefrences>screen resolution it let you go past what you think is safe then gave 10 seconds to comfirm it works like the windows or sax2 versions. im running a 21" crt and at 60hz it makes my eyes bleed.
TFT monitors in the uk are either expensive or not as good as a crt in picture quality so im sure i will have a crt for along time.

WetWilly that howto is for screen resolution, this is for refresh rates :)

---

### Post by wolfchri on 2005-10-27
I have created a little step-by-step blend of several how-tos on this issue (too low screen refresh rate) for absolute beginners. 

Can be found here; feel free to copy it to the Ubuntu Wiki if it is good enough (I have no idea how to do that myself):

[http://vale.homelinux.net/wordpress/?p=32](http://vale.homelinux.net/wordpress/?p=32)

Let me know if it works for you, I hope it helps. If I would have more time, I would try to port the screen selector from Yast myself. I am considering a bounty, since my bugreport on this issue also led to nowhere :???:

---

### Post by freiyath on 2005-11-12
in my kubuntu box, i need to restart my PC in order to get the right configuration and refresh rate, strange but works :confused:

---

### Post by Mikebgr on 2006-03-25
works like a charm! thumbs up!

---

### Post by grandiose on 2006-05-05
[QUOTE=Samuel]This How-to is for people who want to change the refresh rate and/or resolution for their monitor

**i have only tried this on nvidia cards

**use this info at your own risk, i will take no responsibility for damaged hardware 

First we want to get the modeline for our desired resolution and refresh rate, to do this we head to [www.sh.nu/nvidia/gtf.php](www.sh.nu/nvidia/gtf.php) 

At the top of the page is a table, input the settings you want into it, for example, i want to run my monitor @ 1280x1024 85refresh rate, so i enter into the first box marked X: 1280 in the second box marked y: i enter 1024 and the 3rd box i enter 85 (my desired refresh rate)

then i click the Generate modeline button and the output is as follows:
# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync

open a new terminal and type the following:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

in the xorg.conf document find:

Section "Monitor"

and at the bottom of this section copy and paste the modeline you got from the website you visited, mine looks like this:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Modeline "1280x1024_85.00" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

now save the file and restart x by pressing ctrl alt and backspace

if it takes you to a command prompt just log in and type startx 

your monitor should now be running at your chosen settings 

note: this is my first how-to so i would appreciate any feedback on it from you experts, i am still a linux newb but this is a small problem i managed to figure out and hope it can help others like the community has helped me.[/QUOTE]I followed your instructions and produced an outcome that looked like yours, but now the os doesn't work.... I got some blue screens and some messages about things not being set-up correctly...

God this was sooo much easier in Windows... :-( 

Now the OS wont start up at alll!! I made a back-up of the file like you said, but it doesn't seem to have helped any... I keep getting these blue screens with error messages on saying that the X server failed to start my graphical interface..? It asks if I want to view the server output, but the output means nothing to me, so I can't diagnose anything and even if I could I would know how to fix anything!

Do I have to reinstall the whole OS again, or is there another solution..?

------------------------------------------------------------------------------------------
EDIT: Don't bother, I'm not going to wait for a responce, I'll just try to re-install the OS again... If it breaks next time I try this fix I think I'll just install Win2k again... I guess Linux isn't for everybody...
------------------------------------------------------------------------------------------

---

### Post by mcgee on 2006-05-13
You be da man! Thanks for your efforts. :D 

> **wolfchri]I have created a little step-by-step blend of several how-tos on this issue (too low screen refresh rate) for absolute beginners. 

Can be found here said:**
> http://vale.homelinux.net/wordpress/?p=32[/url]

Let me know if it works for you, I hope it helps. If I would have more time, I would try to port the screen selector from Yast myself. I am considering a bounty, since my bugreport on this issue also led to nowhere :???:

---

### Post by shimmyshack on 2006-11-12
I must admit, I use windows XP for detecting monitor settings.
(I have a KVM switch with XP on one box, and xubuntu on the other) 

In XP, I right click on the desktop, select 
properties->settings->
change the bit depth to 32 (if your moniroty looks good using that setting)
advanced->monitor

change the refresh rate till its nice, then using your monitors built-in menu

search the different controls until you can read off the exact refresh rate, copy them down

head off to xubuntu land and stick those values into /etc/X11/xorg.conf and away you go.

On my newly installed edgy box I had to create a section for the 32 bit depth and add a greater resolution of 1024x768, as well as setting the refresh rates. It worked like a charm.
(I had tried looking around and running this that and the other first of course)

i hope that helps someone, still make a backup. and write down the commands needed to get you back to the old settings

backup: cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

restore (blind)
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
[ctrl]+[alt]+[backspace]
startx

:)

---

### Post by janub on 2007-10-03
Thank you wolfchri!!!
Now I can at least use a refresh rate of 75.
But I found it realy strange that some of the options that used to work at windows don't seem to work at linux.
Is there anyway to install a monitor driver?

---

### Post by northicert on 2010-09-03
I've upgraded to the latest Ubuntu and had this slight quiver in the edges.
I changed the refresh rate to see if this would help. This was a disastrous choice. I got an out of range blue screen and no way to default. I'm now logged in under another user because mine will just give me the blue out of range screen. Nice job H.B.

---

