---
title: "HowTo: Disable Synaptics Touchpad While Typing"
date: 2006-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Mais on 2006-10-04
**This Tutorial is outdated for Intrepid (8.10) and later**: see [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

[COLOR=Black]**Purpose: **For many of us, our laptop touchpads get in the way of our typing quite often and can actually cause us to highlight or minimize things we didn't intend. So, this will help to alleviate that by making a small delay in the response of the touchpad after typing.

NOTE: Please read this guide entirely before attempting to do it. There is a section where you must restart X and thus close down your internet browser. The best way to do this would be to print this guide! I hope this works as well for you as it has for me!

[B]Procedure:
[/B]_1. Turn on SHMCONFIG_
  A. Open a Terminal. Applications -> Accessories -> Terminal[/COLOR]
[COLOR=Black]   B. Type *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup*
[/COLOR][LEFT][COLOR=Black]   C. Type *gksudo gedit /etc/X11/xorg.conf* Enter your password if it prompts  you.
[/COLOR][IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16863&d=1159952582[/IMG]
*Note: The second command in the picture is typed wrong. Please see C.*
[/LEFT]
[COLOR=Black]
D. Search for a section that looks like this:
      [/COLOR][INDENT][COLOR=Black]*Section "InputDevice"*[/COLOR]
[COLOR=Black]*                   Identifier    "Synaptics Touchpad"*[/COLOR]
[COLOR=Black]*                   ...*[/COLOR]
[COLOR=Black]*       End Section*[/COLOR] [/INDENT][COLOR=Black]   E. Add a line above the *End Section* line and put this into it:
[/COLOR][INDENT][COLOR=Black][I]Option        "SHMConfig"        "on"
[/I][/COLOR][/INDENT][COLOR=Black]*[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16864&stc=1&d=1159952821[/IMG]*[/COLOR][COLOR=Black] [COLOR=DarkRed]  
[COLOR=Black]F. Save the file and close gedit and the terminal window[/COLOR]
[/COLOR][/COLOR][COLOR=Black][COLOR=DarkRed]G. Write these commands down just in case this screws up your window system: *sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf *and *sudo killall gdm *and [/COLOR]*[COLOR=DarkRed]sudo gdm[/COLOR]*[/COLOR][COLOR=Black]
H. This next step will restart your window system, so save any work and close any open applications. Press: Ctrl-Alt-Backspace. This should take you back to your login screen. If it does not, press Ctrl-Alt-F1 and login at the terminal window. After logging in, type the commands that you wrote down from step F in order hitting return after each command.
  I. If your login screen came up[/COLOR][COLOR=Black] the first time, continue on to part 2, if not, look over waht you did carefully and see if you can spot any mistakes.
[U]
2. Add the Startup Command[/U]
  A. Open the sessions manager: System -> Preferences -> Sessions
  B. Click the far right tab labeled Startup Programs
  C. Click the Add button
  D. Type in the following: *syndaemon -i 1 -d*
[/COLOR][COLOR=Black][I][IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16865&stc=1&d=1159952821[/IMG]
[/I][/COLOR][COLOR=Black]   E. Hit ok then hit close

Congratualations, you are done! Note that this will not take effect until Gnome is restarted or you type the command from 2D in a terminal window. You can restart Gnome with the Ctrl-Alt-Backspace trick (make sure to save everything first!) or you can open a terminal by going to Applications -> Accessories -> Terminal.

If you have any questions, comments, or concerns, feel free to contact me through this board, or more easily through email or AIM.
  
[/COLOR]

---

### Post by funboy116 on 2006-10-06
Hi,

According to your directions, I have to set up a daemon in my Sessions preferences, this however does not appear to exist in my version.

Here are the applications I have under System -

Adept, KCron, Keep, KinfoCenter, Konsole, kpowersave, KSysGuard, KSystemLog, and Language Support.

If you could please tell me how else I might do step 2 of your instructions, I'd much appreciate it.

Thanks,

Ryan

---

### Post by doogleplex on 2006-10-13
Thanks for this how to.

The simplicity of this HowTo is marvelous, and informative. I can finally peacefully type text in Ubuntu on my notebook, without the touchpad getting a mind of its own, and clicking to the cursor!
No more having to keep my hands held above the computer to type, LOL.
:)

I am on an HP Pavilion zv5430us notebook, AMD Athlon 64, Ubuntu 6.06 amd64-generic.

---

### Post by Mais on 2006-10-23
> **funboy116 said:**
> Hi,

According to your directions, I have to set up a daemon in my Sessions preferences, this however does not appear to exist in my version.

Here are the applications I have under System -

Adept, KCron, Keep, KinfoCenter, Konsole, kpowersave, KSysGuard, KSystemLog, and Language Support.

If you could please tell me how else I might do step 2 of your instructions, I'd much appreciate it.

Thanks,

Ryan

Ahh! I didn't think of Kubuntu. I'm not exactly sure how to add this to startup in KDE. I would start with KCron though. That is a program that executes commands based on a schedule.

Since I can't help you directly, here is the goal of your work:
You want this command to run as soon as you log on to KDE
syndaemon -i 1 -d

Perhaps someone else can tell us where to do that?


[quote=doogleplex]
    Thanks for this how to.

The simplicity of this HowTo is marvelous, and informative. I can finally peacefully type text in Ubuntu on my notebook, without the touchpad getting a mind of its own, and clicking to the cursor!
No more having to keep my hands held above the computer to type, LOL.
:smile:

I am on an HP Pavilion zv5430us notebook, AMD Athlon 64, Ubuntu 6.06 amd64-generic.[/quote]

I am very glad to hear that this howto was helpful! My goal was to make it as simple as possible and I really appreciate your encouraging comments!

---

### Post by mms on 2006-10-25
brilliant!  I've attempted many much more complex how-tos on this problem, but none was entirely successful.  Each time I had to resort to disabling my touchpad in my xorg.conf when doing any extensive typing.  

thanks

---

### Post by lagartoflojo on 2006-11-08
Hey!
Thanks a lot for this how to, it worked great!
For anyone who might be interested, the man page of syndaemon (in a terminal type: man syndaemon) has some more options you can use:
```
OPTIONS
       -i <idle-time>
              How  many  seconds  to  wait  after  the  last  key press before
              enabling the touchpad.  (default is 2.0s).

       -d     Start as a daemon, ie in the background.

       -p <pid-file>
              Create a pid file with the specified filename.  A pid file  will
              only be created if the program is started in daemon mode.

       -t     Only  disable  tapping  and  scrolling,  not mouse movements, in
              response to keyboard activity.

       -k     Ignore modifier keys when monitoring keyboard activity.

       -K     Like -k but also ignore Modifier+Key combos.
```

---

### Post by groggyboy on 2006-11-08
> Ahh! I didn't think of Kubuntu. I'm not exactly sure how to add this to startup in KDE. I would start with KCron though. That is a program that executes commands based on a schedule.

Since I can't help you directly, here is the goal of your work:
You want this command to run as soon as you log on to KDE
syndaemon -i 1 -d

Perhaps someone else can tell us where to do that?

I'm not sure about how to do this - i just recently switched to kubuntu myself.

however, i noticed that KDE has an autostart folder (/home/username/.kde/Autostart).  I haven't tried this, but it should be theoretically possible to create a script in this folder.  Paste "syndaemon -i 1 -d" into a new text document using kate.  save it in the autostart folder, and name it "syndaemon".  then make it executable, and restart.  hopefully, if my theory is correct, it should run.


disclaimer: i don't actually know how to write proper scripts - typing "syndaemon -i 1 -d" into a text doc and making it executable is probably not enough.

---

### Post by yxvaan on 2006-12-07
I'd like to disable my touchpad completely, as it is a sheer nuisance on an IBM ThinkPad. Judging from mms's post above, that might be achieved by editing xorg.conf, but how exactly? I tried setting "SendCoreEvents" under" "Synaptics Touchpad" to "false" and rebooting but that changed nothing.
I'd appreciate any suggestions - this touchpad has been bugging me ever since I installed Ubuntu to my latest TP (there weren't any in my previous ones...)

---

### Post by reacocard on 2006-12-24
Excellent HOWTO, I've been looking for a way to do this.  Works perfectly for me.

For you Kubuntu users, follow the instructions of groggyboy above, but put
```
#!/bin/sh
```
as the first line in the file, otherwise it won't work.

Xubuntu users should look in Preferences -> Autostarted Applications

---

### Post by reacocard on 2006-12-24
> **yxvaan said:**
> I'd like to disable my touchpad completely, as it is a sheer nuisance on an IBM ThinkPad. Judging from mms's post above, that might be achieved by editing xorg.conf, but how exactly? I tried setting "SendCoreEvents" under" "Synaptics Touchpad" to "false" and rebooting but that changed nothing.
I'd appreciate any suggestions - this touchpad has been bugging me ever since I installed Ubuntu to my latest TP (there weren't any in my previous ones...)

To disable the touchpad *completely*, open your xorg.conf, and comment out or remove the line that says
```
	InputDevice	"Synaptics Touchpad"
```
in the "ServerLayout" section (it's near the bottom).

---

### Post by ariel on 2007-01-03
This method was more convenient for me:

To disable the touchpad:

```
synclient TouchpadOff=1
```

To enable the touchpad:

```
synclient TouchpadOff=0
```


And: you can put each on a launcher in your desktop. The result works pretty neat in my case. If you are at your desk with a mouse, or typing, just disable the touchpad.

---

### Post by george_apan on 2007-01-22
Brilliant! Thank you very much for the how to!

---

### Post by kulik on 2007-01-22
hello!

i did, but takes no effect....
i can run syndaemon is terminal, and it says enable/disable, but takes no effect

---

### Post by tee2 on 2007-01-22
What is SHMCONFIG and how do I turn it on?

---

### Post by reacocard on 2007-01-22
> **tee2 said:**
> What is SHMCONFIG and how do I turn it on?

SHMConfig is what lets applications configure your touchpad while the XServer is running. To turn it on, open a terminal and type
```
gksudo gedit /etc/X11/xorg.conf
```

Now find the section that starts with this:
```
Section "InputDevice"
Identifier "Synaptics Touchpad"
```
And add this line inside that section:
```
Option "SHMConfig" "on"
```
Save the file, then reboot the computer.

---

### Post by Aruna on 2007-01-29
Very useful and simple.

Thank you very much.:D

---

### Post by osofast on 2007-03-07
Hey, 

Great guide. One problem though for my xorg.conf file there is no where that says "Synaptics Touchpad" for me it says the following

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Any ideas why I dont have a Synaptics Touchpad?

---

### Post by treesurf on 2007-03-08
Wow!  This was an excellent howto that solved a really irritating problem.

Thank you!

---

### Post by treesurf on 2007-03-08
Osofast,

There are several input devices, each with a different "Identifier".  Open your xorg.conf again and keep scrolling through the input devieces until you find the touchpad.

---

### Post by osofast on 2007-03-08
lol thanks for making me look like an idiot.

Just kidding, I really appreciate the help, thanks

---

### Post by osofast on 2007-03-08
Ok, still doesnt work

I added the line to xorg.conf


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

I also did the syndameon thing

[[IMG]http://img249.imageshack.us/img249/774/screenshotnz9.th.png[/IMG]](http://img249.imageshack.us/my.php?image=screenshotnz9.png)

---

### Post by treesurf on 2007-03-10
Osofast,

You misspelled the syndaemon command in the Sessions/Startup Programs window.  Try fixing that and see if it works.

---

### Post by CrazyTn on 2007-03-10
is there a fast way to enable and disable this?

---

### Post by osofast on 2007-03-10
Hey, thanks for the reply,

Im fairly sure I didnt mis spell anything
Just to make sure I copied and pasted it from your post into the sessions manager and still nothing. 

When I type syndaemon -i -d in terminal this is what i get
> Usage: syndaemon [-i idle-time] [-d] [-t] [-k]
  -i How many seconds to wait after the last key press before
     enabling the touchpad. (default is 2.0s)
  -d Start as a daemon, ie in the background.
  -p Create a pid file with the specified name.
  -t Only disable tapping and scrolling, not mouse movements.
  -k Ignore modifier keys when monitoring keyboard activity.
  -K Like -k but also ignore Modifier+Key combos.


---

### Post by treesurf on 2007-03-10
Hey Osofast,

I'm not sure what to tell you.  I'm no expert on this.  I just noticed that the instructions say to enter the command "syndaemon -i 1 d" and your screen shot shows that you have entered "syndaemon -i -d".

---

### Post by osofast on 2007-03-10
Hey, 

I tried putting the 1 there but still not solution.

The "1" is how many seconds you want the touchpad to turn off for. by default (if you leave it empty)  its 2 seconds. I dont think this is the problem. 

Thanks though, I guess Ill have to try something else.

---

### Post by osofast on 2007-03-12
oh well, i think i am just going to go back to using windows

---

### Post by jcard0na on 2007-08-18
> **reacocard said:**
> To disable the touchpad *completely*, open your xorg.conf, and comment out or remove the line that says
```
	InputDevice	"Synaptics Touchpad"
```
in the "ServerLayout" section (it's near the bottom).

This did not work for me, as the Touchpad was still sending events via the default InputDevice ("Configured Mouse").  What worked was:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
[COLOR="Red"]#       InputDevice     "Configured Mouse"[/COLOR]
        InputDevice     "Synaptics Touchpad"
EndSection

```
```


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
[COLOR="Red"]        Option          "TouchpadOff"           "1"[/COLOR]
        Option          "SHMConfig"             "on"
EndSection


```

---

### Post by osofast on 2007-08-18
Oh thanks, i have gotten used to not touching my mousepad...but ill give this a try tonight and see what i get.

thanks a bunch

---

### Post by ice60 on 2007-08-18
thanks for the tutorial, Mais. i'll try it when i next use my laptop. my touchpad was almost perfectly configured by ubuntu, apart from this.

i'm not sure about this, as it looks like no one has mentioned it, but i think there's a mistake at 'C'. you wrote 
>  C. Type gksudo /etc/X11/xorg.conf Enter your password if it prompts you.
and i think it should have gedit after gksudo like this -
>  C. Type gksudo **[color=red]gedit**[/color] /etc/X11/xorg.conf Enter your password if it prompts you.:confused:

---

### Post by urvaksh on 2007-08-21
When I type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup in the terminal window. I am asked for a passwod, but my keyboard won't work and I can't type the password. 
The keyboard is fine when i'm out of the terminal. Please help.

---

### Post by urvaksh on 2007-08-21
OK,
now I'm getting this message in terminal after typing  gksudo /etc/X11/xorg.conf:

/home/urvaksh/.themes/HumanStudio/gtk-2.0/gtkrc:216: Unable to locate image file in pixmap_path: "panel.png"

---

### Post by lagartoflojo on 2007-08-21
> **urvaksh said:**
> When I type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup in the terminal window. I am asked for a passwod, but my keyboard won't work and I can't type the password. 
The keyboard is fine when i'm out of the terminal. Please help.

Actually, your keyboard is working when you type the password, it just doesn't show asterisks or anything to let you know that you are typing anything. This is done to hide the password and the password's length, I suppose. Anyway, when you run that sudo command, and you are asked for the password, type it out and press enter. It should then work.

---

### Post by lagartoflojo on 2007-08-21
> **urvaksh said:**
> OK,
now I'm getting this message in terminal after typing  gksudo /etc/X11/xorg.conf:

/home/urvaksh/.themes/HumanStudio/gtk-2.0/gtkrc:216: Unable to locate image file in pixmap_path: "panel.png"

Please see post #30 (the one above your first post).
The command should be:
```
gksudo **gedit** /etc/X11/xorg.conf
```
(notice that you are missing the "gedit" part.

---

### Post by urvaksh on 2007-08-21
Thanks Lagartoflojo
It worked without a problem...I think. The cursor is not going crazy anymore
sorry for the dumb-*** posts:)
You guys on the forum are really awesome

---

### Post by slughappy1 on 2007-08-22
Thanks for the how to. It works perfectly for me. Although I used sudo nano instead of sudo gedit. I think it is  a little easier, but it comes out to the same end so it doesn't make a big difference.

---

### Post by t2000kw on 2007-08-22
Another person here with the same problem. I found the xorg.conf file and there is no mention of a touchpad, but I have one, a Synaptics on a Dell Inspiron 7000. There is a section on a mouse shown below:
========================
Section "InputDevice"				
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option 		"SHMConfig"  		"on"
EndSection
=====================
 which I replaced with this mentioned in this thread:

=============================
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "TouchpadOff"           "1"
        Option          "SHMConfig"             "on"
EndSection
============================

and then the Xserver wouldn't work. I used Pico to restore it to where it was originally and restarted X and I'm back to "normal," with a "touchy" touchpad that throws text wherever it feels like whenever I bump the pad with my thumb. 

when I run a command cat /proc/bus/input/devices, I get this output in Terminal:

==================================

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 **Synaptics TouchPad**"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6
============================

so I know Ubuntu knows that I have a Synaptics touchpad. 

Where to go from here since I can't add this line to a section that doesn't exist:
  
Option          "SHMConfig"             "on"

and when I add the section manually it breaks Ubuntu?

---

### Post by t2000kw on 2007-08-22
Something that might help me go about this another way is to install this startup script so I can use a different approach using tpconfig. How do I save this and where would it go? The author of the script uses Red Hat and said this:

I usually run tpconfig from a  start-up script which (on my RH system) goes in /etc/rc.d/init.d (and linked under various run levels as S84touchpad) to turn off the tap mode. Installation of this script and links for run levels 3 and 5 are now performed by the binary rpm

I have the program installed but it's not available to the system after Xwindows starts, so it needs to be invoked earlier. Not sure how to do the startup script, though. 


#!/bin/sh
# touchpad
# description: Startup script to disable touchpad tapping
# For Synaptics or ALPS touchpads.
#
# $Log$
#
# $Id$
#
#

test -r /etc/rc.d/init.d/functions && . /etc/rc.d/init.d/functions


echo ""
echo -n "Turning off Touch-Pad 'tapping' "

if [ -f /usr/bin/tpconfig ]; then
  /usr/bin/tpconfig --tapmode=0
  if [ $? ]; then
    echo_failure
  else
    echo_success
  fi
else
  echo_failure
fi
echo ""
exit 0

---

### Post by dustyhawk on 2007-08-26
im using an IBM T42  on ubuntu 7.04 with latest updates as of 27 aug. 

followed the steps above .. but im getting this



XXXXXI:~$ sudo cp /etc/X11/xorg.conf/etc/X11/xorg.conf_synbackup
cp: missing destination file operand after `/etc/X11/xorg.conf/etc/X11/xorg.conf_synbackup'
Try `cp --help' for more information.
XXXXX:~$ 


ps-still a freshie in ubuntu

---

### Post by reacocard on 2007-08-26
> **dustyhawk said:**
> im using an IBM T42  on ubuntu 7.04 with latest updates as of 27 aug. 

followed the steps above .. but im getting this



XXXXXI:~$ sudo cp /etc/X11/xorg.conf/etc/X11/xorg.conf_synbackup
cp: missing destination file operand after `/etc/X11/xorg.conf/etc/X11/xorg.conf_synbackup'
Try `cp --help' for more information.
XXXXX:~$ 


ps-still a freshie in ubuntu

you missed the space in between the two parts, the command should be this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup
```

---

### Post by Mais on 2007-08-26
> **ice60 said:**
> i think it should have gedit after gksudo like this -
:confused:

You are absolutely right. I'll fix that asap.

To everyone else: Thanks for the positive feedback and everyone else who has been so helpful in getting people's problems solved. I have Ubuntu back on my laptop again so I'll try and be around to answer them myself again. You all are so quick at replying though ;)

---

### Post by phyrewall on 2007-08-27
Works for me on a XPS M170, thanks!

---

### Post by dustyhawk on 2007-08-27
ok.... followed the "sudo killall gdm"   however when that was done, system gone back to welcome page but nothing else happened. no login screen what so ever.

after the  "sudo killall gdm"  what was suppose to happen ?

---

### Post by lagartoflojo on 2007-08-27
After killing GDM and Gnome (that's what **sudo killall gdm** does) type **sudo gdm** to start GDM (Gnome) again. You should be back at your login screen. Nothing is supposed to be different, simply login normally and now when you type into, say OpenOffice, tapping on the Touchpad will not actually produce a click for a few seconds. Nothing more to it.

---

### Post by dustyhawk on 2007-08-27
> **lagartoflojo said:**
> After killing GDM and Gnome (that's what **sudo killall gdm** does) type **sudo gdm** to start GDM (Gnome) again. You should be back at your login screen. Nothing is supposed to be different, simply login normally and now when you type into, say OpenOffice, tapping on the Touchpad will not actually produce a click for a few seconds. Nothing more to it.

Therefore after typing **sudo killall gdm** it should not make the system jump back to the **welcome screen** right?

Because this is what is happening to me. Each time i use the **sudo killall gdm** in a terminal, it goes to the **welcome screen** but it will not display the **insert username** interface, it just displays the wallpaper and all keys including touchpad + external mouse connected to the laptop (IBM T42)  does not function.

---

### Post by lagartoflojo on 2007-08-27
To tell you the truth, I never restart Gnome using **sudo killall gdm**. Instead I do **sudo /etc/init.d/gdm restart**
Try that and see if it works.
Regardless, I don't know where you are on the tutorial. It says to issue the killall command only if Ctrl+Alt+Backspace is not restarting Gnome. Is that where you are? If so, it means you have already modified xorg.conf, so you might as well just restart your computer (**sudo shutdown -r now**) and follow the rest of the tutorial (ie from "2. Add the Startup Command" on)

---

### Post by dustyhawk on 2007-08-28
> **lagartoflojo said:**
> To tell you the truth, I never restart Gnome using **sudo killall gdm**. Instead I do **sudo /etc/init.d/gdm restart**
Try that and see if it works.
Regardless, I don't know where you are on the tutorial. It says to issue the killall command only if Ctrl+Alt+Backspace is not restarting Gnome. Is that where you are? If so, it means you have already modified xorg.conf, so you might as well just restart your computer (**sudo shutdown -r now**) and follow the rest of the tutorial (ie from "2. Add the Startup Command" on)

This is where i am in the instruction  :

[B]
H. This next step will restart your window system, so save any work and close any open applications. Press: Ctrl-Alt-Backspace. This should take you back to your login screen. If it does not, press Ctrl-Alt-F1 and login at the terminal window. After logging in, type the commands that you wrote down from step F in order hitting return after each command.[/B]

Should i be doing this :

in the terminal :

*sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf *

enter (thing restarts)

then  *sudo killall gdm*

enter

*sudo gdm*

?? 

Or when i use *sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf * and press Enter and it restarts i go straight to 

[B]
2. Add the Startup Command
A. Open the sessions manager: System -> Preferences -> Sessions
B. Click the far right tab labeled Startup Programs
C. Click the Add button
D. Type in the following: syndaemon -i 1 -d[/B]

?

---

### Post by Gen2ly on 2007-08-28
Hey thanks man!  I here found this thing to be the most aggravating thing in Linux for sure

---

### Post by Mais on 2007-08-28
> **dustyhawk said:**
> This is where i am in the instruction  :

[B]
H. This next step will restart your window system, so save any work and close any open applications. Press: Ctrl-Alt-Backspace. This should take you back to your login screen. If it does not, press Ctrl-Alt-F1 and login at the terminal window. After logging in, type the commands that you wrote down from step F in order hitting return after each command.[/B]

Should i be doing this :

in the terminal :

*sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf *

enter (thing restarts)

then  *sudo killall gdm*

enter

*sudo gdm*

?? 

Or when i use *sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf * and press Enter and it restarts i go straight to 

[B]
2. Add the Startup Command
A. Open the sessions manager: System -> Preferences -> Sessions
B. Click the far right tab labeled Startup Programs
C. Click the Add button
D. Type in the following: syndaemon -i 1 -d[/B]

?

You don't want to issue the cp command you have above unless X won't restart or your mouse won't work. That is your backup 'just in case.'

 Try the ctrl-alt-backspace command and it should bring you to the login screen.

If it does not, hit ctrl-alt-F1, login there, and type *sudo /etc/init.d/gdm restart*.

If that does not work, hit ctrl-alt-F1, login if necessary, and type [I]sudo shutdown -r now.


[/I]

---

### Post by dustyhawk on 2007-08-29
I seem to going along smoothly now, however when placing

2. Add the Startup Command
A. Open the sessions manager: System -> Preferences -> Sessions
B. Click the far right tab labeled Startup Programs
C. Click the Add button
D. Type in the following: syndaemon -i 1 -d

I cannot get what is stated in the following link

[http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821](http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821)

as it states "Text was empty (or included white spaces)

---

### Post by Mais on 2007-09-01
> **dustyhawk said:**
> I seem to going along smoothly now, however when placing

2. Add the Startup Command
A. Open the sessions manager: System -> Preferences -> Sessions
B. Click the far right tab labeled Startup Programs
C. Click the Add button
D. Type in the following: syndaemon -i 1 -d

I cannot get what is stated in the following link

[http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821](http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821)

as it states "Text was empty (or included white spaces)
I really don't know why you would receive that message at all! If you are copying and pasting, try typing it in yourself. If you are typing it in yourself, try copying and pasting. 

If it continues, try adding another command to startup. A good one might be:
 *gaim -n*  
This 
will auto load GAIM without logging you in to any services. If you don't get the same error, then you are probably typing the command out wrong. If you do get the same error then you might want to make sure your keyboard is set to the right layout:
System->Preferences->Keyboard->Layouts

Good luck!

---

### Post by Hans de Visser on 2007-09-04
Thanks dustyhawk. I have a Compaq Presario M2000 Laptop, running Kubuntu 7.04.
This had been bothering me for a long time. A few weeks ago I heard that commenting out some lines in de xorg.conf file should work, but it did not help me at all. 
Your instructions (together with instruction on adding a script in /home/<user>/.kde/autostart) helped me putting this problem to rest.
Thanks!

---

### Post by tronnix75 on 2007-10-09
> **reacocard said:**
> To disable the touchpad *completely*, open your xorg.conf, and comment out or remove the line that says
```
	InputDevice	"Synaptics Touchpad"
```
in the "ServerLayout" section (it's near the bottom).

I did this and now i can not boot into the GUI? what now:(

---

### Post by tronnix75 on 2007-10-10
> **reacocard said:**
> To disable the touchpad *completely*, open your xorg.conf, and comment out or remove the line that says
```
	InputDevice	"Synaptics Touchpad"
```
in the "ServerLayout" section (it's near the bottom).

deleting that comment screwed up my xorg.conf file

---

### Post by reacocard on 2007-10-10
> **tronnix75 said:**
> deleting that comment screwed up my xorg.conf file

Yeah it seems the newer xorg doesn't like this fix (Probably a corepointer thing, bleh). You can disable it in-session with

```
synclient touchpadoff=1
```

if shmconfig is enabled, but that setting is lost when you log out, so if you want it to persist you will need to add it to your startup programs (System->Preferences->Sessions).

---

### Post by cruzer45 on 2007-10-29
Thanks a lot.... this REALLY helps a lot.

---

### Post by jdc on 2007-11-04
> **kulik said:**
> hello!

i did, but takes no effect....
i can run syndaemon is terminal, and it says enable/disable, but takes no effect

The same thing is happening for me with Gutsy on a Macbook Pro/Santa Rosa.  I type "syndaemon -i 2", and when I hit a key, it says it is disabling the touchpad, and then 2 seconds later it says it is enabling it.  But during those two seconds, I can still move the pointer and tap to click on things.

If I do "synclient TouchpadOff=1", this does disable the touchpad, so my SHMConfig setting is working.

Any thoughts? 

Dan

---

### Post by Warpnow on 2007-12-06
I think I love you.

---

### Post by Zorael on 2007-12-23
Is there any way to get this daemon to start before X?

---

### Post by D_invictus on 2007-12-23
The touchpad is the only reason I was using a secondary keyboard. Now I don't have to anymore. Thanks!:guitar:

---

### Post by TomeRaider2 on 2008-01-03
First, Thank you Mais this HowTo is FANTASTIC!!! You Rock!:guitar:

> **dustyhawk said:**
> I seem to going along smoothly now, however when placing

2. Add the Startup Command
A. Open the sessions manager: System -> Preferences -> Sessions
B. Click the far right tab labeled Startup Programs
C. Click the Add button
D. Type in the following: syndaemon -i 1 -d

I cannot get what is stated in the following link

[http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821](http://ubuntuforums.org/attachment.php?attachmentid=16865&d=1159952821)

as it states "Text was empty (or included white spaces)

dustyhawk: I think the sessions manager has changed since Mais wrote this HowTo.
I had the same problem the first time I tried. 
When you click the Add button do you get three (3) text entry boxes?  I did, they are "Name", "Command" and "Comment".
Enter the command in the HowTo in the "Command" box. It should be the middle one. In the other two enter whatever you want to identify the command.

Hope this helps.

---

### Post by Chemist on 2008-01-14
thanks for the how to mate. this had been doing my head in for ages!!

---

### Post by 89vision on 2008-01-15
This HOWTO saved me from so much frustration.  Thank You!

---

### Post by Casual Fan on 2008-01-23
This seems to have worked for me. Many thanks!

---

### Post by rudedcam on 2008-02-09
well well! ain't working for me:/

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	[COLOR="Red"]Option		"SHMConfig"		"on"
	Option		"TouchpadOff"		"1"[/COLOR]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
[COLOR="Red"]#[/COLOR]	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
[COLOR="Red"]#[/COLOR]	InputDevice	"Synaptics Touchpad"
EndSection
```

```
synclient touchpadoff=1
Can't access shared memory area. SHMConfig disabled?

```

anybody sees anything i could of missed?
thx

---

### Post by ugm6hr on 2008-02-10
@rudedcam:
You have turned the Touchpad off permanently in xorg:
```
Option		"TouchpadOff"		"1"
```

You have to delete this line in order to get it to work on bootup!

The synclient entry is case sensitive too:
```
synclient TouchpadOff=0
```

Why don't you use syndaemon to do it automatically though (as per How-To) in OP.

This is my variation: [http://ubuntuforums.org/showpost.php?p=3136787&postcount=8](http://ubuntuforums.org/showpost.php?p=3136787&postcount=8)

---

### Post by rudedcam on 2008-02-10
i have deleted the line in xorg... touchpad still anoying


> Why don't you use syndaemon to do it automatically though (as per How-To) in OP.

This is my variation: [http://ubuntuforums.org/showpost.php...87&postcount=8](http://ubuntuforums.org/showpost.php...87&postcount=8)
well, i'm desperately trying to find anything that will disable this touchpad ;)

[[img]http://img2.freeimagehosting.net/uploads/th.25bb5c5fbb.jpg[/img]](http://img2.freeimagehosting.net/image.php?25bb5c5fbb.jpg)
syndaemon doesn't seem to be working with me
[[img]http://img2.freeimagehosting.net/uploads/th.7a2a8ad884.jpg[/img]](http://img2.freeimagehosting.net/image.php?7a2a8ad884.jpg)

```
synclient TouchpadOff=0
Can't access shared memory area. SHMConfig disabled?

```

i don't know what else to do...:confused:

---

### Post by ugm6hr on 2008-02-11
> **rudedcam said:**
> ```
synclient TouchpadOff=0
Can't access shared memory area. SHMConfig disabled?

```

i don't know what else to do...:confused:

What happens if you just enter the line in Terminal?
```
syndaemon -i 3 -t -K
```

Does that give errors?

Does *syndaemon* appear in the list of processes in System Monitor?

Also - try "1" instead of "on" for SHMConfig in xorg.  It can be funny sometimes.

---

### Post by kryth on 2008-02-11
Thanks for this guide. That's been bugging the heck out of me for a long time.

---

### Post by rudedcam on 2008-02-13
```
syndaemon -i 3 -t -K
Can't access shared memory area. SHMConfig disabled?

```

no syndaemon in the manager terminal

i changed the "on" for "1" or "0"  still no change

let me know if you think of something else.
thanks

---

### Post by Michl on 2008-02-25
What do you do in Hardy Heron where the
xorg.conf file is abbreviated and there
is not section for the toucpad, even though
it works.

---

### Post by jblackthorne on 2008-02-25
This is such a great post that helped so many people that I decided to help take it one step further.  Attached to this post is a deb file:

syndaemon-x11-launch-0.2_all.deb

This deb package installed a X11 startup script to automatically start the syndaemon daemon at the start of every X11 session.  This avoids needing to add the Startup entry to every user's session preferences.  

Also, since there have been so many questions about editing the xorg.conf, I included a sample xorg.conf file and detailed instructions.  After installing this package, browse to the directory:

/usr/share/doc/syndaemon-x11-launch

to find those files.  

So, to summarize: To use the Synaptic Touchpad daemon which locks the touchpad while typing, there are only two required steps:

1.install this deb by double-clicking
2.Use the instructions at /usr/share/doc/syndaemon-x11-launch to walk you through editing your /etc/X11/xorg.conf file to add the single line: 

Option "SHMConfig" "true"

to the InputDevice/ Synaptics Touchpad section.  

	As an added bonus, the installation of this deb also installs the gsynaptics package if it was not previously installed. This is a configuration package for the Synaptics Touchpad allowing further refinement of preferences. You can access this under the 

System/Preferences/Touchpad

menu item. Have fun!

---

### Post by jblackthorne on 2008-02-25
Update: Replaced the above post with deb package version 0.2

---

### Post by apothecaryaaron on 2008-02-27
Worked perfectly first try.  Thank you very much for this easy to use tutorial.

---

### Post by joshzam on 2008-02-28
I'd like to add my thanks to the long list already (and deservedly) here.

I've got a brand new Acer Extensa 5620. It came with Vista and I quickly wiped the HD and installed Hardy. But even with Windows I noticed that the cursor would jump across the screen while I was typing - not from me accidentally touching the touchpad, but from what I can only assume to be the vibrations from me typing! I tried adjusting the touchpad sensitivity in Hardy from System > Preferences > Mouse but there was no effect. Only after applying this fix did I notice how stressed I was becoming while typing from never knowing if the cursor would jump across the screen or not.

So thanks!

---

### Post by Crowchild on 2008-04-03
I would really like to set this up on my laptop but it seems that when I try to modify xorg.conf everything falls apart. 

Basically when I follow the instructions on this howto I end up with a mucked up screen resolution and the touchpad still doesn;t work like I want it to.

This might not be the place to have this conversation so I've started a new thread. 

[http://ubuntuforums.org/showthread.php?p=4645033#post4645033](http://ubuntuforums.org/showthread.php?p=4645033#post4645033)

---

### Post by yskchu on 2008-04-14
For Thinkpad users, you can disable the trackpad with a simple click of the mouse:

System -> Preference -> Mouse

Go to Touchpad tab, uncheck "Enable Touchpad"

PM me if have issues & thinkpad user

---

### Post by ElEdwards on 2008-04-14
I have been trying several different distros (I always come back to Ubuntu, by the way).

I've never liked using my touchpad for tapping, so with every distro I try, I edit **xorg.conf**, adding this line to the end of the "Synaptics Touchpad" section:
```
Option     "MaxTapTime"     "0"
```
This let's me use the touchpad to move my mouse without worrying about accidentally tapping..... and this extra line works whether the "SHMConfig" line is there or not :)

---

### Post by sumanta679 on 2008-04-27
it worked like charm :)
thanks
I added your article in my blog, ofcourse with a link back to your original post :)

---

### Post by Mais on 2008-04-27
> **sumanta679 said:**
> it worked like charm :)
thanks
I added your article in my blog, ofcourse with a link back to your original post :)

Thanks! Can we have a link to your blog?

---

### Post by raghaven.kumar on 2008-04-28
hi guys,
im using gde in ubuntu
do i have to edit in the xorg.conf?

but still i cant see a Synaptics touchpad in it.
Heres my xorg.conf listings.
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


```

Any suggestions ??

---

### Post by twinoatl on 2008-05-02
> **Michl said:**
> What do you do in Hardy Heron where the xorg.conf file is abbreviated and there is not section for the touchpad, even though it works.

I would appreciate an answer to this question too. I have a macbook 4.1. The touchpad works by default with:

1-finger click to left click
2-finger click to middle click
3-finger click to right click (I don't know why 2-finger is not right-click)

I would like to deactivate clicking on the touchpad while I'm typing.

Thank you

---

### Post by Handonam on 2008-05-16
I like the idea of the command to turn off the touchpad temporarily via

syndaemon -i 0.5 -d 

but, i find it a bit annoying when i'm typing and moving the mouse at the same time (on purpose).  Is there a way to distinguish the clicks between using the finger and the palm?  I'm not sure of the pressure commands.

but it would make the most sense because clicking (or even moving) should be based off of how small and condensed the input is (pointy finger) rather than how spread out it is (stubbier palm).

---

### Post by hrsetrdr on 2008-05-17
Thanks so much for the very useful tutorial...this is THE first time typing on this laptop, without everything going screwy!

This laptop does the same thing in Windows(dual boot); I guess I'll have to do more googling to find the solution on that.   ;)


This is so cool; I'm a crappy keyboarder but I'm enjoying this now!

---

### Post by raghaven.kumar on 2008-05-17
> **raghaven.kumar said:**
> hi guys,
im using gde in ubuntu
do i have to edit in the xorg.conf?

but still i cant see a Synaptics touchpad in it.
Heres my xorg.conf listings.

Any suggestions ??
No solns for me??

---

### Post by edmicman on 2008-05-17
> **Handonam said:**
> I like the idea of the command to turn off the touchpad temporarily via

syndaemon -i 0.5 -d 

but, i find it a bit annoying when i'm typing and moving the mouse at the same time (on purpose).  Is there a way to distinguish the clicks between using the finger and the palm?  I'm not sure of the pressure commands.

but it would make the most sense because clicking (or even moving) should be based off of how small and condensed the input is (pointy finger) rather than how spread out it is (stubbier palm).

I'm running into the same issue.  I'm on a Dell 600m, and this howto worked great, and solved my immediate problem of having the cursor move in the middle of writing in a textbox!  Buuuuut, now I'm finding it interferes in some things like you mentioned where I'm purposely wanting to use the keyboard and mouse at the same time.  I.e., in Firefox, I'll hold down ctrl and click on a bunch of links to open them in the background.  There's the lag that I have to account for now, and I have to wait a second before I can continue on.  There's been a couple other places where it's interfered, too.

Maybe shortening the pause would work (can you set it to 0.5?), or would any of the other options that syndaemon offers help?  The suggestion to turn off trackpad tapping altogether sounds interesting...I don't usually tap to click, instead opting for the buttons...but sometimes I do tap to click, too.  

As a recent Ubuntu convert, it does make me wonder how they did it in the trackpad software on Windows.  I don't ever remember having the initial problems with this issue on XP.  Anyway, great job everyone who has helped in this thread!

---

### Post by Handonam on 2008-05-18
> **edmicman said:**
> I'm running into the same issue.  I'm on a Dell 600m, and this howto worked great, and solved my immediate problem of having the cursor move in the middle of writing in a textbox!  Buuuuut, now I'm finding it interferes in some things like you mentioned where I'm purposely wanting to use the keyboard and mouse at the same time.  I.e., in Firefox, I'll hold down ctrl and click on a bunch of links to open them in the background.  There's the lag that I have to account for now, and I have to wait a second before I can continue on.  There's been a couple other places where it's interfered, too.

Maybe shortening the pause would work (can you set it to 0.5?), or would any of the other options that syndaemon offers help?  The suggestion to turn off trackpad tapping altogether sounds interesting...I don't usually tap to click, instead opting for the buttons...but sometimes I do tap to click, too.  

As a recent Ubuntu convert, it does make me wonder how they did it in the trackpad software on Windows.  I don't ever remember having the initial problems with this issue on XP.  Anyway, great job everyone who has helped in this thread!



yea.  i'm hoping someone can help figure this one out.  Would feel so much better to me as a windows --> linux user

---

### Post by ugm6hr on 2008-05-18
> **edmicman said:**
> I.e., in Firefox, I'll hold down ctrl and click on a bunch of links to open them in the background.  There's the lag that I have to account for now, and I have to wait a second before I can continue on.  There's been a couple other places where it's interfered, too.

Maybe shortening the pause would work (can you set it to 0.5?), or would any of the other options that syndaemon offers help?  The suggestion to turn off trackpad tapping altogether sounds interesting...I don't usually tap to click, instead opting for the buttons...but sometimes I do tap to click, too.  


Try this command: [http://ubuntuforums.org/showpost.php?p=3136787&postcount=8](http://ubuntuforums.org/showpost.php?p=3136787&postcount=8)

Ignores all super-key presses (so Ctrl+tap should work), allows movement of touchpad (just turns off tapping), and still allows button clicks.

---

### Post by DantePasquale on 2008-05-18
Hi All,

I have a Jetta Jetbook notebook and I've gone over all the instructions here for disabling or working with the touchpad. 

In my xorg.conf it shows as a synaptics touchpad:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        **Identifier      "Synaptics Touchpad"**
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
```

As you can see I've added the SHMConfig parameter, but none of the synaptics tools connect and all complain about SHMConfig not working:


```
dante@dexter:~/Desktop$ sudo syndaemon -i 1 -d
[sudo] password for dante:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

dante@dexter:~/Desktop$ sudo synclient -h
Can't access shared memory area. SHMConfig disabled?
```

tpconfig looks more promising, but even though I turned off touchpad using tpconfig, it still works:

```
dante@dexter:~/Desktop$ sudo tpconfig -i
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.
```

But when I look at /proc/bus/input/devices, there's no synaptics showing up:
```

dante@dexter:~/Desktop$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=03f0 Product=061d Version=0110
N: Name="HP HP Mouse"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=303

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=event5 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0
```

What do I need to look at? It appears that xorg calls the touchpad a synaptics, but under /proc/bus/input/devices it looks like it's a PS2???
Oh, I do have a HP Wireless USB mouse plugged in at the moment, but have tried to configure w/o having it plugged in.

---

### Post by reacocard on 2008-05-18
> **DantePasquale said:**
> Hi All,

I have a Jetta Jetbook notebook and I've gone over all the instructions here for disabling or working with the touchpad. 

<snip>

What do I need to look at? It appears that xorg calls the touchpad a synaptics, but under /proc/bus/input/devices it looks like it's a PS2???
Oh, I do have a HP Wireless USB mouse plugged in at the moment, but have tried to configure w/o having it plugged in.

Did you restart the computer after adding SHMConfig to xorg.conf? It doesn't take effect until after X restarts.

---

### Post by DantePasquale on 2008-05-19
Hi reacocard,

Yes, I forgot to mention that I tried rebooting and also tried using CTRL-ALT-BS (control alt backspace) which restarts X11. So I'm thinking that either this hardware is misidentified as a Synaptics -- or there's a syntax problem in xorg.conf, but I can't find it.

---

### Post by reacocard on 2008-05-19
> **DantePasquale said:**
> Hi reacocard,

Yes, I forgot to mention that I tried rebooting and also tried using CTRL-ALT-BS (control alt backspace) which restarts X11. So I'm thinking that either this hardware is misidentified as a Synaptics -- or there's a syntax problem in xorg.conf, but I can't find it.

I just looked at your post again, and saw you're running synclient with sudo. That shouldn't be necessary, try it again without the sudo, perhaps that was the problem.

---

### Post by DantePasquale on 2008-05-19
Hi, same results using sudo or not. I thought I'd try sudo in case there was something restricted about accessing the memory, but it didn't matter. Any more ideas?

---

### Post by Blasphemer on 2008-05-23
Thank you. I am on Kubuntu and with a little playing around with Autostart folder I have been able to do it.

:)

---

### Post by suzypeppercorn on 2008-05-28
This tutorial is amazing!! Thank you so much

---

### Post by raequin on 2008-05-31
I have been researching this problem since installing Hardy.  I have done all the things suggested regarding

xorg.conf

syndaemon

synclient

and System -> Preference -> Mouse, Go to Touchpad tab, uncheck "Enable Touchpad"

None of this has any effect on my touchpad, much less making it work better while typing (also, vertical scrolling does not work even though in xorg.conf it says it's enabled).

The only software that modifies the touchpad behavior is Mousetweaks pointer capture.  That is sort of inconvenient, though, to have to take my hands from the home position.

Any ideas?  I would love it if I could get syndaemon working (the following has no effect, even though it shows "Disable").

```
$ syndaemon -i 3 -t -K
eeDisable
Enable

```

Here is part of my xorg.conf, just for reference.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"VertEdgeScroll"	"1"
	Option		"SHMConfig"		"on"
#	Option		"MaxTapTime"		"0"
EndSection

```

This is the thread I started for this issue: [http://ubuntuforums.org/showthread.php?t=812128](http://ubuntuforums.org/showthread.php?t=812128).  I'll be looking back here, though, since this thread has so much activity.

---

### Post by zombrax on 2008-06-09
many thanks my friend for this fantastic tutorial :)

---

### Post by Handonam on 2008-06-17
i wish someone could make a little script so that the mouse doesn't "click" so often, too

aside from distinguishing the pressure of the stubbier palm and the pointier finger, i think there should be a way to distinguish when the pointer is moving compared to a quick tap to click.

This is what i mean:  I don't have a very sensitive touchpad.  I often do short burst of strokes so that i can get across the screen faster.  but the problem with this in ubuntu is that it registers as a tap.   I went over to windows to compare how the Synaptics driver works there, and it doesn't tap whenever the pointer position is not in the same spot.    I have to tap in the same spot for it to register a click.  This is something i don't think the Synaptics driver in ubuntu does, which really annoys me :(

---

### Post by scotcella on 2008-06-23
This is excellent,

took me ages to get it going especially step 2.D 

After alot of difficulty (white spaces error kept coming up), I thought I would have a go with typing in *syndaemon -i 1 -d* in both "Name" and "Command". It worked right away.

Now my only question...   with my touch pad being disabled (YAY!), as soon as I finish typing and start using the touchpad, theres a delay of about 2 seconds. 
Can I get the delay time a bit faster?

Thanks heaps for this how to tutorial.

---

### Post by P4man on 2008-06-30
I think its better to use this:

syndaemon -i 1 -d **-t**

The -t makes sure the touchpad still works while typing, except you can't tap (click) for 1 second (or whatever you set it at) so the cursor can't jump either. This is slightly less annoying than the 1 second delay. With -t you can already position the mouse pointer, and it will probably take 1 second between typing and being ready to click, so its almost unnoticeable.

Still I'm curious why we need this workaround at all. It seems many (most?) Ubuntu users with a synaptic touchpad have issues with jumping cursor even when not using the touchpad. When I pay careful attention not to touch it, the cursor still jumps. This problem doesnt exist in Windows.

I tried various other fixes, like adding i8042.nomux=1 to the kernel parameters, I tried fiddling in xorg.conf by increasing FingerLow sensitivity, but none of it really cures it. This workaround makes it bearable but its hardly an ideal solution as I do pause for a second now and then between sentences  :)

---

### Post by P4man on 2008-06-30
> **scotcella said:**
> 
Can I get the delay time a bit faster?



Yes. the "1" is the delay (in seconds). You can set it to 0.5 if you prefer. But read my post above, adding -t is probably an even better solution.

---

### Post by edmicman on 2008-06-30
I did "syndaemon -i 1 -d -t -K" and that seems to work pretty well.  I agree, though, that this is a simple problem that should be fixed by default!

---

### Post by Paresh on 2008-07-09
Thanks

Simple and effective fix.

I have also tried this on my friend's laptop.  He is partially sighted and cannot tell when the cursor has moved due to an inadvertent touch.  This has helped him muchly after tweaking the delay to his tastes.
=D>

---

### Post by ccl4 on 2008-07-14
hello i can not find the "touchpad section". please help
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

---

### Post by sergiom99 on 2008-07-14
Thanks dude, nice tutorial.
I would give you a star, but somehow theyre not available in this thread.

---

### Post by raghaven.kumar on 2008-07-18
> **ccl4 said:**
> hello i can not find the "touchpad section". please help

dude, im also having the same config but no one seems to know the solution for it.
:-k

---

### Post by b:z on 2008-08-15
> **ariel said:**
> This method was more convenient for me:

To disable the touchpad:

```
synclient TouchpadOff=1
```

To enable the touchpad:

```
synclient TouchpadOff=0
```


And: you can put each on a launcher in your desktop. The result works pretty neat in my case. If you are at your desk with a mouse, or typing, just disable the touchpad.
That's so cool. It really helps me.

;)

---

### Post by zzHanks on 2008-08-28
Thank you. 

No more minimizing and typing in the wrong window :)

---

### Post by johnehowe on 2008-09-01
Thank you... I needed this fix!!!

---

### Post by wladicus on 2008-09-09
Hi reacocard:  I tried all of what you said but it is not working for me.  I am running Kubuntu and but my laptop's touchpad is NOT a Synaptics touchpad. I wonder if that is why this does not work for me?
I created file  syndaemon.sh  in the Autostart folder and rebooted but it is not working for me. I put the following two code lines into the file:
-----------------------
File: syndaemon.sh
-----------------------
#!/bin/sh
syndaemon -i 5 -d
-----------------------
I also did a chmod a+x syndaemon.sh to make it executable.  I really am a novice at this...have been using Linux for about 2 weeks now, so I am guessing at most of this.
Did I write the file correctly?  Is it NOT working because the laptop does not have a Synaptics touchpad?
walt

---

### Post by reacocard on 2008-09-09
> **wladicus said:**
> Hi reacocard:  I tried all of what you said but it is not working for me.  I am running Kubuntu and but my laptop's touchpad is NOT a Synaptics touchpad. I wonder if that is why this does not work for me?
I created file  syndaemon.sh  in the Autostart folder and rebooted but it is not working for me. I put the following two code lines into the file:
-----------------------
File: syndaemon.sh
-----------------------
#!/bin/sh
syndaemon -i 5 -d
-----------------------
I also did a chmod a+x syndaemon.sh to make it executable.  I really am a novice at this...have been using Linux for about 2 weeks now, so I am guessing at most of this.
Did I write the file correctly?  Is it NOT working because the laptop does not have a Synaptics touchpad?
walt

Did you enable SHMConfig? without that syndaemon can't do anything.

---

### Post by wladicus on 2008-09-09
Hi reaocard,
> **reacocard said:**
> Did you enable SHMConfig? without that syndaemon can't do anything.
Yes, I did enable SHMConfig with   [Option  "SHMConfig"   "on"]   and still no go.  :(
[COLOR="Red"][_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/[/COLOR]
[COLOR="Blue"]walt
St. Thomas, Ontario = 42.77°N, 81.11°W =
RASC: Royal Astronomical Society of Canada[/COLOR]

---

### Post by wladicus on 2008-09-09
If anybody knows what these exerpts from the Xorg.O.log file mean in terms of solving the touchpad annoyance then please help.  I noticed that the log reports that my laptop has no Synaptics touchpad.
[ATTACH]84723[/ATTACH]
[COLOR="Red"][_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/_/[/COLOR]
[COLOR="Blue"]walt
St. Thomas, Ontario = 42.77°N, 81.11°W =
RASC: Royal Astronomical Society of Canada[/COLOR]

---

### Post by Mariane on 2008-09-11
Thanks to all of you. I was seriously considering cellotaping all over the touchpad because it was driving me crazy... 

One thing which would be great would be if there was a way to configure the laptop so that plugging in a mouse automatically disables the touchpad completely. Anyone knows a way to do this, please? 

synclient TouchpadOff=1
and
synclient TouchpadOff=0

Are a great substitude, though, it's really nice to be able to control the thing even if I have to type these commands each time. 

Mariane

---

### Post by wladicus on 2008-09-11
> **Mariane said:**
> 
synclient TouchpadOff=1
and
synclient TouchpadOff=0
Are a great substitute...
Mariane

Thank you Mariane for the contribution, but as I have said many times in many threads, I have already tried all the basic suggestions, including the one you just mentioned and about 3 or 4 different variations of that including an automated file that should have taken care of everything on boot-up.  Alas, nothing seems to work!  The Kubuntu development team did not make it on this one. I hope they improve on development of these kind of 'basics'.
Thank you, :)
walt

---

### Post by wladicus on 2008-09-15
From a terminal enter the following code:
To disable the Touchpad -
```
sudo rmmod psmouse
```
To re-enable a disabled Touchpad -
```
sudo modprobe psmouse
```
I suppose this can be automated in a file somehow or even attached to a function key probably if someone has the knowhow.
I received this solution from the following link:
[http://ubuntuforums.org/showpost.php?p=5694509&postcount=13](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)

I managed to work out a detailed HOW TO for setting up **a shortcut key version of this** can be found in the last post at the following link:
>    [http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html](http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html)  

---

### Post by bigb_thedestroyer on 2008-09-16
Great tutorial, I used to do this on my older Dell laptop.  Now, I have a FN + <Function> key combo I can press to turn off my touchpad.  Its on my Acer Aspire.

Bb

---

### Post by roberthr on 2008-09-29
Is there a way to achieve this in Intrepid Ibex?
You can't put SHMConfig in xorg.conf, since it doesn't have any entries. You can't use gsynaptics or syndaemon either because it says you don't have shared memory turned on. Why can't they fix this once and for all with simple gui?

---

### Post by Sponzenbroekske on 2008-10-28
intrepid 64bit laptop

This is my xorg.conf, as you see, i might have a problem, cuz I can't see a section synaptic, I search this thread but I didnt get a real answer
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

---

### Post by Sponzenbroekske on 2008-10-31
Bump

---

### Post by sizzam on 2008-10-31
*CORRECTION*
Here is how I got SHMConfig enabled on Intrepid Ibex 8.10

Edit this file:
```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

Find the section that starts with:
```
<match key="info.product" contains="Synaptics TouchPad">
```

And add this line to that section before </match>:
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
```

So, my file ends up looking like this:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

After I rebooted, SHMConfig was enabled.

---

### Post by loomsen on 2008-10-31
Add sth like this:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"		"True"
	Option		"Device"				"/dev/psaux"
	Option		"Protocol"			"auto-dev"
	Option		"HorizTwoFigerScroll"	"True"
	Option		"VertTwoFingerScroll"	"True"
        Option          "SHMConfig"             "on"
EndSection

```


Adjust it to your needs... Google for xorg.conf synaptic..

Heres a list of possible Options. If you want to add one, simply append it to your section as above...
```

Section "InputDevice"
	Identifier	"touchpad"
	Driver		"synaptics"
	# general settings
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"on"
	Option		"Device"		"/dev/psaux"
	#
	# Synaptics options
	#
	# "auto-dev" (automatic, default), "psaux" (raw) or
	# "event" (linux 2.5 kernel events)
	Option		"Protocol"		"auto-dev"
	#
	# switch on/off shared memory for configuration
	Option		"SHMConfig"		"on"
	#
	# coordinates for left/right/bottom/top `virtual' edge
	Option		"LeftEdge"		"1900"
	Option		"RightEdge"		"5400"
	Option		"BottomEdge"		"4000"
	Option		"TopEdge"		"1900"
	#
	# When finger pressure drops below this value, the
	# driver counts it as a release.
	Option		"FingerLow"		"25"
	#
	# When finger pressure goes above this value, the
	# driver counts it as a touch.
	Option		"FingerHigh"		"30"
	#
	# max. time (in milliseconds) for detecting a tap
	Option		"MaxTapTime"		"180"
	#
	# max. movement of the finger for detecting a tap
	Option		"MaxTapMove"		"220"
	#
	# max. time (in milliseconds) for detecting a double tap
	#Option		"MaxDoubleTapTime"	"180"
	#
	# the duration of the mouse click generated by tapping
	#Option		"ClickTime"		"100"
	#
	# Makes the driver react faster to a single tap, but
	# also makes double clicks caused by double tapping slower.
	#Option		"FastTaps"		"off"
	#
	# max time (in milliseconds) for middle button emulation.
	Option		"EmulateMidButtonTime"	"20"
	#
	# move distance of the finger for a scroll event
	Option		"VertScrollDelta"	"100"
	#
	# move distance of the finger for a scroll event
	Option		"HorizScrollDelta"	"100"
	#
	# min./max./acceleration Speed factor
	Option		"MinSpeed"		"0.02"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0010"
	#
	# finger pressure at which minimum edge motion speed is set
	#Option		"EdgeMotionMinZ"	"30"
	#
	# finger pressure at which maximum edge motion speed is set
	#Option		"EdgeMotionMaxZ"	"160"
	#
	# slowest setting for edge motion speed
	#Option		"EdgeMotionMinSpeed"	"1"
	#
	# fastest setting for edge motion speed
	#Option		"EdgeMotionMaxSpeed"	"400"
	#
	# If on, edge motion is also used for normal movements,
	# if off, egde motion is used only when dragging
	#Option		"EdgeMotionUseAlways"	"off"
	#
	# If on, the up/down buttons generate button 4/5 events.
	# If off, the up button generates a double click and
	# the down button generates a button 2 event.
	Option		"UpDownScrolling"	"off"
	#
	# Switch off the touchpad. Valid values are:
	# 0 : Touchpad is enabled
	# 1 : Touchpad is switched off
	# 2 : Only tapping is switched off
	#Option		"TouchpadOff"		"0"
	#
	# switch on/off guest mouse (often a stick)
	#Option		"GuestMouseOff"		"off"
	#
	# If off, a tap and drag gesture ends when you release
	# the finger. If on, the gesture is active until you
	# tap a second time.
	Option		"LockedDrags"		"off"
	#
	# Mouse button actions for corners
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
	Option		"RTCornerButton"	"1"
	Option		"RBCornerButton"	"2"
	Option		"LTCornerButton"	"3"
	Option		"LBCornerButton"	"0"
	#
	# Which mouse button is reported on a non-corner n-finger tap
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"2"
	Option		"TapButton3"		"3"
	#
	# If on, circular scrolling is used
	Option		"CircularScrolling"	"1"
	#
	# Move angle (radians) of finger to generate a scroll event
	#Option		"CircScrollDelta"	"0.1"
	#
	# Trigger region on the touchpad to start circular scrolling
	# 0=All Edges, 1=Top Edge, 2=Top Right Corner, 3=Right Edge,
	# 4=Bottom Right Corner, 5=Bottom Edge, 6=Bottom Left Corner,
	# 7=Left Edge, 8=Top Left Corner
	Option		"CircScrollTrigger"	"3"
	#
	# Instead of being a rectangle, the edge is the ellipse
	# enclosed by the Left/Right/Top/BottomEdge parameters.
	# For circular touchpads.
	Option		"CircularPad"		"off"
	#
	# If palm detection should be enabled
	Option		"PalmDetect"		"on"
	#
	# Minimum width at which touch is considered a palm
	#Option		"PalmMinWidth"		"10"
	#
	# Minimum finger pressure at which touch is considered a palm
	#Option		"PalmMinZ"		"200"
	#
	# Coasting threshold scrolling speed. 0 disables coasting.
	#Option		"CoastingSpeed"		"0"
EndSection
```

---

### Post by Sponzenbroekske on 2008-11-01
> **sizzam said:**
> *CORRECTION*
Here is how I got SHMConfig enabled on Intrepid Ibex 8.10

Edit this file:
```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```


This didnt work :(, it did nothing at all, up to the next tip :)

---

### Post by Arcnsparc on 2008-11-02
Yeah I am trying to adjust this file: 
 /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

so that the entire touchpad on my laptop is the edge (i like the entire touchpad to scroll).  On Hardy I enabled SMHconfig and then ran this at start up:
```
synclient rightedge=0
```
that made my entire touchpad a scrolling device, but not i cant figure out how to do it with Intrepid....  Any advice?

---

### Post by zoniq on 2008-11-06
> **sizzam said:**
> *CORRECTION*
Here is how I got SHMConfig enabled on Intrepid Ibex 8.10

Edit this file:
```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```


Great. That worked for me. Even without rebooting. Although I think the <?xml ...> tag is wrong in there:
```
[COLOR="Red"]<?xml version="1.0" encoding="ISO-8859-1"?>[/COLOR]
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
```



Thanks!

---

### Post by chalewa on 2008-11-09
this worked better for me...
```

sudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
```

---

### Post by muadnu on 2008-11-10
Nothing of the above works for me, I still get
```
$ syndaemon -i 1 -d -t 
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

---

### Post by muadnu on 2008-11-11
Ok, I think my problem is that SHM is not working, even though I did turn it on (both in my xorg.conf file and by adding the file /etc/hal/fdi/policy/shmconfig.fdi as in [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig"). If it was working, the above link says that running
```
xinput list
```
should show the position of the cursor being updated when I move it using the touchpad, which doesn't happen.

I know that synaptics should work without SHM enabled now, but it doesn't in my case...

---

### Post by binbash on 2008-11-12
> **sizzam said:**
> *CORRECTION*
Here is how I got SHMConfig enabled on Intrepid Ibex 8.10

Edit this file:
```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

Find the section that starts with:
```
<match key="info.product" contains="Synaptics TouchPad">
```

And add this line to that section before </match>:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
```

So, my file ends up looking like this:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

After I rebooted, SHMConfig was enabled.

Thanks for the trick, it is working fine here ;)

---

### Post by monkeys on 2008-11-16
I'm trying to remod my rightedge value so that my vertical scroll will stop coming -half-way- into my touchpad.

I've tried to alter the values in 11-x11-synaptics.fdi but still but it doesn't seem to be working. As well, I'm not sure exactly how the values we once put in the xorg.conf match up with the values in 11-x11-synaptics.fdi.

The exact line I'm looking at...
```
<merge key="input.x11_options.RightEdge" type="string">1500</merge>
```

---

### Post by David Cartwright on 2008-11-17
Ok, albeit on Fedora 9, but using the original template given by sizzam, I added the line to the similar file on Fedora as per the example.

After rebooting it still didn't work.

I then checked my Xorg log files for items related to touch, e.g.

cat Xorg.0.log | grep touch

and this showed the hardware on my Acer notebook was AlpsPS/2.

I therefore moved the SHMConfig line under the AlpsPS/2 section. Rebooted. And now it works and I can run **synclient touchpadoff=1** to disable, and **synclient touchpadoff=0** to enable.

I imagine it will be the same on the latest Ubuntu.

---

### Post by muadnu on 2008-11-20
I got it working by using the binary provided [here]("http://people.ubuntuwire.com/~fujitsu/syndaemon") instead of the one coming in Intrepid. But I'm still seeing some weird things, though I'm not sure they're related to this. The most annoying is that I cannot use scrolling on my touchpad anymore. I have it set up both through gsynaptics and in my xorg.conf, but nothing. It did work before in Intrepid, but somehow it doesn't now (killing syndaemon doesn't help). Also, today while I'm using the touchpad I've noted that sometimes it takes a couple of seconds to respond: when I move it it stays still until 1 or 2 seconds and then it starts moving.


The other thing is that it seems to me that setting things up through gsynaptics doesn't make any difference for my touchpad, it simply doesn't change anything...

---

### Post by DantePasquale on 2008-11-22
Hi Everyone.

I've tried to use the various methods in this thread and in [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) to no avail. I'm wondering if I don't have a synaptics touchpad, but some other touchpad?

Here's xinput -l :

```
xinput list
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"ImPS/2 Logitech Wheel Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HP HP Mouse"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
```

And dmesg doesn't mention "synaptics" or "touchpad" but has the following:

```
dmesg | grep -i mouse
[    1.730420] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.774775] mice: PS/2 mouse device common for all mice
[   15.542561] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[  494.024266] input: HP HP Mouse as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input9
[  494.040524] input,hidraw0: USB HID v1.10 Mouse [HP HP Mouse] on usb-0000:00:1d.0-1
```

There's a key on this laptop that looks like it enables or disables a USB mouse, but it's not mapped to anything and I wouldn't know what to map it to:
```

Nov 22 17:05:26 dexter-laptop kernel: [  899.336323] atkbd.c: Unknown key pressed (translated set 2, code 0xf9 on isa0060/serio0).
Nov 22 17:05:26 dexter-laptop kernel: [  899.336338] atkbd.c: Use 'setkeycodes e079 <keycode>' to make it known.
Nov 22 17:05:26 dexter-laptop kernel: [  899.577871] atkbd.c: Unknown key released (translated set 2, code 0xf9 on isa0060/serio0).
Nov 22 17:05:26 dexter-laptop kernel: [  899.577889] atkbd.c: Use 'setkeycodes e079 <keycode>' to make it known.
```

Ideas anyone?

---

### Post by havok1977 on 2008-11-25
Have tried every recommendation to get this to work on my Sony Vaio VGS-170F.

Heres my xinput list output:

```

"Virtual core keyboard" id=0    [XKeyboard]
        Num_keys is 248                    
        Min_keycode is 8                   
        Max_keycode is 255                 
"Virtual core pointer"  id=1    [XPointer] 
        Num_buttons is 32                  
        Num_axes is 2                      
        Mode is Relative                   
        Motion_buffer is 256               
        Axis 0 :                           
                Min_value is 0             
                Max_value is -1            
                Resolution is 0            
        Axis 1 :                           
                Min_value is 0             
                Max_value is -1            
                Resolution is 0            
"Generic Keyboard"      id=2    [XExtensionKeyboard]
        Num_keys is 248                             
        Min_keycode is 8                            
        Max_keycode is 255                          
"Configured Mouse"      id=3    [XExtensionPointer] 
        Num_buttons is 9                            
        Num_axes is 2                               
        Mode is Relative                            
        Motion_buffer is 256                        
        Axis 0 :                                    
                Min_value is -1                     
                Max_value is -1                     
                Resolution is 1                     
        Axis 1 :                                    
                Min_value is -1                     
                Max_value is -1                     
                Resolution is 1                     
"Synaptics Touchpad"    id=4    [XExtensionPointer] 
        Num_buttons is 12                           
        Num_axes is 2                               
        Mode is Relative                            
        Motion_buffer is 256                        
        Axis 0 :                                    
                Min_value is 0                      
                Max_value is -1                     
                Resolution is 1                     
        Axis 1 :                                    
                Min_value is 0                      
                Max_value is -1                     
                Resolution is 1                     
"AlpsPS/2 ALPS GlidePoint"      id=5    [XExtensionPointer]
        Num_buttons is 12                                  
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is 0
                Max_value is -1
                Resolution is 1
"PS/2 Mouse"    id=6    [XExtensionPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Sony Vaio Keys"        id=7    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"AT Translated Set 2 keyboard"  id=8    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255

```

And after modifying the hal xml database files as specified and editing my xorg.conf file to get this to work to no avail.

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "on"
EndSection

```

Suggestions anyone?

---

### Post by kronictokr on 2008-11-25
configure your "SHMConfig" above your scroll option
then place the whole section above the mouse "InputDevice"
as mine is bellow, this fixed my srolling and all my touchpad related problems
also you can try changing your scroll line to match mine, that was another change i added


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option          "SHMConfig"             "on"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

---

### Post by Tiler on 2008-12-03
I only checked first and last few pages to see if anyone else has run into this but for me to get it to work, I had to do the following:


> Option 		"SHMConfig" 		**[COLOR="Red"]"true"[/COLOR]**

[Was discussing it here.]("http://ubuntuforums.org/showthread.php?t=874604&highlight=madness+touchpad")


Again, please excuse if this was discussed already in this thread.

Hardy Ubuntu-eee 1000

---

### Post by sojusnik on 2008-12-03
my xorg.conf:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "SHMConfig" "true"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection


Still doesn't work:

xxx:~$ syndaemon -i 1 -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

---

### Post by james.wilde on 2008-12-05
> **roberthr said:**
> Is there a way to achieve this in Intrepid Ibex?
You can't put SHMConfig in xorg.conf, since it doesn't have any entries. You can't use gsynaptics or syndaemon either because it says you don't have shared memory turned on. Why can't they fix this once and for all with simple gui?

The method described here:

[http://forums.techguy.org/unix-linux...d-kibuntu.html](http://forums.techguy.org/unix-linux...d-kibuntu.html)

works for me in Ibex.  Admittedly I haven't bothered to make it a key combination, but his script 2 works for me and toggles the synaptic pad.  I put it on the menu bar as a button.  I always have a usb mouse attached, otherwise it would be very good to make it a key combo.

BTW, I found that I had to make the script file in /usr/bin (which I called tp) mod 7755 and make sure the owner is root.  Having made the owner root (originally a user) it would probably do to have mod 4755 but I haven't experimented.

//James

---

### Post by james.wilde on 2008-12-05
> **wladicus said:**
> I managed to work out a detailed HOW TO for setting up **a shortcut key version of this** can be found in the last post at the following link:

[http://forums.techguy.org/unix-linux...d-kibuntu.html](http://forums.techguy.org/unix-linux...d-kibuntu.html)

First a big thanks to wladicus for this.

His link points to a couple of scripts that one can use in a terminal window, and goes on to convert these to a key combination.  However wladicus is using kubuntu and I'm using gnome.  Have not found any way to create a key combination which will work in gnome.  Anyone have a pointer please?

//James

---

### Post by kyle.p on 2008-12-17
The tutorial is great! However after messing around with this for a couple hours and still having issues getting syndaemon to actually start up, the simplest solution I found to all of this was to install a program called "Touchfreeze" from Synaptic.  A search of "touchpad" gave me this. I am just regretting not searching for that earlier!  It disables your touchpad clicks and scrolling after typing and lets you choose the delay time. It also lets you disable your touchpad completely.

I just added it as a startup program under "Sessions" and this works quite slick.  

I suggest at least giving it a try to those who are having issues getting this working or at least want a pretty GUI to go with it :)

-kyle

---

### Post by KC1117 on 2008-12-30
LOL!  I didn't even realize it was my touchpad causing the cursor to jump around while I was typing until I came across this How To.  I can't wait to try it.  Thank you!

---

### Post by Tanikaze on 2009-01-06
I am running standard eeeBuntu 8.10 on an Asus Eee PC(900ha if it matters). I have no "Synaptics Touchpad" entry in my xorg.conf and the new ideas in the past two/three pages haven't done anything to enable SHMConfig for me. Does anyone have any experience with this particular netbook, or any ideas for me? I have a little mouse that I use sometimes, so I'm thinking I might just disable the touchpad altogether at this point.

---

### Post by bixejo on 2009-01-06
Just a few things to add:

I realized that **syndaemon** always turns on the touchpad after typing whatever though I had disabled it. So I had to write the following scripts to enable/disable touchpad and using **syndaemon** while it's enabled:

Touchpad enabling script:

```
#!/bin/sh
synclient TouchpadOff=0
syndaemon -i 1 -d

```Touchpad disabling script:

```
#!/bin/sh
killall syndaemon
synclient TouchpadOff=1

```I've got two shortcuts associated to these scripts. I've thought also in writing just one script that checks the output of:

```
synclient -l | grep TouchpadOff

```, and then just toggle its status accordingly. Maybe I'll do it later. Time is gold, and I'm poor :)

Regards,

* Edit: Ok, here's the single script to toggle touchpad status:*

Script **toggle_touchpad**:
```
#!/bin/bash
#
if [[ $( ps aux | grep syndaemon | grep -v "grep syndaemon" | wc -l ) == "0" ]]; then
    # syndaemon is not running, enable touchpad and launch syndaemon
    synclient TouchpadOff=0
    syndaemon -i 1 -d ;
else
    # syndaemon is running, kill syndaemon and disable touchpad
    killall syndaemon
    synclient TouchpadOff=1 ;
fi
```NOTES:

[LIST=1]
[*]It's based on the existence of the syndaemon process rather than on the current touchpad status (TouchpadOff=0|1) because syndaemon process temporally disables it while typing, so it might happen that this status were confusing.
[*]If syndaemon is not lauched at session startup, the first time this script is invoked it would just launch syndaemon rather than disabling the touchpad.
[*]I've associated this script to the shortcut that theoretically should do this job, and that is not working on Ubuntu as it is in XP.
[*]It probably could be done much better, so feel free to improve it :D
[/LIST]
Regards,

---

### Post by raj9786 on 2009-01-07
I am using a Dell 1520 with Ibex 8.10 running. When I look at my xorg.conf file, I see no "Input Devices" section. Is that normal? How can I use this Howto without that section? Thanks.

---

### Post by beatrice on 2009-01-11
That jumpy cursor drives me mad! :KS But I also don't have a "Input device" section. Touchpad is not even mentioned. :confused:


That's my xorg.conf file
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection 
```


I tried Touchfreeze and so far it seems to be doing okay. The cursor still jumps occasionally, but not as much as it used to.

---

### Post by ChaKy on 2009-01-11
> **raj9786 said:**
> I am using a Dell 1520 with Ibex 8.10 running. When I look at my xorg.conf file, I see no "Input Devices" section. Is that normal? How can I use this Howto without that section? Thanks.

I also have Dell Inspiron 1525, but you do not have to do this in xorg.conf. Just go to system > preferences > mouse, there is a third tab name "Touchpad", than just turn off the touchpad. This is what I did and it works.
I hope this helps :)

---

### Post by bixejo on 2009-01-11
> **ChaKy said:**
> I also have Dell Inspiron 1525, but you do not have to do this in xorg.conf. Just go to system > preferences > mouse, there is a third tab name "Touchpad", than just turn off the touchpad. This is what I did and it works.
I hope this helps :)
That's indeed the best way to enable/disable the touchpad. The only drawback I find in this is that if you disable it, forget to enable it before shutting down and next time you boot your laptop you don't have an external mouse... You may run into problems to enable it by using just the keyboard.

---

### Post by ChaKy on 2009-01-12
> **bixejo said:**
> That's indeed the best way to enable/disable the touchpad. The only drawback I find in this is that if you disable it, forget to enable it before shutting down and next time you boot your laptop you don't have an external mouse... You may run into problems to enable it by using just the keyboard.

Actually, my external mouse works after boot and touchpad is disabled. I have wireless Logitech v450 mouse.

---

### Post by bixejo on 2009-01-12
> **ChaKy said:**
> Actually, my external mouse works after boot and touchpad is disabled. I have wireless Logitech v450 mouse.
I believe that either I did not explain it correctly or you did not read carefully my post.

I meant that if you boot your laptop with your touchpad disabled **and do not have an external mouse available** at that time, you may run into problems.

If you always carry on an external mouse with your laptop, this is nothing to worry about for you.

---

### Post by ChaKy on 2009-01-12
> **bixejo said:**
> 
I meant that if you boot your laptop with your touchpad disabled **and do not have an external mouse available** at that time, you may run into problems.


You are right, sorry, I wasn't reading your post correctly.

> 
If you always carry on an external mouse with your laptop, this is nothing to worry about for you.

Yes, I do carry my wireless mouse always in my bag.

---

### Post by raj9786 on 2009-01-12
> **ChaKy said:**
> I also have Dell Inspiron 1525, but you do not have to do this in xorg.conf. Just go to system > preferences > mouse, there is a third tab name "Touchpad", than just turn off the touchpad. This is what I did and it works.
I hope this helps :)


Why does my xorg.conf not have this section? Is that abnormal? The disable/enable touchpad does not seem like a very elegant nor practical solution to the problem. Why does the touchpad have these problems in ubuntu but not in Windows?

---

### Post by ugm6hr on 2009-01-12
> **raj9786 said:**
> Why does my xorg.conf not have this section? Is that abnormal? The disable/enable touchpad does not seem like a very elegant nor practical solution to the problem. Why does the touchpad have these problems in ubuntu but not in Windows?
[B]
If you are using Hardy (8.04):[/B]

You can add this section to xorg.conf - the SHMConfig line is necessary.

The latest xorg does not require so much manual configuration, so xorg.conf is much shorter than it used to be.

Presumably, the default sensitivity of the Touchpad in Linux is greater than that in Windows.  My touchpad is annoyingly slow in Windows, but much better in Linux.

You can use synclient to check what "pressure" you normally apply.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
EndSection

```
[B]
If you are using Intrepid (8.10):[/B]

Use this guide to enable SHMConfig: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)
Then the syndaemon will work as described.

---

### Post by bixejo on 2009-01-15
> **raj9786 said:**
> Why does my xorg.conf not have this section? Is that abnormal? The disable/enable touchpad does not seem like a very elegant nor practical solution to the problem. Why does the touchpad have these problems in ubuntu but not in Windows?
In fact, you may tweak touchpad settings to the ones that make you feel more comfortable.

After following ugm6hr instructions to make touchpad accessible from xserver-xorg-input-synaptics package stuff, you may have a look at all touchpad options you may configure with the following command:

```

synclient -l
```All those parameters may be adjusted as convenience by using synclient too. When you find the ones you like, you may add one entry in "Systems -> Preferences -> Sessions" to launch synclient to set these options any time you log in (probably it can be done in a more elegant way, but I found this one that works great and did not take the time to research any more.)

Currently I get the following line executed any time I log in:

```

synclient TouchpadOff=0 MaxSpeed=0.4 AccelFactor=0.015 MinSpeed=0.05
```Hope this helps,

---

### Post by Zumbs on 2009-01-18
Fortunately that is pretty easy (at least on my machine):

1) Ctrl+F1 opens Applications in the toolbar.
2) Use arrows to go to System->Preferences->Mouse.
3) Use arrows to browse the tabs to the Touchpad tab.
4) Use the down-arrow to go to the "Enable Touchpad" checkbox and press return.
5) Use the down-arrow to get to the "Close"  and press return.

---

### Post by keishia.tee on 2009-01-24
Hi,
I enabled SHMconfig (I think) using the instructions here:  
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig) 

Then I installed Touchfreeze, which appears to work: 

```
typing delay is 500ms
SynDaemon::Syndaemon

start typing
Can't access shared memory area. SHMConfig disabled?
stop typing
Can't access shared memory area. SHMConfig disabled?
```

I don't get why SHMConfig is disabled though, because I followed the instructions! 

Any suggestions would be great!

Thanks

---

### Post by Zebro on 2009-04-16
> 
xxx:~$ syndaemon -i 1 -d
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

I got exactely the same error. I found a clue in this post [(click me)]("http://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing").
The key is to start the syndaemon with the additional option -S, e.g.,
[INDENT]syndaemon -i 1 -d -t -S[/INDENT]
This worked for me!

Good luck,

Zebro

---

### Post by infamousnation on 2009-04-16
how about a working fix for 8.10

---

### Post by infamousnation on 2009-04-16
> **ugm6hr said:**
> [B]

If you are using Intrepid (8.10):[/B]

Use this guide to enable SHMConfig: [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)
Then the syndaemon will work as described.

no it does not work

---

### Post by schlort on 2009-04-24
I skimmed through here and see the same questions over and over. Hopefully this will clear things up.  To enable SHMConfig on Intrepid and Jaunty, the following is correct:

Use your preferred text editor (as root) to edit /etc/hal/fdi/policy/shmconfig.fdi
(i.e. sudo nano /etc/hal/fdi/policy/shmconfig.fdi )
It should contain --
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>

```


I use amd64 and the syndaemon will never start.  The latest attempt on Jaunty failed with the error:
> X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

To remedy this, install the fixed synaptics driver from William Grant's PPA repo.  

For Intrepid (8.10):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=0.15.2-0ubuntu7~wgrant3
```

For Jaunty (9.04):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=1.1.0-0ppa2~wgrant3
```

---

### Post by mxboy15u on 2009-04-24
I am getting an error that says the vim is not a valid command. What am I doing wrong?

---

### Post by sgosnell on 2009-04-24
Replace it with gedit, nano, or whatever your favorite text editor may be.

---

### Post by schlort on 2009-04-24
woops, i'll edit to make that more clear.. just habit i guess.

---

### Post by johnnylavah on 2009-04-26
> **Mais said:**
> [COLOR=Black]**Purpose: **For many of us, our laptop touchpads get in the way of our typing quite often and can actually cause us to highlight or minimize things we didn't intend. So, this will help to alleviate that by making a small delay in the response of the touchpad after typing.

NOTE: Please read this guide entirely before attempting to do it. There is a section where you must restart X and thus close down your internet browser. The best way to do this would be to print this guide! I hope this works as well for you as it has for me!

[B]Procedure:
[/B]_1. Turn on SHMCONFIG_
  A. Open a Terminal. Applications -> Accessories -> Terminal[/COLOR]
[COLOR=Black]   B. Type *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup*
[/COLOR][LEFT][COLOR=Black]   C. Type *gksudo gedit /etc/X11/xorg.conf* Enter your password if it prompts  you.
[/COLOR][IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16863&d=1159952582[/IMG]
*Note: The second command in the picture is typed wrong. Please see C.*
[/LEFT]
[COLOR=Black]
D. Search for a section that looks like this:
      [/COLOR][INDENT][COLOR=Black]*Section "InputDevice"*[/COLOR]
[COLOR=Black]*                   Identifier    "Synaptics Touchpad"*[/COLOR]
[COLOR=Black]*                   ...*[/COLOR]
[COLOR=Black]*       End Section*[/COLOR] [/INDENT][COLOR=Black]   E. Add a line above the *End Section* line and put this into it:
[/COLOR][INDENT][COLOR=Black][I]Option        "SHMConfig"        "on"
[/I][/COLOR][/INDENT][COLOR=Black]*[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16864&stc=1&d=1159952821[/IMG]*[/COLOR][COLOR=Black] [COLOR=DarkRed]  
[COLOR=Black]F. Save the file and close gedit and the terminal window[/COLOR]
[/COLOR][/COLOR][COLOR=Black][COLOR=DarkRed]G. Write these commands down just in case this screws up your window system: *sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf *and *sudo killall gdm *and [/COLOR]*[COLOR=DarkRed]sudo gdm[/COLOR]*[/COLOR][COLOR=Black]
H. This next step will restart your window system, so save any work and close any open applications. Press: Ctrl-Alt-Backspace. This should take you back to your login screen. If it does not, press Ctrl-Alt-F1 and login at the terminal window. After logging in, type the commands that you wrote down from step F in order hitting return after each command.
  I. If your login screen came up[/COLOR][COLOR=Black] the first time, continue on to part 2, if not, look over waht you did carefully and see if you can spot any mistakes.
[U]
2. Add the Startup Command[/U]
  A. Open the sessions manager: System -> Preferences -> Sessions
  B. Click the far right tab labeled Startup Programs
  C. Click the Add button
  D. Type in the following: *syndaemon -i 1 -d*
[/COLOR][COLOR=Black][I][IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=16865&stc=1&d=1159952821[/IMG]
[/I][/COLOR][COLOR=Black]   E. Hit ok then hit close

Congratualations, you are done! Note that this will not take effect until Gnome is restarted or you type the command from 2D in a terminal window. You can restart Gnome with the Ctrl-Alt-Backspace trick (make sure to save everything first!) or you can open a terminal by going to Applications -> Accessories -> Terminal.

If you have any questions, comments, or concerns, feel free to contact me through this board, or more easily through email or AIM.
  
[/COLOR]


this is working perfectly for me in ubuntu 9.04!

thank you very much!

---

### Post by sgosnell on 2009-04-27
Ummm... 9.10 won't be released for 6 months.  9.04 was just released this week.

---

### Post by johnnylavah on 2009-04-27
> **sgosnell said:**
> Ummm... 9.10 won't be released for 6 months.  9.04 was just released this week.

you are correct...typo on my part

---

### Post by andre_orwell on 2009-05-09
After editing my xorg.conf I found my display resolution (which is a little "new" at 1280x800) was not detected correctly.  This, combined with a lot of posts out and about suggesting that xorg.conf may be falling from favour as a way of configuring X got me digging.  I found that settings for my synaptics trackpad could be set in /etc/hal/fdi/policy/11-x11-synaptics.fdi

which looks like this:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">190</merge>
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
...
   </match>
 </device>
</deviceinfo>

```
which enables SHMConfig and sets up vertical two finger scrolling.

This got me wondering if there was a way to configure this particular option (tapping off while typing) via this file - thus keeping all the configuration information in one place! Anybody know?

Anybody care to suggest if this is a "better"way to configure the track-pad settings (better than xorg.conf).

Thanks

---

### Post by sgosnell on 2009-05-09
I use touchfreeze.  It's in the repositories, and it works for me.

---

### Post by majikins on 2009-05-14
Nice one - was using the old method in this post to solve this annoying problem but have tried your tip on touchfreeze and it works for me too.  Painless!

Thanks

---

### Post by meravblum on 2009-05-14
can somebody please help me? i cant open synaptics because when i do, i get this message:
 Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

im quite a bigginer and am really stuck.

---

### Post by sgosnell on 2009-05-14
You may have your sudoers file either corrupted or missing.  Can you run anything else using sudo?

How are you trying to run Synaptic?  From the menus or from the command line?  If from the System/Administration menu, it should run if you put in the correct password when prompted.

---

### Post by Shekibobo on 2009-05-14
When I open xorg.conf, there is not one section that mentions "Input Device."  What am I do to?  

Right now, I'm using touchfreeze, which doesn't even seem to work half the time, and anyway my taskbar is getting full.  I really just want something that will run at startup and keep going in the background.  Is there possibly another way I can do this?

I love ubuntu, but I keep running into problems and exceptions with my system on nearly every tutorial I go through, and the problems I encounter always seem like one of the rarest kinds, so I spend hours trying to fix something that seems very simple for everyone else.  :?  

Using ubuntu 9.04 on a 64bit.

---

### Post by sgosnell on 2009-05-14
The other fixes in this thread, involving editing the hal file or the xorg.conf file, will work.  If you don't have a necessary section, just add it by copying and pasting.

---

### Post by FokkerCharlie on 2009-05-18
This isn't working for me.

I have set up the /etc/hal/fdi/policy/shmconfig.fdi file as discussed, and tried several variations on the syndaemon command.

However, there's no effect from running syndaemon, my touch pad is still just as responsive when I'm typing as it ever was!

I am using Jaunty 64.

Any ideas?
Cheers
Charlie

---

### Post by sergiom99 on 2009-05-23
maybe this doesnt work in JJ.
There is no such section in xorg.conf and when I added it, there was no response either.

---

### Post by smalldog on 2009-06-06
> **sergiom99 said:**
> maybe this doesnt work in JJ.
There is no such section in xorg.conf and when I added it, there was no response either.

First of all, you must confirm that your touchpad is correct detected when kernel bootup instead of a PS/2 mice. You can using "dmesg" to verify it. 

Secondly, you can check the HAL setting by "lshal".  

Last, it must loaded with proper drive under X-windows. Using "xinput list" to verify your touchpad was properly setup under X-windows. Sometimes, it is detected as PS/2 device. 

All of above, you should find a word "synaptics", Otherwise, you should reconfigure you system.

Good luck

---

### Post by ugm6hr on 2009-06-07
This is in the Outdated tips section - since it does not apply to Intrepid or Jaunty.

The new automatic xorg settings mean that enabling shmconfig requires a different setting:
[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

This gives a comprehensive overview of how to do exactly this.

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for nice how-to

---

### Post by 73ckn797 on 2009-12-06
Ubuntu 9.10 has the ability to disable Synaptics Touchpad While Typing.

Go to System/Preferences/Mouse and there is an option to disable the touchpad when typing.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Tootler on 2010-09-30
> **73ckn797 said:**
> Ubuntu 9.10 has the ability to disable Synaptics Touchpad While Typing.

Go to System/Preferences/Mouse and there is an option to disable the touchpad when typing.


This is enabled by default in my (Lucid) setup. However I found the 2s default time is insufficient.

This page from the Ubuntu support documentation explains how to increase it:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by andreisun on 2011-03-02
> **edmicman said:**
> I did "syndaemon -i 1 -d -t -K" and that seems to work pretty well.  I agree, though, that this is a simple problem that should be fixed by default!

Hi, i have a problem, my touchpad doesn't  work. I've tried various solutions from the forum and i get: Unable to find a synaptics device.
What should i do? I am a beginner...

Thanks,

Andrei

---

