---
title: "show pop-up each minute when battery is 100% charged"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-12-01
Hi all, 

How do I show pop-up each minute when battery is 100% charged? Maybe even with some sound... 

It does show pop-up only once. I can miss it easily. I'd like to know when it is time to unplug charger in time. 

How do I perform it? 
Thanks ahead. 

Lubuntu 14.04.1 LTS


Upd: 

The battery percentage charge is likely to be found in /sys/class/power_supply/BAT0/capacity.
Popup messages can be created using 'xmessage'.
Sounds can be played using 'aplay'.
Regular checks can be scheduled using 'cron'.

Could someone please help to write a script that can be run as a cron job?

---

### Post by marchello_lippi2 on 2014-12-01
Tried to do it in python, can someone please comment where is my error ?
> 
Python 3.4.0 (default, Apr 11 2014, 13:05:18) 
[GCC 4.8.2] on linux
Type "copyright", "credits" or "license()" for more information.
>>> fh = open("/sys/class/power_supply/BAT0/capacity", "r")
>>> lines = [ i.rstrip() for i in fh.readlines()]
>>> print lines[2]
SyntaxError: invalid syntax
>>>


---

### Post by marchello_lippi2 on 2014-12-01
My bash version for this moment... 

> 
#!/bin/sh
valuea=`cat /sys/class/power_supply/BAT0/capacity`
echo "$valuea"
if [ $valuea -eq "98" ] || [ $valuea -eq "99" ] || [ $valuea -eq "100" ] || [ $valuea -eq "97" ]
then 
  echo "please unplug charger"
#  xmessage "please unplug charger"
  aplay /home/user1/test.wav
  xmessage "please unplug charger"
else 
  echo "still charging"
#  xmessage "still charging"
fi
exit
power_100.sh (END)


---

### Post by llamabr on 2014-12-01
[http://unix.stackexchange.com/questions/60778/how-can-i-get-an-alert-when-my-battery-is-about-to-die-in-linux-mint](http://unix.stackexchange.com/questions/60778/how-can-i-get-an-alert-when-my-battery-is-about-to-die-in-linux-mint)

---

### Post by buzzingrobot on 2014-12-02
Do you really need to run a once-per-minute cron job to pop up a notice every minute, or is the goal just to have something pop up when the battery is 100% charged *and stay on the screen* until you notice it?

---

### Post by marchello_lippi2 on 2014-12-02
This is my actual bash version. It is like resident program. It is started at lubuntu desktop boot and reside in memory. Well, I will test it during few days, but now it looks just fine. 

> 
#!/bin/sh

DELAY=60
while sleep $DELAY
do
    valuea=`cat /sys/class/power_supply/BAT0/capacity`
    echo "$valuea"
    if [ $valuea -eq "98" ] || [ $valuea -eq "99" ] || [ $valuea -eq "100" ] || [ $valuea -eq "97" ]
    then
    echo "please unplug charger"
    aplay /home/user1/test.wav
    if ! xmessage -nearmouse -buttons continue:0,stop:1 "please unplug charger"
    then
        exit 0
    fi
    else 
    echo "still charging"
    # xmessage "still charging"
    fi
done



---

