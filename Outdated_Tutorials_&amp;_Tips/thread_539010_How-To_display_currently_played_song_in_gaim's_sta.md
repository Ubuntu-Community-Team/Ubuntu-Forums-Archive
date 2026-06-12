---
title: "How-To: display currently played song in gaim's status."
date: 2007-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by applegrew on 2007-08-30
This article can be found on my blog too at [http://applegrew.blogspot.com/2007/08/how-to-display-currently-played-song-by.html](http://applegrew.blogspot.com/2007/08/how-to-display-currently-played-song-by.html) .
A tip. If you need to install new fortune data then I have a how to on it here at [http://applegrew.blogspot.com/2007/08/installing-new-fortune-data-for-fortune.html](http://applegrew.blogspot.com/2007/08/installing-new-fortune-data-for-fortune.html) .
--------------------------------------------------------
[SIZE="5"]Updated to version 1.2.4. See change log below.[/SIZE]

Like me many others might have tried to display currently played song in *Gaim*'s status. The *AmarokPidgin* no longer works with *Gaim* and the *Autoprofile* plugin for *Gaim* is broken for Feisty. So, below I introduce a **_hack_** that actually works!

_Features_:-
[LIST]
[*]Can change status of Gaim to currently played song in Amarok. The status of Gaim changes to the form...
```
&#9835; The Song Artist- Song Title
```

[*]Can change status of Gaim to currently played song or video in Kaffeine. The status of Gaim changes to the form...
same as above if music file is being played. For video files the status become...
```
&#9863;&#9834; Video Title
```

[*]When Amarok and Kaffeine are not playing or are closed then it can display random messages from **fortune**.
[/LIST]

_Tested on system with_:-
[LIST]
[*]Kubuntu 7.04 Feisty Fawn
[*]Gaim 2.0.0beta6
[*]Amarok 1.4.7 (optional)
[*]Kaffeine 0.8.5 (optional)
[*]fortune-mod version 9708 (optional)
[*]KDE 3.5.7
[*]Intel Pentium (32-bit)
[/LIST]

Depends upon **gaim-remote** (probably gets installed with **Gaim**, can anyone confirm this?).

The following code is based on code from [http://gentoo-wiki.com/TIP_Gaim_Autoprofile_plugin](http://gentoo-wiki.com/TIP_Gaim_Autoprofile_plugin) .

[LIST=1]
[*]Copy the following shell script code and save it as **gaim-status**, anywhere you feel like. I am assuming you copied it to **/usr/bin** so that it is accessible just by typing **gaim-status**.
You can also download this code from the attachment section (below). Note the attached file is named **gaim-status.sh**, but this guide assumes its name is **gaim-status**.
```
#!/bin/bash
#Filename: gaim-status
#Version: 1.2.4
#License: GPL version 2
#Code by AppleGrew
#Based on code from http://gentoo-wiki.com/TIP_Gaim_Autoprofile_plugin.

sleep_time=90 #Adjust the timer to suit your likings.
#Setting it to too lower value will consume CPU cycles
#and the script may also exit if Gaim fails to load in the above time.

if [[ $1 == "startgaim" ]] || [[ $2 == "startgaim" ]]
then
	#Checking if gaim is allive or not.
	if `pgrep -x gaim >/dev/null`
	then
		echo "Gaim already running, continuing to load gaim-status..."
	else
		gaim &
	fi
fi

#Checking if the script is already running or not. If yes then exitting.
gaimstatus_proc_count=`pgrep -c gaim-status`
if [ $gaimstatus_proc_count -ge 2 ]
then
	echo "Only one instance of the script can run at a time."
	exit 1
fi

skip=0
while [[ 1 == 1 ]]
do	
	player_title=""
	isVideo=0
	player_artist=""
	player_song=""
	#Checking if Amarok is allive and kicking or not.
	if `dcop | grep amarok >/dev/null` && [[ `dcop amarok player isPlaying` == "true" ]]
	then
		player_artist=`dcop amarok player artist`
		player_song=`dcop amarok player title`
	fi
	
	#Checking if Kaffeine is allive and kicking or not.
	if `dcop | grep kaffeine >/dev/null` && [[ `dcop kaffeine KaffeineIface isPlaying` == "true" ]]
	then
		if [[ `dcop kaffeine KaffeineIface isVideo` == "true" ]]
		then
			player_title=`dcop kaffeine KaffeineIface title`
			isVideo=1
		else
			player_artist=`dcop kaffeine KaffeineIface artist`
			player_song=`dcop kaffeine KaffeineIface title`
		fi
	fi
	
	if [[ $isVideo == 0 ]]
	then
		if [[ $player_artist == "" ]] && [[ $player_song == "" ]]
		then
			player_title=""
		else
			player_title="$player_artist- $player_song"
		fi
	fi
	if [[ "$player_title" != "" ]]
	then
		if [[ $isVideo == 1 ]]
		then
			msg="&#9863;&#9834; $player_title"
		else
			msg="&#9835; $player_title"
		fi
	fi
	
	if [[ "$player_title" == "" ]]
	then
		if [[ $1 != "nofortune" ]]  && [[ $2 != "nofortune" ]]
		then
			if [[ $skip == 1 ]]
			then
				skip=2
			else
				# Displaying random messages.
				msg=`fortune -ue|cat`
				msg=`echo -en "Auto Message (Ignore if offensive): \n$msg"`
				skip=1
				#Comment out the line above if you donot want fortune
				#messages to change at twice the period of song messages.
			fi
		else
			msg=""
		fi
	else
		skip=0
	fi
	if [[ $skip != 2 ]]
	then
		gaim-remote "setstatus?status=available&message=$msg"
	else
		skip=0
	fi
	sleep "${sleep_time}s"

	#Checking if gaim is allive or not.
	if ! `pgrep -x gaim >/dev/null`
	then
		exit 0
	fi
done

```
[*]Don't forget to set the permission of the script to allow execution. If the script is stored in **/usr/bin** then write
```
sudo chmod +x,u+x,o+x /usr/bin/gaim-status
```
Enter your account's password when asked.
[*]Make the Gaim entry in the menu to trigger
```
gaim-status startgaim
```
instead of
```
gaim
```
Note you will need to give path to **gaim-status** if you haven't stored **gaim-status** in **/usr/bin**.
That's it! Note if you donot want random quotes be set in status while *Amarok* is not playing then pass another argument **nofortune**. So it becomes
```
gaim-status startgaim nofortune
```
[/LIST]

_Current unresolved issues_:-[LIST=1]
[*]gaim-status doesn't close when gaim is closed. [COLOR="SeaGreen"](Resolved in version 1.1.0)[/COLOR]
[*]Gaim's status shows that I am playing a song or video when in fact it is paused.
This isn't an issue of the script. Actually **Kaffeine**'s **isPlaying** method returns **true** even when it is paused, and there isn't any other method to know the true state of Kaffeine. If you have any way then please suggest.
[*]gaim-status polls at specified time and updates the status then. It would be lot better if the script is notified when status of **Amarok** and **Kaffeine** changes.
[*]The script will always set status to Available. Is there a way to query the status? So that Away or Idle don't get reset to Available.
[*]Problem with non-UTF-8 encoded fortune cookies. Fortune messages which are not in UTF-8 will make **gaim-remote** generate error messages like the one below in the console.
```
No handlers could be found for logger "dbus.proxies"
Traceback (most recent call last):
  File "/usr/bin/gaim-remote", line 208, in <module>
    output = execute(arg)
  File "/usr/bin/gaim-remote", line 123, in execute
    gaim.GaimSavedstatusSetMessage(saved, message)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 155, in __call__
    message.append(signature=introspect_sig, *args)
UnicodeError: String parameters to be sent over D-Bus must be valid UTF-8

```
Also the output may contain incomplete messages. e.g. All message from** bofh-excuses** will generate the above error and the out will contain only the message *BOFH* only.
[/LIST]

Hope this helps. Please give suggestions, because the above is just a dirty hack. [COLOR="Red"]And since this is a dirty hack so I may not be able to support you. _Use at your own risk!_[/COLOR]

------------
_Change Log_:-
**Version 1.2.4**
Last version failed to start the 1st time it was started after a computer boots - complaining about multiple instances of **gaim-status** running, even though **pgrep -c gaim-status[/B returned 0]! Anyway storing the output of the aforementioned pgrep command in a variable then comparing that as [B]if [ $theVariable -ge 2 ]** seems to resolve the problem. Any idea why writing the pgrep command directly instead of the variable does not work the 1st time after a computer boot? Note after the 1st try after boot, all later execution of the script worked without hitch.

**Version 1.2.3**
[LIST=1]
[*]Last version had serious bug which prevented gaim-status from starting at all.
[/LIST]

**Version 1.2.2**
[LIST=1]
[*]Added* -u* switch to *fortune* command, to force it not to convert UTF-8 characters to locale one. I once spotted an error by *gaim-remote*, complaining about non-UTF-8 character.
[*]Added *-e* switch to *fortune* command, to display messages from all fortune data files with equal probability.
[*]Added restriction that only one instance of* gaim-status* can run.** Note** for this to work the script must be exactly named *gaim-status*.
[*]Added code so that* gaim-status* doesn't try to launch another instance of Gaim when it is supplied with *startgaim* switch.
[/LIST]

**Version 1.2.0**
[LIST=1]
[*]Major change. Code re-write.
[*]Added support for Kaffeine too.
[/LIST]

**Version 1.1.0**
[LIST=1]
[*]Now gaim-status automatically closes when Gaim closes.
[/LIST]

---

### Post by applegrew on 2007-08-31
Please note that the script above has been updated. The last one had bugs. Sorry.

---

### Post by applegrew on 2007-09-01
Updated **gaim-status**. Now it auto closes when Gaim closes.

---

### Post by applegrew on 2007-09-01
Updated yet another time.

---

### Post by GeneralHooHa on 2007-09-01
Thank you very much! Works like a charm! (Now I just need to convert all my friends to gaim so they will see the status :))

---

### Post by applegrew on 2007-09-02
Good that it helped you. :) Another thing it offeres which my Windows or non-Gaim friends feel jealous about is notification about the video that is being played (GTlak doesn't support this) and the random quotes. ;)

---

### Post by applegrew on 2007-09-02
@GeneralHooHa  BTW you don't need to change ur friends to Gaim so that they can see ur status.Your friends from Yahoo or GTlak can see ur status.

---

