---
title: "I can't get Ubuntu Software Center to open"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by awood929 on 2011-10-14
It won't start at all. I've been searching around for about an hour trying to find fixes and nothing seems to be working. Sorry if you keep seeing this question but I've tried so many things I don't know what else to do but make a new thread. I might add that this is my first day using Ubuntu (yippee) and I'm actually running Wubi so it's alongside Windows. I don't know if that has anything to do with anything but I'll just give all the information I can. I've tried doing the whole "sudo apt-get update" and even "sudo apt-get upgrade" and that didn't work either. 

Note: what happens when I click on the Software Center icon is it does the whole blinking/fading thing like it's about to start but then it just stops and nothing happens. I've tried getting it to go by attempting to install Flash in the Software Center but of course there was no reaction at all. If anyone could help me I would really appreciate it! Thank you so much!

---

### Post by drs305 on 2011-10-14
awood929,

Welcome to the Ubuntu forums.

Please open a terminal (ALT-F2 gnome-terminal) and try to open it via the command line:
```
gksu software-center
```
When you press ENTER you will be asked for your password. 

See what, if any, error messages are generated and let us know what they are if Software Center still won't open.

---

### Post by awood929 on 2011-10-14
Hi, and thanks for responding. So I did what you said and this is what I got as a result:

```
(gksu:5742): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:5742): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:5742): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:5742): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
    from gi.repository import GObject
  File "/usr/lib/python2.7/dist-packages/gi/repository/__init__.py", line 25, in <module>
    from ..importer import DynamicImporter
ImportError: cannot import name DynamicImporter
```

---

### Post by drs305 on 2011-10-14
There was a bug filed on this. The solution in the bug report was to run this command:
```
sudo apt-get install gtk2-engines-pixbuf
```

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/quickly/+bug/853232]("https://bugs.launchpad.net/ubuntu/+source/quickly/+bug/853232")

The bug report was from last week, but I also found a similar report from 2006.

If you haven't run a 'sudo' command from the terminal, you will be asked for your password. In this case, you won't see it as you type it into the terminal. Just type it and press ENTER.

---

### Post by awood929 on 2011-10-14
Ok, I just tried that and...still nothing. I don't know if maybe I'm doing something wrong or what. Again thanks for your efforts. Do you think I should perhaps try rebooting my laptop and seeing if that changes anything? I'm running out of ideas here haha.

---

### Post by drs305 on 2011-10-14
Rebooting won't hurt if you don't have any installation apps open. I am not finding other solutions regarding this but will keep looking.

I'm assuming you are getting the same errors when you use "sudo apt-get ...", which would rule out a problem specifically with "gksu/gksudo" . If the errors are different with "sudo", please post them as well.

I don't know if it might be something specific to Wubi - I wouldn't think but I'm not a Wubi expert. Offhand, I would think not.

[COLOR="DarkRed"]Added[/COLOR]: Can you try using another theme? Right click the Desktop, then 'Change Desktop Background' and see if other themes are available in the lower right.
You can also try:
```
sudo apt-get install --reinstall light-themes
```

---

### Post by awood929 on 2011-10-14
Still nothing. But when I tried your second suggestion it gave me this:
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

EDIT:
nevermind I had to exit something I guess...but still the software center will not launch. Do you you think maybe I should just start with an entirely clean slate and just re-install Ubuntu?

---

### Post by drs305 on 2011-10-14
> **awood929 said:**
> Still nothing. But when I tried your second suggestion it gave me this:
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

EDIT:
nevermind I had to exit something I guess...but still the software center will not launch. Do you you think maybe I should just start with an entirely clean slate and just re-install Ubuntu?

The message was probably because you had two package managers running at the same time - usually it's Synaptic and a terminal apt-get command running at the same time. 

I generally am not a fan of recommending reinstallations but in truth sometimes that is quicker than troubleshooting. The problem with a reinstall is that there is no guarantee it will work the next time.

Since your system is most likely running other than being able to install or update, if you can do what you need on your system you may wait a bit to see if someone else can come up with a solution. Depending on your download speeds, you could probably reinstall before you will get an answer, but you never know...

One other thing you could try would be booting to the recovery mode from the Grub menu, getting to a command prompt, and running the apt-get commands to see if they will work from there. If you are at a root prompt, you don't use 'sudo'. You could also try the 'fix broken packages' just in case it can find a problem.

---

### Post by awood929 on 2011-10-14
Yeah, so I went ahead and re-installed...It didn't take too long since my connection isn't that bad so I really didn't mind. Lo and behold, Software Center works! I don't know, maybe something just went wonky in my first attempt to download the OS...Still, thank you so much for all your help and your quick responses. It's nice to know there are people I can count on for advice :D

Have a good one!

---

### Post by djahma on 2011-10-15
Hi,
Typing software-center doesnt open the ubuntu software centre for me as well. In term of messages, it hangs after this:
```

2011-10-15 18:11:48,235 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-15 18:11:48,913 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-15 18:11:49,025 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for adwaita Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css

```
Then I get a blank window with "ubuntu software center" in the title, but I can't close it so I must kill its process. 
However typing sudo software-center does work fine:confused:
After that I tried to modify certain .desktop files to be able to launch the app from icons in gnome-shell. 
so I modified /usr/share/applications/ubuntu-sofware-center.destop property to $ sudo software-center
Tried also with /usr/share/app-install/desktop/ubuntu-sofware-center.desktop property to gksudo software-center
But nothing worked.

Basically, I'm trying to get the software-center app icons to work again, any help?
Thanks

---

