---
title: "I can't open/find the Terminal or use The Software Center in 11.04"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by scalcave on 2012-02-27
I tried doing multiple things but nothing worked. I used ctrl-f2 to try and run terminal, but nothing happened. I went to the Dash to go to Add More Apps and nothing came up. 

Is there anyway to find and use the terminal/fix the Software Center?

---

### Post by HeroOfCanton on 2012-02-27
Terminal shortcut in Unity is Ctrl-Alt-t.

Software center should be located on the quick launch bar on the left (as well as the terminal icon). To add programs from dash enter "software" into the search and the software center should pop-up. That's the program you need for adding software.

Hope I'm not over-simplifying your issue, but wanted to cover the basics since you don't have any responses yet.

---

### Post by Jake5 on 2012-02-27
Try this in the terminal, when its done reboot the computer and try to open the software center, and let us know if it works or not.
```
sudo apt-get update
```

---

### Post by wildmanne39 on 2012-02-27
Hi, if software center is broken tell us the exact issue, then see if you can install packages by using the terminal as stated above, he gave you directions to open it then type:
```
sudo -apt-get update
```
if there are errors please post all of them here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by scalcave on 2012-02-28
> **HeroOfCanton said:**
> Terminal shortcut in Unity is Ctrl-Alt-t..

Thank you for telling me about the keyboard short cut. The terminal works!  I think I removed it from the side bar because I forgot how much I would be using it. However, I still couldn't get the software center to work. 

I used "sudo -apt-get update" and rebooted, but the issue stayed the same: When I click on the Ubuntu Software Center icon it will flash and act like it is about to open, but then nothing happens.

Also, the dash system has stopped working. If I type something in the search bar nothing comes up.

[QUOTE=wildmanne39;11724048]
if there are errors please post all of them here by clicking on new reply and click # and paste the information between the brackets.
Thank you [/QUOTE

I don't think there are any errors. At least none of them pop up saying error.

---

### Post by scalcave on 2012-02-28
[simon@simon-1000HE:~$ gksu software-center

(gksu:2274): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2274): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2274): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:2274): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
2012-02-27 22:12:28,695 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-02-27 22:12:29,289 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-02-27 22:12:44,425 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0]

I was able to open the Software center through the Terminal. I found another one of Wildman's posts. It opened and this was the result in the terminal.Although, it still wouldn't work when I hit the icon.

---

