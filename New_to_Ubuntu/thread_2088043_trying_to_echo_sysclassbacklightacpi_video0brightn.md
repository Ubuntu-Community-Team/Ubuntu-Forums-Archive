---
title: "trying to echo /sys/class/backlight/acpi_video0/brightness : Permission denied"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by mobody on 2012-11-25
Hi Community, 

i'm new to UBUNTU. I've recently installed ubuntu 12.10 and have several issues. One of them is that my brightness always sets itself to 100% at a new boot. I've a line in /etc/rc.local: 

```
echo 7 > /sys/class/backlight/acpi_video0/brightness  
```but it won't execute. Every boot the screen gets set to max.
If i run the command logged in as root ```
sudo su
``` it works.
but 
```
mo@x1-carbon:~$ sudo echo 6> /sys/class/backlight/acpi_video0/brightness
bash: /sys/class/backlight/acpi_video0/brightness: Permission denied

```gives me no permission. 

What am I missing?

Thanks for your help,
m

---

### Post by steeldriver on 2012-11-25
Your command gives elevated permissions to the echo command (which doesn't need them), but not to the part that redirects the output stream to the root-owned file (which does)

In a terminal, you can either do

```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```which gives the elevated permission to the bit that really needs it, or

```
sudo sh -c "echo 7 > /sys/class/backlight/acpi_video0/brightness"
```which runs the whole command in a sudo shell

HOWEVER you shouldn't use sudo at all in /etc/rc.local since it should be executed as root - something else must be going wrong there

---

### Post by mobody on 2012-11-25
> **steeldriver said:**
> In a terminal, you can either do

```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```which gives the elevated permission to the bit that really needs it, or

```
sudo sh -c "echo 7 > /sys/class/backlight/acpi_video0/brightness"
```which runs the whole command in a sudo shell


Thanks for your quick response, steeldriver. Both solutions did it for me, which brings me to the question,  why the line in rc.local doesn't get executed? I DO NOT run the line with a sudo command.
I also tried the two commands you gave me without the sudo in it in rc.local, with no luck.

I thought that it had something to do with permission. I've another line in rc.local which rfkills bluetooth, but you don't need to be root to do that... and this works fine.
Any ideas?

---

### Post by steeldriver on 2012-11-25
It should work - are you sure you put it ahead of the 'exit 0' line? 

The only other thing I can think of is that it's working, but something later in your startup process is overwriting it

---

### Post by mobody on 2012-11-25
> **steeldriver said:**
> 
The only other thing I can think of is that it's working, but something later in your startup process is overwriting it

Thanks. It was kind of this behavior. I've installed tlp for powermanagement and it has an own startup script. Putting the original "echo 7 > ..." line there solved the proplem. Strange thing is that commands without the need of sudo are still getting executed from rc.local.

---

### Post by linrunner on 2012-11-28
Hi,

> **mobody said:**
> I've installed tlp for powermanagement and it has an own startup script. Putting the original "echo 7 > ..." line there solved the proplem. 
You should not do it that way. Either the next TLP update will kill your local changes or you're excluding yoursef from further updates of the TLP startup script.

Instead create the script file  [B]/etc/pm/power.d/backlight

[/B]```
#!/bin/sh
# /etc/pm/power.d/backlight 
# set backlight brightness depending on power source
LEVEL_AC=15
LEVEL_BAT=7  
BRIGHT=/sys/class/backlight/acpi_video0/brightness
case "$1" in     
    true)  level=$LEVEL_BAT ;;      
    false) level=$LEVEL_AC ;;
    *) exit 0 # invalid argument
esac
[ "$(cat $BRIGHT)" != "$level" ] && echo -n $level > $BRIGHT
exit 0
```Make it executable:
```
sudo chmod 755 /etc/pm/power.d/backlight
```

---

