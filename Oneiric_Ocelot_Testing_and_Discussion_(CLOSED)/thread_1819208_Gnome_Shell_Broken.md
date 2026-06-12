---
title: "Gnome Shell Broken"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-08-05
Todays updates seemed to have killed my Gnome Shell.   Anybody else or is it just me?

---

### Post by FatAngus on 2011-08-05
Gnome Shell is broken here as well :(

---

### Post by aeronutt on 2011-08-05
No workie for me either, but it didn't work in A2 either. :)

---

### Post by mdhollis on 2011-08-05
It seems pretty widespread.
 
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477)

---

### Post by Harry33 on 2011-08-06
This issue has been fixed by the newest update of gnome-session (3.1.3-0ubuntu8 ).

---

### Post by mdhollis on 2011-08-06
> **Harry33 said:**
> This issue has been fixed by the newest update of gnome-session (3.1.3-0ubuntu8 ).

Hey Harry, this round of updates didn't do it for me.:confused:

---

### Post by TDK800 on 2011-08-06
The updates didn't fix it here either. Gnome shell still broken.

---

### Post by paul_in_london on 2011-08-06
These were the updates that fixed it for me:

```
paul@oneiric:~$ ls -lart /var/cache/apt/archives/gnome*
-rw-r--r-- 1 root root  427632 2011-08-02 15:05 /var/cache/apt/archives/gnome-settings-daemon_3.1.4-0ubuntu3_i386.deb
-rw-r--r-- 1 root root 1362812 2011-08-02 21:05 /var/cache/apt/archives/gnome-keyring_3.1.1-0ubuntu3_i386.deb
-rw-r--r-- 1 root root 1362802 2011-08-03 21:04 /var/cache/apt/archives/gnome-keyring_3.1.1-0ubuntu4_i386.deb
-rw-r--r-- 1 root root    5412 2011-08-05 08:04 /var/cache/apt/archives/gnome-session-fallback_3.1.3-0ubuntu7_all.deb
-rw-r--r-- 1 root root   40356 2011-08-05 08:04 /var/cache/apt/archives/gnome-session-common_3.1.3-0ubuntu7_all.deb
-rw-r--r-- 1 root root   13772 2011-08-05 08:04 /var/cache/apt/archives/gnome-session_3.1.3-0ubuntu7_all.deb
-rw-r--r-- 1 root root  168612 2011-08-05 08:04 /var/cache/apt/archives/gnome-session-bin_3.1.3-0ubuntu7_i386.deb
[B]-rw-r--r-- 1 root root    5436 2011-08-06 07:04 /var/cache/apt/archives/gnome-session-fallback_3.1.3-0ubuntu8_all.deb
-rw-r--r-- 1 root root   40358 2011-08-06 07:04 /var/cache/apt/archives/gnome-session-common_3.1.3-0ubuntu8_all.deb
-rw-r--r-- 1 root root   13768 2011-08-06 07:04 /var/cache/apt/archives/gnome-session_3.1.3-0ubuntu8_all.deb
-rw-r--r-- 1 root root  168644 2011-08-06 07:05 /var/cache/apt/archives/gnome-session-bin_3.1.3-0ubuntu8_i386.deb[/B]
```

I'm also using the **ricotz/testing** ppa.

```
paul@oneiric:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.1.3+git20110718.a012dd83-0ubuntu1~11.10~ricotz0
  Candidate: 3.1.3+git20110718.a012dd83-0ubuntu1~11.10~ricotz0
  Version table:
 *** 3.1.3+git20110718.a012dd83-0ubuntu1~11.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status
     3.1.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages
paul@oneiric:~$
```

---

### Post by TDK800 on 2011-08-06
Tried the ricotz/testing repository, but no change, "startx" is still going to Nautilus.

---

### Post by Sennaista on 2011-08-06
Yep, still broken and attempting to log into gnome-shell seem to break unity too.

---

### Post by sammiev on 2011-08-06
I updated from unity from one of my laptops and the others I had a choices of other gnome desktops I could load to take the update. They all updated fine. GL :)

---

### Post by sgage on 2011-08-06
GS seems to more or less work for me, but the menus in Firefox do not work. Click on the menu item, and simply nothing happens. Oh well. Two steps forward, one step back.

---

### Post by xebian on 2011-08-06
Updated today and it works.  Surprisingly, the nouveau driver is working while the nvidia current or the proprietary 280.13 doesn't work at all

---

### Post by aeronutt on 2011-08-06
Same here, updated in Unity, and GS is now working. Awesome. Graphics/response is much snappier than in 11.04 on my laptop.:D:D

---

### Post by Sennaista on 2011-08-06
Here's my situation:

Did a clean install of Alpha 3, rebooted and logged into Unity. Installed gnome-shell, logged out and tried to log into gnome-shell but nothing happens. Everything, including gnome-session, gnome-session-common and gnome-session-bin is the latest version. I can drop to terminal by Ctrl+Alt+F1, log in and restart lightdm but again I am unable to log into either Unity or gnome-shell and trying to drop to terminal and restart lightdm for a second time results in an almighty crash that only a physical restart can deal with. I'm using an ATI card by the way.

It's naff.

---

### Post by mdhollis on 2011-08-06
> **xebian said:**
> Updated today and it works.  Surprisingly, the nouveau driver is working while the nvidia current or the proprietary 280.13 doesn't work at all

I'm going to give that a try right now and see how I make out.


The nouveau driver fixed it for me too.

---

### Post by Harry33 on 2011-08-07
> **xebian said:**
> Updated today and it works.  Surprisingly, the nouveau driver is working while the nvidia current or the proprietary 280.13 doesn't work at all

The biggest problem I had with nvidia-current in Oneiric is that it is incompatible with the recent cairo package, which is built with gl enabled.
Downgrading to the earlier, non gl enabled version (1.10.2-2ubuntu4) solves those issues.
After that downgrading, these troublesome packages can be removed:
- libegl1-mesa
- libgbm1
- libxcb-dri2-0
- libxcb-xfixes0

The working cairo is here:
[https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4](https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu4)

---

### Post by TDK800 on 2011-08-07
Could you give the method/commands used for doing the libcairo downgrade? 

It wants to remove hundreds of packages when I try to remove the newer libcairo version and building the older libcairo version isn't downgrading from the newer.

---

### Post by mc4man on 2011-08-07
> **TDK800 said:**
> Could you give the method/commands used for doing the libcairo downgrade? 

It wants to remove hundreds of packages when I try to remove the newer libcairo version and building the older libcairo version isn't downgrading from the newer.
When you want/need to downgrade a package or group of packages you put them in a folder, cd to that folder in a terminal and run 
```
sudo dpkg -i *.deb
```

If for some reason, (like you where missing a package) it errors, then you'd get what you need and re run until it runs without error

In this case someone has created a ppa build so you may wish to use that instead - link to ppa in this thread, post 25

[http://ubuntuforums.org/showthread.php?t=1818790&page=2](http://ubuntuforums.org/showthread.php?t=1818790&page=2)

(the only thing about using a ppa or older package version is it may in some cases prevent you from filing an apport bug if that's a concern

---

### Post by Sennaista on 2011-08-07
It has mysteriously started working again on my installation but now there's a white panel, with a sort of global menu used in Unity, behind the top gnome-shell panel which doesn't do anything.

---

### Post by Rifester on 2011-08-07
Mine is working again as well, but with the global menu in the gnome shell panel.....

---

### Post by TDK800 on 2011-08-08
"startx" loads a purple background, no panel version of destkop, alt+f2 isn't working and there's a top menu where "Help > About" says it's Nautilus. I can create a .html file on desktop and launch Firefox through that.

"start lightdm" loads a nice graphical user selection box and I can even select between "Gnome / Ubuntu / Ubuntu 2D" ...but all these options load a black background with a low-graphics X shaped mouse pointer, which is even more useless than the Nautilus.

Also, lightdm loads up to the user selection menu without problems whereas gdm is hangs on the "Checking battery state..."

Any suggestions?

---

### Post by TDK800 on 2011-08-08
ok made some progress - If I log in through lightdm as Guest all the desktops work ok, though very slow, but as normal user, nothing's working.

---

### Post by zonum on 2011-08-08
gnome-shell/Alpha 3 was working fine for me, until I performed "today's dist-upgrade/upgrade", and I am now getting the black screen with a low-res X on the screen.

Thanks

---

### Post by sgage on 2011-08-08
> **zonum said:**
> gnome-shell/Alpha 3 was working fine for me, until I performed "today's dist-upgrade/upgrade", and I am now getting the black screen with a low-res X on the screen.

Thanks

I upgrade every day with Synaptic. Gnome Shell works fine here, as does Unity.

---

### Post by 64bitguy on 2011-08-08
After my "Partial Upgrade" which was run from Ubuntu 2D, I lost the ability to login to GNOME getting the, "Failed to load session 'GNOME'" message.

During that upgrade (from my 11.10 daily build from last week), I saw DOZENS of Gnome related errors.

---

### Post by sgage on 2011-08-08
> **64bitguy said:**
> After my "Partial Upgrade" which was run from Ubuntu 2D, I lost the ability to login to GNOME getting the, "Failed to load session 'GNOME'" message.

During that upgrade (from my 11.10 daily build from last week), I saw DOZENS of Gnome related errors.

Partial Upgrade = All Bets Are Off.

Have you never read the sticky at top?

---

### Post by sgage on 2011-08-09
BTW, I am still having the problem in GS that menus in Firefox don't work - is anyone else seeing this?

FF menus work fine in Unity, and everything else in GS seems fine, as well.

[Edit: FF menus are now working in GS, at least this session. They did not work for several sessions in a row, and nothing has changed - very odd.]

---

### Post by mdhollis on 2011-08-09
> **zonum said:**
> gnome-shell/Alpha 3 was working fine for me, until I performed "today's dist-upgrade/upgrade", and I am now getting the black screen with a low-res X on the screen.

Thanks

It's weird I had a similiar issue and it turned out for some reason gnome-shell wasn't installed on my system.:confused:  I re-installed gnome-shell and I was ok.

---

### Post by TDK800 on 2011-08-20
Yesterday's updates solved all issues here too. Gnome and Unity running without problems now!

---

