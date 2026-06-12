---
title: "udev rules not running my script"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by WongFuChu on 2012-01-20
I created a script that would switch the on/off states of my external monitors of my laptop monitor and my TV when connected via HDMI. I set it to run via a keyboard shortcut and it was. But I wanted to run the script whenever I plugged my HDMI cable in/out. I read I can do this by creating a udev rule. I did in /etc/udev/rules.d as hdmi.rules. However, it never ran the script correctly. In order to test if the rules worked, I made the script simply echo a line of text to a empty file whenever it ran. The script did work under the udev rules then, so I think my udev rules are correct. So I'm not sure what's going on...


Does #!/bin/sh and #!/bin/bash make a difference? I read that I should be using #!/bin/sh for udev rules, but my was using #!/bin/bash, so I changed it. Then my script didn't work even when not using udev. My script calls for uses xrandr and xbacklight to toggle monitor and adjust the backlight of my laptop when it is disconnected. Would this cause my script to not work under udev?

Using Ubuntu 11.10

---

### Post by anewguy on 2012-01-20
Try putting a number in the front of the rules file name - a high number so it overrides any previous - such as:

100-hdmi.rules


I've worked with udev rules before, and just always had a number on the front.  The higher the number the better as it overrides the lower numbered rules.

I know it walks the folder as far as reading the rules, but I don't know if it might require the number in order to be processed at all or at least at the tail end so it overrides previous rules.

You might also put echo statements in your script to trace what's happening:

echo **** Beginning xxxxx   > ~/mytest.log
some statement(s)
echo *******  Completed step 1 >> ~/mytest.log
some statement(s)
echo *******  Completed step 2 >> ~/mytest.log
some statements(s)
echo **** End of xxxxx >> ~/mytest.log


Dave ;)

---

### Post by WongFuChu on 2012-01-20
After hours of googling, I came across something like this:

```

USER="$(who | grep :0\) | cut -f 1 -d ' ')"
export XAUTHORITY=/home/$USER/.Xauthority
export DISPLAY=:0

```

Adding this to the top of my script allowed my script to work for commands that used xrandr or xbacklight.

---

