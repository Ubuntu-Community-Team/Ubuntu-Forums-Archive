---
title: "gnomescreensaver mythtv and lirc"
date: 2008-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by oobe-feisty on 2008-08-30
Hi i just started using gnome as apose to KDE recently and noticed that
mythtv would go straight into gnome screensaver after 10 mins while watching video in Internal player since i like gnome screensaver on and prefer Internal player i had to figure out how to disable enable it i thought myth would of done that apparently there is a patch but its not in the ubuntu repos AFAIK.

so i decided to bind commands on my remote to enable disable gnome screensaver

**Assumptions**

you already have mythtv working with lirc configured you run mythtv on a desktop if you have a standalone mythbox then i wouldnt advise running gnome i would use fluxbox

you have lircrc in ~/.mythtv/ and a symbolic link to ~/.lircrc or vice versa


**Here is how I did it **

after a bit of googleing i found this [thread]("http://ubuntuforums.org/showthread.php?t=591090&page=4")  which turns off gnome screensaver so this is how i made it usefull

I made 3 files

powersave0 powersave1 and daemon

powersave0 turns power management and screensaver off 

powersave1 turns power management and screensaver on

and daemon checks if irexec is running if it isnt it will start a new instance 

**powersave0**
```

#!/bin/bash
gconftool-2 --type boolean -s /apps/gnome-screensaver/idle_activation_enabled false
sleep 1
gconftool-2 --type boolean -s /apps/gnome-power-manager/timeout/sleep_display_ac 0
```

**powersave1**

```
#!/bin/bash
gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_display_ac --type int 640
sleep 1
gconftool-2 --type boolean -s /apps/gnome-screensaver/idle_activation_enabled true
```

**daemon**

```
#!/bin/sh
# \
 
if ps -ef|grep -v grep|grep irexec
then
# do nothing
echo "irexec already running"
else
# start irxevent
irexec -d /home/oobe/.lircrc &
fi


```

you will have to edit this line "irexec -d /home/oobe/.lircrc &" to your appropriated user name 
 
then i put all 3 files in /usr/local/bin and make them executable

sudo cp powersave* /usr/local/bin

sudo cp daemon     /usr/local/bin

sudo chmod a+x   /usr/local/bin/powersave*

sudo chmod a+x /usr/local/bin/daemon

now make add daemon to your ~/.config/autostart 

ln -s /usr/local/bin/daemon ~/.config/autostart

or in system / preferences / sessions add it as a start up application

then open ~/.mythtv/lircrc 

and add


```
## disabled enable gnome screen saver and power saving
begin
  prog = irexec
  button = ok
  config = powersave0
end
begin
  prog = irexec
  button = more-i
  config = powersave0
end

begin
  prog = irexec
  button = start
  config = powersave1
end

begin
  prog = irexec
  button = back
  config = powersave1
end

##end gnome screensaver 
```


I chose to execute turn off powersave with buttons related to playing video and turn on powersave with buttons related to stopping watching video  you can bind these commands to as many keys as you want. 

I hope this helps

---

