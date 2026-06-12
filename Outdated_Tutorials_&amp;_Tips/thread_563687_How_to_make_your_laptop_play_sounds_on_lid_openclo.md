---
title: "How to make your laptop play sounds on lid open/close :)"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by KIAaze on 2007-09-30
[SIZE="4"]_Main howto:_[/SIZE]
Have you ever wanted your laptop to act like a Starcraft tank?
Well, with Ubuntu it's possible and very easy to do. :)

Whenever the lid of your laptop is opened or closed, Ubuntu runs the **/etc/acpi/lid.sh** script.
This script determines if the lid is open or closed by looking at the contents of "/proc/acpi/button/lid/LID/state".

So all you have to do to play opening/closing sounds is add this after the "#!/bin/bash" line:

```
grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
        aplay /etc/acpi/closing.wav;
else
        aplay /etc/acpi/opening.wav;
fi

```
where closing.wav and opening.wav are the sound files I use, placed in /etc/acpi.

Here's my complete lid.sh file:
```

#!/bin/bash

grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
	aplay /etc/acpi/closing.wav;
else
	aplay /etc/acpi/opening.wav;
fi

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

If you have Starcraft, you can extract the game sounds using the sound utilities available here: [http://www.battle.net/files.shtml]("http://www.battle.net/files.shtml")
The sound files for the tank are ttatra00.wav and ttatra01.wav.

[SIZE="4"]_Additional remarks:_[/SIZE]
[SIZE="4"]_Note 1:_[/SIZE]
It is of course possible to run **any command** on lid open/close events.
If you have other fun or useful ideas of what a laptop should do on lid events, please post them here. :)
(Sleep and hibernate isn't original. :p)

I was thinking about a switch into full download mode on lid close, so that your PC automatically starts using bandwidth for P2P for example when you aren't using it. ^^
I just don't know how to do that by command-line yet.

[SIZE="4"]_Note 2: How to run scripts for laptop lid open/close and dock/undock events:_[/SIZE]
Please refer to the howto from lunatico here:
[[HOWTO] Run scripts for laptop lid open/close and dock/undock events]("http://ubuntuforums.org/showthread.php?t=1076486")

[SIZE="4"]_Note 3: How to run GUIs:_[/SIZE]
[edit]
cf note above which is a better way to do it. ;)
[/edit]

I found a way to do it. :)
_To run a GUI as root:_
```
DISPLAY=:0 && command
```
_To run a GUI as normal user:_
```
DISPLAY=:0 && sudo -u username command
```

And for those interested in running GUI apps from root crontab, here's how:
_To run a GUI from root crontab as root:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * sudo -u username command

```
_To run a GUI from root crontab as normal user:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * command

```

_Useful links:_
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)
A script to launch another xserver and run a command on it:
[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
(basically, use "chvt <tty nb>" and then DISPLAY=... && command)

[SIZE="4"]_Note 3: Synthetizing voice_[/SIZE]
You can use "espeak" or "festival" for this.
```
espeak "hello"
```
```
echo "hello" | festival --tts
```
To read a whole text file:
```
festival --tts speak.txt
```

[SIZE="4"]_Note 4: make the console acknowledge each of your commands with an audio sound_[/SIZE]
I don't think this deserves its own howto (would need a full .bashrc tutorial), but this might also interest some people: **make the console acknowledge each of your commands with an audio sound.**

Again, RTS sounds are the best for this. :)
"By your command..."

Original post: [http://ubuntuforums.org/showpost.php?p=3788432&postcount=61](http://ubuntuforums.org/showpost.php?p=3788432&postcount=61)

========================================================

If you want to play sounds in your terminal when running any command (or just pressing enter), do the following:

Open ~/.bashrc.
Search for a string looking like "PS1=<some string>".
Add "\$(playsound)" at the beginning of the string.
It should then look like this for example:
```

PS1="\$(playsound)\e[0;1;33;41m[\u@\h:\w]\$ \e[m "

```

Then before that (at the beginning of the file), add:
```
playsound()
{
	aplay somefile.wav 1>/dev/null 2>&1 &
}

```

Note the "&" at the end of the aplay command to avoid having to wait for the end of the soundfile playing.
It also makes spamming possible when pressing enter several times. :D

example:"NuNuNuclear lalalaunch detectededed." :lolflag:

Some documentation:
[http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html#setps](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html#setps)
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x279.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x279.html)
========================================================

---

### Post by Knoeki on 2007-10-01
Nice, I like the idea... the possibilities are endless, to speak in sale-terms ;_)

but yeah, cool stuff can be done with it.

---

### Post by KIAaze on 2007-11-25
I don't think this deserves its own howto (would need a full .bashrc tutorial), but this might also interest some people: **make the console acknowledge each of your commands with an audio sound.**

Again, RTS sounds are the best for this. :)
"By your command..."

Original post: [http://ubuntuforums.org/showpost.php?p=3788432&postcount=61](http://ubuntuforums.org/showpost.php?p=3788432&postcount=61)

========================================================> **justin whitaker said:**
> 
6. Each terminal command receives an audible response of "as you command dread lord."


Ok, I did it. :D
If you want to play sounds in your terminal when running any command (or just pressing enter), do the following:

Open ~/.bashrc.
Search for a string looking like "PS1=<some string>".
Add "\$(playsound)" at the beginning of the string.
It should then look like this for example:
```

PS1="\$(playsound)\e[0;1;33;41m[\u@\h:\w]\$ \e[m "

```

Then before that (at the beginning of the file), add:
```
playsound()
{
	mplayer somefile.wav 1>/dev/null 2>&1 &
}

```

Note the "&" at the end of the mplayer command to avoid having to wait for the end of the soundfile playing.
It also makes spamming possible when pressing enter several times. :D

example:"NuNuNuclear lalalaunch detectededed." :lolflag:

Some documentation:
[http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html#setps](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html#setps)
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x279.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x279.html)
========================================================

---

### Post by nikoPSK on 2007-12-01
I like! But, my laptop is soooo slow I dont think it can run linux. Ive tried like 7 distros for it so far.... Any way for my laydown pc to have cool noises say....

Laptop specs:
128 RAM
267 MGz Processor
heaven knows how much Hard-drive Space....

---

### Post by KIAaze on 2007-12-02
Have you tried the light GNU/Linux distros?:
-[xubuntu]("http://www.xubuntu.org/get") (this one may be too heavy)
-[Puppy Linux]("http://www.puppylinux.org/wikka/MinReq")
-[Feather Linux]("http://featherlinux.berlios.de/docs.htm")
-[Damn Small Linux (DSL)]("http://en.wikipedia.org/wiki/Damn_Small_Linux#System_requirements")
etc

> DSL has been demonstrated browsing the web with Dillo, running simple games and playing music on systems with a 486 processor and 16MB of RAM.

> Feather should be able to run on a 486 with 16Mb of RAM, but only in console (non-graphical) mode. To use X, 24Mb of RAM or more are required.

---

### Post by nikoPSK on 2007-12-02
I've tried all those and more except feather. Mine has half the processor speed required. :(

---

### Post by santiagoward2000 on 2007-12-02
Sounds nice!! Do I need to have mplayer for doing this? Can't I do it with other players?

---

### Post by KIAaze on 2007-12-02
Anything you can run by command-line should work.

---

### Post by santiagoward2000 on 2007-12-02
> **santiagoward2000 said:**
> Sounds nice!! Do I need to have mplayer for doing this? Can't I do it with other players?

Hey, I found hoe to do it with **alsa**. In case anyone needs it the code is:
```
alsa "soundfile"
```

---

### Post by Bossieman on 2007-12-02
worked like a charm: [http://www.youtube.com/watch?v=0282dCSCTbQ](http://www.youtube.com/watch?v=0282dCSCTbQ)

---

### Post by nikoPSK on 2007-12-02
I like that. I wish I had a camcorder....

---

### Post by KIAaze on 2007-12-02
You can also use **espeak** or **festival** to synthetize voice. ;)

---

### Post by nikoPSK on 2007-12-02
heard of espeak but what's festival?

---

### Post by simplyw00x on 2007-12-02
> festival "Hello"
makes your computer say 'hello'.

Would do this but I already have an huge reputation as a nerd and it could get annoying in lectures :D

---

### Post by nikoPSK on 2007-12-02
...

```
niko@home:~$ festival "hello"

WARNING
No default voice found in ("/usr/share/festival/voices/")
either no voices unpacked or voice-path is wrong
Scheme interpreter will work, but there is no voice to speak with.
WARNING

SIOD ERROR: could not open file hello
niko@home:~$ 

```

---

### Post by apothecaryaaron on 2007-12-03
It works on lid close for me, but not open.  I'm new to Ubuntu and Linux in general, but not to programming, so is there a way for me to see what value is returned when lid state is open?  More curiosity than anything.  Thanks for the idea though.  I found all kinds of files in that directory to play with.

---

### Post by KIAaze on 2007-12-03
Just read the contents of the file "/proc/acpi/button/lid/LID/state":
```
cat /proc/acpi/button/lid/LID/state
```
I don't know why it doesn't work on lid open for you though. :/

@nikoPSK and simplyw00x:
```
espeak "hello"
``` works, but for festival, the syntax is different:
From the man page:
>  --tts   Synthesize text in files as speech no files means read from stdin (implies no interaction by default)


So you can use:
```
echo "hello" | festival --tts
```
or:
```
festival --tts speak.txt
```
where "speak.txt" is a text file containing the text you wish to hear. (very practical :) )

---

### Post by apothecaryaaron on 2007-12-03
> **KIAaze said:**
> Just read the contents of the file "/proc/acpi/button/lid/LID/state":
```
cat /proc/acpi/button/lid/LID/state
```
I don't know why it doesn't work on lid open for you though. :/


The state seems to show correctly.  I have seen posts throughout the forum where laptop lid detection for suspend/hibernate doesn't always work for certain laptops.  Mine probably doesn't throw the event (is that what it's called in Linuxspeak?) when the lid opens for some reason, or I need to delay the sound from playing long enough for the screen to re-illuminate.  Something to play with in my spare time.  The close by itself is still fun.  I let my coworker shut the lid.  When the computer asked him "Hey! Who turned out the lights?", he was quite startled.  There is also fun to be had with power.sh...

---

### Post by chronusdark on 2007-12-03
does anyone know how i can make this work when i plug a usb device in?

---

### Post by santiagoward2000 on 2007-12-03
HEY!
I just got some voices from **Red Alert 2** to use as my system sounds! It's so cool!
When I close the lid, I hear Sophia saying *"On hold"*, and when I open it, a conscript says: *"Good to see you, Sir. What are our orders?"*. As I was with this, I also put the *"Low power"* message for when my laptop's battery gets to 10%.
I love it! Thanks for the idea! :D

---

### Post by nikoPSK on 2007-12-03
sweet, red alert 2 was a great game. PS, did you just extract the sounds from your installation of it? Or could you send them to me...

---

### Post by mouseboyx on 2007-12-03
> **nikoPSK said:**
> I've tried all those and more except feather. Mine has half the processor speed required. :(

I currently have a home server running with 92 megs of ram and a 233mhz processor, it can act as my squid proxy, http server, ftp server, and ssh server all at once. and still has enough stuff to run X.
(jwm)

---

### Post by santiagoward2000 on 2007-12-03
> **nikoPSK said:**
> sweet, red alert 2 was a great game. PS, did you just extract the sounds from your installation of it? Or could you send them to me...

Actually, I looked for them on my CDs and inside the installation folders and I couldn't find them, so I finally got them from FrostWire. I'm still looking for the *"You have 30 seconds to comply"* that you hear when the installation asks for the key. I wanted to use that one on my login screen.
Let me compress the files and I'll send them to you. Just let me tell you they have no useful name, so you'll have to listen to some minutes of speeches to find the one you want.

_EDIT:_
Where can I send them to? Would there be any problems by attaching them here?

---

### Post by KIAaze on 2007-12-03
@NicoPSK:

I forgot this for your problem with festival:
Just install one of the voice packs. Search for festival in name&desription in synaptic.
ex:
```
festival-czech - Czech support for Festival speech synthesis system
festival-doc - Documentation for Festival
festival-freebsoft-utils - Festival extensions and utilities
festival-gaim - gaim plugin to hear incoming messages using voice synthesis
festival-hi - Festival text to speech synthesizer for Hindi
festival-mr - Festival text to speech synthesizer for Marathi
festival-te - Festival text to speech synthesizer for Telugu (te) language
festlex-ifd - Italian support for Festival
festlex-poslex - Part of speech lexicons and ngram from English
festvox-czech-ph - Czech male speaker for Festival
festvox-hi-nsk - Hindi male speaker for Festival
festvox-italp16k - Italian female speaker for Festival
festvox-itapc16k - Italian male speaker for Festival
festvox-kallpc16k - American English male speaker for festival, 16khz sample rate
festvox-kallpc8k - American English male speaker for festival, 8khz sample rate
festvox-kdlpc16k - American English male speaker for festival, 16khz sample rate
festvox-kdlpc8k - American English male speaker for festival, 8khz sample rate
festvox-mr-nsk - Marathi male speaker for Festival
festvox-suopuhe-common - Common files for Festival Finnish speakers
festvox-suopuhe-lj - Finnish female speaker for Festival
festvox-suopuhe-mv - Finnish male speaker for festival
festvox-te-nsk - Telugu (te) male speaker for Festival
festvox-don - minimal British English male speaker for festival
festvox-ellpc11k - Castilian Spanish male speaker for Festival
festvox-rablpc16k - British English male speaker for festival, 16khz sample rate
festvox-rablpc8k - British English male speaker for festival, 8khz sample rate

```

P.S: Just discovered this:
festival-gaim - gaim plugin to hear incoming messages using voice synthesis
Must try out.
If somebody finds it for IRC, please tell me. :D

---

### Post by nikoPSK on 2007-12-03
I have to try that out too, are there any funny voices?:lolflag: My gps has some funny ones...

---

### Post by weeman7007 on 2007-12-04
ignore this post, just subscribing for when i have sound in laptop again

---

### Post by loadeddreams on 2007-12-04
I really like this.

I made my laptop close sound from an OpenOffice.Org .wav file.
/usr/lib/openoffice/share/gallery/sounds/beam.wav but I edited the file with audacity to get rid of the "BIP" noise at the end of the file...

but after reading more of this thread, I'm thinking about using some fesitval stuff ;)

very interesting thread... thanks :)

---

### Post by dakuran on 2008-01-08
When i first followed this howto it worked like a charm for me, but for some reason after I reinstalled its not working anymore, i made sure to convert the sound flies (CS, Ownage & Wicked Sick) to 16bit .wav I threw everything in /etc/acpi and copied the code and placed it properly in lid.sh.

However, the hinge on the left side of my laptop (that keeps the display connected to the keyboard) is a bit lose, but, when I apply a bit of pressure my display shuts off (thats when it used 2 play) and when I opened it up it worked flawlessly

any suggestions/tips?

Thanks in advance

~dak

---

### Post by Pru on 2008-09-20
How can I get it to work with other programs? I really want to be able to use xbindkeys so i can change the mapping of some keys while it's closed (my laptop has -some- exposed keys)

I also tried running stuff like firefox and xfce4-terminal to open when i open the lid and that doesn't work either.


btw thanks for the great tutorial (i have the starcraft sounds :) )

---

### Post by KIAaze on 2008-09-22
> However, the hinge on the left side of my laptop (that keeps the display connected to the keyboard) is a bit lose, but, when I apply a bit of pressure my display shuts off (thats when it used 2 play) and when I opened it up it worked flawlessly

any suggestions/tips?

I don't quite understand the problem.:confused:
Seems more like a hardware issue.

> How can I get it to work with other programs? I really want to be able to use xbindkeys so i can change the mapping of some keys while it's closed (my laptop has -some- exposed keys)

I also tried running stuff like firefox and xfce4-terminal to open when i open the lid and that doesn't work either.

The problem is that **the commands get run by root and don't seem to have access to the display/ X server.**
I'm still trying to figure out how to launch GUIs from there (as well as from root crontab).
As for xbindkeys, I don't know how to use it, so if you could tell me what command you are trying to run, it might help me.

Here's what I do to debug:
```
date 1>>/home/user/temp.log 2>&1

grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
        export DISPLAY=:0 && xfce4-terminal 1>>/home/user/temp.log 2>&1
        xbindkeys  1>>/home/user/temp.log 2>&1
else
        export DISPLAY=:0 && xfce4-terminal 1>>/home/user/temp.log 2>&1
        xbindkeys  1>>/home/user/temp.log 2>&1
fi


```
It will write all output from the commands into /home/user/temp.log

Here's what I'm currently getting:
```
Mon Sep 22 13:37:27 CEST 2008
No protocol specified

(xfce4-terminal:14256): Gtk-WARNING **: cannot open display: :0

```

Some things I found:
[http://ubuntuforums.org/archive/index.php/t-5281.html](http://ubuntuforums.org/archive/index.php/t-5281.html)
[http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

---

### Post by KIAaze on 2008-09-29
> **Pru said:**
> How can I get it to work with other programs? I really want to be able to use xbindkeys so i can change the mapping of some keys while it's closed (my laptop has -some- exposed keys)

I also tried running stuff like firefox and xfce4-terminal to open when i open the lid and that doesn't work either.


btw thanks for the great tutorial (i have the starcraft sounds :) )

I found a way to do it. :)
_To run a GUI as root:_
```
DISPLAY=:0 && command
```
_To run a GUI as normal user:_
```
DISPLAY=:0 && sudo -u username command
```

And for those interested in running GUI apps from root crontab, here's how:
_To run a GUI from root crontab as root:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * sudo -u username command

```
_To run a GUI from root crontab as normal user:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * command

```

_Useful links:_
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)
A script to launch another xserver and run a command on it:
[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
(basically, use "chvt <tty nb>" and then DISPLAY=... && command)

---

### Post by lunatico on 2009-02-28
> **KIAaze said:**
> I found a way to do it. :)
_To run a GUI as root:_
```
DISPLAY=:0 && command
```
_To run a GUI as normal user:_
```
DISPLAY=:0 && sudo -u username command
```

And for those interested in running GUI apps from root crontab, here's how:
_To run a GUI from root crontab as root:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * sudo -u username command

```
_To run a GUI from root crontab as normal user:_
```

XAUTHORITY=/home/username/.Xauthority
DISPLAY=:0.0

# m h  dom mon dow   command
* * * * * command

```

_Useful links:_
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)
A script to launch another xserver and run a command on it:
[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
(basically, use "chvt <tty nb>" and then DISPLAY=... && command)

I don't think this is enough. Some people might notice that things some times work or some commands will not work.
It is important to understand that the lid event is managed by the acpid deamon which is owned by root. Anything you run from that /etc/acpi/lid.sh scripts will be run by root. Just running GUI things on DISPLAY:0 might not be enough for some programs or commands that rely on other user environment variables. For example the purple-remote command (which uses dbus) to change your pidgin status from command line will not work, aplay will not work either. So you need to do a bit more to expose your user's environment.
If anyone is interested [I wrote a tutorial]("http://ubuntuforums.org/showthread.php?t=1076486") which covers what's already covered on this tutorial for the lid open/close events but also includes a fix for the root stuff I just mentioned and it also covers how to do stuff when you dock/undock your computer.

Cheers!

---

### Post by KIAaze on 2009-03-01
Thanks. I added a link to your howto in the initial post. :)

By the way, you should fix your howto a bit.
There are some unclosed [code] tags:

> [code]#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/falling.wav"


> [code]#!/bin/bash
#This runs so that root can run the following command under the user's environment
source /home/your_user/.Xdbus
#play a sound
DISPLAY=:0.0 su your_user -c "aplay /usr/lib/openoffice/basis3.0/share/gallery/sounds/sparcle.wav"


---

### Post by lunatico on 2009-03-03
> **KIAaze said:**
> By the way, you should fix yout howto a bit.
There are some unclosed [code] tags:

Wow. I haven't noticed. Thanks for letting me know!

---

### Post by erick404 on 2011-05-28
Nice idea! I loved it, except that the closing sound plays both when I open and close the lid... any suggestions?

EDIT: Realized it myself. In the command line applying grep, I had to change the directory LID for LID0.

---

### Post by cracker89 on 2011-05-29
lol... kinda reminds me of nite rider... :D my lids going crazy!! :D nice 'un!

---

### Post by sectshun8 on 2011-05-29
What am I missing to make this work?  Does it involve not being the root user?

This is my current lid.sh

```
#!/bin/bash
# TODO:  Change the above to /bin/sh

grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
    aplay /etc/acpi/cartman.wav;
else
    aplay /etc/acpi/myniga.wav;
fi 

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"        
        . /usr/share/acpi-support/screenblank
    fi
    done
else
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
        if pidof xscreensaver > /dev/null; then 
            su $user -c "xscreensaver-command -unthrottle"
        fi
        fi
        if [ x$RADEON_LIGHT = xtrue ]; then
        [ -x /usr/sbin/radeontool ] && radeontool light on
        fi
        if [ `pidof xscreensaver` ]; then
        su $user -c "xscreensaver-command -deactivate"
        fi
        su $user -c "xset dpms force on"
    fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

---

### Post by KIAaze on 2011-05-29
Try running lid.sh directly from a terminal and check for any error output.
If necessary run it with sudo.

---

### Post by sectshun8 on 2011-05-29
typed ./lid.sh into terminal got the following"

grep: /proc/acpi/button/lid/LID/state: No such file or directory
aplay: test_wavefile:876: can't play WAVE-file format 0x0055 which is not PCM or FLOAT encoded

The same happens running with sudo

I'd also like to add this is on a fresh 11.04 install... I don't currently have an internet connection that I'm permitted to hook my netbook up to in order to get any of the updates.

---

### Post by KIAaze on 2011-05-29
For the grep error, check if you have LID0 instead of LID like erick404.
i.e. You should have "/proc/acpi/button/lid/LID0/state" or something similar somewhere.

For the aplay error, it looks like aplay can't play your soundfile, so try to convert it to a compatible format or just use mplayer:

So your code could be changed like this for instance:
```
grep -q closed /proc/acpi/button/lid/LID0/state
if [ $? = 0 ]
then
    mplayer /etc/acpi/cartman.wav;
else
    mplayer /etc/acpi/myniga.wav;
fi 
```

mplayer is in the repositories and supports mp3s. :)
```
sudo apt-get install mplayer
```

For converting sound files, you can use ffmpeg I think, but I don't have that much experience with it.

---

### Post by sectshun8 on 2011-05-30
> **KIAaze said:**
> For the grep error, check if you have LID0 instead of LID like erick404.
i.e. You should have "/proc/acpi/button/lid/LID0/state" or something similar somewhere.

For the aplay error, it looks like aplay can't play your soundfile, so try to convert it to a compatible format or just use mplayer:

So your code could be changed like this for instance:
```
grep -q closed /proc/acpi/button/lid/LID0/state
if [ $? = 0 ]
then
    mplayer /etc/acpi/cartman.wav;
else
    mplayer /etc/acpi/myniga.wav;
fi 
```mplayer is in the repositories and supports mp3s. :)
```
sudo apt-get install mplayer
```For converting sound files, you can use ffmpeg I think, but I don't have that much experience with it.

Seems like what you stated here was all correct.  After changing to the "LID0" that error went away... but sadly, as in my previous post I stated that I cannot currently connect to the internet with my netbook (restrictions here at work in the middle of the ocean), I'm pretty much at an impass in regards to getting mplayer installed.

I'll just have to wait until I'm back on dry land in about 8 days to get it all sorted ;)

---

### Post by sectshun8 on 2011-05-30
Well I found some acceptable .wav files from StarCraft online and tranferred them to my netbook and updated the script with aplay.

running ./lid.sh works ;)

However when i actually shut or close my netbook lid... nothing happens...???

---

### Post by sectshun8 on 2011-05-30
Well I got it finally to work when I close the lid, but not open...

To do it, just changed the "closed" in the script to "open", so it looks like this:

```

grep -q **open** /proc/acpi/button/lid/LID**0**/state 
if [ $? = 0 ] 
then     
      aplay /etc/acpi/tbapss00.wav; 
else     
      aplay /etc/acpi/pteWht03.wav;
 fi 
```That being said, where and what would I change to make a specific sound when the login screen is displayed?

---

