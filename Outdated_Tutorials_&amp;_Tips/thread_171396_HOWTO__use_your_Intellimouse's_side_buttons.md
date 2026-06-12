---
title: "HOWTO:  use your Intellimouse's side buttons"
date: 2006-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by teimu on 2006-05-06
I had ubuntu for a while, and one thing that really bugged me was that I couldn't seem to get my USB Intellimouse to use it's side buttons for navigation. I searched these forums for help, and indeed I found some. However, these solutions went through more hassle than needed (ie imwheel...why?). There was no quick and easy way to make this simple fix. Through trial and error, I found out a very simple way to get these navigation buttons working like they should in applications like firefox.

First sudo to root:
```
sudo -s -H
```

Then, open your xorg.conf, which, in most cases is in /etc/X11/:
(Use whatever editor you like; vi is a personal preference. replace 'vi' with 'gedit' for a presumably more familar feel to you newbies)
```
vi /etc/X11/xorg.conf
```

Find the section labeled
```
Section "InputDevice"
```

Include, at least, the following lines in that section. Change whatever needed. You dont need to insert the comments:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"    #new explorer protocol...even works with usb mice
        Option          "Buttons"               "7"      #tells X11 the number of buttons on the mouse
        Option          "ZAxisMapping"          "4 5"    #tells X11 which buttons to use for scrolling, 4 is up, 5 is down (i think)
EndSection

```

I would also recommend commenting the Emulate3DButtons line. Its a feature for old mice, which Intellimouse is not:
```
#       Option          "Emulate3Buttons"       "true"

```

Then restart Gnome (assuming that's your desktop. sorry KDEers):
```
/etc/init.d/gdm restart
```

And viola! Now your sidebuttons work!!! Test it out in firefox. That was simple and easy, wasn't it?

Enjoy!

Post any questions, and with prayer, you will get a response. However, it probably won't be from me...I don't really know Linux too well.

---

### Post by crypto178 on 2006-05-08
Thanks! Only one file to edit, and it works fine.

---

### Post by Adragontattoo on 2006-05-08
Just for the sake of my brain, does this enable my Optical trackball that has 5 buttons to work? 

XP the two far right buttons are forward and back in Firefox
Ubuntu(which I am valiantly trying to figure out how to use, total noob to linux) one does nothing and the other ports me to a random page if I click it.

---

### Post by teimu on 2006-05-09
[QUOTE=Adragontattoo]Just for the sake of my brain, does this enable my Optical trackball that has 5 buttons to work? 

XP the two far right buttons are forward and back in Firefox
Ubuntu(which I am valiantly trying to figure out how to use, total noob to linux) one does nothing and the other ports me to a random page if I click it.[/QUOTE]

I wouldn't really know, as I only have a the Intellimouse. It would be interesting to see how that could work though. Play around with the config file and tell me if you get anywhere. I would start by replacing the 7 buttons to 5 buttons.

Also, if its any consolation, whenever I used to right click, I also was ported to a wierd page. Hopefully with the right config, that will change as it did for me. Good luck!

---

### Post by RavenOfOdin on 2006-05-09
I have an Intellimouse, and I've always been able to use the side buttons.

---

### Post by Mellon on 2006-05-10
it works for me on a BTC 5 Buttons mouse


thx :-D

---

### Post by adam.tropics on 2006-05-10
Not problem related, but

> ports me to a random page if I click it.

Ha! I kind of like that idea!...just with the net being what it is these days, you might need a childlock for the mouse!!

---

### Post by ketsugi on 2006-05-11
No go for me. I'm using a Wireless Intellimouse Explorer 2.0 with the tilt wheel, which makes for 9 buttons in total. Prior to doing this, my forward button mapped to a right click and the back mapped to a middle-click. Now neither button does anything at all.

---

### Post by KillrBuckeye on 2006-05-14
This actually worked for me, but it created another problem.  I can no longer restart GDM using Ctrl+Alt+Backspace---it just takes me to a command line login prompt.  If I try to manually start GDM, it [FAIL]s.  I can start X just fine though.  Oddly, after a reboot GDM starts up just fine.  What would cause this strange behavior?

---

### Post by BrowneR on 2006-05-18
I have a IntelliMouse optical USB and am running Dapper.
My side buttons have never done anything so i thought i would give this a try.
I have updated my xorg.conf as above but my mouse buttons still dont work.
As far as i can tell the buttons that do work are mapped as follows:

button1=left click
button2=right click
button3=?
button4=wheel up
button5=wheel down
button6=middle click
button7=?

this mapping seems a bit odd to me as it leaves button 3 and 7 for the side buttons on my mouse. would changing the zaxis mapping to "3 4" just move everything up so that my side buttons were 6 and 7?

I have also tried the method using imwheel which gave some odd results. I managed to get my side buttons to do the job of the mouse wheel scrolling but then my mouse wheel did nothing! Its obviously just a configuration problem but i cant seem to get it to work correctly even after multiple tweaks to the config.

Any bright ideas? :p
TIA

(i also have my laptops trackpad in the xorg.conf. not sure if it may be fouling things up?```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "Edges" "1900 5400 1800 3900"
    Option         "Finger" "25 30"
    Option         "MaxTapTime" "20"
    Option         "MaxTapMove" "220"
    Option         "VertScrollDelta" "100"
    Option         "HorizScrollDelta" "5000"
EndSection
```)

---

### Post by BrowneR on 2006-05-18
Right i have done some more fiddling and come up with something that works for me. im not entirely sure why it works and the guides fail... but it does

I left my xorg.conf reading as follows:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option	   "Resolution" "100"
EndSection
```

I then installed the imwheel package.

The guides all talk about issuing the follwing command at startup (in the /etc/X11/Xsession.d/57xmodmap file)
```

xmodmap -e "pointer = 1 2 3 6 7 4 5" &

```
this command swaps the button codes for buttons 45 with 67 and vice versa. (i guess :p)

This didnt work for me as i got the following error upon execution:
```

chris@res05-cib3:~$ xmodmap:  commandline:1:  bad number of buttons, must have 11 instead of 7

```

xorg.conf only specifies 7 buttons so im not sure where the extra 4 are coming from!!?

anyway i decided i wouldnt remap any buttons so i issued
```

xmodmap -e "pointer = default" &

```

from looking at the imwheel manpage the -b switch can also be used to remap buttons and this was being used in the command that i had from the guides:
```

imwheel -k -b "67" &

```

my button mappings however seemed to match those on the imwheel man page, namely:

4 wheel up
5 wheel down
6 wheel right (doesnt exist on my mouse)
7 wheel left (doesnt exist on my mouse)
8 thumb 1
9 thumb 2

and so i removed the -b switch from the imwheel command and everything worked!

i now have no /etc/X11/Xsession.d/57xmodmap file as i am using the default mappings and i am calling imwheel with only the -k switch.

just thought i'd post this in case someone else is having similar trouble.

my mouse is an IntelliMouse Optical 1.1A USB

My imwheelrc simply reads the following (for back/forward operation in firefox)

```

".*Mozilla Firefox$"
None,Thumb1,Alt_L|Left
None,thumb2,Alt_L|Right

```

---

### Post by SShadow on 2006-06-04
Hmmm...  This is something to do with Dapper...  By following this How To in Breezy, it worked perfectly every time.  Now that I am updated to Dapper, it is no longer working.  :(  I hate it when things that were working perfectly get broken with a new release.
](*,)

---

### Post by Blazeix on 2006-07-18
I thought I would post this here. I also have an "Intellimouse Optical 1.1A USB and PS/2 Compatible" mouse. I tried the above instructions, but they didn't work. Here's how I got this mouse to work with Ubuntu Dapper Drake 6.06 (also Edgy 6.10) on a Dell laptop:

Its really simple. You do not need imwheel or any other key mapping program.
First, back up your xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Edit your xorg.conf by typing the following into the terminal:
```
sudo nano /etc/X11/xorg.conf
```
Note: I use nano as my text editor, you may be using others such as gedit.

Find the InputDevice section that has to do with your mouse. It should look similar to this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        ...
EndSection
```

Edit it so it looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

Restart your computer, start up your browser, and it should work!

---

### Post by ericdsr on 2006-07-20
This also worked for me in Dapper. The addition of the "ButtonMapping" line did the trick, thanks!

---

### Post by Pekkalainen on 2006-07-20
Ever since Dapper came out (well actually since flight 5 or so) I have been trying to get the forward/backward buttons to work in Konqueror, my conclusion is that it is impossible :(

---

### Post by bryonhowley on 2006-07-22
I have come from Gentoo to Ubuntu and the side buttons did not work with Konqueror in Gentoo ether. Works fine in Firefx/Swiftfox but not in Konqueror. Something with Kde and not Ubuntu.

---

### Post by dvord on 2006-11-02
Blazeix that worked for me.  I did leave the emulate3buttons option true and it still works on Edgy.

SWEET!  I'm so jazzed.  After 3 years of trying Linux distros which can deliver what I need out of an OS this is as close as I've ever gotten.  Thanks!!

---

### Post by esaym on 2006-12-26
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

That worked for me but it only works in firefox.  How do I get the side buttons to work in Konqueror?

---

### Post by Trekko on 2007-01-02
> **Blazeix said:**
> 
Edit it so it looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

Restart your computer, start up your browser, and it should work!

I also have an "Intellimouse Optical 1.1A USB and PS/2 Compatible" mouse.
Works like a charm in Opera to:) :) 
Thx!

---

### Post by mastergunner on 2007-01-02
So copying the above will get my buttons working?

---

### Post by kwas101 on 2007-01-03
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

Definitely works for me :-)
Tried the earlier suggestion no go. Couldn't get it to work in debian :-(

---

### Post by esaym on 2007-01-03
I still haven't figured out how to get it working in Konqueror.  Any ideas anyone?

---

### Post by zeltak on 2007-01-03
be careful with it, it didnt work for me and i managed to ruin my xorg file. make sure to back it up before!

Zeltak

---

### Post by mastergunner on 2007-02-04
Once you make the change how do you save the change?

---

### Post by esaym on 2007-02-05
> **mastergunner said:**
> Once you make the change how do you save the change?

You have to edit it as root.

---

### Post by TimJBart on 2007-02-25
> **Blazeix said:**
> 

Edit it so it looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

Restart your computer, start up your browser, and it should work!

I copied your settings and it now works perfectly.  Thanks very much

---

### Post by TimJBart on 2007-02-25
> **mastergunner said:**
> Once you make the change how do you save the change?

This command lets you open and EDIT it.

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by romprod on 2007-03-03
Option          "ButtonMapping"         "1 2 3 6 7"

Works great, maybe it should be edited to the first post so people don't have to read the entire thread to use the fix?

Thanks

---

### Post by ceedubu on 2007-03-03
I had to change my xorg.conf a bit to get my Wireless IntelliMouse Explorer 2.0 to work.

My scrollwheel was doing the back and forward in firefox and the side buttons were doing the scrolling. So I just swapped the "4 5" and the "6 7" now it works. 

Here's my xorg.conf:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "ButtonMapping" "1 2 3 [COLOR="Red"]4 5[/COLOR]"
    Option         "ZAxisMapping" "[COLOR="Red"]6 7[/COLOR]"
#   Option         "Resolution" "100"
EndSection
```

Now my side buttons work correctly in Firefox... Yeah! :)

---

### Post by degsyw on 2007-03-10
> Edit it so it looks like this:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

Restart your computer, start up your browser, and it should work!

thanks Blazeix perfect

degsy

---

### Post by herbster on 2007-03-12
> **ceedubu said:**
> I had to change my xorg.conf a bit to get my Wireless IntelliMouse Explorer 2.0 to work.

My scrollwheel was doing the back and forward in firefox and the side buttons were doing the scrolling. So I just swapped the "4 5" and the "6 7" now it works. 

Here's my xorg.conf:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "ButtonMapping" "1 2 3 [COLOR="Red"]4 5[/COLOR]"
    Option         "ZAxisMapping" "[COLOR="Red"]6 7[/COLOR]"
#   Option         "Resolution" "100"
EndSection
```

Now my side buttons work correctly in Firefox... Yeah! :)

WOW, I have the exact same mouse and from the moment I installed Ubuntu I have used imwheel, every kind of edit to xorg.conf and no results, but right there you got it going for me man, thank you sooooo much! Now it goes back/for in Firefox AND Opera! Woo! :) :) Thx!

---

### Post by Callaghan on 2007-03-16
Why not have back/forward in your file manager too? Try this link

[http://wiki.serios.net/wiki/Mouse_side_buttons](http://wiki.serios.net/wiki/Mouse_side_buttons)

It works throughout kde in file pickers as well as konqy, nautilus and firefox etc I'd been looking for a solution to the side button back/forward issue since way back when rocks were soft. I never could quite fathom imwheel out. Hats off to PCLinuxOS for setting that up from the get go in their latest edition. 

You don't even have to touch your xorg.conf just put it back the way it was if you've tweaked the mouse section to smithereens.

xbindkeys and xvkbd is the way to go!

---

### Post by IronWolve on 2007-03-19
Ok, all these "use this config" for xorg.conf and etc, doesnt work for everyone..

Using imwheel -c, I found out my Intellimouse optical has left/right for the 6/7 keys.  4/5 is mapped to up/down (scroll wheel).

Creating a imwheel config for the left/right mouse button below fixed it for me. YMMV, check your mouse bindings first!    Then if you need to fix your xorg.conf for your mouse, do that last.

.imwheelrc  
```
"^Firefox-bin$"
None,Left,Alt_L|Left
None,Right,Alt_L|Right

```

---

### Post by esaym on 2007-03-22
> **Callaghan said:**
> Why not have back/forward in your file manager too? Try this link

[http://wiki.serios.net/wiki/Mouse_side_buttons](http://wiki.serios.net/wiki/Mouse_side_buttons)

It works throughout kde in file pickers as well as konqy, nautilus and firefox etc I'd been looking for a solution to the side button back/forward issue since way back when rocks were soft. I never could quite fathom imwheel out. Hats off to PCLinuxOS for setting that up from the get go in their latest edition. 

You don't even have to touch your xorg.conf just put it back the way it was if you've tweaked the mouse section to smithereens.

xbindkeys and xvkbd is the way to go!

So you are saying that by using that you don't have to mess with the xorg file and the buttons work in firefox and in konqueror?? That would be great...

---

### Post by rudeboyintrouble on 2008-04-19
Thank you Blazeix,

I tried another howto that didn't work. 

Yours worked like a charm right away.

---

### Post by master_kernel on 2008-04-19
This problem is fixed in Ubuntu Hardy.

---

### Post by pannerrammer on 2008-05-01
> **master_kernel said:**
> This problem is fixed in Ubuntu Hardy.

A clean install of Hardy doesn't  appear to fix anything... my side buttons don't work without imwheel.

---

### Post by Toadicus on 2008-05-01
I similarly do not have the use of my side buttons in hardy.  They just fine in gutsy (and all the way back through breezy), but when I did the upgrade to hardy, they quit.  I'd really like to find a resolution to this that doesn't require xmodmap or imwheel... I've tried several howtos found on google, to no effect (though, they're all for older versions; I can't find one that is actually for hardy).

Any ideas? :)

**edit: I'm using an intellimouse optical 1.1a**

---

### Post by pannerrammer on 2008-05-02
See [http://ubuntuforums.org/showthread.php?t=787790](http://ubuntuforums.org/showthread.php?t=787790)

---

### Post by danger89 on 2010-05-05
It's 2010 this option is still not available in Ubuntu 10.04. Also there is no xorg.conf anymore?

---

### Post by MiniMe on 2010-05-12
I'm using Ubuntu 10.04 64 bit. The side buttons work in Firefox and chromium without any tweaking but how do I get them to work in the file manager (Nautilus)?

Many thanks.

---

### Post by MiniMe on 2010-08-04
I just noticed in Ubuntu 10.04 the side buttons don't work in epiphany as well as nautilus. Any solutions to this?

---

### Post by notty on 2010-09-01
never mind

---

### Post by Ecip on 2010-10-26
I also have some issues with a wireless mouse... benq m310.
seems the buttons work, including the scroll wheel, but the mouse cursor itself will not move.
and xorg.conf does seem to be missing... or perhaps just moved to a different location?

This is ubuntu 10.10, btw.

---

### Post by Ecip on 2010-10-26
Seems that ubuntu is seeing the mouse as a keyboard, so the buttons work but the cursor wont track.
As per this: [https://bugs.launchpad.net/ubuntu/+bug/325581](https://bugs.launchpad.net/ubuntu/+bug/325581)

is there any more info on this on how to fix the problem?

---

