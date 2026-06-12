---
title: "adding a -$x argument to a shell script"
date: 2007-05-07
forum: Programming Talk
---

### Post by frup on 2007-05-07
I am just making a shell script, mainly to learn how to do it.

I've come on to one obstacle that I can't seem to find a solution for and that is when running it, how do I add an argument to the script eg

script -install or script -i would install the script,
script -configure or script -i would configure it,
and the else of this would just run it.

I'm guessing i go 
function() {
...
}
if [ something in here]
function
fi

cheers.

---

### Post by grzecisz on 2007-05-07
Hello. Take a look at my sample (actually taken from iptables firewall script) this might be helpfull for You.

```

#!/bin/sh

start()                                                                          
{                                                                               
/home/test/program
}                                                                               

stop()                                                                          
{                                                                               
kill procid
}                                                                               
                                                                                
restart()                                                                       
{                                                                               
stop                                                                            
start                                                                           
echo "Restarted"                                                                                                                                   
} 

case "$1" in                                                                    
'start')                                                                        
  start                                                                      
  ;;                                                                            
'stop')                                                                         
  stop                                                                          
  ;;                                                                            
'restart')                                                                      
  restart                                                                       
  ;;                                                                            
*)                                                                              
  echo "usage $0 start|stop|restart"                                            
esac

```

this will allow You to use 3 commands: start, stop and restart, and then call specific function.

---

### Post by bashologist on 2007-05-07
This might be useful. Idk.
[http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq#head-1e14a175482b437ee80b8937307c352c5318e3f4](http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq#head-1e14a175482b437ee80b8937307c352c5318e3f4)

---

### Post by frup on 2007-05-07
Thankyou,

That helped it get working :)

if anyone wants to tell me why this isn't activating cron i would be very happy and finished

*/5 * * * * ~/./test.sh

as ~/./test.sh in the command line it works :(
would exec ~/test.sh or something work better?

*/5 should allow it to operate every 5 mins no?

Cheers again.

---

### Post by Ramses de Norre on 2007-05-07
> **frup said:**
> Thankyou,

That helped it get working :)

if anyone wants to tell me why this isn't activating cron i would be very happy and finished

*/5 * * * * ~/./test.sh

as ~/./test.sh in the command line it works :(
would exec ~/test.sh or something work better?

*/5 should allow it to operate every 5 mins no?

Cheers again.

Have you tried using an absolute path? In which user's cron are you adding it?

---

### Post by frup on 2007-05-07
I thought with out adding the user it would just go to the logged in user?
I will try those.

It doesn't appear to work...

laurent@lars:~$ crontab -l
49 18 * * 6 /home/laurent/machine-update -m
*/1 * * * * laurent /home/laurent/./test.sh >> /dev/null 2>&1

It's is supposed to take a screenshot every 5 minutes... It's not spyware parental stuff I just saw it was a good project to learn shell scripting off and scrot was the first tool I could think off :)

```
#!/bin/bash
# Copyright frup 2007 Licensed under GPL v2
#version 1
install () {
	if [ -d /home/laurent/.scr ]; then
		echo "Making ~/.scr skipped, already exists..."		
	else 
		mkdir ~/.scr
	fi
#dir for screenshots (hidden)
	crontab -l > /home/laurent/test.txt
	echo '*/5 * * * * /home/laurent/./test.sh >> /dev/null 2>&1' >> ~/test.txt
	crontab /home/laurent/test.txt >> /dev/null 2>&1
	rm /home/laurent/test.txt
	echo "Removed temporary installation files..."
#add script to crontab
}
run () { 
	scrot '%Y-%m-%d-%H:%M:%S_$wx$h.png' -e 'mv $f /home/laurent/.scr'
#activate scrot picture saved as something like 2007-05-07-21:22:53_1024x768.png
}
usage () {
echo "";echo ""
echo "Shell script to add scrot command to cron"
echo "Copyright frup 2007 Licensed under GPL v2"
echo ""
echo "-i | --install : Install this script"
echo "-h | --help : This page"
echo "";echo ""
}
### Main. (figures out if install or run is active)
install=
while [ "$1" != "" ]; do
    case $1 in
        -i | --install )    install=1
                                ;;
        -h | --help )           usage
                                exit
                                ;;
    esac
    shift
done

if [ "$install" = "1" ]; then
	echo "Preparing to install..."
	install
else
	run
fi
```

---

### Post by hartz on 2007-05-07
Looking at the below entries I notice a few things:

```
49 18 * * 6 /home/laurent/machine-update -m
*/1 * * * * laurent /home/laurent/./test.sh >> /dev/null 2>&1
```

The first line executes are 18:49 once a week on Saturdays.

The second line executes the command "laurent" with some arguments.  I think you meant to execute test.sh from your home directory.

[LIST]
[*]the */1 means every minutes - you can just use a * for that, (or use */5 for "every 5 minutes".)
[*]/dev/null can be overwriten or appended, all input into it is discarded.
[*]/./ refers back to the same directory as the path before it, so it is redundant.
[/LIST]

So I would suggest the following:
```
* * * * * /home/laurent/test.sh > /dev/null 2>&1
```

I think the only thing preventing this from working is the word "laurent" on the second line, so you were very clsoe to getting it to work :-)

Post back with an update once you've done more testing.

---

### Post by frup on 2007-05-07
I added the laurent because Ramses de Norre suggested I define the user... I thought that was where it was supposed to go, but obviously I am wrong :)

I am not at home so can't test it but the /./ is probably what is making it fail... I did that because to run the script from terminal I write ./test.sh ...

Thanks, will update once I get back home and test it.

---

### Post by frup on 2007-05-08
i've done the changes and it still doesn't work :S

look at this

laurent@lars:~$ /home/laurent/test.sh
laurent@lars:~$ cd ..
laurent@lars:/home$ /home/laurent/test.sh
giblib error: Saving to file 2007-05-08-17:36:37_1280x1024.png failed
laurent@lars:/home$ crontab -l
49 18 * * 6 /home/laurent/machine-update -m
*/2 * * * * /home/laurent/test.sh

interestingly sudo /home/laurent/test.sh works from any directory... but how can I make the command run as root with out asking for a password?


```

#!/bin/bash
# Copyleft frup 2007 Licensed under GPL v2
#version 1
install () {
	if [ -d /home/laurent/.scr ]; then
		echo "Making /home/laurent/.scr skipped, already exists..."		
	else 
		mkdir /home/laurent/.scr
	fi
#dir for screenshots (hidden)
	crontab -l > /home/laurent/test.txt
	echo '*/5 * * * * /home/laurent/test.sh >> /dev/null 2>&1' >> /home/laurent/test.txt
	crontab /home/laurent/test.txt >> /dev/null 2>&1
	rm /home/laurent/test.txt
	echo "Removed temporary installation files..."
#add script to crontab
}
run () { 
	scrot '%Y-%m-%d-%H:%M:%S_$wx$h.png' -e 'mv $f /home/laurent/.scr'
#activate scrot picture saved as something like 2007-05-07-21:22:53_1024x768.png
}
usage () {
	echo "";echo ""
	echo "Shell script to add scrot command to cron"
	echo "Copyleft frup 2007 Licensed under GPL v2"
	echo ""
	echo "-i | --install : Install this script"
	echo "-h | --help : This page"
	echo "";echo ""
}
### Main. (figures out if install or run is active)
install=
while [ "$1" != "" ]; do
    case $1 in
        -i | --install )    install=1
                                ;;
        -h | --help )           usage
                                exit
                                ;;
    esac
    shift
done

if [ "$install" = "1" ]; then
	echo "Preparing to install..."
	install
else
	run
fi

```

---

### Post by hartz on 2007-05-08
I have not looked at the script itself but it is clearly trying to write to a location which is relative to the path where you are when you execute the script, probably the "current working directory".  Root has got access to write and create files anywhere, which is why it works anywhere with sudo.

When cron executes the script, it may not be in the same directory where you think it is.  To solve this:

Option nr1:

Modify the script to include a "cd" command to ensure that it is executing in the right directory, early on in the script.

option nr 2:

Modify the script to send its output to a pre-defined location in stead of a location relative to where you are execiting it from.

Option nr 3:
Write a wrapper script which will do the following:
cd to a known location, eg your home directory,
then execute the test.sh script

option nr 4:
Put the command in root's crontab

option nr 5:
Modify the script to take an option which specifies where the output must be created.

You can optionally make sudo run the script without prompting for a password, but this is a very very very bad way of fixing this problem.

Some considerations:
Who do you want to be the "owner" of the output file?
Do you want the job to be generic and work for multiple users?

If you want I can take a look at the script.  I'm just suffering from a lazy-attack right now.

---

### Post by frup on 2007-05-09
Thank you! I realised the problem from that, it was me not understanding scrot. it saves the ss in the current working directory, so I did need to CD to home first so the user can access it... 

EXCEPT... while this allows the test.sh to be accessed from any dir... by running /home/user/test.sh it does not work on crontab yet... so does cron use a different user or something?

Is there a log I can view from cron?

This is in the Auth log

May  9 21:57:01 localhost CRON[9952]: (pam_unix) session opened for user laurent by (uid=0)
May  9 21:57:01 localhost CRON[9952]: (pam_unix) session closed for user laurent

this is from the syslog
May  9 21:58:01 localhost /USR/SBIN/CRON[9981]: (laurent) CMD (/home/laurent/test.sh)

I have it set to run every minute at the moment but it still isn't taking the screen shot
:S


Current version
```

#!/bin/bash
# Copyleft frup 2007 Licensed under GPL v2
#version 1
install () {
	if [ -d /home/laurent/.scr ]; then
		echo "Making /home/laurent/.scr skipped, already exists..."		
	else 
		mkdir /home/laurent/.scr
	fi
#dir for screenshots (hidden)
	crontab -l > /home/laurent/test.txt
	echo '*/5 * * * * /home/laurent/test.sh >> /dev/null 2>&1' >> /home/laurent/test.txt
	crontab /home/laurent/test.txt >> /dev/null 2>&1
	rm /home/laurent/test.txt
	echo "Removed temporary installation files..."
#add script to crontab
}
run () { 
	cd /home/laurent/
	scrot '%Y-%m-%d-%H:%M:%S_$wx$h.png' -e 'mv $f /home/laurent/.scr'
#activate scrot picture saved as something like 2007-05-07-21:22:53_1024x768.png
}
usage () {
	echo "";echo ""
	echo "Shell script to add scrot command to cron"
	echo "Copyleft frup 2007 Licensed under GPL v2"
	echo ""
	echo "-i | --install : Install this script"
	echo "-h | --help : This page"
	echo "";echo ""
}
### Main. (figures out if install or run is active)
install=
while [ "$1" != "" ]; do
    case $1 in
        -i | --install )    install=1
                                ;;
        -h | --help )           usage
                                exit
                                ;;
    esac
    shift
done

if [ "$install" = "1" ]; then
	echo "Preparing to install..."
	install
else
	run
fi

```

---

