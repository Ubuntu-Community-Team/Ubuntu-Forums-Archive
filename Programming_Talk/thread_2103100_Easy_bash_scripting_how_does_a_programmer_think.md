---
title: "Easy bash scripting: how does a programmer think?"
date: 2013-01-09
forum: Programming Talk
---

### Post by LtPitt on 2013-01-09
Hi all!

I am fiddling with my small home server and preparing "muscles" with a little programming because I'm waiting for a Telldus DUO and I want to do a very little domotics.

I've started with a simple thing: everytime I get back home I want my home server to tell my girlfriend I'm parking and I want my pc to turn on.

I've prepared this script:


```

#!/bin/bash
while [ 1 ];
do
ping -c 1 `cat /proc/net/arp | grep "MYPHOMEMACADDRESS" | cut -d" " -f 1` >/dev/null; echo $? > imhome
imhome=`cat imhome` 
if test $imhome == 0
then
#     You need to install etherwake to turn on a PC on your lan and enable wake on lan in its BIOS
     /usr/sbin/etherwake < pcmacaddress ;
     mv /home/pcmacaddress /home/pcmacaddressstop ;
#     You need to install mpg123 to play mp3 from command line
     mpg123 /home/home.mp3 && mv /home/home.mp3 /home/home.mp2
else
#    Next row is for simple visual debug help
     echo "Not home yet" | figlet
fi
done

``` 

Main problem is that a similar script works...
Always! (unless you tweak it like I did)

So my pc turns on all the time I'm home and the mp3 file plays all the time.

I thought about using a text file (you can see the implementation in the script) to load the right MAC address and make it readable only at specific times of the day thanks to cron and rename it to a different file when I'm home from work or for lunch.
Same for the home.mp3 file that gets a rename in home.mp2 and therefore is not in play 24/7 :)

It works without problems this way but I think it's very ugly and not flexible...
I wanted to ask you for different ideas and point of views to improve my very small and limited "programmer's mind".

Thank you for your help and patience!

---

### Post by ofnuts on 2013-01-09
> **LtPitt said:**
> Hi all!

I am fiddling with my small home server and preparing "muscles" with a little programming because I'm waiting for a Telldus DUO and I want to do a very little domotics.

I've started with a simple thing: everytime I get back home I want my home server to tell my girlfriend I'm parking and I want my pc to turn on.

I've prepared this script:


```

#!/bin/bash
while [ 1 ];
do
ping -c 1 `cat /proc/net/arp | grep "MYPHONEMACADDRESS" | cut -d" " -f 1` >/dev/null; echo $? > imhome
imhome=`cat imhome` 
if test $imhome == 0
then
     /usr/sbin/etherwake MYPCMACADDRESS ;
     mpg123 home.mp3 && mv home.mp3 home.mp2
else
     echo "Not home" | figlet
fi

done

```It works without problems but of course it works...
Always!

So my pc turns on all the time I'm home.

I thought about using a text file to load the right MAC address and fill it with the right MAC only at specific times of the day and wipe it when I get home from work or for lunch.
I am already doing the same with the home.mp3 file that gets a rename in home.mp2 and therefore is not in play 24/7 :)

It will work this way but I wanted to you different ideas and point of views to improve my very small and limited "programmer's mind".

Thank you for your help and patience!
Clever stuff, that demonstrates how trackable we are :)

You problem is that you are triggering on a state (telephone in range) and not on a transition (from telphone not in range to telephone in range). So you should have something somewhere that tell you the previous state. Pseudocode:

```

if inrange
     if not in_range_before
          mark in_range
          wake_up_pc
else
     if  in_range_before
          mark out_of_range

```

However, this is still shaky if you are "not far" with your hone connecting and disconnecting. So you should really add something to only start the PC when you have been gone for a while:

```

if inrange
     if not in_range and left_range_more_than_one_hour_ago
          mark in_range
          wake_up_pc
else
     if  in_range_before
          mark out_of_range

```

where marking in_range/out_of_range is really just touching a file. In fact you only need an "out_of_range" file (if not found you assume you are in range), and its modification date will tell you when you went out of range, with "stat -c '%Y {file}' to have its last mod date in seconds since epoch, and  "date '+%s'" to gave the current time in the same format.

---

### Post by LtPitt on 2013-01-09
Omg this is enough to feed my brain for ages.

Thanks a lot! :)

I'll come back with news when I'll finish my homework.

---

### Post by LtPitt on 2013-01-10
Hello there!

I passed wonderful (and terrible) hours fighting my way to the result.

Here's the latest code:

```

#!/bin/bash
# CONFIGURATION #
# Insert in the rows below your smartphone and pc mac address search Google if you don't know how to get this information (where you have the example 00:00:00:00:00:00) 
smartphone_mac_address="38:aa:3c:e9:50:91"
pc_mac_address="00:24:1D:C0:F1:7C"

while [ 1 ];
do

# Comment the following two rows for testing using the next comment manual tweak. Uncomment for normal function
ping -w 1 `cat /proc/net/arp | grep $smartphone_mac_address | cut -d" " -f 1` &> /dev/null; echo $? > arrived ;
arrived=`cat arrived`

# Uncomment the following two rows and change the arrived variable below to 0 to simulate smartphone at home and 2 to simulate smartphone out of home. Comment for normal function
#arrived=0
#echo $arrived

            if [ $arrived == 0 ]; then
                /usr/sbin/etherwake $pc_mac_address
                if [ -f smartphone_out ]; then rm smartphone_out; fi
                if [ ! -f smartphone_in ]; then touch smartphone_in; fi
                if [ -f home.mp3 ]; then mpg123 home.mp3 &> /dev/null && mv home.mp3 home.mp2; fi

            elif [ $arrived == 1 ]; then
                if [ -f smartphone_in ]; then rm smartphone_in; fi
                if [ ! -f smartphone_out ]; then touch smartphone_out; fi
                if [ -f home.mp2 ]; then mv home.mp2 home.mp3; fi
            fi
done

```

I think I wrote horrible code and any kind of suggestion to learn better how to rethink it are incredibly welcome :)

I am suffering much for two issues...
This is ok:

```
if [ $arrived == 0 ]; then
                bla bla fi
```

But... If I want to verify two conditions at the same time?

I've read that you can use -a 

```
if [ $arrived == 2 ] -a [ test `find "smartphone_out" -mmin +10` ]; then
                bla bla fi
```

And there are various ideas about using () and or [] around the whole expression or single conditions and I've tried them all but failed...

The other thing that is really driving me mad is to execute script at startup.
I've read about doing it adding a simple row to /etc/rc.local
Unsecure but easy but...
It doesn't work :/

I add full path of the script and I can see the script running using top but it doesn't work.
The same script ran from command line works flawlessly.
I've tried adding 
bash /home/myuser/script

but no luck anyway.

I've also tried crontab -e with the @reboot option but...

Nothing.

Any suggestions?

Thanks!

---

### Post by ofnuts on 2013-01-10
```

if [[ $arrived -eq 2 ]] && find "smartphone_out" -mmin +10`
then
...
fi

```


[LIST]
[*][[]] delimit "conditional expressions"
[*]A command is the same as "true" if it returns 0 (succeeds)
[*]&& and || are the boolean operators (commands on the right aren't executed as soon at the global result is known)
[*]Use '-eq' (and -ne/-gt/-lt) to test numeric values.
[*]see [http://www.gnu.org/software/bash/manual/html_node/Conditional-Constructs.html](http://www.gnu.org/software/bash/manual/html_node/Conditional-Constructs.html)
[/LIST]
Beware the locations and access rights to the various files you use. These may not apply to the system daemon. What id runs it when it autoruns?


Your script should log the results of its tests and its actions (as well as their success status and possible error messages) to some file in var/log. Then you can check what happened (and what is currently happening, with a "tail -f")

---

### Post by LtPitt on 2013-01-10
Thank you again for your precious hints and help!

I'll study better what you wrote about conditional expressions...

About the autostart I'm really going mad but I'm investigating further.

I've read that if rc.local is not working you can debug it adding two rows at the beginning of it (right after the end of comments):

exec 2> /home/YOURUSERNAME/rc.local.debug
set -x

This way I've found that the script hangs at the beginning, I get in the log:

```
Usage: ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface]
            [-M pmtudisc-hint] [-m mark] [-S sndbuf]
            [-T tstamp-options] [-Q tos]
```

I'm going for a stab in the dark:
the arp table is not populated yet when the script starts and it hangs.
The strange thing is that the script is a loop so at a certain moment it should start working.
Strange :/

I'll investigate further.

Edit:

DAMN YOU, ABSOLUTE PATH!

The more you dive into being a mad scientist the more you find out you're a newbie :P

The autostart is now working!

I'm back to understand better conditional expressions :)

---

