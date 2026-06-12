---
title: "Terminal from grub"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Sub101 on 2008-09-13
Is it possible to create a grub option that will boot to a console?

---

### Post by Bucky Ball on 2008-09-13
ctrl/alt/f1 will take you to a terminal from the login screen if that is any good. Asks for login then you are in a shell.

---

### Post by Sub101 on 2008-09-13
hmmm yeh. What i am after is something that loads straight into the console so it loads in a few seconds.

---

### Post by billgoldberg on 2008-09-13
> **Sub101 said:**
> hmmm yeh. What i am after is something that loads straight into the console so it loads in a few seconds.

Correct me if I am wrong, but the system still has to load even when you only need a console.

The only thing that won't load is X.

---

### Post by Bucky Ball on 2008-09-13
Exactly.

---

### Post by Sub101 on 2008-09-13
Yeh thats a good point. Maybe this idea isnt so useful then. Cheers

---

### Post by Bucky Ball on 2008-09-13
You could run a system with no desktop (text only) and that would be like one big terminal. You could load the server version to do this and just add packages as you need them. There are other ways and distros for the bare-bones fan.

---

### Post by billgoldberg on 2008-09-13
One of the standard grub options should allow you to boot straight to a console.

I forget which one (never use it), it might be useful.

You should be able to make this the default behaviour. Google should help you with that.

You would then start gnome using the command "startx" should you need a gui interface.

---

### Post by caljohnsmith on 2008-09-13
It sounds like what you want is basically what happens when you boot into "recovery mode" from the Grub menu. It dumps you into a console as root user. Is that sort of what you are looking for?

---

### Post by ChanServ on 2008-09-13
i think what you want to do is get rid of gdm (gmd? cant remember) and then you will get loged into a terminal. and start the gui with startx.

---

### Post by louieb on 2008-09-13
Not so easy to do in Ubuntu. The short of it is Linux has  run levels 

[LIST]
[*]0 is for shutdown
[*]1 is for single user mode. (that what you get when you select recovery mode)
[*]2-5 multi user mode (in Ubuntu run levels 2-5 all do the same thing)
[*]6 reboot
[/LIST]

What you would need to do is modify one of the runlevels to boot in multi user mode but not start x. Thats the hard part.

Then you can modify GRUB to pass the  run level you want the kernel to use.
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

### Post by caljohnsmith on 2008-09-13
> **louieb said:**
> Not so easy to do in Ubuntu. The short of it is Linux has  run levels 

[LIST]
[*]0 is for shutdown
[*]1 is for single user mode. (that what you get when you select recovery mode)
[*]2-5 multi user mode (in Ubuntu run levels 2-5 all do the same thing)
[*]6 reboot
[/LIST]

What you would need to do is modify one of the runlevels to boot in multi user mode but not start x. Thats the hard part.

Then you can modify GRUB to pass the  run level you want the kernel to use.
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)
Or how about logging in as single user mode (recovery mode), and just doing:
```
su -l <username>
```
To become username instead of root. Wouldn't that accomplish the same thing, or is my brain 404 right now? :)

---

### Post by lswb on 2008-09-13
It's harder with the upstart system that ubuntu uses than with the older init and runlevel system. IIRC dapper was the last ubuntu version that used the older init style. In that setup, you could simply add for example "3" to the end of the kernel command line in grub to have it start in runlevel 3. If your /etc/rc3.d links didn't include gdm or other graphical display manager. you'd get a text-mode login.

Unfortunately with the upstart system as configured in ubuntu desktop, the default runlevels are all the same, and the "single" option is used to start in recovery mode. Anything other than "single" will run a default starup, which will always be reported as runlevel 2

However, it is possible to change a few things and get a non-graphical login. Here's a web page that describes a way:

[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)

The method described changes the file /etc/event.d/rc-default so that it scans the kernel command line, which is available at /proc/cmdline, and takes action accordingly. For actually setting up say runlevel 3 so that it doesn't use gdm, kdm, or other graphical login, install package sysv-rc-conf. Run it from a terminal and uncheck gdm and whatever else you don't want running in the column for your text-only runlevel.

Please note the cautions on the website! A typo in editing /etc/rc-default can stop your system from booting! Make sure you have a live CD, live USB drive or some othe means of booting just in case, and that you know how to mount your hard drive and edit a file from that method!

---

