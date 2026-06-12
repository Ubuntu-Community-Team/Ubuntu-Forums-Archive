---
title: "monitor auto switch or via shortcut key"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by raghav6 on 2014-09-13
I've an 1080p VGA monitor connected as an external monitor to my laptop I can easily switch between monitors with 'default display settings'  but my external monitor is directly connected to the power supply so when ever power shortage happens monitor shuts off immediately and I've no way of switching display back to laptop monitor :( so is there any way I can make lubuntu switch to default laptop display when ever power out rage happens or is it possible to setup a shortcut key  via witch i can switch display ? 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
```

---

### Post by raghav6 on 2014-09-14
anybody ?

---

### Post by raghav6 on 2014-10-04
an update after a lot of research I finally found this nifty command now all I need to to know how to execute a command via a specific shortcut key I'll just put the codes here if anyone is interested

for turning off external/vga monitor and turning on laptop monitor
```
xrandr --output LVDS1 --auto --output VGA1 --off
```
for turning on external/vga monitor and turning off laptop monitor
```
$ xrandr --output LVDS1 --auto --output VGA1 --off
```

now i just want to learn how to make it work via a shortcut key

---

### Post by Vladlenin5000 on 2014-10-04
Many laptops have a keyboard switch for that.

---

### Post by raghav6 on 2014-10-05
I tried the one that I have on my laptop but it didn't worked :(

---

### Post by feyenoord on 2014-10-05
I don´t know if it will succeed, but try this idea:
- Make a bin directory in your home folder. (mkdir -p ~/bin)
- In this directory, write a script called switchmonitor in your bin folder like this and make it executable:
> $ mkdir -p ~/bin
$ cat > ~/bin/switchmonitor << 'EOF'
#!/bin/sh
exec xrandr --output LVDS1 --auto --output VGA1 --off
EOF
$ chmod +x ~/bin/switchmonitor




- Add the path of your script in the Path Variable (echo $PATH, EXPORT PATH=¨PATH¨) or logout and logBiin again.
- Bind this script with keyboard shortcut keys (Keyboard binding, DCONF or something)

---

### Post by tgalati4 on 2014-10-05
See if you have a *battery* script:

> tgalati4@Mint14-Extensa /etc/acpi/events $ cat battery
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh


If you do not have a *power.sh* file in /etc/acpi, then you can susbstitue the script called *switchmonitor* described by feyenoord in Post #6.

If you do have a *power.sh* file, then modify it and add the contents from the *switchmonitor* script.

```
cd /etc/acpi
cat battery
cat power.sh
gksudo gedit battery

```

Change the action=/etc/acpi/power.sh to action=/etc/acpi/switchmonitor.

Be sure to copy the *switchmonitor* script from ~/bin to /etc/acpi.

```
cd
cd bin
sudo cp switchmonitor /etc/acpi

```

You might need to reboot to get the new ACPI events to be registered.

Test it by unplugging the Laptop's AC from the wall.  The display should switch to the laptop screen and the external display should go dark.

---

### Post by raghav6 on 2014-10-07
thank you so much guys, I'm on it I'll post the result as soon as possible !!

---

### Post by raghav6 on 2014-10-07
@_[tgalati4]("http://ubuntuforums.org/member.php?u=241895")_ & [feyenoord]("http://ubuntuforums.org/member.php?u=1949072") I admit it i might need a little 'holding hand here' i searched in root folder i.e '/' and in /home i couldn't find any file named power or battery, i think I'm going about the wrong way here do a step by step explanation would be great help

---

### Post by raghav6 on 2014-10-09
if I I wasn't sure before when i said 'holding hand' ,I meant more beginner friendly version of what you guys told me, like go here,click there,paste this etc could  you guys please help me with that ? you see I'm still a toddler in Ubuntu so please  I could really use some help :)

---

### Post by raghav6 on 2014-10-11
well...........this what  Under stood from @[feyenoord]("http://ubuntuforums.org/member.php?u=1949072") posts it would great help if someone break it down like this 
1.first I ran this command 
```
$ mkdir -p ~/bin 
# which creates a folder named bin in home directory
```
2.```
$ cat > ~/bin/switchmonitor << 'EOF' 
# I don't Know what this does may be creates a bash file  named 'switch monitor' in bin? (what cat and EOF stands for?)
```
3```
.#!/bin/sh
exec xrandr --output LVDS1 --auto --output VGA1 --off
EOF
# this must be the code that need to placed in the file again no idea what EOF means may be at the begin suggest start of the script and this suggest end ?
```
4```
$ chmod +x ~/bin/switchmonitor 
# no clue maybe it's making it executeable ?(oh and there isn't excute tic mark in 'permissions' in lubuntu ) 
```

see if this is my level of know-how,now how am supposed to understand/operate/create or even fallow the instruction given by @tgalati4? I'm really interested in his method and i want to learn about it but, I've no idea where to begin with I need more in depth instructions please help me out

---

### Post by raghav6 on 2014-10-15
Bump

---

### Post by raghav6 on 2014-10-17
OK i was able to make monitor switch via a shortcut key now I want to automate the switch between display when ever laptop goes to battery mode like tgalati4 explained here  
> **tgalati4 said:**
> See if you have a *battery* script:



If you do not have a *power.sh* file in /etc/acpi, then you can susbstitue the script called *switchmonitor* described by feyenoord in Post #6.

If you do have a *power.sh* file, then modify it and add the contents from the *switchmonitor* script.

```
cd /etc/acpi
cat battery
cat power.sh
gksudo gedit battery

```

Change the action=/etc/acpi/power.sh to action=/etc/acpi/switchmonitor.

Be sure to copy the *switchmonitor* script from ~/bin to /etc/acpi.

```
cd
cd bin
sudo cp switchmonitor /etc/acpi

```

You might need to reboot to get the new ACPI events to be registered.

Test it by unplugging the Laptop's AC from the wall.  The display should switch to the laptop screen and the external display should go dark.

so after bit of research and with great help from [CantankRus]("http://ubuntuforums.org/member.php?u=1938181") I was able to scrape a little bit of info from one another thread that files weren't located in above mentioned directory but instead they are located in /usr/lib/pm-utils/power.d and any user script should be saved in /etc/pm/power.d.now I all want is a script and also I found this 
```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        # enter your commands here
    ;;
    false) ### laptop enters ac mode
        # enter your commands here
    ;;
    *) exit ;;
esac
```

so can I use this to my advantage ?

---

### Post by raghav6 on 2014-10-26
Bump bump!

---

