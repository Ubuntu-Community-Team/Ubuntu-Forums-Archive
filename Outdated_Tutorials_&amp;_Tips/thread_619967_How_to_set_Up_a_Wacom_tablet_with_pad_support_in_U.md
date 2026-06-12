---
title: "How to set Up a Wacom tablet with pad support in Ubuntu Gusty"
date: 2007-11-22
forum: Outdated Tutorials &amp; Tips
---

### Post by gali98 on 2007-11-22
Okay this is a new updated tutorial with a bit more organization&#8230;
I moved this to the tutorial sectoin when I realized there was a tutorial section... :) 
This is now for Gusty. If you have Feisty then go [here.]("http://ubuntuforums.org/showthread.php?t=553573") There are a few minor differences.

_**About this tutorial...**_
Okay here we go. This is sort of a mini tutorial that sort of brings together a lot of posts so you can get this working. I am doing this because There is not a real new tutorial that I know of, and I wanted to help new users (like myself) to be able to do this. I will explain things as thoroughly as possible so sorry to all you linux-heads. This all started from a post about the tablets and I didn't want to divert the topic.
[http://ubuntuforums.org/showthread.p...ighlight=wacom](http://ubuntuforums.org/showthread.p...ighlight=wacom)
[B][U]
Some Notes about this tutorial:[/U][/B]
I use a Graphire4 so some of this may not apply, but it should work all around.
As far as I know, the Bamboo is not completely implemented yet and expresskeys does not work at all, but this is just my guess as I have not tested it. But don't worry, it shouldn't be long.
(UPDATE: the linuxwacom project has come out with a new version that is supposed to support Bamboo and some other new features but the ubuntu packages are not out yet. I will try to update this when I can.) 
I'm pretty new to Linux and wanted this to be as explanatory as possible, so it may get tedious in some places. Please bear with me.
[B][U]
Installing Expresskeys on Ubuntu Gusty 7.10  to enable pad support[/U][/B]

First make sure you have the newest wacom-tools and xserver-xorg-input-wacom packages installed.(I think they come with feisty but try to install them anyway.) Second make sure you have build-essential, xorg-dev, and libc6-dev and their dependencies installed. (just use apt-get or synaptic to install the three. Of course the dependencies will be installed with it.) Now download expresskeys from
[http://freshmeat.net/projects/wacomexpresskeys/](http://freshmeat.net/projects/wacomexpresskeys/)
extract the tar.gz where ever and cd into it. Do the basic


```
./configure
make
sudo make install
```

now open your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

(I suggest backing it up first because it caused me some pain when it messed up and x wouldn't start)
and put this in with the rest of the "wacoms"



```
Section "InputDevice"

Driver "wacom"

Identifier "pad"

Option "Device" "/dev/input/wacom" 

Option "Type" "pad"

EndSection
```


and put this in the Server Layout part



```

InputDevice "pad"
```

okay save that and restart x (CTL+ALT+Backspace)
and log back in

open up that terminal


```
expresskeys -d
```

that starts up the Daemon.
That will let you use the 3 buttons on the pad. They are shift scroll and alt by default. You can change that by editing /home/yourusername/.expresskeys/yourtablet.conf or something close to that.
[U][B]
PressCurve[/B][/U]

Presscurve is to change to curve of the pressure(obviously that's the best way to explain it) as for how it works here it goes...
Okay basically it designing a belzier curve. You have two set points: (0,0) and (100,100)
The four values you choose define the support points. i.e. where you have your four values of presscurve:
"x1,y1,x2,y2"
(x1,y1) is your support point for the set point (0,0) and (x2,y2) is the support point for (100,100)
Therefore you can set the curve of this belzier curve however you want. If you had
Presscurve "0,0,100,100"  this would give you a straight line and even pressure whereas
Presscurve "0,75,25,100"  would give you a very steep curve and a soft pressure feel and
presscurve "75,0,100,25"  would give a very shallow curve and a firm pressure feel. You'll have to experiment to find how you really want it.

_**Scroll Fix**_

Make a file named something useful i.e. wacominversion or whatever..


```

#!/bin/sh
xsetwacom set cursor RelWUp 5
xsetwacom set cursor RelWDn 4
xsetwacom set pad RelWUp 5
xsetwacom set pad RelWDn 4

```
put that in a folder named .wacom in your home folder.
okay now make another file named expresskeysstart or whatever

```


#!/bin/sh
expresskeys -d
```

Put this in the same place. This will start expresskeys as a daemon. See below for how to run it at startup.

**_Cursor Speed_**

You need to put this in your xorg.conf under the "cursor" InputDevice section.

```
Option "Speed" "Rspeed"
```
Where Rspeed is the speed you want. 1.0 is default. 
Higher than 1.0 = Faster
Lower than 1.0 = Slower
Don't put it too close to 0 are some wierd bugs occur.

[U][B]
WacomTools and other helpful tools[/B][/U]

xev - This is a very helpful tool in discovering keycodes.
Just run that command and any key you press will be shown in the command line.

wacdump and xidump - These are both tools to monitor your pad. You can use these to check what keys your pad is sending.

xprop - this is useful for identifying program records for later use with expresskeys. Use
"xprop | grep WM_CLASS | cut -d ',' -f2" for easy usage.

xsetwacom - a very useful tool that sets what your tablet sends the xserver. This is covered below.

_**Xsetwacom**_

This is the command to use to bypass expresskeys. This was used above to correct the scroll.
There are many uses for it. I will try to list all the helpful commands.
xsetwacom -h  This displays the help blurb.
xsetwacom list or xsetwacom list dev  This displays the available events. i.e. pad, stylus, cursor, pad, etc...
xsetwacom list param  This lists all available parameters for each event i.e. button1, button2, RelWUp, RElWDn, etc... and at the bottom it shows how to set up these modifiers.

xsetwacom list mod   This list all special modfiers such as SHIFT, CTL, etc... And also it list special keys such as space, backspace, F1...

xsetwacom get [dev_name] [param]  i.e. xsetwacom get pad button1   This would return what button1 on the pad is set as.   This command is used to find what command a current param is set to.

xsetwacom getdefault [dev_name] [param]  This gives the default value for the specified param.
xsetwacom set [dev_name] [param] [value]  This is used to set the value for a param. This can be a number of things.
If the value was set to a button such as "button 1" or "dblclick 1" or even 5 (without the quotes) then then when pressed this param would return what button one does on your computer.
To set it as one in the list of mods then you would write "core key mod" such as "core key F1" You can do multiple keys.
Then you can set it to return a key "core key /key" such as "core key /W" would write W.
To do a string write "core key quotedbl string here quotedbl" That would return string here.
Note for values with "" you must include them when setting the keycode.

_**How to edit the Expresskeys Configuration File**_

This file is a lot friendlier than xsetwacom but as far as I have been able to try, it lacks some stuff. If you can't get it to work try xsetwacom and see if you can get it to work. One cool thing about this is the special keycodes, especially the Presscurve ones. You can also have a set of keycodes for a certain program.

You will find the configuration file in yourusername/.expresskeys/graphire4.conf1 or someting similar if your tablet is different.

If you mess up your file really bad then just delete it and start expresskeys over again to regenerate it again.

I will go at it section by section.
The first is some information on how to use the file, and what the defaults are for the pad buttons. Do not change these as they affect nothing and can be used for reference later.
Next is about special keycodes of which I will highlight here. Note: Most of this is taken straight form the file.

keycode 999 - Use the value 999 as a keycode to enable stylus mode toggling between
Absolute/Relative mode (this refers to how the cursor works. The mouse is relative and the cursor is absolute.)

keycodes 991, 992, 993, 994, 995, 996, 997 -  Use the values 991 to 997 for simulating mouse buttons 1 to 7.

keycodes 1004, 1005, 1006, 1007, 1008, 1009 - Use the value 1004 to return from a tablet rotation (NONE), 1005 to flip a
 tablet 180 degrees (HALF), 1006 to rotate 90 degrees clock-wise (CW) and
 1007 to rotate 90 degrees counter-clock-wise (CCW). By using 1008 you can
 rotate the tablet endlessly in a clock-wise manner (CW-HALF-CCW-NONE-CW-)
 and 1009 does the same motion counter-clock-wise (CCW-HALF-CW-NONE-CCW-).


keycodes 1001, 1002, 1003 - 1001 will decrease the PressCurve, while 1003 will increase it.
 1002 restores the curve to its default state: "0 0 100 100".

Next is the PressCurve values:

  Values for the stylus 'PressCurve' ie 'sensitivity' can be chosen the easy
 way - copying from how the wacomcpl program writes them, or the hard way -
 by experimenting.. The seven curves picked by wacomcpl are (Soft to Firm):
 1               2               3               4 (default)
 "0 75 25 100" | "0 50 50 100" | "0 25 75 100" | "0 0 100 100"
 5               6               7
 "25 0 100 75" | "50 0 100 50" | "75 0 100 25"


And now the Fun part! Okay now we set all the stuff for each program record.  (okay a brief explanation... Each record i.e. default, gimp, blender... can have its own set of keycodes. You can even add your own which I will show later)

I will go over the default and the rest will follow the same suit.

First we have The ProgramName which here is set to "default"

Next is Stylus1PressCurve and Stylus2PressCurve which are both set to "0 0 100 100"
1 is the normal end and 2 is the eraser. See the PressCurve part of this tutorial above for how to do this.

Next is DelayEachKeycode which is set to 0.0. I recommend leaving it there unless you have special need of it.

Up next is ButtonRepeatAfter and DelayButtonRepeat which are set to 0.5 and 0.1 respectively. These are pretty obvious. The option RepeatLeft or RepeatRight must be set to 1 on the respective button for these options to mean anything.

Next is HandleScrollWheel which is set to 1. This is turn on/off the scroll wheel. No reason to change this.

After that is ScrollWheelUp and ScrollWheelDown which are set to 994 0 and 995 0 respectively. This sets the scroll. Don't change this unless you know what you're doing it for. I'm not quite sure what the zeros do. They are obviously a second keycode. It is probably to say that is the end of that keypress.

Next is LeftButton and RightButton which are set to 50 0 and 64 0 respectively. These obviously set what the right and left buttons do.

And last is RepeatLeft and RepeatRight which are both set to 0. This specifies whether the key should repeat.

_**How to add your own Program Record**_

This is pretty simple. Just paste the default record from the line:

" %%            # <---  ******** BEGIN NEW PROGRAM RECORD *********"

to the line:

"RepeatRight        0    # Switch 1/0 (Press and hold button repeat keys)"

onto the bottom. Next use xprop as shown above to find the record name of the program you want to specify. Put that where default is and then use xev to find the keycodes you want.

_**How to enable all this at startup**_

First of all you should have those files you made up at the top named wacominversion and expresskeys_start or whatever in username/.wacom/
Now make another file in there named wacomstart or something similar. In it put

```
#! bin/sh
/home/username/.wacom/wacominversion
/home/username/.wacom/expresskeys_start
```

with the actual files you created. 
Now save that then go to System>Preferences>sessions
make a new one name Wacom or something useful and for the command put 
"sh /home/username/.wacom/wacomstart"
That should do it. And yes you could put all this in one file, but I find it better to do it this way. Don't ask me why...


[U][B]
Some endnotes[/B][/U]
This is my first tutorial, and is definitely not perfect. If you have something you want to contribute or correct or whatever please post or pm me or something. My email is korylp at yahoo dot com if you want to do that.
I hope this helps someone. I know I have learned a lot researching this. I will try to update this whenever some new thing comes out, but I am hard-pressed on time, so Don't expect a whole lot. I want to thank all of the people with mini tutorials and the creators of these programs, y'all (yes, I'm a Texan, get over it.) are great. I guess that is all. Thanks,
Kory

Please note: I am not responsible for you crashing you system. I will try to help to the best of my abilities.

---

### Post by narehart on 2007-11-28
when do you think you will update the guide for the bamboo?

---

### Post by gali98 on 2007-12-02
> **narehart said:**
> when do you think you will update the guide for the bamboo?

Well the problem with that is that I don't have a bamboo and therefore couldn't really know what to do. I can look around at other threads though and try to integrate it, but it won't be quite as up to par. Though I guess it should go pretty much as this tutorial goes. I'll try and update it when needed.

And if someone else knows how don't hesitate to pm me or post here.
Kory

---

### Post by MaxVK on 2008-08-27
Hi gali98, thanks for your in depth explanations - by far the most informative Iv read to date.

I have a question for you (that may have been answered in the post, I just cant seem to get to it):

I have an Intuos3. Its working very well really, except for one thing - On the side of the stylus there is a rock switch with two buttons on it. By default the top button is set to be a right mouse click, which is fine, however, the bottom button does not seem to do anything, and I would like to set it so that it can 'grab' a page to scroll it down.

By default this seems to work when viewing pdf files or working in Gimp, but it does not work in other programs, most notably a web browser.

Do you know of any way that I can actually determine which button this is? I'm sure with that knowledge I could make use of the button, but so far I have been unable to identify it.

Using wacdump identifies the tablet correctly, but does not show any activity at all, even when I'm using the tablet as a mouse. xev produces much to much information that I cant follow or in any way relate to xsetwacom or expresskeys.

Any help you could give would be most appreciated.

Regards

Max

---

### Post by brooklyn123 on 2008-08-27
Ok I'm sorry but I'm a little confused.
(sorry I don't know much abut computers)

I have a year old cheap bamboo tablet.
It lags horribly and won't draw anything.

So did you say that they don't have a soft ware thing for bamboo yet?
And if they are getting one how would I get it and how do I know?
Will this express key help my problem?

I'm so sorry I just don't know much about computers 
So if you already explained these things I'm sorry I didn't get it fully [COLOR="DarkOrange"][/COLOR]

---

### Post by gali98 on 2008-08-29
This thread is actually quite old. Please go here for the most up to date tutorial:

[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

Welcome to Ubuntu!

Kory

---

