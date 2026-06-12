---
title: "&quot;Modular&quot; Conky"
date: 2007-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by jr.gotti on 2007-10-05
Just screwing around, I thought it'd be nice to have shell script "modules" to call from the conkyrc instead of the rather awkward conky config language.

With that said, I made two since last night.

This one will retrieve your HDD temperature and battery life. I called this one "System Info," although theres a lot more you could add to a sysinfo module. Heres the shell script:

```

#!/bin/sh
#
# Script by Jason Gotti (email removed for spambots)
# Written and tested on Ubuntu 7.04.
#
# Developed for use with conky, but also can be used 
# for other information related purposes. 
#
# Variables. Change "BAT1" to reflect your battery. (Check in /proc/acpi/battery)
# You also need to install hddtemp, and change the path to the HDD to match yours.
remaining=$(cat /proc/acpi/battery/BAT1/state | grep remaining | awk '{ print $3 }')
life=$(calc $remaining/4044 | awk -F. '{ print $2 }' | head -c 2)
temp=$(sudo hddtemp /dev/sda | awk -F: {' print $3 '} | awk {' print $1 '}
)

echo CPU Temperature: $temp
echo Battery Life: $life%

```And it is called in conkyrc like this:

```

${color #ffcb48}System Info:
${color #FFFFFF}${execi 5 sysinfo}

```And it outputs like this:

```

System Info:
CPU Temperature: 34 (Degree Symbol) C
Battery Level: 80%

```The second one is network info: Heres the script:

```

#!/bin/sh
#
# Script by Jason Gotti (email removed for spambots)
# Written and tested on Ubuntu 7.04.
#
# Developed for use with conky, but also can be used 
# for other information related purposes.

# Variables. Don't change these.
network=$(iwconfig ath0 | grep ESSID | awk -F'"' '{ print $2 }')
one=$(iwconfig ath0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $1 '})
two=$(iwconfig ath0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $2 '} | awk {' print $1 '})
quality=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2)
qualitychars=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2 | wc | awk {' print $3-$1 '})
netaddr=$(ifconfig ath0 | grep "inet addr" | awk -F: {' print $2 '} | awk {' print $1 '})

# Output
echo "Connected to:" $network
# This loop was added to fix a bug that displayed
# percentages ending in "0" (40, 50, 60) as one digit.
# Ex. 50% was displayed as 5%. This loop checks the word count
# of the quality variable and acts accordingly.
if [ $qualitychars = 2 ]
then
echo "Link Quality:" $quality%
else
echo "Link Quality:" $quality"0%"
fi
# End of Link Quality loop.
echo "Address:" $netaddr

```And it is called in conkyrc like so:

```

${color #ffcb48}Network Info
${color #FFFFFF}${execi 5 networkinfo}

```And it outputs like this:

```

Network Info:
Connected to: BCC_Students
Link Level: 74%
Address: xxx.xxx.xxx.xxx (Outputs the actual address, of course.)

```This one should work on all installs with no special additions. Also if your on a wired network you would change the script accordingly. *On second thought, I'll just write up a wired network info script.*

Using conky this way significantly reduces the clutter in your config file. Instead of illegible jarble, my rc looks like this (after the "text to be formatted part)

```

TEXT
${color #ffcb48}System Info:
${color #FFFFFF}${execi 5 sysinfo}

${color #ffcb48}Network Info
${color #FFFFFF}${execi 5 networkinfo}

```This might seem pointless to some, but it makes it easier for me, as all I have to do to change a certain part is edit that script, and it auto updates in conky.

Just thought I'd share...if you want to add more, feel free!

-Jason

---

### Post by jr.gotti on 2007-10-05
Edited the original post to include comments, and fix a bug in the network info script. (it displayed percents ending in zero as a single digit [50%=5%, 60%=6%]. Whoops.)

Also, heres another one. This ones for Disk space info.

Heres the script:

```

#!/bin/sh
#
# Script by Jason Gotti ([email removed for spambots)
# Written and tested on Ubuntu 7.04.
#
# Developed for use with conky, but also can be used 
# for other information related purposes. 
#
# If you don't have a seperate /home partiton, then just comment out
# all the variable lines having to do with a home partition, and all
# the echo lines having to do with /home. 
#
# To add partitions to this script, simply follow the same format. 
# To determine what to place after the grep command in the script,
# run "df -h" on a terminal, and use whatever is listed under "mounted on"
# for the desired partition.

# Home variables. (Comment out if you don't have a home partition.)
homesize=$(df -h | grep /home | awk {' print $2 '})
homeused=$(df -h | grep /home | awk {' print $3 '})
homefree=$(df -h | grep /home | awk {' print $4 '})
homeuseperc=$(df -h | grep /home | awk {' print $5 '} | awk -F% {' print $1 '})
homeperc=$(calc 100-$homeuseperc | awk {' print $1 '})

# Root variables.
rootsize=$(df -h | grep -w / | awk {' print $2 '})
rootused=$(df -h | grep -w / | awk {' print $3 '})
rootfree=$(df -h | grep -w / | awk {' print $4 '})
rootuseperc=$(df -h | grep -w / | awk {' print $5 '} | awk -F% {' print $1 '})
rootperc=$(calc 100-$rootuseperc | awk {' print $1 '})

# Root output.
echo "/ (root)"
echo "  Size:" $rootsize
echo "  Used:" $rootused
echo "  Free:" "$rootfree ($rootperc%)"

# Home output. (Comment out if you don't have a home partition.)
echo /home
echo "  Size:" $homesize
echo "  Used:" $homeused
echo "  Free:" "$homefree ($homeperc%)"

```
And it is called in conkyrc like so:

```

${color #ffcb48}Disk Usage Info:
${color #FFFFFF}${execi 5 diskfreeinfo}

```
And it outputs like:

```

Disk Usage Info:
/ (root)
   Size: 28G
   Used: 4.4G
   Free: 22G (83%)
/home
   Size: 30G
   Used: 4.8G
   Free: 24G (83%)

```

---

### Post by matthew on 2007-10-05
Jason, that's pretty cool. I like Conky for this specific reason. Thanks for the ideas and examples.

---

### Post by Crinos512 on 2007-10-05
So these are seperate files in your /home dir that are "executed" inside the .conkyrc?

/home
 - .conkyrc
 - sysinfo
 - networkinfo
 - diskfreeinfo

( btw, a good source for config files for conky is here " [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky) " )

---

### Post by jr.gotti on 2007-10-05
> **Crinos512 said:**
> So these are seperate files in your /home dir that are "executed" inside the .conkyrc?

/home
 - .conkyrc
 - sysinfo
 - networkinfo
 - diskfreeinfo

( btw, a good source for config files for conky is here " [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky) " )

Kinda. They're separate scripts, which are either in your home bin directory or, more than likely, your systemwide bin directory. (/bin.)

Just save one of the scripts in a new text file, then in the terminal make it executable.

```

sudo chmod +x *scriptname*

```

then cp it to the bin file.

```

sudo cp *scriptname* /bin

```

now all you have to do is call it from the terminal and it'll work.

And yeah...I've seen the configs in that thread...it's different this way...it's using conky through shell scripts. IMO more configurable.

---

### Post by Crinos512 on 2007-10-05
Hmmm... I like it! 

1. Can you pass arguments to the scripts from your .conkyrc? ie.
```

${color #ffcb48}System Info:
${color #FFFFFF}${execi 5 sysinfo **option1**}
```

2. can you move your ${color} Statements into the scripts? ie.
```
#!/bin/sh
#
# Script by Jason Gotti (email removed for spambots)
# Written and tested on Ubuntu 7.04.
#
# Developed for use with conky, but also can be used 
# for other information related purposes. 
#
# Variables. Change "BAT1" to reflect your battery. (Check in /proc/acpi/battery)
# You also need to install hddtemp, and change the path to the HDD to match yours.
remaining=$(cat /proc/acpi/battery/BAT1/state | grep remaining | awk '{ print $3 }')
life=$(calc $remaining/4044 | awk -F. '{ print $2 }' | head -c 2)
temp=$(sudo hddtemp /dev/sda | awk -F: {' print $3 '} | awk {' print $1 '})

**${color #ffcb48}**System Info:
**${color #FFFFFF}**echo CPU Temperature: $temp
**${color #FFFFFF}**echo Battery Life: $life%
```
And it is called in conkyrc like this:
```

#System Info Module
${execi 5 sysinfo}
```

and IF both are true you could move the color statements into your modules and pass them as arguments! :D

---

### Post by jr.gotti on 2007-10-05
I'm not sure what you mean...do you mean set the color on the command line when you run conky? If so...im sure it's possible.

---

### Post by Crinos512 on 2007-10-05
kind of... this would be your .conkyrc
```

#System Info:
${execi 5 sysinfo **"#ffcb48" "#FFFFFF"** }

#Network Info
${execi 5 networkinfo  **"#ffcb48" "#FFFFFF" **}

#Disk Usage Info:
${execi 5 diskfreeinfo  **"#ffcb48" "#FFFFFF" **}
```

sysinfo```
#!/bin/sh
# ...
remaining=$(cat /proc/acpi/battery/BAT1/state | grep remaining | awk '{ print $3 }')
life=$(calc $remaining/4044 | awk -F. '{ print $2 }' | head -c 2)
temp=$(sudo hddtemp /dev/sda | awk -F: {' print $3 '} | awk {' print $1 '})

**${color %1}**echo "System Info:"
**${color %2}**echo "CPU Temperature: "$temp
**${color %2}**echo "Battery Life: "$life%
```

networkinfo```
#!/bin/sh
# ...
network=$(iwconfig ath0 | grep ESSID | awk -F'"' '{ print $2 }')
one=$(iwconfig ath0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $1 '})
two=$(iwconfig ath0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $2 '} | awk {' print $1 '})
quality=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2)
qualitychars=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2 | wc | awk {' print $3-$1 '})
netaddr=$(ifconfig ath0 | grep "inet addr" | awk -F: {' print $2 '} | awk {' print $1 '})

# Output
**${color %1}**echo "Network Info:"
**${color %2}**echo "Connected to:" $network
# This loop was added to fix a bug that displayed
# percentages ending in "0" (40, 50, 60) as one digit.
# Ex. 50% was displayed as 5%. This loop checks the word count
# of the quality variable and acts accordingly.
if [ $qualitychars = 2 ]
then
**${color %2}**echo "Link Quality: " $quality%
else
**${color %2}**echo "Link Quality: " $quality"0%"
fi
# End of Link Quality loop.
**${color %2}**echo "Address: " $netaddr
```

... and so on

---

### Post by jr.gotti on 2007-10-05
yeah thats possible, but why set the color in two places instead of one?

---

### Post by jr.gotti on 2007-10-05
Oh, and can someone post the output of both:

```

cat /proc/acpi/battery/BAT[insertwhatevernumber]/state

```

and

```

cat /proc/acpi/battery/BAT[insertwhatevernumber]/info

```

?

Only if you have a laptop, of course. I ask because I set the calculations for the battery life to the capacity of my battery (thats the 4044 you see in the script) and I just thought that thats probably not going to be universal. lol

---

### Post by Crinos512 on 2007-10-05
> **jr.gotti said:**
> yeah thats possible, but why set the color in two places instead of one?

you mean like this?
```

#Variables
color1 = "#ffcb48"
color2 = "#FFFFFF" 

#System Info:
${execi 5 sysinfo color1 color2 }

#Network Info
${execi 5 networkinfo color1 color2}

#Disk Usage Info:
${execi 5 diskfreeinfo color1 color2}
```

(... can't help on the battery  info , sorry.)

---

### Post by matthew on 2007-10-05
```
cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      4400 mAh
present voltage:         14800 mV
```

```
cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      4400 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 440 mAh
design capacity low:     176 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3960 mAh
model number:            BAT0
serial number:           236
battery type:            Lion
OEM info:                SMP
```

---

### Post by jr.gotti on 2007-10-05
> **matthew said:**
> ```
cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      4400 mAh
present voltage:         14800 mV
``````
cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      4400 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 440 mAh
design capacity low:     176 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3960 mAh
model number:            BAT0
serial number:           236
battery type:            Lion
OEM info:                SMP
```

Thanks matt...looks like I'll have to change it a lil.

---

### Post by jr.gotti on 2007-10-05
> **Crinos512 said:**
> you mean like this?
```

#Variables
color1 = "#ffcb48"
color2 = "#FFFFFF" 

#System Info:
${execi 5 sysinfo color1 color2 }

#Network Info
${execi 5 networkinfo color1 color2}

#Disk Usage Info:
${execi 5 diskfreeinfo color1 color2}
```(... can't help on the battery  info , sorry.)

Yeah..but even here your still manually setting the color...just in a different place.

---

### Post by jr.gotti on 2008-02-06
Not to revive this old thread, but I figure this is a good place to keep all these for the time being, so heres a new one.

This script will use Nmap to determine all hosts which are currently connected to the network you are on. Before this script can be used you must have nmap, apcalc, and dog installed. (Yes...dog. It's kinda like cat v2.0)

```

#!/bin/sh
#
# Script by Jason Gotti (email removed for spambots)
# Written and tested on Ubuntu 7.04.
#
# Developed for use with conky, but also can be used 
# for other information related purposes. 
#
# Variables. Change "ath0" to reflect your network interface. (Check in "ifconfig")
# You also need to install nmap, apcalc, and dog for this script to function correctly..
addressrange=$(ifconfig ath0 | grep "inet addr" | awk -F: {' print $2 '} | awk {' print $1 '} | awk -F. '{ print $1,".",$2,".",$3,".",0,"/24" }' | tr -d " ")
numberofhosts=$(nmap -sP $addressrange | grep Host | wc -l)
currenthost=1
host=$(nmap -sP $addressrange | grep Host | dog -l $currenthost | awk '{ print $2 }')

while [ $currenthost -le $numberofhosts ]
do
echo $host
currenthost=$(calc $currenthost+1)
host=$(nmap -sP $addressrange | grep Host | dog -l $currenthost | awk '{ print $2 }')
done

```It's callled in conkyrc like so:

```

${color #ffcb48}Disk Usage Info:
${color #FFFFFF}${execi 5 diskfreeinfo}

```And finally, it outputs like this on my current network. Of course, it's going to change to display the hosts on your network.

```

Hosts Online:
192.168.2.1
192.168.2.20
192.168.2.104

```Enjoy!

---

