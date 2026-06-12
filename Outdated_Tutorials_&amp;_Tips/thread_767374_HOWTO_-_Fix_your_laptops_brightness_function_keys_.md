---
title: "HOWTO - Fix your laptops brightness function keys operating properly in 8.04 Hardy"
date: 2008-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by AaronMT on 2008-04-25
Hello folks,

If you're like me, you recently installed Ubuntu Hardy Heron 8.04 and discovered that your laptops function keys are not properly adjusting the brightness. In essence, you are pressing the key combination and nothing is happening.

I have written a fix that simply replaces two script files. This may or may not work for you. **Always create a backup first**.

Here is what I edited within two files:

**First we are going to change brightness up**

```
sudo gedit /etc/acpi/video_brightnessup.sh
```

**Replace everything in the file with the following**

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
12)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac
```

**_Save and quit_**

**Now we are going to edit brightness down**

```
sudo gedit /etc/acpi/video_brightnessdown.sh
```

**Replace everything in the file with the following**

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

12)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
100)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac
```

**_Save and quit_**

:KS No reboot or logout required, simply press your function combination on your laptop to change brightness. If you're laptop is like mine, I press **FN + Up/Down Arrow**. 

Let me know how it works. If this does nothing, it's best to restore the backup you made prior.

Post your comments in this thread, let me know how it goes. :KS


- AaronMT

---

### Post by AaronMT on 2008-04-26
Just want to add that I have tested this as well on a new HP Laptop and it works. :KS

---

### Post by pritamps on 2008-04-26
Tested on Dell Latitude 131L and it works!

Thanks!

---

### Post by likwid on 2008-04-26
Unfortunately does not work with Samsung R60plus.

---

### Post by JJ_Kame_R on 2008-04-26
Unfortunaly it doesn't work on asus notebook.

My brightness with asus_laptop module on is always set to minimum and controls don't change a thing.

Only way to use the notebook is to boot with acpi=off option or to blacklist asus_laptop module.

I'm sorry but I have to admit that hardy is 2 steps behind gutsy.

---

### Post by coachwhip on 2008-04-26
Do you think it will work with Kubuntu ?

i will try it once I get the 'sudo' working. i can open files with kate but not with sudo kate.

I'll let you know once i get to try it.

Mike

Edit. I've just tried it and it appears to work, not rebooted yet but so far so good, got brightness back and funcion keys work fine.

Thanks for that

---

### Post by windwisp on 2008-04-26
works on dell vostro.

---

### Post by pormogo on 2008-04-26
Tried this fix on my Dell m1330n and it didn't do anything. I still have the 3 "stages" of brightness. I am also having another issue where anytime I watch a video (in say VLC) the backlight turns back up to maximum brightness for some reason.

---

### Post by ra300z on 2008-04-26
I have an HP DV2000 laptop and this did not work for me.

This thread did solve the problem
[http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness](http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness)

---

### Post by guevara on 2008-04-27
why do we need change brightness :confused:for battery?
I almost never changed :lolflag:

---

### Post by AaronMT on 2008-04-27
> **guevara said:**
> why do we need change brightness :confused:for battery?
I almost never changed :lolflag:

If you never change your laptop's brightness than that means you are shortening the time you have available when away from AC power. The screen is the biggest power drain.

---

### Post by dublued on 2008-04-27
tested and working with gateway c140-x tablet pc

thank you!

---

### Post by microwaver on 2008-04-28
What I want to know for sure is, Does this work also for Gutsy GIbbon 7.10?

---

### Post by shawalli on 2008-04-28
does not work on the fujitsu T4220 Tablet

---

### Post by flamelab on 2008-04-28
Doesn't work here (laptop)

Terminal output :

```
flamelab@flamelab-laptop:~$ su
root@panagiotis-laptop:/home/flamelab# sh /etc/acpi/video_brightnessup.sh
grep: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
/etc/acpi/video_brightnessup.sh: 35: cannot create /proc/acpi/video/VGA/LCD/brightness: Directory nonexistent
root@flamelab-laptop:/home/flamelab# 
```

---

### Post by microwaver on 2008-04-29
There is a workaround in 7.10: just adapting the script manually. 
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by madjr on 2008-04-29
another workaround is using the gnome panel brightness applet.

just add it to your panel and use the mouse wheel to make it go up or down, works great.

---

### Post by madjr on 2008-04-29
another workaround is using the gnome panel brightness applet.

just add it to your panel and use the mouse wheel to make it go up or down, works great on my Dell inspiron.

---

### Post by TwiceOver on 2008-04-29
THANK YOU!!

One of the last hardware problems on my Dell Inspiron 1501.

---

### Post by taiye on 2008-04-29
Works nicely on a Compaq Presario M2512 AU. Thanks!

---

### Post by Iago1989 on 2008-04-29
Does not work on ASUS M50sv, as my function keys work for up/down as stop/(play/pause) and ymy brightness keys are fn f5 and fn f6, so when I try to change brightness with the up/down keys my music stops, and I can start it again with fn f6!

---

### Post by Kougaiji on 2008-04-29
Thanks a lot!!

Also got a dell 1501, and this has plagued us dell users for a long time! I'm having a good experience in hardy, with wireless, video acceleration, and now finally brightness working properly :D! Woo happy to be a ubuntu user!

---

### Post by RangerDanger on 2008-04-30
I can't get this to work at all on my vostro 1700, I think it may have added on more step, but had to tell.  It is weird because with 7.10 my brightness function keys worked great with eight distinct brightness levels.  So I booted up my 7.10 livecd and sure enough it worked just fine.  So I checked the brightnessup and brightnessdn files on the livecd and they are exactly the same as the ones in my 8.04 install, so I am thinking there must be some other config files that must be different.  If I knew where to look for the settings for the brightness applet in the taskbar, maybe I could copy them from there.  

On a side note, sound, suspend and hibernate all work for me with 8.04 but never did with 7.10.

---

### Post by Nexano on 2008-05-01
Not working on a new intel macbook.

---

### Post by olavjunior on 2008-05-02
For all of you who this doesn't work for, try this [http://ubuntuforums.org/showthread.php?p=4178093#post4178093](http://ubuntuforums.org/showthread.php?p=4178093#post4178093)
Works like a charm!

---

### Post by RangerDanger on 2008-05-06
Add this "blacklist video" in /etc/modprobe.d/blacklist then restart.

---

### Post by Goodbytes on 2008-05-10
Works on my Gateway E-295C. First time through completely hung Gedit, though, and a few seconds later the rest of the system. After a reboot, I tried again and it's worked fine.

---

### Post by deadtom on 2008-05-13
Just confirmed that this is working beautifully on my Gateway NX560X laptop. Thanks!

---

### Post by Tristam Green on 2008-05-13
this works on my Dell 1501.  Brightness does not step like it should, but it is not so bad that there are only 3 levels of brightness.


Great tutorial and many thumbsups ^^

---

### Post by Samjo8 on 2008-05-13
This didnt work for my macbook but thats not suprising lol

---

### Post by philheaton on 2008-05-13
the VGA part of the command is laptop specific, eg: instead of just copy and pasting the line **/proc/acpi/video/VGA/LCD/brightness**, you need to look at what this is actually pointing to on your laptop. 

mine is: /proc/acpi/video/**ATIM**/LCD/brightness

the bit after /video/ is where you need to look.

having said that, the script still doesn't run on my laptop, however if i bring up a root terminal and enter:

[B]echo # > /proc/acpi/video/ATIM/LCD/brightness
[/B]
where # is the value of the screen brightness i want (such as 80 or 100 etc) then i get the screen to respond. however, i've no idea how to incorporate this into a shell script or alter the one provided.

if anyone is feeling generous enough to make this into a shell script, i'd be most grateful. the output of 

**cat /proc/acpi/video/ATIM/LCD/brightness** 

on my machine is 

**levels:  100 10 30 40 50 60 70 80**

by the way, for those who want to know, the laptop is a samsung x22 t7500 core2 duo

---

### Post by James_the_dude on 2008-05-14
This brightness key issue was a huge annoyance for me, as having my screen on full brightness during battery power stole about 40 minutes from my battery, and the only other option was the darkest setting, which was too dark. The fix posted at the start of this thread has worked perfectly for me on my Gateway NX570X.

Thank you AaronMT!

- J

---

### Post by dje on 2008-05-14
Works great on my inspiron 1501, thanks :)

dje

---

### Post by KingArthur10 on 2008-05-19
Saved my butt.  I was getting annoyed.  Thanks a lot!

Gateway C-140XL

---

### Post by dirtygreek on 2008-05-20
My fix for a Toshiba Satellite A215:

Back up your current /etc/acpi/video_brightnessup.sh and /etc/acpi/video_brightnessdown.sh

Create a file: /etc/brightness.dat
Set the value of the file initially to, say, 50

/etc/acpi/video_brightnessup.sh

```

#!/bin/bash
bness=`cat /etc/brightness.dat`
bness2=$(echo "scale=9; $bness+10" | bc) #add 10 to current value
sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value
sudo echo $bness > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

/etc/acpi/video_brightnessdown.sh

```

#!/bin/bash
bness=`cat /etc/brightness.dat`
bness2=$(echo "scale=9; $bness-10" | bc) #subtract 10 from current value
sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value
sudo echo $bness > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

What's going on: The changed brightness value will be set every time you change it to /etc/brightness.dat.  This value will be read in by the scripts when you hit the brightness button (or just run the scripts) and used to determine the new brightness.

---

### Post by clauguia on 2008-05-25
Tested on an Acer Aspire 4520 and it worked! with Ubuntu 8.04 Hardy Heron 64bits.

---

### Post by martin5349 on 2008-05-27
> **RangerDanger said:**
> Add this "blacklist video" in /etc/modprobe.d/blacklist then restart.

Great. Now it works on Toshiba Portege M400. Thanks a lot

---

### Post by DR583V3 on 2008-05-28
Works perfectly on my Gateway MT6457.

---

### Post by bhuthogg on 2008-05-30
works good dell vostro 1000

---

### Post by themuddler on 2008-06-02
On the battery power settings I have chosen "Dim display when idle". The frustration is that when I then use the laptop again it jumps to a mid-value of brightness rather than the previous brightness. This means if I'm reading an ebook late at night and let the machine idle, on scrolling down my laptop lights up brightly, floods the room with light and wakes my wife. Needless to say, this is a problem!

Any ideas on getting it to resume the previous brightness setting rather than a mid-level brightness on returning from idle?  A compromise is not to use the dim-on-idle setting but that results in more drain in the daytime when I wander away from it.

---

### Post by kris1351 on 2008-06-02
Just did this on my Vostro 1500 with 8.04 and works beautifully. Thanks!!

---

### Post by tklopp on 2008-06-07
> **AaronMT said:**
> Hello folks,

If you're like me, you recently installed Ubuntu Hardy Heron 8.04 and discovered that your laptops function keys are not properly adjusting the brightness. In essence, you are pressing the key combination and nothing is happening...


I faced the same problems but had only 4 brightness levels even after writing the levels of my control file into your scripts.

The reason is that my Dell D530 fires each acpi key event TWO TIMES!?!?

So I rewrote your script to ignore the second event if it is coming two fast. Another change is to read all available levels and switch to the next/previous one on key press. So there's no need to change the levels on another notebook. As this is scary in bash I used PHP5 to do this.

You can copy the script to /etc/acpi/video_brightnessup.sh and create a link named /etc/acpi/video_brightnessdown.sh to the same file. The extension ".sh" is no problem. Give it owner and rights like the other scripts there.

Here's my code:
[PHP]
#!/usr/bin/php5
<?php
// (C) 2008 by t.kloppenburg
// License: GPL
// I use it on my DELL D530 notebook as replacement for /etc/acpi/video_brightnessup.sh and *down.sh

$ctlfile = '/proc/acpi/video/VID/LCD/brightness';

$isWithTimeDelay = true; // needed for D530 and Ubuntu 8.04/KDE 3.5.8
$timeCtlFile = '/var/tmp/acpi_brightness_timectl';
$timeDelay = 0.2; // units: seconds

// ------------------------------------------------------------------------
// Allow only one call per 400ms as my D520 always fires two events on each keypress:
if ($isWithTimeDelay)
{
        $nowTime = microtime(true);
        $previousTime = (float)@file_get_contents($timeCtlFile);
        if (($nowTime - $previousTime) <= $timeDelay)
                exit(0); // exit if last event is not long enough ago

        if (! is_link($timeCtlFile)) // at least SOME security :-)
                file_put_contents($timeCtlFile, $nowTime); // write new microtime value
}
// ------------------------------------------------------------------------
// detect mode up/down:
$isDown = stripos(basename($argv[0]), 'down') !== false;

// ------------------------------------------------------------------------
// read current mode and possible modes:
$ctldata = file($ctlfile);
foreach ($ctldata as $ctlline)
{
   if (preg_match('/^levels: (.*)/', $ctlline, $matches))
      $levelsData = preg_split('/ +/', $matches[1], -1, PREG_SPLIT_NO_EMPTY);
   if (preg_match('/^current: (.*)/', $ctlline, $matches))
      $current = (int)$matches[1];
}
// ------------------------------------------------------------------------
// Prepare levels to get next/previous level:
$levelsData = array_unique($levelsData); // preserves the keys
$levelsData = array_values($levelsData); // throws keys away
sort($levelsData);

// ------------------------------------------------------------------------
// find index of current mode and switch to next/prev mode:
$currentPos = array_search($current, $levelsData);
echo 'currentPos' . $currentPos . "\n";
if ($isDown)
{
   $currentPos--;
   if ($currentPos < 0) $currentPos = count($levelsData)-1;
}
else
{
   $currentPos++;
   if ($currentPos == count($levelsData)) $currentPos = 0;
}

// echo 'currentPos' . $currentPos . "\n";

$cmd = "echo -n $levelsData[$currentPos] > $ctlfile";
// echo "$cmd\n";
`$cmd`; // execute the command.
[/PHP]

---

### Post by drdanield@gmail.com on 2008-06-08
Gateway M-6319 has similar problem. Brightness doesn't work by either function keys nor brightness applet.  The function keys work following similar "hacks" on /etc/apci/video_brightnessup.sh and video_brightnessdown.sh as described on following forum threads:
[http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374)
[http://ubuntuforums.org/showthread.php?t=673946](http://ubuntuforums.org/showthread.php?t=673946)
[http://ubuntuforums.org/showthread.php?t=767219](http://ubuntuforums.org/showthread.php?t=767219)

But applet still doesn't work. I think whatever is called by acpi_fakekey 224 and 225 is not working correctly.  Running Hardy 8.04 on
<code>
$ sudo dmidecode -s system-manufacturer
Gateway
$ sudo dmidecode -s system-version
3409361R
$ sudo dmidecode -s system-product-name
M-6319
</code>
xev output for function keys brightness up (key code 212) and down (101):
<code>
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
</code>


I would really appreciate it if this can be fixed fundamentally by an update from main Ubutnu repository.  It's an important problem for laptops running on battery.

---

### Post by lestrade on 2008-06-08
It worked for my new Toshiba Satellite p305 17 in.  Thanks!

---

### Post by J0oJ0o on 2008-06-23
Works wunderful with Samsung R20.
Thanks a lot

---

### Post by Jesus_Valdez on 2008-06-24
It worked for my Gateway Mx6947m

Thanks

---

### Post by ernest-le-voyage on 2008-06-25
> **AaronMT said:**
> Hello folks,

If you're like me, you recently installed Ubuntu Hardy Heron 8.04 and discovered that your laptops function keys are not properly adjusting the brightness. In essence, you are pressing the key combination and nothing is happening.

I have written a fix that simply replaces two script files. This may or may not work for you. **Always create a backup first**.

Here is what I edited within two files:

**First we are going to change brightness up**

```
sudo gedit /etc/acpi/video_brightnessup.sh
```

**Replace everything in the file with the following**

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
12)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac
```

**_Save and quit_**

**Now we are going to edit brightness down**

```
sudo gedit /etc/acpi/video_brightnessdown.sh
```

**Replace everything in the file with the following**

```
#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

12)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
100)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac
```

**_Save and quit_**

:KS No reboot or logout required, simply press your function combination on your laptop to change brightness. If you're laptop is like mine, I press **FN + Up/Down Arrow**. 

Let me know how it works. If this does nothing, it's best to restore the backup you made prior.

Post your comments in this thread, let me know how it goes. :KS


- AaronMT
It did work fine on my 2007 Inspiron 1501. Excellent, thanks for your job
Jean

---

### Post by viterico on 2008-06-25
> **J0oJ0o said:**
> Works wunderful with Samsung R20.
Thanks a lot

Hi, I have the same laptop, the R20, and don't understand what was the solution for the brightness problem in hardy. What's the procedure? ¿? I say this because in this page there are a lot of posible solutions. :)
Thanks in advance,

Viterico.

---

### Post by tomisachef on 2008-07-21
Habe ein Dell Vostro 1000,
Wow! Ging auf Anhieb! Perfekt! Danke!

---

### Post by Aleksandr Sahakyan on 2008-07-22
The suggested modification does not work for Gateway MX6920.:(

---

### Post by Glutexo on 2008-07-22
Doesn't work for Fujitsu Siemens Esprimo Mobile V5505. :(

---

### Post by formanner on 2008-08-02
> **dirtygreek said:**
> My fix for a Toshiba Satellite A215:

Back up your current /etc/acpi/video_brightnessup.sh and /etc/acpi/video_brightnessdown.sh

Create a file: /etc/brightness.dat
Set the value of the file initially to, say, 50

/etc/acpi/video_brightnessup.sh

```

#!/bin/bash
bness=`cat /etc/brightness.dat`
bness2=$(echo "scale=9; $bness+10" | bc) #add 10 to current value
sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value
sudo echo $bness > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

/etc/acpi/video_brightnessdown.sh

```

#!/bin/bash
bness=`cat /etc/brightness.dat`
bness2=$(echo "scale=9; $bness-10" | bc) #subtract 10 from current value
sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value
sudo echo $bness > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

What's going on: The changed brightness value will be set every time you change it to /etc/brightness.dat.  This value will be read in by the scripts when you hit the brightness button (or just run the scripts) and used to determine the new brightness.

I took this code and changed it a little to work with my Toshiba A215-6820. It works, and now I have everything working on my laptop!

You'll still need the /etc/brightness.dat file created with a starting value in it, say 50.

Then, replace the contents of /etc/acpi/video_brightnessup.sh with:

```

#!/bin/bash

bness=`cat /etc/brightness.dat`

bness2=$(echo "scale=9; $bness+5" | bc) #add 10 to current value

if [ $bness2 -gt 70 ] #sets the maximum

then

bness2=70

fi

sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value

sudo echo $bness2 > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

Next, replace the contents of /etc/acpi/video_brightnessdown.sh with:

```

#!/bin/bash

bness=`cat /etc/brightness.dat`

bness2=$(echo "$bness-5" | bc) #subtract 10 from current value

if [ $bness2 -lt 0 ]  #sets the minimum

then

bness2=0

fi

sudo echo $bness2 > /proc/acpi/video/VGA/LCD/brightness #set new value

sudo echo $bness2 > /etc/brightness.dat #make sure this file exists initially and has a value (say, 50)

```

No reboot necessary. :)

---

### Post by growingneeds on 2008-08-03
I managed to fine-tune the LCD brightness to a greater degree by adding the 'Brightness Applet' to the Gnome Panel.
1.Right-click a specified location on the Gnome Panel and select 'Add to Panel...'
2.Select 'Brightness Applet'.

To achieve 7 adjustable levels of brightness on the function keys (instead of the usual 3), and to keep the LCD brightness from being set at the maximum after every reboot:
1.In a terminal, type “gksudo gedit”.
2.Open the file “/etc/modprobe.d/blacklist”.
3.Add a new line “blacklist video”.
4.Reduce brightness to mimimum (or desired level).
5.Reboot.

---

### Post by klashwithknick on 2008-08-08
Thank you!  This fixed my problem right away.  It works on my Dell Inspiron 1501.

---

### Post by sotirisp on 2008-08-08
I have a thinkpad T43 and brightness UP works fine (**7 steps**) with the FN+PgUp key.

I have a problem with the **FN+PgDn** key which reduces the brightness immediately at the **minimum level** without any **steps** through it.

Tried the changes described in teh first page but still the same...

Anyone knows what might be the cause of this?

P.S. Setting the brightness using the "Brightness panel applet" and mouse scroll wheel works ok.

---

### Post by TrevorPace on 2008-08-26
Ok so I had thought I had solved the problem...but it turns out I had not. But here is my situation:

I have a Toshiba A300-034 with Ubuntu 8.04 completely up to date.

Currently my brightness keys do NOT work and I have no folder called /proc/acpi/video/VGA/ only with OVGA. The problem is that in that there is no brightness file there is only a bunch of folder called DD01, DD02...DD05. All of them DO contain brightness files but only DD03 contains one that doesn't say "Not Supported". It gives me:

trevor@trevor-laptop:~$ cat /proc/acpi/video/OVGA/DD03/brightness 
levels:  90 35 10 25 35 50 60 75 90 100
current: 100

Now I noticed that there is a file called /etc/acpi/toshbright.sh that contains a script to adjust brightness unfortunately it refers to a file called "/proc/acpi/toshiba/lcd" from which it both gets the current value and sets the current value. That folder does NOT exist for me.

Now I'm going to go reset the computer and see if brightness works (it seems completely random sometimes.) If it does work I'll post if some of those folders appear and maybe someone will be able to figure out why it only works some times.

---

### Post by birkopf on 2008-08-30
> **AaronMT said:**
> Hello folks,
If you're like me, you recently installed Ubuntu Hardy Heron 8.04 and discovered that your laptops function keys are not properly adjusting the brightness. In essence, you are pressing the key combination and nothing is happening.
- AaronMT

I have Kubuntu on Acer Aspire with nVIDIA 7000m (610)
My problem is slightly different. Bright* controll works, but everytime system starts, screen is frying my eyes like two eggs by going to brightest option after desktop loads.

Interesting thing is that during startup it remembers old settings, and when desktop and all programs are fully loaded - bang & flash!

I have installed xbacklight, but it doesn't work. Just returns:

(after $ xbacklight -set 50)

No outputs have backlight property

I am new user and have no idea what to do now. 
- Can you help ?

---

### Post by mb_webguy on 2008-08-31
> **growingneeds said:**
> I managed to fine-tune the LCD brightness to a greater degree by adding the 'Brightness Applet' to the Gnome Panel.
1.Right-click a specified location on the Gnome Panel and select 'Add to Panel...'
2.Select 'Brightness Applet'.

To achieve 7 adjustable levels of brightness on the function keys (instead of the usual 3), and to keep the LCD brightness from being set at the maximum after every reboot:
1.In a terminal, type “gksudo gedit”.
2.Open the file “/etc/modprobe.d/blacklist”.
3.Add a new line “blacklist video”.
4.Reduce brightness to mimimum (or desired level).
5.Reboot.

The OP's solution didn't work for me, even after altering the script to work with my Dell Inspiron 1720.

Growingneed's solution, however, worked perfectly.  Thanks!

---

### Post by treesurf on 2008-08-31
Yippee!!  The original post worked wonderfully for me on a Gateway N570X.  Thank you!

---

### Post by jeromer43 on 2008-08-31
Worked on my Dell 1501 also.   Sometimes have trouble with the AMD64 processor.  (Still trying to work out the Brother printer.)

Thanks!  One less problem!

---

### Post by Gorgoth on 2008-09-02
Works nicely on a Gateway MT6840. Thanks :D

---

### Post by scathmandra on 2008-09-15
Doesn't work on the Dell Inspiron 1501--at least, not mine.

*sigh* I'm never gonna get this brightness issue solved...

---

### Post by Red.Rabbit on 2008-09-15
Tested on my Gateway M-6843 and works perfectly. Thanks a lot. :)

---

### Post by rekado on 2008-09-23
None of the workarounds mentioned worked for my notebook (Haier A61). I can write to the brightness file (in IGD instead of VGA) but the brightness will not change. The brightness can only be changed before booting Linux from GRUB.
Booting without ACPI support also fixes that - but you are losing so much more for just making the brightness work...

---

### Post by Tsunami713 on 2008-10-02
used it on my ibm t40 it didint work TT.TT

---

### Post by skippuff54 on 2008-10-02
i fixed brightness on a toshiba satellite laptop by using gconf editor

```
gksudo gconf -editor
```

then going to /apps/gnome-power-manager/backlight and set everything to 100

that&#347; how i fixed it. after i did that, i found out i could also add a brightness meter to the panel

right click on panel> add to panel> brightness applet

---

### Post by Zdravko on 2008-10-02
I have an Acer Aspire 5715z and the brightness keys do function. However, each time Ubuntu starts with lowered brightness level and I have to increase it :( Any ideas?

---

### Post by kmself on 2008-10-23
A couple of notes.

The script could be a lot shorter and simpler.  The sample below shows code to step the brightness down by a value of 10 from the current value with a floor check of 0.

The specific file in which the brightness values are adjusted seems to move around a bit.  I've abstracted this to an environment variable (BRIGHTFILE).  You may have to search through /proc/acpi/video to find various files named 'brightness' and toss values at them to see what actually controls behavior.  Code below is for a Lenovo T61.

```
#!/bin/bash

BRIGHTFILE=/proc/acpi/video/VID1/LCD0/brightness
CURRENT=$(awk '$1 == "current:" {print $2}' $BRIGHTFILE )
echo "Current: $CURRENT"

NEW=$(( CURRENT - 10 ))
if [ $NEW -lt 0 ]; then NEW=0; fi

echo -n "$NEW > $BRIGHTFILE"
```

---

### Post by bazu on 2008-10-23
Dosen`t work at fujitsu siemens amilo p 3553

---

### Post by odysseusjak on 2008-10-25
Worked on my Gateway M-6843.  Thanks a lot!

---

### Post by the_fury on 2008-11-02
> **skippuff54 said:**
> i fixed brightness on a toshiba satellite laptop by using gconf editor

```
gksudo gconf -editor
```

then going to /apps/gnome-power-manager/backlight and set everything to 100

that&#347; how i fixed it. after i did that, i found out i could also add a brightness meter to the panel

right click on panel> add to panel> brightness applet

this "brightness applet" may come in handy... if the brightness would actually change. lol.

i have the power management settings to dim the backlight when i unplug the computer, but it just sits there with 100% brightness, soaking up the battery. it's a sony vaio, which may be part of the problem.. ideas?

---

