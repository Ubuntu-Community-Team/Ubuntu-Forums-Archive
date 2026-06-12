---
title: "BASH: math with variables"
date: 2011-10-01
forum: Programming Talk
---

### Post by layr on 2011-10-01
I have this line:
```
		if [[ $current_hours = $(($metar_hours+1)) ]];then
```
current_hours is 10 and metar_hours 09.
When i run the script it says:
```
/home/laur/.scripts/script2.sh: line 66: 09: value too great for base (error token is "09")

```
Is there something wrong with the adding part ($metar_hours+1)?

---

### Post by Arndt on 2011-10-01
> **layr said:**
> I have this line:
```
		if [[ $current_hours = $(($metar_hours+1)) ]];then
```
current_hours is 10 and metar_hours 09.
When i run the script it says:
```
/home/laur/.scripts/script2.sh: line 66: 09: value too great for base (error token is "09")

```
Is there something wrong with the adding part ($metar_hours+1)?

09 is probably taken as octal, since it starts with a 0. 9 is not a valid digit in octal.

(But you should have started a new thread with your question.)

---

### Post by sisco311 on 2011-10-01
> **Arndt said:**
> 09 is probably taken as octal, since it starts with a 0. 9 is not a valid digit in octal.


Yep.

@OP
See:
```
man bash | less +/"^ +Constants"
```

> **Arndt said:**
> 
(But you should have started a new thread with your question.)

Done, posts moved to new thread.


@OP:

You can force metar_hours to be treated as base 10:
```
if (( current_hours == $((10#$metar_hours+1)) ));then
```

```
[sisco@acme ~]$ foo=001230321
[sisco@acme ~]$ ((foo=10#$foo))
[sisco@acme ~]$ echo "$foo"
1230321
```

EDIT:

I finally found the relevant pages at Greg's Wiki. :)

Here you go:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)
[http://mywiki.wooledge.org/BashFAQ/067](http://mywiki.wooledge.org/BashFAQ/067)

---

### Post by layr on 2011-10-01
So much to learn:P
Anyway, if anyone is interested in what am i trying to accomplish, then this is it:

```
#!/bin/bash
# Script for downloading METARS into file (here 'EETU.txt') and comparing it's release time to current time - whether the METAR is new or old.
# If METAR is current, 'new_EETU.dat' is created, which is used by conky. 
# This gives ability to make the formatting of METAR in conky dependant of the status without making exessive data requests to METAR provider.
#
# Written by Laur Aliste with the help of ubuntuforums.org community.
# Special thanks to ubuntuforums.org user sisco311
#========================================================================================
# Startup sleep:
sleep 10

# Set startup values:
s=1
already_old=0
delete_loop=1

# The script itself:
while :
do
   global_sleep=60
   current_mins=$(date -u "+%M")
   if [ $current_mins = 50 ];then		# Sets variable 's' value to 1, so the second loop gets started when time gets HH:50 (new METAR is released at :50)
   	s=1
   fi
   if [ $s = 1 ];then				# This is needed if script is started at :49:somethingseconds, otherwise loop might miss a whole METAR release cycle.
	global_sleep=0
   fi

   while [ $s = 1 ]			# Start the second loop, if 's' value is 1
   do
	if [ -f ~/.conky/METAR/EETU.txt ]; then 
	    delete_loop=0
	fi
	until ping -c 1 www.google.com > /dev/null 2>&1		# Script waits until there is an active Internet connection.
	do
	    current_hours=$(date -u "+%H")
	    if [ $current_hours = 00 ];then
	       current_hours=24					# Needed for system and METAR release hours comparison (otherwise 00 wouldn't be later than 23)
	    fi
	    if [ $delete_loop = 0 ]; then
	    	metar_hours_pre=$(cat ~/.conky/METAR/EETU.txt)
	    	metar_hours=$(echo $metar_hours_pre|cut -c12-13)
	    	if [[ $(echo {50..59}) =~ $current_mins ]] && (( $metar_hours == $((10#$current_hours-1)) )) || ! [ $current_hours = $metar_hours ] && ! (( $metar_hours == $((10#$current_hours-1)) ));then
				   rm ~/.conky/METAR/EETU.txt   # Delete old METAR
				   delete_loop=1		# Set delete_loop variable to '1' so script doesn't have to compare METAR release time against system time within ping loop after the file has been already deleted.
	    	fi
	    fi
	sleep 10;
	done
	current_mins=$(date -u "+%M")		# Defines system clock minutes (UTC)
	current_hours=$(date -u "+%H")		# Defines system clock hours (UTC)
	if [ $current_hours = 00 ];then
	   current_hours=24
	fi
	curl -s 'http://weather.noaa.gov/pub/data/observations/metar/stations/EETU.TXT' > ~/.conky/METAR/EETU.txt		# download METAR and save to file
	metar_hours_pre=$(cat ~/.conky/METAR/EETU.txt)		# This line is used for getting the METAR onto one line.
	metar_hours=$(echo $metar_hours_pre|cut -c12-13)	# Define METAR release time HH (UTC)
	sleep 1					# Give time for saving the data
	if ! [[ $(echo {50..59}) =~ $current_mins ]] && (( $metar_hours == $((10#$current_hours-1)) )) || [ $current_hours = $metar_hours ]; then
			echo "New METAR"
			> ~/.conky/METAR/new_EETU.dat
			s=0
			already_old=0
	else
			if [ $already_old = 0 ]; then
			echo "Old METAR"
			    if [ -f ~/.conky/METAR/new_EETU.dat ]; then
			    rm ~/.conky/METAR/new_EETU.dat
	       	   	    fi
			already_old=1		# Same thing as with delete_loop variable.
			fi
	fi
   sleep 29
   done
sleep $global_sleep
done
```

---

