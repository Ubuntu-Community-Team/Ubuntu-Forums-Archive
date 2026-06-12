---
title: "Latest mesa (7.10.3) breaks gnome-shell"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-16
Latest mesa upgrade from 7.10.2 to 7.10.3 from Oneiric repos breaks gnome-shell.
This happens in my setup with Nvidia graphics card and latest nvidia-current (275.09.07) in use.

The .xsession-errors file gives this message:

```
gnome-session-is-accelerated: No hardware 3D support.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session[1113]: WARNING: Session 'gnome' runnable check failed: Exited with code 1
```

So 3D is not anymore working with 7.10.3 mesa.
Downgrading to 7.10.2 solves this issue.

---

### Post by Harry33 on 2011-06-16
Here is the bug report (#798007):

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/798007](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/798007)

---

### Post by mc4man on 2011-06-16
Broke all 3d support here as well though I'd suspect it may work w/nvidia if using or switching to  nouveau (3d 

It seems to include what was formerly libgl1-mesa-dri-experimental, I'd guess O is now going to include 3d support for supported nvidia adapters thru nouveau

---

### Post by Harry33 on 2011-06-16
> **mc4man said:**
> Broke all 3d support here as well though I'd suspect it may work w/nvidia if using or switching to  nouveau (3d 

It seems to include what was formerly libgl1-mesa-dri-experimental, I'd guess O is now going to include 3d support for supported nvidia adapters thru nouveau

The incompatibility with nvidia-current and fglrx is due to the migration of alternatives for the ld.so.conf snippets.

However, the installation of the package libgl1-mesa-glx 7.10.3-0ubuntu1 breaks:
fglrx (<= 2:8.850-0ubuntu1)
nvidia-173 (<= 173.14.30-0ubuntu2)
nvidia-current (<= 270.41.19-0ubuntu1)

The latest nvidia-current is, however, version 275.09.07, so it does not break that.
Not even though it breaks all 3D anyway.

---

### Post by mc4man on 2011-06-16
> The latest nvidia-current is, however, version 275.09.07, so it does not break that.
That makes sense due to the timing of the packages (somewhat.

While I won't use for real here it's fine with nvidia removed and the nouveau 3d support default supplied. 
(even though there is a significant mem saving with nouveau vs. nvidia - about 80MB @ login w/ non gl cairo and 350 - 400MB w/ the current gl enabled cairo on a unity/compiz login.

---

### Post by paul_in_london on 2011-06-16
I seem to have run into this in VB as well. When gnome-shell failed to load after login (and before I looked at the logs) I just tried to start it manually:

```
paul@oneiric:~$ gnome-shell &
[1] 1271
paul@oneiric:~$ Window manager warning: Locale not understood by C library, internationalization will not work

(gnome-shell:1271): Clutter-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.

(gnome-shell:1271): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
failed to create drawable

(gnome-shell:1271): Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
```

Seeing the same as **Harry33** in **.xsession-errors**.

---

### Post by t.rei on 2011-06-16
I had abandoned the xorg-edgers ppa on this install, but now enabled it 
Upgrade including their repository made gnome-shell to work again.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Harry33 on 2011-06-16
> **t.rei said:**
> I had abandoned the xorg-edgers ppa on this install, but now enabled it 
Upgrade including their repository made gnome-shell to work again.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Do you mean you upgraded the mesa 7.11.0 tree from Edgers PPA?

It may very well be that the path Canonical has choosen with the multiarch support prevents people from using proprietary driver updates from PPA's in the future.
You see nvidia-current has now been removed from Xorg-Edgers PPA (Oneiric).

---

### Post by Harry33 on 2011-06-16
Mesa (bug #798007) has now been fixed.
The package libgl1-mesa-glx now breaks all nvidia-current versions, thus preventing them from being installed into the same setup.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu2)

---

### Post by paul_in_london on 2011-06-16
> **t.rei said:**
> I had abandoned the xorg-edgers ppa on this install, but now enabled it 
Upgrade including their repository made gnome-shell to work again.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Not for me in VB yet. I still have the **xorg-edgers** ppa enabled in my VB install, but apparently I don't have your latest mesa update yet?

```
paul@oneiric:~$ ls -lart /var/cache/apt/archives/*mesa* | grep 7.10.3
-rw-r--r-- 1 root root  163302 Jun 16 03:05 /var/cache/apt/archives/libglu1-mesa_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  107464 Jun 16 03:05 /var/cache/apt/archives/libgl1-mesa-glx_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root 2586374 Jun 16 03:05 /var/cache/apt/archives/libgl1-mesa-dri_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  871844 Jun 16 03:05 /var/cache/apt/archives/libegl1-mesa_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  788718 Jun 16 03:05 /var/cache/apt/archives/libegl1-mesa-drivers_7.10.3-0ubuntu1_i386.deb
paul@oneiric:~$ 
```


And this is what I get if I try:

```
paul@oneiric:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  gnome-panel{b} gnome-panel-data 
The following packages are RECOMMENDED but will NOT be installed:
  alacarte evolution-data-server 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 671 kB of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
  gnome-panel: Breaks: libpanel-applet-3-0 but 1:2.32.1-0ubuntu6.5 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     indicator-applet            
2)     indicator-applet-appmenu    
3)     indicator-applet-complete   
4)     indicator-applet-session    
5)     libpanel-applet-3-0         



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

instead of a safe-upgrade.

Btw, I also have the ricotz ppa enabled. Now I've just checked my apt sources and I'm not seeing the xorg-edgers ppa. Maybe I don't have it enabled in this OO ibnstall after all. Will post back...

---

### Post by Harry33 on 2011-06-16
> **paul_in_london said:**
> Not for me in VB yet. I still have the **xorg-edgers** ppa enabled in my VB install, but apparently I don't have your latest mesa update yet?

```
paul@oneiric:~$ ls -lart /var/cache/apt/archives/*mesa* | grep 7.10.3
-rw-r--r-- 1 root root  163302 Jun 16 03:05 /var/cache/apt/archives/libglu1-mesa_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  107464 Jun 16 03:05 /var/cache/apt/archives/libgl1-mesa-glx_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root 2586374 Jun 16 03:05 /var/cache/apt/archives/libgl1-mesa-dri_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  871844 Jun 16 03:05 /var/cache/apt/archives/libegl1-mesa_7.10.3-0ubuntu1_i386.deb
-rw-r--r-- 1 root root  788718 Jun 16 03:05 /var/cache/apt/archives/libegl1-mesa-drivers_7.10.3-0ubuntu1_i386.deb
paul@oneiric:~$ 
```


And this is what I get if I try:

```
paul@oneiric:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  gnome-panel{b} gnome-panel-data 
The following packages are RECOMMENDED but will NOT be installed:
  alacarte evolution-data-server 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 671 kB of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
  gnome-panel: Breaks: libpanel-applet-3-0 but 1:2.32.1-0ubuntu6.5 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     indicator-applet            
2)     indicator-applet-appmenu    
3)     indicator-applet-complete   
4)     indicator-applet-session    
5)     libpanel-applet-3-0         



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

instead of a safe-upgrade.

You probably have the mesa 7.10.3-0ubuntu1.
The fixed version is mesa 7.10.3-0ubuntu2 and it is still building.

---

### Post by paul_in_london on 2011-06-16
> **Harry33 said:**
> You probably have the mesa 7.10.3-0ubuntu1.
The fixed version is mesa 7.10.3-0ubuntu2 and it is still building.

Thanks **Harry33**. With the edgers updates gnome-shell is working again and I now have:

```
paul@oneiric:~$ ls -lart /var/cache/apt/archives/lib*mesa* | grep 7.11
-rw-r--r-- 1 root root   197676 Jun 14 23:59 /var/cache/apt/archives/libglu1-mesa_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
-rw-r--r-- 1 root root    53152 Jun 14 23:59 /var/cache/apt/archives/libglapi-mesa_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
-rw-r--r-- 1 root root   131670 Jun 14 23:59 /var/cache/apt/archives/libgl1-mesa-glx_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
-rw-r--r-- 1 root root 12730402 Jun 14 23:59 /var/cache/apt/archives/libgl1-mesa-dri_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
-rw-r--r-- 1 root root 11741616 Jun 14 23:59 /var/cache/apt/archives/libegl1-mesa-drivers_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
-rw-r--r-- 1 root root  3553322 Jun 14 23:59 /var/cache/apt/archives/libegl1-mesa_7.11.0+git20110614.7d488ade-0ubuntu0sarvatt_i386.deb
paul@oneiric:~$
```

Thought I already had it in this VBox install, but anyway...

Still need something from the main repos or the gnome3-team ppa to fix this though:

```
paul@oneiric:~$ sudo aptitude full-upgrade
The following packages will be upgraded: 
  gnome-panel{b} gnome-panel-data 
The following packages are RECOMMENDED but will NOT be installed:
  alacarte evolution-data-server 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 671 kB of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
  gnome-panel: Breaks: libpanel-applet-3-0 but 1:2.32.1-0ubuntu6.5 is installed.
```

Well..unless I remove **indicator-applet-session**:

```
paul@oneiric:~$ sudo aptitude why libpanel-applet-3-0
i   indicator-applet-session Depends libpanel-applet-3-0
```

Actually, no. Should have known just from the names that: ```
paul@oneiric:~$ sudo apt-cache show gnome-panel | grep libpanel-applet
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10.0), libdconf0 (>= 0.7), libecal1.2-8 (>= 3.0.2.1), libedataserver1.2-14 (>= 3.0.2.1), libedataserverui-3.0-0 (>= 3.0.2.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libgnome-desktop-3-0 (>= 2.91.5), libgnome-menu2 (>= 2.27.92), libgtk-3-0 (>= 3.0.0), libgweather-3-0 (>= 2.91.0), libical0 (>= 0.30), libice6 (>= 1:1.0.0), libpanel-applet-4-0 (>= 2.91.93), libpango1.0-0 (>= 1.18.0), librsvg2-2 (>= 2.14.4), libsm6, libtelepathy-glib0 (>= 0.14.0), libwnck-3-0 (>= 2.91.6), libx11-6, libxrandr2 (>= 2:1.2.99.3), gnome-icon-theme-symbolic (>= 3.0.0), gnome-panel-data (= 1:3.0.2-0ubuntu4), gnome-menus (>= 2.27.92)
Breaks: gnome-applets (<< 2.91), gnome-control-center (<< 1:2.91), gnome-power-manager (<< 2.26), gnome-session (<< 2.26), gnome-settings-daemon (<< 2.91), libpanel-applet-3-0, libpanel-applet2-0, netspeed (<< 0.16-2), python-gnomeapplet
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10.0), libdconf0 (>= 0.7), libecal1.2-8 (>= 3.0.0), libedataserver1.2-14 (>= 3.0.0), libedataserverui-3.0-0 (>= 3.0.0), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libgnome-desktop-3-0 (>= 2.91.5), libgnome-menu2 (>= 2.27.92), libgtk-3-0 (>= 3.0.0), libgweather-3-0 (>= 2.91.0), libical0 (>= 0.30), libice6 (>= 1:1.0.0), libpanel-applet-4-0 (>= 2.91.93), libpango1.0-0 (>= 1.18.0), librsvg2-2 (>= 2.14.4), libsm6, libtelepathy-glib0 (>= 0.14.0), libwnck-3-0 (>= 2.91.6), libx11-6, libxrandr2 (>= 2:1.2.99.3), gnome-icon-theme-symbolic (>= 3.0.0), gnome-panel-data (= 1:3.0.2-0ubuntu3), gnome-menus (>= 2.27.92)
paul@oneiric:~$
```

Or I could also have said:

```
paul@oneiric:~$ sudo aptitude why -vv libpanel-applet-3-0 | grep gnome-panel
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
    ++ Examining gnome-panel Breaks libpanel-applet-3-0
```

---

### Post by Harry33 on 2011-06-16
Paul_in_London,

The newest Gnome-Panel (in Oneiric official repos) needs these packages to fully work:
- gnome-panel_3.0.2-0ubuntu4
- gnome-panel-data_3.0.2-0ubuntu4
- libpanel-applet-4-0_3.0.2-0ubuntu4

Note, that the package libpanel-applet-3-0 is from GTK+2 version of gnome-panel and not in use any more. You should remove it from your setup. And yes, Gnome-Panel GTK+3 breaks it now.
Also indicator-applet-session is a GTK+2 package and should not be used any more with Gnome3 (Gnome-Shell or Gnome-Panel).

You perhaps should not use any packages from the Gnome3 PPA, they are for Natty, not for Oneiric.
However, most of the packages there are only copied from Oneiric.

---

### Post by paul_in_london on 2011-06-17
Hi Harry33,

Thanks for taking the time to respond. I think I was still half-asleep when I posted yesterday. :lolflag:

Having checked the dependencies again properly, I removed:

```
**indicator-applet-session indicator-applet libpanel-applet-3-0 indicator-applet-appmenu** and **indicator-applet-complete**
```

and then I was able to upgrade:

```
**gnome-panel** and **gnome-panel-data**
```

This is in a VM and I don't remember having this conflict in either of my *real* OO installs @home so I can only assume I don't have the **indicator-applet-*** stuff etc. in those and yet I still seemed to have the functionality that I thought was (only) provided by those packages. And now that I've removed them from the VM install it doesn't look as if I've lost anything particularly obvious.

I've kept the **gnome3-team** ppa in my apt sources for now. From what you say I probably don't really need it any more, but I *should* always pick up anything newer from the main repos when I upgrade anyway.

Cheers.

---

