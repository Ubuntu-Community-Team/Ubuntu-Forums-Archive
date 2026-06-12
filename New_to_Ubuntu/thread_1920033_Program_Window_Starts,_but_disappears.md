---
title: "Program Window Starts, but disappears"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by ebeth on 2012-02-04
I'm having a problem with application starting.

This has happened twice, both with application I've tried to install - the two are Clementine Music Organizer and Player and Synaptic.

With Clementine I've started the app, which I installed via the "Software Center", from the "Dashboard'.  I see it for about a second then its gone.  

With Synaptic, I've used the tutorial here: [http://ubuntuforums.org/showthread.php?t=1901446](http://ubuntuforums.org/showthread.php?t=1901446)  When I run this I get a warning "unable to locate theme engine in module_path pixmap" but I've been told this is just a bug.

Any ideas why this is happening.

---

### Post by carl4926 on 2012-02-04
Try starting from a terminal and report any feedback you get there

---

### Post by ebeth on 2012-02-04
Still the same issue.  

However, I did find this: [http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing](http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing)  Apparently, the issue is with the accessibility settings.

I used 
> 
gsettings set org.gnome.desktop.interface toolkit-accessibility false

and it runs fine now.




[URL="http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing"]
[/URL]

---

