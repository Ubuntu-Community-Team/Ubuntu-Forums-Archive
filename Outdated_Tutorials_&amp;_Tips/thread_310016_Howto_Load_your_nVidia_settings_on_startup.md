---
title: "Howto: Load your nVidia settings on startup"
date: 2006-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Malikith on 2006-11-30
This howto is very simple, quick and easy. But to start off, I was wondering for the longest time how to do this but figured it out on my own. Lets say, you have anti aliasing and anisotropic filtering settings set in your nVidia settings along with digital vibrance settings and color settings. Now lets say you reboot your computer, now you have to run nvidia-settings again to make them take effect, since they do not take effect on reboot by default. Well theres a way to make them take effect when starting up gnome.

This howto only goes for Gnome at the moment, but if someone could kindly show me how to do it in KDE as well, that would be great for others to know. Well anyway, enough of my rambling, lets get started.

[SIZE="4"]How to do it:[/SIZE]

1). First go to System at the top left, preferences then sessions. 

2). Now click the Startup Programs tab.

3). Click add.

4). Type this in the box, nvidia-settings -l

5). The -l is a L but it **MUST** be lowercase else it will be a unrecognized option.

6). Now click ok, and go ahead and close the sessions menu there and you're all set. Enjoy!

---

### Post by 454redhawk on 2006-12-16
I use this in the sessions startup tab.


```
nvidia-settings --load-config-only
```

nvidia-settings must have been at least once in order for settings to be restored. The settings file is stored in ~/.nvidia-settings-rc

---

### Post by fillintheblanks on 2008-03-10
just what I've been looking for thanks!

---

### Post by floyin on 2008-07-02
Thanks for posting this! Helped alot!

---

### Post by jualin on 2008-07-06
just what i have been looking for too. My friend was asking this the other day and I couldn't give him an answer. Thanks!:KS

---

### Post by deepclutch on 2009-05-30
thanks.Was just wondering how to achieve this.

---

### Post by royfmont13 on 2010-04-26
Thanks! Just the kind of thing I was looking for!
Ubuntu 9.10 Karmic
nvidia settings

---

### Post by Lloyd Ewing on 2010-12-26
This work-around is still required for Ubuntu 10.04 LTS!
In my case, this is how it worked:

1). First click on System at the top left, Preferences, then "Startup Applications".
2). Under the "Startup Programs" tab there is an application called "NVIDIA X Server Settings" which was not checked!
3). Check the box then click Close at the bottom of the window.


It is amazing how much wrong information there is on this problem in help.ubuntu.com and wiki.ubuntu.com.  I spent days trying to find a way to use xrandr as described on those pages, and I never was able to find a way to make it work.

---

### Post by VietCanada on 2010-12-31
Same instructions for Ubuntu 10.10 as for 10.04 above.

I dual boot and while I can set up my 42" flat screen a s a seperate monitor with Ubuntu I can't seem to do the same with Windows 7. In fact I sometimes have to change my TV input back to PC mode so I can retrieve windows that open there instead of on my monitor.

It often seems to be the case that Ubuntu works while Windows makes me work.

Same with my wireless keyboard and mouse. Windows stops everything and spends a bit of time searching and installing drivers. They worked immediately on Ubuntu. I just plugged in the little USB thingy and unplugged the old stuff. Didn't even reboot.

---

### Post by chaoticist on 2011-02-15
I had a lot of trouble with this solution not working, until after Googling for solutions many times...I came across something interesting.

It's a good idea to use "sudo nvidia-settings" to save your config as root, we know that. What you may not know is that for the above solution to work, "include X Display Names in Config File" must ***not*** be selected. This is what causes nvidia-settings to revert to the default settings, rather than using nvidia-settings-rc to remember what settings you have selected.

---

### Post by avengery on 2011-05-17
that was helpful .. Thanks

---

