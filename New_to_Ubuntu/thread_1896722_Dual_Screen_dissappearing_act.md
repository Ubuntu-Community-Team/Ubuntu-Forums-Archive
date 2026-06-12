---
title: "Dual Screen dissappearing act"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by lile001 on 2011-12-17
Successfully reinstalled Ubuntu after a bad crash.  A win!  Especially since I don't know much about Linux.  

I have a dual screen monitor - right after the reinstall it was working.  Have an Nvidia graphics card of some kind.  Was able to use the Display settings to get the second screen to not mirror the first.  

Today I wake up and Screen #2 is blank.  Yes, the monitor is turned on, I have rebooted a couple of times and the cables are connected.  Anyone have a suggestion as to where to start troubleshooting?

---

### Post by lile001 on 2011-12-17
Another hint that might be important - when the computer comes back from a Suspend power operation, the one working screen looks crazy and I end up rebooting.  Fortunately, I have figured out how to get a terminal started (control alt F1) and reboot kindly, instead of hitting BOB the Big Off Button.  

Does this give us a clue as to why Screen #2 isn't working?  

I did the other obvious thing and swapped cables, the second screen works OK if the cables are swapped.

---

### Post by Blinkiz on 2011-12-17
Hello
Start by looking into "nvidia-settings" under X Server Display Configuration. Report back what you can see there.

---

### Post by lile001 on 2011-12-17
> **Blinkiz said:**
> Hello
Start by looking into "nvidia-settings" under X Server Display Configuration. Report back what you can see there.


Now we are getting somewhere:
```

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

```

Not that I have a clue what that means, but it sounds bad.

---

### Post by Blinkiz on 2011-12-17
Yeah, that is not good.
Lets generate a new xorg.conf file.
Run "sudo nvidia-xconfig". Restart your computer and see if you can manage your display with "nvidia-settings".

---

### Post by audiomick on 2011-12-17
the nvidia-settings utility needs to be run with root privileges in order to be able to save to the xorg.config file.

If you want to start it from a terminal, use 

```
gksudo nvidia-settings
```

It is a graphical application, so you should use "gksudo" or "gksu" instead of plain "sudo".

If you are using 11.04 or 11.10, you can find the nVidia settings appication by clicking on the Ubuntu symbol at the top left of the screen and starting to type nVidia into the search window.

On 10.10 and 10.04 it should be in system> adminstration. 

These versions, I believe, were able to save to the xorg.conf file. Previous versions, as far as I remember, had to be started via the terminal with root privileges to be able to save properly.

---

### Post by lile001 on 2011-12-18
Still no luck.  Ran Nvidia xconfig then
 ```

gksudo nvidia-settings

(gksudo:1758): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1758): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1758): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:1758): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

Once the dialog box comes up, it says 

```
Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.
``` 
under "X-Server display configuration".  I assume all that gibberish above is something bad, since monitor 2 is still black.

---

### Post by lile001 on 2011-12-18
OK, let me ask this question a different way, since so far no luck.  

How do I reinstall the NVIDIA, X-server,  and graphics driver stuff that came out of the box when I installed Ubuntu 11.10 a couple of days ago?  It worked then, and maybe some thumb-fingered thing I did since then has broken it.  That is likely, since I have little idea what I am doing most of the time here.

---

### Post by lile001 on 2011-12-19
> **lile001 said:**
> OK, let me ask this question a different way, since so far no luck.  

How do I reinstall the NVIDIA, X-server,  and graphics driver stuff that came out of the box when I installed Ubuntu 11.10 a couple of days ago?  It worked then, and maybe some thumb-fingered thing I did since then has broken it.  That is likely, since I have little idea what I am doing most of the time here.

Does anyone have the slightest idea what to do about this?  Reinstalling this stuff should be straightforward, but I don't know where to start.   Specifically what programs are involved in controlling the monitor, and how do I put them back like they were in the Ubuntu installation?

---

### Post by lile001 on 2011-12-19
> **lile001 said:**
> Does anyone have the slightest idea what to do about this?  Reinstalling this stuff should be straightforward, but I don't know where to start.   Specifically what programs are involved in controlling the monitor, and how do I put them back like they were in the Ubuntu installation?


Not much help here for a helpless N00B.  

I went through this routine

[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

with no luck.  Then on a whim, I removed and then re-installed ndivia-settings via apt-get.  Now the second screen seems to be working, so maybe that was the problem? 

Anyway, thanks to those that did respond.

---

