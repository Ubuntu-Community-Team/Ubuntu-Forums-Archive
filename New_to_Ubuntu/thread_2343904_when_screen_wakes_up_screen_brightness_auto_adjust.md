---
title: "when screen wakes up screen brightness auto adjusts to highest setting on Acer laptop"
date: 2016-11-20
forum: New to Ubuntu
---

### Post by juntjoo2 on 2016-11-20
I couldn't find anything in settings that looked like it could help with this?  Did I miss something?  Thanks

---

### Post by juntjoo2 on 2016-11-21
Anyone have any ideas?  Haven't found anything on this yet.

well I found this possible solution: 

[https://itsfoss.com/ubuntu-mint-brightness-settings/](https://itsfoss.com/ubuntu-mint-brightness-settings/)

([FONT=monospace]sudo add-apt-repository ppa:nrbrtx/sysvinit-backlight
[/FONT]sudo apt-get update 
su[FONT=monospace]do apt-get install sysvinit-backlight[/FONT] )


but haven't tried it yet as I don't know how to remove this script if it doesn't work.  Can anyone explain how to undo such changes if they don't work for you?

---

### Post by deadflowr on 2016-11-21
> but haven't tried it yet as I don't know how to remove this script if it doesn't work. Can anyone explain how to undo such changes if they don't work for you?
Change the install command to remove
from
```
sudo apt-get install sysvinit-backlight
```
to
```
sudo apt-get remove sysvinit-backlight
```
then remove the repository by adding the -r option for remove like
```
sudo add-apt-repository -r ppa:nrbrtx/sysvinit-backlight
```
then re-run the apt-get update command.

---

### Post by juntjoo2 on 2016-11-21
thank you!

didn't work.  right now I'm looking at this page:

[http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart)

as it appears to address my exact problem but they're all over the place with various code and I haven't a clue on what to start typing into my command line. Any advice? I don't care what brightness it boots up with, I just want it to remember after suspending the last level I had it on.

oops

someone suggested this:


[LIST=1]
[*]Check brightness levels by running this command as root:
cat /sys/class/backlight/acpi_video0/max_brightness 
(my laptop max brightness is 20)
[*]Set you screen brightness to minimum and check current level by evoking next command
cat /sys/class/backlight/acpi_video0/brightness 
(my laptop min brightness level is 0;)
[*]Edit /etc/rc.local and *add before* exit 0 the following line:
echo YOUR_VALUE > /sys/class/backlight/acpi_video0/brightness
[/LIST]
[COLOR=#111111][FONT=Ubuntu]From now on this brightness level will be set every time you start your computer.

Someone else suggested using:

[/FONT][/COLOR]echo X > /sys/class/backlight/intel_backlight/brightness

a little different, and either one produced an error, of which the last one was:

** (gedit:6802): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
 
but it kinda worked as now when I wake up my laptop the brightness is really dark, darker than my lowest setting regardless of what number I put in the instruction and darker is better than brightest.  Anyone familiar with these parts of the system and how I can just simply get the system to keep in memory the last brightness level I've set?  Thanks

actually,
now after restarting comp it doesn't work.  Back to resorting to highest brightness level :(

---

