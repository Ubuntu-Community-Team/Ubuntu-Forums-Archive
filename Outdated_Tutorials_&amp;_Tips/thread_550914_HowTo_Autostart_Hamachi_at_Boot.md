---
title: "HowTo: Autostart Hamachi at Boot"
date: 2007-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by wyth on 2007-09-14
I've seen a few requests for this info, and I've looked for it myself.  Many people use the hamachi vpn client.  In windows, you can set it to start on boot.  That was once a little trickier in linux, but no longer.  [This page]("http://www.neohide.com/automatic-start-up-hamachi-for-ubuntu-feisty-fawn") at the [NeoHide]("http://www.neohide.com") site worked for me on Feisty Fawn (and I posted about it on a thread [here]("http://ubuntuforums.org/showpost.php?p=3364675&postcount=4")).  I'm not sure if the directions originated at NeoHide or someplace else, because I've found them in a few place.

But anyway, here are the directions:[LIST=1]
[*]Create the start-up script for hamachi, as shown below. Remember to change the user name "your name" *(line 5)* to your system user name in Ubuntu (or your linux distribution).  Call the script "hamachi."[INDENT] #!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=your name
case "$1" in
start)
    /sbin/tuncfg
    /bin/su - $USER -c "hamachi start"
    ;;
stop)
    /bin/su - $USER -c "hamachi stop"
    ;;
restart|force-reload)
    /bin/su - $USER -c "hamachi start"
    /bin/su - $USER -c "hamachi stop"
    ;;
*)
    exit 1
    ;;
esac
 exit 0 
[/INDENT]
[*]Make the script executable:[INDENT]chmod +x hamachi
[/INDENT]
[*]Move the script to /etc/init.d/ directory:[INDENT]sudo mv hamachi /etc/init.d
[/INDENT]
[*]Finally, link the script to the appropriate run-level for booting up the system:[INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/S99hamachi
[/INDENT][INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/K99hamachi
[/INDENT]It seems **2** is the default level for Debian and Ubuntu. In most other distribution, it is **5**.
[*]Finally, reboot your system and Hamachi will be automatically loaded and connected to the server.[/LIST]

---

### Post by felker2 on 2007-09-17
Step 5 says "reboot your system". I'm sure that works, what maybe this is more elegant:


```
sudo /etc/init.d/hamachi start
```

HTH

---

### Post by wyth on 2007-09-17
That is more elegant.

---

### Post by rautamiekka on 2009-01-28
Nice tut', but does it work for all defaultly ? If not, please find a way to make it so.

---

### Post by wyth on 2009-01-28
> **rautamiekka said:**
> Nice tut', but does it work for all defaultly ? If not, please find a way to make it so.

Yeah, we'll get right on that boss.  By the way, can I have next Thursday off?

---

### Post by rautamiekka on 2009-01-28
> **wyth said:**
> Yeah, we'll get right on that boss.  By the way, can I have next Thursday off?
Thanks for the respect, but you still ask wrong person ;)

---

### Post by skarootz on 2009-02-19
Ok, I don't know if it should be here... However if you want to do this in centos 5 you can use rc3.d runlevel folder.

It worked for me.

Bye

---

### Post by binbash on 2009-02-21
Works like a charm, thanks

---

### Post by Quazza on 2009-03-11
Hi,
Linux newbie alert :D

I have Hamachi installed on Mythbuntu 8.10 Intrepid and its working fine but I cannot get it to start with the script it will only start with 

```
sudo hamachi -c /etc/hamachi start
```

When I try to run the script 

```
sudo /etc/init.d/hamachi start
```

I get the following error

```
/etc/init.d/hamachi: 1: !/bin/bash: not found
tuncfg: already running
Cannot find configuration directory /home/jase/.hamachi. Have you run 'hamachi-init' ?
```

Any help would be greatly appreciated as I am so close to getting this working.

Cheers Quazza

---

### Post by rautamiekka on 2009-03-11
Welcome newcomer :)

Please copypaste the contents of **/etc/init.d/hamachi**. That error sounds really fishy.

---

### Post by wyth on 2009-03-11
I wrote my stuff a long time back, and I know some things have changed.  I rarely set up Hamachi to autostart anymore, but I have for some other people's machines, and I used [this page from The CompuTech Group]("http://www.computechgroup.com/?p=360") as a guide.  

Be sure to scan through it all before doing anything; it jumps around a bit (user level, system level), and depending on what you want it to do, you'll need to either follow one path or another, and you won't necessarily know that path unless you read through it first.

From what I can recall, I've not had much luck autostarting Hamachi at the user level, but setting it up to autostart at the system level has worked okay.

---

### Post by Quazza on 2009-03-11
> **rautamiekka said:**
> Welcome newcomer :)

Please copypaste the contents of **/etc/init.d/hamachi**. That error sounds really fishy.

Thanks for the Welcome  

Contents of **/etc/init.d/hamachi**

```
!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=jase
case "$1" in
start)
/sbin/tuncfg
/bin/su - $USER -c "hamachi start"
;;
stop)
/bin/su - $USER -c "hamachi stop"
;;
restart|force-reload)
/bin/su - $USER -c "hamachi start"
/bin/su - $USER -c "hamachi stop"
;;
*)
exit 1
;;
esac
exit 0

```

Cheers Quazza

---

### Post by rautamiekka on 2009-03-11
Just as I predicted, the first line says **!/bin/bash** where it should say **#!/bin/bash**. Change, save and run the script, should be one less error :) One could be that you copypaste the original to the file, to be on safer side.

---

### Post by Quazza on 2009-03-12
Ok made the change to the script as you suggested and yes that has fixed one error. So now when I run the script I am getting the below errors.

```
jase@mythtv-shed:~$ sudo /etc/init.d/hamachi start
[sudo] password for jase: 
tuncfg: already running
Cannot find configuration directory /home/jase/.hamachi. Have you run 'hamachi-init' ?

```

The error of tuncfg: already running is not I a problem as I have put tuncfg to be run as a daemon as per instructions but the second error is strange as I have setup hamachi using 
```
sudo hamachi-init -c /etc/hamachi
```

anyway hope you or someone else can help further and thanks so far.

Cheers Quazza :D

---

### Post by Quazza on 2009-03-12
Hi again,  I have had success with this now as I went to the page that wyth posted in his reply and copied the script on that page to my hamachi script and now it is all good.

Thanks guys very much appreciated

Cheers

Quazza :D

---

### Post by Quazza on 2009-03-18
Hi again,

As per my previous post I have got the script to work upon boot in Ubuntu 8.10 now I am wondering how I would do this for Arch?  

Arch doesn't have an /etc/init.d to copy the hamachi script to and also no rc2.d or to run the script as a certain run level, so if anyone could assist it would be greatly appreciated.

So to clarify I have installed linux using package manager as hamachi is now an AUR in arch and I have got to the point of creating the script but I am not sure if to create it in the rc.d directory and then if I do that how do I set the links to get it to run at boot?

Cheers

Quazza

---

### Post by holytotemic on 2009-05-27
is there any way to have it autolog into your networks at boot too? like convert this into a script i can put into my startup:

hamachi login
hamachi go-online "network name" password
hamachi go-online "network name" password
hamachi-gui


i have to manually do this every time i reboot and its a pain. not a linux genius but not a total noob either....more of a fedora fan but ubuntu has impressed me lately. after fedoras last repository hack i lost faith. anyways, off subject, thanks in advance

---

### Post by wyth on 2009-05-28
> **holytotemic said:**
> is there any way to have it autolog into your networks at boot too?

I haven't used Hamachi in some time (haven't needed to), but there is a great app in sourceforge that may do what you need, [hamachi-gui]("http://hamachi-gui.sourceforge.net/").

It looks almost exactly like the native Hamachi interface, and has a few nifty extra features -- like opening a vnc from the context menu, and being able to choose what vnc you'd like to use.  Once you have hamachi set up and running, hamachi-gui sits on top of that as a graphical interface (obviously).  It also automatically logs in to your preferred networks when it starts.

If you could start that at boot -- and it may be just a matter of adding it to System - Preferences - Start Applications -- it may do exactly what you need (and more).

I love this app; it was invaluable when I had a two-year job managing a writing center team of 30 employees, each using a computer, across three different locations on our campus.  Unfortunately, the developer has put development on permanent hold right now.  I believe it was because the direction the original Hamachi was going in was just too unlcear, and he didn't want to develop something that would eventually break.  However, the current build has no problems, and as far as I know, still works fine with Hamachi.  

You could also look into OpenVPN.  It's been a while since I scoped that (a few years), and it was a bit of a complicated maze before, but the installation and its management may be a lot more streamlined now.

---

### Post by Defrector on 2009-07-31
I modified your script a bit to automatically log in. Replace YOUR_NETWORK with the name of the network into which you wish to log and replace USER_NAME with your username. I also switched the stop and start commands in the reload case.

For this code to work, you must have already joined a network some time in the past (not necessary for every reboot; it remembers).


```
#!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=USER_NAME
case "$1" in
start)
/sbin/tuncfg
/bin/su - $USER -c "hamachi start"
/bin/su - $USER -c "hamachi login"
/bin/su - $USER -c "hamachi go-online YOUR_NETWORK"
;;
stop)
/bin/su - $USER -c "hamachi stop"
;;
restart|force-reload)
/bin/su - $USER -c "hamachi stop"
/bin/su - $USER -c "hamachi start"
;;
*)
exit 1
;;
esac
exit 0

```

---

### Post by flysen on 2009-08-24
For me this is an option, I'm a big fan of logfiles and checks:P
```
#!/bin/bash
##########################################
#	Scriptname:hamachi.sh		##
#	Start-up script for Hamachi     ##
#	Date: 2009-02-14                ##
##########################################
BIN="/usr/bin"
HPROFILE="/etc/hamachi"
LOGDIR="/home/fredrik/scritps/logs"
LOGFILE="$LOGDIR/Hamachi_`date '+%d'`.log"
NAME=$(basename $0 .sh)
WAI=`id -u`
Tpid="0"
Huserpid="NONE"
Hpid="0"

exec >> $LOGFILE 
exec 2>&1
	

CheckState () {
	##Hpid=`ps -ef | awk '/hamachi.sh start/ && !/awk/ {print $2}'`
	Hpid=`pidof hamachi`
	  if [ "$Hpid" = "" ]; then
		Hpid="0"
	  fi
	##Tpid=`ps -ef | awk '/tuncfg/ && !/awk/ {print $2}'`	
	Tpid=`pidof tuncfg`
	  if [ "$Tpid" = "" ]; then
		Tpid="0"
	  fi	
}

Hstart () {
	CheckState
	echo "== Starting HAMACHI ==`date`=="
	  if [ "$Tpid" -le "1" ]; then
		/sbin/tuncfg
		CheckState
		echo "tuncfg now running op pid $Tpid"
	  else
		echo "tuncfg already running on pid $Tpid"
	  fi
	
	CheckState
	  if [ "$Hpid" -le "1" ]; then
		$BIN/hamachi -c $HPROFILE start
	  fi
	sleep 1
	CheckState
	echo "hamachi is running on PID $Hpid"
}

Hstop () {
	echo "== Stoping HAMACHI ==`date`=="
	$BIN/hamachi -c $HPROFILE stop
}

Hrestart () {
	echo "== Reloading HAMACHI ==`date`=="
	Hstart
	Hstop
	Hstart
}

HcatchAll () {
	echo "== NoMatch catchALL HAMACHI ==`date`=="
	echo "Not accepted variable"
	exit 1
}


	  if [ "$WAI" -ne "0" ]; then
		echo "== You are not root! ==`date`=="
		exit 1
	  else
		case "$1" in
		start)
			Hstart
		;;
		stop)
			Hstop
		;;
		restart|force-reload)
			Hrestart
		;;
		*)
			HcatchAll
		;;
		esac
	  fi


exit 0
```

---

### Post by amlife on 2010-12-22
Well, to make things better I think this will work

edit /etc/rc.local file and add the following command

```
hamachi join network id password
exit 0

```
This command will get executed after all services are loaded after system reboot.

---

### Post by rautamiekka on 2010-12-22
> **amlife said:**
> Well, to make things better I think this will work

edit /etc/rc.local file and add the following command

```
hamachi join network id password
exit 0

```
This command will get executed after all services are loaded after system reboot.Today Hamachi(2) starts on boot. However this could be useful for the rare exceptions it doesn't.

---

### Post by abiheiri on 2011-03-21
Shame on you! You should be using update-rc.d for creating startup scripts.

---

