---
title: "Timed Cached Memory Cleaner (TCMC)"
date: 2011-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by test666 on 2011-08-07
Warning : this was tested in Ubuntu 10.10 (gnome)

I saw this neat trick initially here
[http://ubuntuforums.org/showthread.php?t=589975]("http://ubuntuforums.org/showthread.php?t=589975")

And searching through Google:
[http://tinyurl.com/3k8sbwf]("http://tinyurl.com/3k8sbwf")

Timeline

I never gave it much appreciation until 2 of my 4 ram modules went bad.
Now, mostly after using browsers and closing them, I had trouble starting Evolution.
Logout and then login solved this issue.

This was not good, but it was better than a reboot.

Going through my saved tips, I found the solution, a saved page from 
[http://ubuntuforums.org/showthread.php?t=589975](http://ubuntuforums.org/showthread.php?t=589975)

So, in the terminal, typing
	sudo sync
	and the password
	and then 
	sudo echo 3 > /proc/sys/vm/drop_caches
	and the password
solved the login/logout issue.

OK, this was neat, this was a real improvement.

I cut a few steps:
	sudo su
	and the password
	sync
	echo 3 > /proc/sys/vm/drop_cachesTCMCD

I managed to downsize a little more
	sudo su
	and the password
	sync; echo 3 > /proc/sys/vm/drop_caches

And still downsizing the typing:
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
and the password

So this was a great improvement.

Everytime I needed, I just had to open a terminal shell and do the typing (mostly recovering last command using the up arrow and entering the sudo password).

Improving a little more, I put it in the Gnome panel, so it was just a click and a password away, everytime I "needed" to recover some cached memory.

But I am a lazy person.
What if I could have it running the "cleaning" in a timed, automatic way?

Searched through Google, but apparently nobody had bothered with it, probably everyone has better (read more) ram than me.

So I started to tinker here and there. And then...
I did it! I was happy with it, so I had the nerve and posted it online (in my poor excuse for a blog, just a test to see if I could keep it alive and routinely upated, well, I wasn't).
[http://linuxzinho.wordpress.com](http://linuxzinho.wordpress.com) (sorry, in portuguese)

It was a very crude script, but it worked.  And by putting it in the Gnome panel, it was only a click and a password away, working all the time. NEAT!!!

But I am a lazy person. Granted, I could automate it, but the password thingy was inescapable.

SOOOO... I had to go the service way. I think I made it (crudely, again...).

I am putting this here for anyone that is ram deprived to test and, eventually, use and improve.

I called this script "timed_cached_memory_cleaner.sh" (TCMC).

The script has the following capabilities:

0 - To run
	sudo [path or ./]timed_cached_memory_cleaner.sh [startup or remove]
0.1 - runmode 1 - no defining parameters : runs in the terminal
0.2 - runmode 2 - parameter STARTUP (lowercase) : installs the service "timed_cached_memory_cleaner_daemon.sh" and warns that it will be running upon next reboot
0.3 - runmode 3 - parameter REMOVE (lowercase) : kills the installed service and removes the script from startup services
1 - TCMC running without sudo - explanatory error message
2 - TCMC running  with wrong parameters or more than one - explanatory error message
3 - needs zenity for error messaging

So, this is my script.
1 - Copy/paste onto gedit
2 - save it as "timed_cached_memory_cleaner.sh"
3 - make it executable through nautilus (right mouse click on the filename > properties > permissions > allow executing file as program (tick it) and close properties)
		or in a terminal window
		chmod +x [path to saved folder/]timed_cached_memory_cleaner.sh
4 - Run it

Copy/paste beyond this line or download from a prettier text version [http://dl.dropbox.com/u/5761057/timed_cached_memory_cleaner.sh]("http://dl.dropbox.com/u/5761057/timed_cached_memory_cleaner.sh")

[B]#!/bin/bash
# Timed Cached Memory Cleaner
# 2011-August-08, by test666

#BSD license, modified

#Copyright (c) 2011, test666
# All rights reserved.

#Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
#Redistributions of source code must retain the above copyright notice, this list of conditions, the "General Notes", "The Disclaimer and personal notes", the "Political note" and the following disclaimer.
#Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
#Neither the name of the <ORGANIZATION> nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

#THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# General notes
# 1 - run as sudo (sudo timed_cached_memory_cleaner.sh)
# 2 - without parameters TCMC will run normally and is killed by keypressing
# 3 - optional parameter STARTUP (in lowercase) will install a startup service efective on next reboot
# 4 - Optional parameter REMOVE (in lowercase) will kill TCMCD (if running) and remove startup service
# 5 - zenity needed for reporting start error (another TCMCD running or a zombie lock file lost in transit)
# 6 - remove TCMCD zombie lock files by running
#			sudo rm /tmp/time_cached_memory_cleaner_daemon*.lock
# 7 - service start|stop|restart|status - whenever I find the time for doing it; DIY if you have some spare time to do it
# 7.1 - if you improve/modify/found_a_bug in this script, please share on the thread

# Disclaimer and personal notes
# 1 - there are rough edges, I'm forever a learning newbie...
# 2 - use TCMC/TCMCD at your own risk, because it may kill your machine
# 3 - Limited assistance, I just don't have the time
# 4 - don't contact me except in the Ubuntu Forum thread and even so I may never answer (see #3)
# 5 - #3 & #4 : sorry, not playing role as a snob, I am honestly deprived of time
# 6 - good luck

# Political note
# 1 - unity sucks, OMG Ubuntu/Canonical, where are you heading and will I follow you?
# 2 - #1 NOT flame bait, just venting, cool it, keep it to yourself, no issue here, move along

error ()
{
echo
echo -e $1
echo
echo 'sudo [path or .]/timed_cached_memory_claner.sh [startup/remove]'
echo
echo -e 'Optional parameter \033[1;32mstartup\033[m will install TCMCD as a service'
echo
echo -e 'Optional parameter \033[1;32mremove\033[m will kill TCMCD and remove the service, effective immediately'
echo
exit
}

startup ()
{
echo
echo 'Installing Timed Cached Memory Cleaner as a startup service'
echo
echo '#!/bin/sh' > /etc/init.d/timed_cached_memory_cleaner_daemon.sh
# wait 5 minutes until system stabilizes to be on the safe side
#echo 'sleep 300' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo 'if [ -f /tmp/timed_cached_memory_cleaner_daemon.lock ]' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '	then' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '   	zenity --info --title="timed_cached_memory_cleaner_daemon" --text="Apparently, I am already running (/tmp/timed_cached_memory_cleaner_daemon.lock)"' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '		exit' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '	else' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '		echo > /tmp/timed_cached_memory_cleaner_daemon.lock'  >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo 'fi'  >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo 'while [ true ] ; do' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
# The routine is set for a waiting time of 15 minutes (15x60=900 seconds) between each cleaning, change it the way you want
echo '	echo > /tmp/timed_cached_memory_cleaner_daemon_working.lock' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '	sync' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '	echo 3 > /proc/sys/vm/drop_caches"' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo '	rm /tmp/timed_cached_memory_cleaner_daemon_working.lock' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
# The routine is set for a waiting time of 15 minutes (15x60=900 seconds) between each cleaning, change it the way you want
echo '	sleep 900' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
echo 'done' >> /etc/init.d/timed_cached_memory_cleaner_daemon.sh
# set as executable
chmod +x /etc/init.d/timed_cached_memory_cleaner_daemon.sh
# Update startup services list
update-rc.d timed_cached_memory_cleaner_daemon.sh defaults
echo
echo 'Timed Cached Memory Cleaner Service is installed, effective on next reboot'
echo
exit
}

remove ()
{
# Use caution, do not interfere with a running TCMCD
while [ -f /tmp/timed_cached_memory_cleaner_daemon_working.lock ] 
	do
		sleep 2
	done
# Let's kill TCMCD
tryout=3
while ps ax | grep -v grep | grep timed_cached_memory_cleaner_daemon.sh > /dev/null
	do
		if [ $tryout -eq 0 ]
			then 
#Force killall if "gracefull" killall failed for 3 times
				killall -9 timed_cached_memory_cleaner_daemon.sh
			else
#Try to kill
				killall timed_cached_memory_cleaner_daemon.sh
				if ps ax | grep -v grep | grep timed_cached_memory_cleaner_daemon.sh > /dev/null
					then
#Pause for 2 seconds if killall failed
						sleep 2
						let tryout=tryout-1
				fi
		fi
	done
# Again, be cautious
sync
#OK let's remove TCMCD
if [ -f /etc/init.d/timed_cached_memory_cleaner_daemon.sh ]
	then 
		rm /etc/init.d/timed_cached_memory_cleaner_daemon.sh
fi
if [ -f /tmp/timed_cached_memory_cleaner_daemon.lock ]
	then
		rm /tmp/timed_cached_memory_cleaner_daemon.lock
fi
if [ -f /tmp/timed_cached_memory_cleaner_daemon_working.lock ]
	then
		rm /tmp/timed_cached_memory_cleaner_daemon_working.lock
fi
update-rc.d -f timed_cached_memory_cleaner_daemon.sh remove
exit
}

tests ()
{
# test if we are running with sudo
if [ `id -u` -ne 0 ]
	then
		error "Error: No sudo"
fi
#test the number of parameters; 0 or 1 is OK
if [ $# -gt 1 ]
	then 
		error "Error: Allowed only optional parameter"
fi
#Test if there is one parameter: search for STARTUP (install as service) or REMOVE (kill and remove as service), all other words will be reported as  errors
if [ $# -eq 1 ]
	then
		case "$1" in
		        startup)
		            startup
					;;
		         remove)
		            remove
					;;
					*)
		            error
		esac
fi
}

run_in_a_terminal_window ()
{
while [ true ] 
	do 
		clear
		echo "Cleaning Cached Memory !!! DO NOT CLOSE THIS WINDOW !!!"
		sync
		echo 3 > /proc/sys/vm/drop_caches
		clear
		echo "Timed Cached Memory Cleaner"
		echo "Counting down the seconds"
		echo "Press keyboard to exit"
		SECONDS_TO_GO=900
		while [  $SECONDS_TO_GO -gt 0 ]; do
			printf "\r$SECONDS_TO_GO "
			let SECONDS_TO_GO=SECONDS_TO_GO-1
			read -t 1 -n 1 
			if [ $? = 0 ]	
				then
					exit
			fi
		done
	done
}

################################
# Main script body starts here #
################################

tests $1

# so, no failure, all is well, lets run normally (in a terminal window ?)
run_in_a_terminal_window[/B]

---

