---
title: "Learning Python: Indicator applet"
date: 2012-11-29
forum: Programming Talk
---

### Post by for.i.am.root on 2012-11-29
Hi All:

So I have started teaching myself python and I figured for my first "program" I could finish something I started a few years back, an applet to display the uptime in human readable format.

By now there are probably a few somebody else has already created, however, I want to write my own. I want it to MEAN something when I check my uptime. Pride thing I guess.

I'm still learning how to code in python so it is technically a BASH script.

I'm looking to update the uptime and display as a menu item, but I'm not sure how.

If you save this in a file and run it from a terminal you will see what I am getting at. The uptime when the script was initially ran will be displayed in the terminal when you click the menu uptime, however, I can't get it to update inside the python code or the bash script itself.

Anyway, help cleaning up code (please HELP, not do it for me (i.e. references to possible solutions not the code) would be much appreciated.

Note: The first two commented lines are for adding the icon to the theme.

Thanks!

```

#!/bin/bash
#sudo xdg-icon-resource install --theme hicolor --novendor --size 24 /home/user/Desktop/UpTime.png
#sudo xdg-icon-resource install --theme ubuntu-mono-dark --novendor --size 24 /home/user/Desktop/UpTime.png
actualsecondsup=`cat /proc/uptime | cut -d'.' -f1-1` && tempminutes=`expr $actualsecondsup / 60` && temp1=`expr $tempminutes \* 60` && realseconds=`expr $actualsecondsup - $temp1` && realhours=`expr $tempminutes / 60` && temp2=`expr $realhours \* 60` && realminutes=`expr $tempminutes - $temp2` && export HumanUpTime=$realhours":"$realminutes":"$realseconds
python - <<END
import sys
import gtk
import appindicator
import os

class UpTime:

    def __init__(self):
        self.ind = appindicator.Indicator("uptime", "UpTime",appindicator.CATEGORY_APPLICATION_STATUS)
        self.ind.set_status(appindicator.STATUS_ACTIVE)
        self.menu_setup()
        self.ind.set_menu(self.menu)

    def menu_setup(self):
        self.menu = gtk.Menu()
        self.item_update = gtk.MenuItem("$HumanUpTime")
        self.item_update.connect("activate", self.update)
        self.item_update.show()
        self.menu.append(self.item_update)
        self.item_quit = gtk.MenuItem("Quit")
        self.item_quit.connect("activate", self.quit)
        self.item_quit.show()
        self.menu.append(self.item_quit)

    def quit(self, widget):
        sys.exit(0)

    def update(self, widget):
        os.system('actualsecondsup=`cat /proc/uptime | cut -d'.' -f1-1` && tempminutes=`expr $actualsecondsup / 60` && temp1=`expr $tempminutes \* 60` && realseconds=`expr $actualsecondsup - $temp1` && realhours=`expr $tempminutes / 60` && temp2=`expr $realhours \* 60` && realminutes=`expr $tempminutes - $temp2` && export HumanUpTime=$realhours":"$realminutes":"$realseconds && echo $HumanUpTime')

    def main(self):
        gtk.main()

if __name__ == "__main__":
    indicator = UpTime()
    indicator.main()
END

```

---

### Post by M!K3_$ on 2012-11-29
> **for.i.am.root said:**
> 
an applet to display the uptime in human readable format.


I hate to burst your bubble, but what is wrong with uptime?
```

 23:43:29 up 2 days,  5:34,  2 users,  load average: 0.49, 0.32, 0.42

```

My local time is 23:43. my system has been up 2 days, 5 hours and 34 minutes. There are two users logged in and my load is peachy. :)

---

### Post by M!K3_$ on 2012-11-29
I took a longer look, it looks like you are parsing /proc/uptime. 
I still say that the uptime command is useful, but for the sake of learning Python I wish you the best of luck!

---

### Post by for.i.am.root on 2012-11-29
Hi M!K3_$:

Nothing, other than it doesn't suit my needs.

I would like an indicator in the panel with JUST my uptime displayed when I click the icon.

I don't want to open a terminal windows and run uptime, if that makes sense.

Thanks!

EDIT: An interesting fact is I can't grab a screen shot while the indicator applet has focus (i.e. You click on an icon to display the menu and the print screen key on your keyboard doesn't work. Interesting.

EDIT2: Got a screenshot, hopefully it clarifies:
sleep 10; import -window root screenshot.png

---

### Post by for.i.am.root on 2012-11-29
Hi All:

Wow. So I figured out that my syntax (format?, new to python so not positive on proper terminology) was wrong when I originally used .set_label. It's now working to update the menu item.

On to more pressing matters, like performing mathematical equations using python so I can eliminate the need for BASH. Should be easy :-D

On another note is it "better" to use subprocess or commands to run a single command?

i.e. 
import commands
humanuptime = commands.getouput("cat /proc/uptime | cut -d'.' -f1-1")
or
from subprocess import call
humanuptime = call(["cat", "/proc/uptime", "|", "cut", "-d'.'", "-f1-1"])

Not sure if the above is correct or not yet, haven't had time to test.

Thanks!

---

