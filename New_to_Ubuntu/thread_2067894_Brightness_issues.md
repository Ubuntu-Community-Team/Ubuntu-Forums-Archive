---
title: "Brightness issues"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by will1982 on 2012-10-07
Whenever I wake up my laptop from sleep or start it up, brightness is set to max.
 Is there any way I can set it lower by default?

---

### Post by pqwoerituytrueiwoq on 2012-10-07
if we can find a command that will affect the backlight yes
```
xbacklight -set 50
```
does that work on your system?

---

### Post by will1982 on 2012-10-08
It does not work...

---

### Post by NikTh on 2012-10-08
Give the results of this command 

```
ls /sys/class/backlight/*/
``` 

Thanks

---

### Post by will1982 on 2012-10-08
Here you go: 
```
/sys/class/backlight/acpi_video0/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/apple_backlight/:
actual_brightness  brightness      power      type
bl_power           max_brightness  subsystem  uevent

/sys/class/backlight/intel_backlight/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

```

---

### Post by pqwoerituytrueiwoq on 2012-10-08
you may need to edit the BOLD parts of this post for this to work for you based on the output of [FONT=Courier New]ls /sys/class/backlight/[/FONT]
I just made a script
this is meant as a replacement for xbacklight
```
sudo apt-get remove xbacklight
gksu gedit /usr/local/bin/xbacklight
sudo chmod +x /usr/local/bin/xbacklight
sudo chmod 777 /sys/class/backlight/**acpi_video0**/brightness
```script:
```
#!/bin/bash
where="/sys/class/backlight/**acpi_video0**"
max=`cat $where/max_brightness`
current=`cat $where/actual_brightness`
if [ "$1" == "--set" ];then
    if [ ! "`echo $2 | sed 's/[a-Z]//g'`" == "$2" ];then
        `dirname $0`/`basename $0`
        exit
    elif [ 0`echo "$2" | sed 's/.//' | grep "^[0-9]*$"` -gt 0 ] && [ ! "`echo \"$2\" | grep \"^[0-9]*$\"`" == "$2" ];then
        if [ "`echo ${2:0:1}`" == "+" ];then
            X=$(($current+`echo ${2:1}`))
        elif [ "`echo ${2:0:1}`" == "-" ];then
            X=$(($current-`echo ${2:1}`))
        else
            echo "${2:0:1} is not a +/-"
            exit
        fi
        if [ $X -gt $max ];then
            echo $max > $where/brightness
        elif [ $X -lt 0 ];then
            echo 0 > $where/brightness
        else
            echo $X > $where/brightness
        fi
        exit
    fi
    if [ ! "`echo \"$2\" | grep \"^[0-9]*$\"`" == "$2" ];then
        echo "$2 is not a Intiger"
    elif [ "$2" -lt $(($max+1)) ] && [ "$2" -gt -1 ];then
        echo $2 > $where/brightness
    elif [ "$2" -lt 0 ];then
        echo 0 > $where/brightness
    else
        echo $max > $where/brightness
    fi
elif [ "$1" == "--get" ];then
    if [ "$2" == "current" ];then
        echo $current
    elif [ "$2" == "max" ];then
        echo $max
    else
        echo -e "Current: $current\nMaximum: $max"
    fi
else
    echo -e "Usage:\n\t`basename $0` --set Int | +Int | -Int"
    echo -e "\t`basename $0` --get current | max | NULL"
fi
exit
```This makes the script not need sudo every time you reboot:
```
sudo sed '/^[^#]*exit 0/i chmod 777 /sys/class/backlight/**acpi_video0**/brightness \&' -i /etc/rc.local
```

---

### Post by NikTh on 2012-10-08
Hi ,
is this script really needed ? 
I mean 
I would ask for the results of 

```
sudo cat /sys/class/backlight/acpi_video0/brightness
sudo cat /sys/class/backlight/apple_backlight/brightness
sudo cat /sys/class/backlight/intel_backlight/brightness
``` 

Then we can see what value affects the brightness 
with ```
echo **"VALUE"** | sudo tee /sys/class/backlight/**acpi_video0**/brightness
```
bolds may change.. 

and after we found what is the correct command , we could just add the command to  /etc/rc.local . 

By the way , I don't know coding - scripting , I admire "scripters" and I wish will work. :) 

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-10-08
the script i made would pre-process the command you gave
as long as VALUE is a valid value your command is the same as my script (except mine cat tell you your brightness and max brightness)
with the script i made you could put xbacklight --set VALUE in the /etc/rc.local script
could also make custom keyboard shortcuts for it to increase/decrease brightness

there was one person who was not able to set the brightness in /etc/rc.local but it worked from a lightdm startupscript
but that was using xbacklight whch may act like numlockx and require lightdm to be running to work

---

### Post by NikTh on 2012-10-08
> **pqwoerituytrueiwoq said:**
> 
could also make custom keyboard shortcuts for it to increase/decrease brightness

OK! 

This is the advantage of your script . ;)

Cuz all other things seems to me the same.. But shortcuts , OK, this is an advantage. 
:)

---

### Post by pqwoerituytrueiwoq on 2012-10-08
These are good for calling it from a script (i assume the min is 0 for everyone)
[FONT=Courier New]xbacklight --get max
xbacklight --get current[/FONT]
This is good for humans
[FONT=Courier New]xbacklight --get[/FONT]
This is to increase the brightness
[FONT=Courier New]xbacklight --set +2[/FONT]
This is to decrease the brightness
[FONT=Courier New]xbacklight --set -2[/FONT]
This is to set the brightness
[FONT=Courier New]xbacklight --set 5[/FONT]
This is for the help output
[FONT=Courier New]xbacklight
xbacklight --help
xbacklight -h
xbacklight "I dont know what I am doing"[/FONT]

---

### Post by NikTh on 2012-10-08
If you allowed me a question. 

Here you add the command **before exit 0 **with sed's magic . 
> **pqwoerituytrueiwoq said:**
> 
```
**sudo sed '/^[^#]*exit 0/i** chmod 777 /sys/class/backlight/acpi_video0/brightness \&' -i /etc/rc.local
```

If I want to remove the specific command how can I do it ? 

Which is better , sed of find ? 

_Please DO not give me the solution_.. just a clue if you want.. 

Apologize for the OffTopic [will1982]("http://ubuntuforums.org/member.php?u=1740328")  

Thanks 

:)

---

### Post by pqwoerituytrueiwoq on 2012-10-08
personally i would use nano but you can use any editor you like
but if you insist on sed
```
sudo sed 's/chmod 777 \/sys\/class\/backlight\/acpi_video0\/brightness\/ \&//' -i /etc/rc.local
```it will leave a empty line behind, but i suck at sed (i just moded a line a person gave me [here]("http://ubuntuforums.org/showthread.php?t=2054259"))

i edited my script several times since i posted it if you are using it you may want to know that

---

### Post by NikTh on 2012-10-08
Thanks [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")

Yes I wanted  a straight command from the terminal , no editors (I use nano too) .

> **pqwoerituytrueiwoq said:**
> 
```
sudo sed 's/chmod 777  \/sys\/class\/backlight\/acpi_video0\/brightness\/ \&/' -i  /etc/rc.local
```it will leave a empty line behind, but i suck at sed  (i just moded a line a person gave me [here]("http://ubuntuforums.org/showthread.php?t=2054259"))
 
This returns ```
sed: -e expression #1, char 66: unterminated `s' command
``` 

But I found the correct command 

```
sudo sed 's/chmod 777 \/sys\/class\/backlight\/acpi_video0\/brightness//g' -i /etc/rc.local
``` 
:)

---

### Post by pqwoerituytrueiwoq on 2012-10-08
i fixed it in my above post, yours will leave a stray & symbol (that i forgot to remove when i made the line to add this line)

---

### Post by NikTh on 2012-10-08
> **pqwoerituytrueiwoq said:**
> i fixed it in my above post, yours will leave a stray & symbol (that i forgot to remove when i made the line to add this line)

Hah.. yes.. 

Look , your command was just an example.. specifically I have this command in my rc.local 

```
(sleep 2;echo 600 > /sys/class/backlight/intel_backlight/brightness)&
```And I managed to remove it with this 

```
 sudo sed 's/(sleep 2;echo 600 > \/sys\/class\/backlight\/intel_backlight\/brightness)&//g' -i /etc/rc.local
```sed is magic 

Thanks for your assistance :) 

[B]No more Offtopic - hijaking [will1982]("http://ubuntuforums.org/member.php?u=1740328")
[URL="http://ubuntuforums.org/member.php?u=1740328"] :popcorn:
[/URL][/B]

---

### Post by will1982 on 2012-10-08
Whew, info overoload. Have to go to bed, will try this when I can

---

