---
title: "zenity script to check internet connectivity"
date: 2006-10-16
forum: Programming Talk
---

### Post by suoko on 2006-10-16
Hi,

I'm writing a simple script to check whether the pc is connected to internet or not.
I wrote the below reported script and I must say it works pretty well. 
The only annoyance is that in case I'm not connected to internet or that I loose connection, the ping timeout is veery slow

I'm looking for a timeout option for ping in case of network unreachable because the -W and -w options do not work.
I read about a -m option which could be the answer, however that option is not available in the ping provided from edgy...


#!/bin/sh

HOST=www.freenet.de

# first initiate the values
if ping  [www.google.com](www.google.com) -w 0.1 -W 0.1 -c 1 >/dev/null 

	then
		NET=true
		NETOLD=true
		echo "Connection available." | festival --tts
		zenity --info --text="connection available."
	else
	if ping  [www.freenet.de](www.freenet.de) -w 0.1 -W 0.1 -c 1 >/dev/null 
		then
			NET=true
			NETOLD=true
			echo "Connection available." | festival --tts
			zenity --info --text="connection available."
		else	
			NET=false
			NETOLD=false
      	echo "Connection NOT available." | festival --tts			
			zenity --info --text="connection NOT available."
		fi
fi

# endless loop
while true
	do
		#if ping -i0.1 -s0 -t2 -o $HOST &> /dev/null
		if ping  [www.google.com](www.google.com) -w 0.1 -W 0.1 -c 1 >/dev/null 
			then
				NET=true;
				LOST_NET_COUNT=0;
			else
				if [ $LOST_NET_COUNT == 1 ]
					then
						NET=false;
					else
						let "LOST_NET_COUNT += 1";
				fi
		fi

	if [ $NET != $NETOLD ]
		then
			if [ $NET = true ]
				then
					echo "Connection available again." | festival --tts
					zenity --info --text="connection available again."
				else
			      echo "Connection lost." | festival --tts
					zenity --info --text="connection lost."
			fi
	fi
	NETOLD=$NET
	sleep 2
done

---

