---
title: "HOWTO: thumb buttons"
date: 2004-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by TravisNewman on 2004-11-09
Have a Microsoft Intellimouse or a Logitech Mouseman? This will get you going with using the side buttons.

You can also find this document on the wiki at:
[https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons](https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons)

**Step 1:** Editing the config file:
[indent]Edit your /etc/X11/XF86Config-4 or /etc/X11/xorg.conf file so that the mouse section looks like this:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

```
Note1: The resolution option is optional, that's just for mouse accuracy.
Note2: even if you're using a Logitech Mouseman with only one thumb button, this will still work.[/indent]

**Step 2:** Installing imwheel:
[indent]Now we need to install imwheel using apt-get:
```
$ sudo apt get install imwheel
```
or by using synaptic to find and install it.[/indent]

**Step 3:** Creting the imwheel config file
[indent]Create a file called /etc/X11/imwheelrc using your favorite text editor, in this case, nano:
```
$ sudo nano /etc/X11/imwheelrc
```
and put this text in it:
```


".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right

```[/indent]

**Step 4-1:** Configuration for GDM, KDM, and XDM
[indent]If you don't use GDM, KDM, or XDM (if you log in through a graphical interface, you DO use one of these), skip this step. If you do, create a file called "57xmodmap" in /etc/X11/Xsession.d/:
```
 sudo nano /etc/X11/Xsession.d/57xmodmap
```
and put this code in it:
```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"

```
Save the file and then change the permissions so that it can be executed:
```
sudo chmod 777 /etc/X11/Xsession.d/57xmodmap
```
To explain the naming convention, the number at the beginning tells the xsession when to load a process. If you list the contents of /etc/X11/Xsession.d/ you'll notice that the file starting with 60 is the imwheel script. It was automatically created when installed. We need the xmodmap to run before that, so I chose 57. Now log out and log back in to get everything working. You should now be able to use the forward and back buttons (or just the back button, depending on how many buttons your mouse has). Log out and log back in to see the changes.[/indent]

**Step 4-2:** Editing for startx users
[indent]If you use GDM, KDM, or XDM, you're already done. If you use text mode login and use startx to enter X, put the following in your /home/username/.xinitrc file, before the line that starts your window manager (which you have to have if you're using an .xinitrc, as far as I can tell):
```

xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &

```

You may have to make this file. If so, be sure you put in
```
gnome-session &
``` or ```
startkde &
``` or whatever command your Window Manager uses at the very end of it. Log out and log back in to see the changes.[/indent]

This concludes the tutorial. Maybe that expensive mouse wasn't a waste after all!

---

### Post by TravisNewman on 2004-11-10
Edited to include instructions for GDM users.
See if there's anything you think I should add/remove or if there's any easier ways to do some of these things.

I hope this helps some people with their mouse problems! Maybe I'll even get stickied!

---

### Post by TravisNewman on 2004-11-10
Could a mod please change the title of this topic to "Intellimouse/Mouseman extra buttons config"? I changed it in the title on the top post, but I guess that just changes the title of the first post and not the topic title itself. Thanks!

---

### Post by volvoguy on 2004-11-11
Hey thumb man. :-)

The GDM instructions work great! This was the last major thing that was bugging me in Ubuntu, so I'm a happy man. 

I signed up to the forums to elect this as a sticky. Is this all I need to do? 

Thanks again!

---

### Post by TravisNewman on 2004-11-11
[QUOTE=volvoguy]Hey thumb man. :-)

The GDM instructions work great! This was the last major thing that was bugging me in Ubuntu, so I'm a happy man. 

I signed up to the forums to elect this as a sticky. Is this all I need to do? 

Thanks again![/QUOTE]
 Thanks for the support volvoguy. I guess more people need to think that its useful before it'll get stickified. I think it's useful, you think its useful,  but what do other people think? If you really like it you can give it a high rating (see the rating section at the top). I don't know if that's what they base what gets sticky and what doesn't, but hey, it's still giving the thread a high rating.

---

### Post by oddabe19 on 2004-11-11
Excellent Job!!!!!! My intellimouse works perfectly now.

You my friend, are my hero.

I could never fully get thumbbuttons to work on gentoo.

---

### Post by HiddenWolf on 2004-11-11
If it works in GDM, I'll go and try it right now, and you are my savior.

This is indeed the last thing that bugged me.

---

### Post by TravisNewman on 2004-11-11
[QUOTE=HiddenWolf]If it works in GDM, I'll go and try it right now, and you are my savior.

This is indeed the last thing that bugged me.[/QUOTE]
 It was the one thorn in my side for a couple years until I pieced together all the documentation I could find and figured out how to do it.

Let me know how it works! :)

---

### Post by HiddenWolf on 2004-11-11
Definatly works. Very smooth, very helpfull

Actually I feel this should be automated, but since that's probably not possible, it should be wiki or manual.

---

### Post by TravisNewman on 2004-11-11
I'm adding this to the wiki. Learning a new markup language in the process (ReST), so it may be a bit. I'll post here when it's done.

---

### Post by TravisNewman on 2004-11-11
OK maybe I won't be adding to the wiki, I didn't know you had to have special privileges for adding pages to it. If anyone with privileges wants to add it, I have it in ReST format already if you want to put it up, or alternatively, if someone can tell me how to get these privileges, I'll put it up.

Edit: I still don't know why I was getting that error, but it saved it anyway.

---

### Post by TravisNewman on 2004-11-11
[https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons](https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons)
This is the new home of the wikipage. Test it out and make suggestions!

---

### Post by zenwhen on 2004-11-13
This HOWTO made my night. Ive gotten so many obscure things working in Linux, and this always eluded me in Slackware. I copied and pasted my way to victory. Thanks so much.

---

### Post by TravisNewman on 2004-11-13
[QUOTE=zenwhen]This HOWTO made my night. Ive gotten so many obscure things working in Linux, and this always eluded me in Slackware. I copied and pasted my way to victory. Thanks so much.[/QUOTE]
 Excellent, glad to hear that it's working for you! I'm always here to help (and to get help)!

---

### Post by Zundfolge on 2004-11-15
[QUOTE=panickedthumb]**Step 2:** Installing imwheel:
[indent]Now we need to install imwheel using apt-get:
```
$ sudo apt get install imwheel
```
or by using synaptic to find and install it.[/indent][/QUOTE]

Hmm ...  can't find imwheel

when I type *$ sudo apt-get install imwheel*

I get:

> Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package imwheel

and I can't find it using synaptic   :-|

---

### Post by adbak on 2004-11-15
Enable Universe repository, reload.

---

### Post by TravisNewman on 2004-11-15
You have to enable universe. There's a thread in the how-to forum about how to do this.

Edit: aaahhh you beat me to it

---

### Post by FLeiXiuS on 2004-11-16
Alright here is something I haven't been able to do.  Get my MX-510 forward / back buttons to work with firefox.  It's simply not working even after IMwheel.  Roar?

---

### Post by TravisNewman on 2004-11-16
did you do all the steps? Editing the config, the xmodmap, imwheel, all of it?

It might use a different mapping, I dunno.

---

### Post by FLeiXiuS on 2004-11-16
Just about everything...I'll get it working later today lol.  I'm determined. 8-[

---

### Post by TravisNewman on 2004-11-16
Be a brave little toaster FleiXius!

---

### Post by TravisNewman on 2004-11-17
Hey, at some point in upgrading packages in hoary (apparently) this has stopped working in Nautilus. Any clue why that may be?

---

### Post by bob k on 2004-11-19
I did the steps outlined but my mouse didn't respond the way it was supposed to.  My wheel is now my fwd page and back page and my thumb buttons are up and down without repeat. I'm thinking it is in the imwheelrc file. Can you give more info on the options in imwheel, so that I can try to remap my buttons.

MOUSE

A4Tech wireless

TIA
Bob

---

### Post by TravisNewman on 2004-11-19
It sounds like the xmodmap didn't work. Check that you created the startup script correctly.

---

### Post by bob k on 2004-11-19
Thanks this is GREAT, My bad I missed a step

Thanks again
Bob

---

### Post by zenwhen on 2004-11-19
[QUOTE=panickedthumb]Hey, at some point in upgrading packages in hoary (apparently) this has stopped working in Nautilus. Any clue why that may be?[/QUOTE]

Hmm... never did work in Nautilus for me.

---

### Post by TravisNewman on 2004-11-19
[QUOTE=zenwhen]Hmm... never did work in Nautilus for me.[/QUOTE]
 Bob K: excellent :) glad its working for you!

zen: poop. Why did it work for me? Come to think of it, it may not have worked for me in Ubuntu ever, but it DID work in Gentoo. Probably different configuration, I guess the hotkeys are different in Nautilus.

---

### Post by zenwhen on 2004-11-19
Perhaps, but I wish you hadn't mentioned it. :(

I'll poke around and see what I can do.

---

### Post by travisat on 2004-11-22
interesting.  However I got my Logiteck mx700 to work with hoary (xorg) by just installing imwheel and editing the xorg.conf file by adding the buttons option to 7 and the type from IMPS/2 to ExplorerPS/2.  Might work without imwheel and in warty.

---

### Post by unikum on 2004-11-22
Help, how do i get back the old settings?

Edit: I found an old copy. Puh!

---

### Post by TravisNewman on 2004-11-22
[QUOTE=travisat]interesting.  However I got my Logiteck mx700 to work with hoary (xorg) by just installing imwheel and editing the xorg.conf file by adding the buttons option to 7 and the type from IMPS/2 to ExplorerPS/2.  Might work without imwheel and in warty.[/QUOTE]
 You definitely need imwheel, but it may work without xmodmap now. I know that before, and with other distros, something about the protocol wouldn't let you use those buttons accurately without remapping them.

---

### Post by Infamous Jum on 2004-12-05
Hello all, I'm completely new to Linux and all of this is a pretty big learning experience for me-really takes me back to the days of my first PC. Anyway, I follow these steps, but now my scroll wheel up and down are foward and back, and me left thumb button (which is the only thumb button on this mouse) scrolls up. I'm using an IBM mouse so maybe thats the problem, but this is the only guide I could fine so I figured I'd give it a try. I ran xev and it is mapping the buttons (scroll wheel is 6 & 7 and the thumb button is 4), so maybe the imwheelrc needs to be altered. Again, I'm brand new to this so any help would be greatly appreciated. Thanks for the guide, at the very least its taught me a thing or two I didn't know before :).

---

### Post by TravisNewman on 2004-12-05
Seems like the xmodmap isn't working. Double check your work in step 4 and make sure you did everything.

---

### Post by Infamous Jum on 2004-12-05
Right you are, I printed the instructions rather than just read from the site, and it put #/bin/bash on the same line as the mapping. I thought it looked odd when I typed it, but then I'm pretty new so I didn't realise that # is a comment tag, thus making the whole line useless. Although I would have to ask, should then the first line of step 4 be #/bin or #!/bin? Either I misunderstand the comments or that line isn't really needed. Again, thanks a ton for the help!

---

### Post by TravisNewman on 2004-12-05
That line, albeit a commented line, is necessary in UNIX scripts. I've never understood why exactly, I think it tells the system what to use, and it looks in the initial comment for that, so it's not actually executed, but I really don't know. I need to get out my UNIX book ;)

---

### Post by kingmob on 2004-12-10
[QUOTE=panickedthumb]That line, albeit a commented line, is necessary in UNIX scripts. I've never understood why exactly, I think it tells the system what to use, and it looks in the initial comment for that, so it's not actually executed, but I really don't know. I need to get out my UNIX book ;)[/QUOTE]
 Using this howto i get the following error in xsession-errors:
```

xmodmap:  commandline:0:  bad number of buttons, must have 3 instead of 7
xmodmap:  1 error encountered, aborting.

```

I have done exactly what the howto says. I have a mouseman dual optical, so it's true that i don't have 7 buttons, but i have more than three. I got a wheel and one thumbbutton, so i figured i had 6 buttons. Just don't know how i would change that in all the configs

Ok, i was too fast, the mousewheel works now and i don't get the errors anymore. The thumbbutton still doesn't work though. Anyone?

---

### Post by ensiferum on 2005-01-05
[QUOTE=travisat]interesting.  However I got my Logiteck mx700 to work with hoary (xorg) by just installing imwheel and editing the xorg.conf file by adding the buttons option to 7 and the type from IMPS/2 to ExplorerPS/2.  Might work without imwheel and in warty.[/QUOTE]

Yep. Same here. I've got Logitech mx700, and scroll and back/forward thumb buttons work in hoary without imwheel. Just changed protocol to ExplorerPS/2 in XF86Config-4. I also added "Buttons" "7". 

Just noticed though that the little button on top of the wheel (supposed to be cruise up button or whatever) generates two kinds of events. 4 and 6. This is a bit of a problem. Tried to remap with xmapmod but that didn't help. (Still was getting two events)

---

### Post by ow50 on 2005-01-06
I got my logitech mouseman single thumb button working as a doubleclick. I'll post my settings in case someone finds it useful.

I followed the first post in this topic with the exception that i left the file /etc/X11/imwheelrc empty. Next i created ~/.imwheelrc with the following:
```
".*"
None, Left, Control_L|Shift_L|Pointer_EnableKeys|-Pointer_EnableKeys|-Shift_L|-Control_L|KP_Add|-KP_Add|Control_L|Shift_L|Pointer_EnableKeys

```
For some reason this didn't work for me in /etc/X11/imwheelrc. The single thumb button in my logitech seems to be Left to imwheel. I don't quite understand what that line does but it works.

I found this at [linux questions forum](http://www.linuxquestions.org/questions/showthread.php?s=&forumid=18&threadid=173232).

---

### Post by woodbridge on 2005-01-09
This may also interest some of you. I've got my Logitech MX900 (diNovo) thumb buttons working without using imwheel.

[http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)

A few minor adjustments are needed to get it working,

My xorg.conf mouse section looks like
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol" "evdev"
	Option		"Dev Name" "Logitech USB Receiver" # cat /proc/bus/input/devices
	Option		"Dev Phys" "usb-0000:00:10.0-2.1/input1" # cat /proc/bus/input/devices	
	Option		"Device" "/dev/input/event4" # (/dev/input/mice also appears to work)
	Option		"Buttons" "10"
	Option		"ZAxisMapping" "9 10"
	Option		"Resolution" "800"
EndSection
```

My ~/.xinit file contains 
xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"

I hope this helps some people. :)

---

### Post by ensiferum on 2005-02-05
I have a Logitech mx700 mouse myself and went through the trouble of understanding how X works regarding the mouse. And how the IMWheel works with this. My understanding is not complete yet (and probably never will be) but at least I got the mouse working...

[http://www.student.oulu.fi/~savaisan/stuff/mx700.txt](http://www.student.oulu.fi/~savaisan/stuff/mx700.txt)

---

### Post by siroj on 2005-02-06
After I followed the explanation in the first post in this thread, my Logitech MX500's forward/back-buttons didn't work... (don't know what went wrong)

Google found this page: [http://www.kaltmacher.de/artikel35408-0-asc-0.html](http://www.kaltmacher.de/artikel35408-0-asc-0.html) and after following the procedure laid out in that document, forward/back-buttons worked perfectly... don't know what's so different about the steps in both howtos...

Maybe it's of use to someone... It's in German though...

---

### Post by sagara on 2005-02-10
[QUOTE=woodbridge]This may also interest some of you. I've got my Logitech MX900 (diNovo) thumb buttons working without using imwheel.

[http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)

A few minor adjustments are needed to get it working,

My xorg.conf mouse section looks like
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol" "evdev"
	Option		"Dev Name" "Logitech USB Receiver" # cat /proc/bus/input/devices
	Option		"Dev Phys" "usb-0000:00:10.0-2.1/input1" # cat /proc/bus/input/devices	
	Option		"Device" "/dev/input/event4" # (/dev/input/mice also appears to work)
	Option		"Buttons" "10"
	Option		"ZAxisMapping" "9 10"
	Option		"Resolution" "800"
EndSection
```

My ~/.xinit file contains 
xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"

I hope this helps some people. :)[/QUOTE]


Did u install those patches from Gentoo in order to get this to work?
Step #1 on that site

---

### Post by Datchew on 2005-02-12
am about to try it. 

however, last time i messed with this config file under the X11 dir, i screwed up my X irreparably. 

Suggest everyone do this before you start:

"Fiddling with config files is great, but do this first:
cp configfile configfile.bak
that way once you screw everything up you can just do the reverse command and replace your screwedup file with the origonal one."

---

### Post by Datchew on 2005-02-12
well, i got done and rebooted. 
absolutely nothing has changed. 

i have a logitech M-bj58 regular usb optical mouse with 2 buttons and a scroll wheel. 
scroll wheel already worked when i roll it, but i was hoping this would make it have the function where i click (push down) the scroll wheel and then can move the cursor around to make the screen scroll up/down without turning and turning and TURNING the mousewheel.   

if you have any ideas, i'd love to hear them.

---

### Post by Dihi Doctor on 2005-02-15
I have an MX700 and the mouse section of my XF86Config-4 file looks like this (I followed a guide somewhere). The comments indicate the command you should type to get the "Dev Name" and "Dev Phys" values for your own system.

All the buttons (inc. wheel, cruise and thumb buttons) now work fine in firefox :). I'm a very happy man, Thanks to whoever posted the link and I hope this helps some other MX700 owner

```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Protocol" "evdev"
        Option "Dev Name" "Logitech USB Receiver" # cat /proc/bus/input/devices
        Option "Dev Phys" "usb-*/input0" # cat /proc/bus/input/devices
        Option "Device" "/dev/input/mice" # (/dev/input/mice also appears to work)
        Option "Buttons" "10"
        Option "ZAxisMapping" "9 10"
        Option "Resolution" "800"
EndSection

```

---

### Post by Datchew on 2005-02-15
hmmm....
guess i'll do a backup of the config file and give that a try. 

will post when i get done... probably this weekend.

---

### Post by miatapaul on 2005-02-22
I got this to work. I tried the method with the edev as the person in another post said we did not need to do the patches, no joy for me. I tried this and side buttons work but not the cruse or the other one on my MX700 do you think we could get this to work for those buttons by using 10 instead of 7? I figure I will have to add the buttons to the other fields as well. any ideas? i am done hosing my system this afternoon, perhaps tonight?

---

### Post by JohnQ on 2005-02-24
Just now got this to work WITHOUT imwheel.  (Similar to the above)  When I used imwheel, my top "fast scroll" button went back in history while everything else worked as it should.  This problem has been resolved by not using imwheel.

In my /etc/X11/xinit/xinitrc file I have added:
/usr/bin/X11/xmodmap -e "pointer = 1 2 3 6 7 4 5"

And in my xorg.conf  file (I'm running Hoary) I commented out the old pre-configured stuff and replaced it with:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
## Using a fix from [http://www.ubuntuforums.org/showthread.php?t=3828&page=5&pp=10](http://www.ubuntuforums.org/showthread.php?t=3828&page=5&pp=10)
        Option          "Protocol" "evdev"
        Option          "Dev Name" "Logitech USB Receiver" # cat /proc/bus/input/devices
        Option          "Dev Phys" "usb-0000:00:0d.0-3/input1" # cat /proc/bus/input/devices
        Option          "Device" "/dev/input/event4"
        Option          "Buttons" "7"
        Option          "ZAxisMapping" "4 5"
EndSection

Note the different ZAxisMapping.  Also, be sure to change the values of Dev Name, Dev Phys, and Device to the appropriate values of your system (`cat /proc/bus/input/devices`).  Also, if this is your second pointer (like it is mine) be sure to add Option "SendCoreEvents" "true" in there.

Hope this helps someone else!

John

---

### Post by jtopping on 2005-02-24
anyone done the following on a Logitech "Click Plus" mouse(it comes with the LX700 desktop kit.

I can get the thumbs working good, but I have a left to right scroll wheel and an application switch button...any ideas on these?

---

### Post by martijntje on 2005-02-26
[QUOTE=jtopping]anyone done the following on a Logitech "Click Plus" mouse(it comes with the LX700 desktop kit.

I can get the thumbs working good, but I have a left to right scroll wheel and an application switch button...any ideas on these?[/QUOTE]
 This worked great! Thanks alot.

Anyways, you have "apt get" instead of "apt-get", but that's the only thing i can find that's incorrect.

---

### Post by Sapper2ID on 2005-02-28
I've found 2 different ways to get my MX700 working but am currently using the config in the first post. I allways seem to have the same problem. My MX sometimes (40%) goes back 2 pages when using my back thumb button. All else works great.
I've changed nothing in Firefox about:config except for ipv6.

Warty 2.6 K7
Mouse hooked to PS/2

---

### Post by martijntje on 2005-02-28
[QUOTE=Sapper2ID]I've found 2 different ways to get my MX700 working but am currently using the config in the first post. I allways seem to have the same problem. My MX sometimes (40%) goes back 2 pages when using my back thumb button. All else works great.

Warty 2.6 K7
Mouse hooked to PS/2[/QUOTE]
 That's really strange, because i use the MX700 too, and it works great here!

---

### Post by Mike Eberhart on 2005-03-01
Can someone explain to me why if I use Knoppix with the same computer that I am having Intellimouse thumb-button issues under Ubuntu, the Knoppix Linux automatically sets up my mouse-buttons just fine.

Is this because KDE has something built-in to recognise and configure Intellimouse properly, or is it a Knoppix thing?

Either way, does anyone in development land plan to fix this in Ubuntu code (in the core, Gnome, or wherever it needs fixed?).

---

### Post by globalspace on 2005-03-05
Oh yes !!!!
Thanks a lot !!
Now my Logitech Mx 700 works like in WIndows !!!  :D 

ehmmm one thing please :
if i click my Button to scrool down/up (the button near the scroll) the movement is very slowly ... is there a configuration to do it more quickly ?

if not .. NO PROBLEM ! ;)

---

### Post by vassalle on 2005-03-15
hi, the howto works, in firefox atleast.. is there a way to make it work in nautilus ? thanks !

---

### Post by audscott on 2005-03-19
Worked great!!

Thanks!

I had been going a bit ape without my thumb buttons (forward/back) on my Logitech MX1000.

By the way, these enhanced "how to:" are really a God send for us Linux newbys.   \\:D/

---

### Post by dlpfmVfH on 2005-03-23
[QUOTE=panickedthumb]Have a Microsoft Intellimouse or a Logitech Mouseman? This will get you going with using the side buttons.

You can also find this document on the wiki at:
[https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons](https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons)

**Step 1:** Editing the config file:
[indent]Edit your /etc/X11/XF86Config-4 or /etc/X11/xorg.conf file so that the mouse section looks like this:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

```
Note1: The resolution option is optional, that's just for mouse accuracy.
Note2: even if you're using a Logitech Mouseman with only one thumb button, this will still work.[/indent]

**Step 2:** Installing imwheel:
[indent]Now we need to install imwheel using apt-get:
```
$ sudo apt get install imwheel
```
or by using synaptic to find and install it.[/indent]

**Step 3:** Creting the imwheel config file
[indent]Create a file called /etc/X11/imwheelrc using your favorite text editor, in this case, nano:
```
$ sudo nano /etc/X11/imwheelrc
```
and put this text in it:
```


".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right

```[/indent]

**Step 4-1:** Configuration for GDM, KDM, and XDM
[indent]If you don't use GDM, KDM, or XDM (if you log in through a graphical interface, you DO use one of these), skip this step. If you do, create a file called "57xmodmap" in /etc/X11/Xsession.d/:
```
 sudo nano /etc/X11/Xsession.d/57xmodmap
```
and put this code in it:
```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"

```
Save the file and then change the permissions so that it can be executed:
```
sudo chmod 777 /etc/X11/Xsession.d/57xmodmap
```
To explain the naming convention, the number at the beginning tells the xsession when to load a process. If you list the contents of /etc/X11/Xsession.d/ you'll notice that the file starting with 60 is the imwheel script. It was automatically created when installed. We need the xmodmap to run before that, so I chose 57. Now log out and log back in to get everything working. You should now be able to use the forward and back buttons (or just the back button, depending on how many buttons your mouse has). Log out and log back in to see the changes.[/indent]

**Step 4-2:** Editing for startx users
[indent]If you use GDM, KDM, or XDM, you're already done. If you use text mode login and use startx to enter X, put the following in your /home/username/.xinitrc file, before the line that starts your window manager (which you have to have if you're using an .xinitrc, as far as I can tell):
```

xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &

```

You may have to make this file. If so, be sure you put in
```
gnome-session &
``` or ```
startkde &
``` or whatever command your Window Manager uses at the very end of it. Log out and log back in to see the changes.[/indent]

This concludes the tutorial. Maybe that expensive mouse wasn't a waste after all![/QUOTE]
 "(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

this one is needed for konqueror

---

### Post by jeremy on 2005-03-25
[QUOTE=vassalle]hi, the howto works, in firefox atleast.. is there a way to make it work in nautilus ? thanks ![/QUOTE]
Yes, if anyone knows, please pass it on. The keyboard shortcuts for nautilus are the same as before, ie. alt + left arrow = back, alt + right arrow = forward.

---

### Post by adbak on 2005-04-05
Anyone know how to make this work with Hoary/Xorg?  I miss being so lazy.  It seems like so much work to go _all_ the way to the upper left corner to go "back".  Hrmph.

---

### Post by TravisNewman on 2005-04-05
Actually, in hoary it's much easier. Just edit the xorg.conf to add buttons, set the z-axis to 4 and 5, and emerge imwheel.

Edit: oh my god! I can't believe I just said "Emerge." I haven't even used gentoo in about 8 months. I meant apt-get install imwheel, of course.

---

### Post by Obsidians on 2005-04-08
I've got most of the functions on my MX700 working, except for the fast scroll buttons, the ones just above and below the scroll wheel. The problem is that, no matter what, it always sees the top one as the same button as the back thumb button, and it doesn't register the down button at all. Even with no Zmapping and no xmodmap, the buttons just don't register properly. Changing the protocol doesn't seem to have any affect, so I just left it on Auto. How do I get those buttons to register properly?

---

### Post by CowPie on 2005-04-08
[QUOTE=Obsidians]I've got most of the functions on my MX700 working, except for the fast scroll buttons, the ones just above and below the scroll wheel. The problem is that, no matter what, it always sees the top one as the same button as the back thumb button, and it doesn't register the down button at all. Even with no Zmapping and no xmodmap, the buttons just don't register properly. Changing the protocol doesn't seem to have any affect, so I just left it on Auto. How do I get those buttons to register properly?[/QUOTE]

Protocol MUST be ExplorerPS/2
"Option" "Buttons" "a"

a should equal the number of buttons you have, excluding the scroll wheel, then add to 2. (so 5 buttons would be inserered as 7)

But I dunno if it will work with those fast scroll buttons.. :(

---

### Post by Obsidians on 2005-04-08
[QUOTE=CowPie]Protocol MUST be ExplorerPS/2
"Option" "Buttons" "a"

a should equal the number of buttons you have, excluding the scroll wheel, then add to 2. (so 5 buttons would be inserered as 7)

But I dunno if it will work with those fast scroll buttons.. :([/QUOTE]
 Thanx, but that didn't help either. The protocol doesn't seem to have any effect at all on the buttons or anything. I've got:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2" 
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "10
        Option          "ZAxisMapping"          "4 5"
EndSection

to get most of it working, but it simply doesn't recognize the button presses correctly, it insists that the top button is actually the same button as the back button.

---

### Post by Lupine on 2005-04-10
I have a similiar setup with the mx510 and the same problem.  The little buttons above the scroll wheel don't seem to work no matter what configuration I throw at them.  I'm trying to get this to work with UT2k4.  ](*,)

---

### Post by idn on 2005-04-11
Good tutorial, worked perfectly for me.

---

### Post by morphodone on 2005-04-12
awesome, just did this in hoary and it worked great \\:D/

---

### Post by Spudgun on 2005-04-12
Hi there,
Will this also work with my Logitech MX500?
Thanks in advance,
Spudgun

---

### Post by Lupine on 2005-04-12
And if someone could post files and results from a mx510, I would appreciate it.  I'm still having no luck with the buttons below and above the scroll button.

Thx,
Lup

---

### Post by skwerl530 on 2005-04-13
Great How to.  I am a first time Ubuntu user and new to Linux in general.  This worked very well for my intellimouse 2.0.  Using Gnome I never had to install IMWheel.  The only problem I had was the side buttons controlled scrolleding and the  mouse wheel controlled forward and back.  I just edited the xorg.conf file to map the z axis to "4  5" instead of "6 7" as shown in this guide.  That fixed it straight off with no other issues. 

Thanks for the great info.  Now if I can only get this cursed soundblaster live 24 bit playing...

---

### Post by Slalomsk8er on 2005-04-14
Logitech mx 510:

It works but fast scroll up is now scrolling plus back and the window switcher is still not working.

I have to go to sleep now but I will look more in to it.

Thanks,
Dominik

---

### Post by Firetech on 2005-04-19
[QUOTE=Slalomsk8er]Logitech mx 510:

It works but fast scroll up is now scrolling plus back and the window switcher is still not working.

I have to go to sleep now but I will look more in to it.

Thanks,
Dominik[/QUOTE]
I had the same problem with my MX700 (Codless Optical Desktop MX), but when I moved it from the USB port to the separate PS/2 ports, it workes perfectly (Apart from the scrollwheel of the keyboard, which now instead of trigging scroll-buttons (of the mouse), now trigs the up/down arrow keys, but I almost never use that wheel...)

---

### Post by asimon on 2005-04-20
Having only mice with thumb buttons this is usally one of the first things I do after installing a Linux distribution.

But actually I think it's quite sad that after so many years (just look how many mice have thumb buttons nowadays) there is not even one Linux distribution which sets this up automatically. Most distros detect my mouse correctly, but not one configures it right.

Regarding the setting of the Resolution. With my intellimouse explorer this setting doesn't seem to have any effect at all. I can set it to everything between 50 and 2000 but perceive no difference.

Someone mentioned that this doesn't work with Gentoo: it does, Gentoo just has no /etc/X11/Xsession.d/ so you have to put the commands somewhere else like Xsession.

---

### Post by Heliode on 2005-05-16
I'm using this (on Hoary) for my MX1000:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol"      "evdev"
        Option          "Dev Name"      "Logitech USB Receiver" #cat /proc/bus/input/devices
        Option          "Dev Phys"      "usb-0000:00:1d.0-1/input0" #cat /proc/bus/input/devices
        Option          "Device"        "/dev/input/mice"
        Option          "Buttons"       "12"
        Option          "ZAxisMapping"  "4 5"
        Option          "Resolution"   "800"
        Option          "CorePointer"
EndSection

With this all buttons do their job except for the horizontal scroll buttons.

---

### Post by whiskybar on 2005-05-16
Hi everyone,

since there is no definitive guide to configuring the mouse with several buttons in Ubuntu, I bringing in my experience; hopefully it will be of some help to someone. My goal is to control Konqueror using Logitech MX510.

With the help of the guides in this thread, I have come to the following:

1. To use *evdev*, I had to unplug my other USB devices (printer, palm, and camera). I am not sure which device is causing the conflict but with all of them plugged in, the X won't start - the mouse init will fail. Then, I included the following in */etc/X11/xorg.conf*:

```

    Section "InputDevice"
          Identifier  "Configured Mouse"
          Driver "mouse"
          Option "CorePointer"
          Option "Protocol" "evdev"
          Option "Dev Name" "*"
          Option "Dev Phys" "usb*"
          Option "Device" "/dev/input/mice"
          Option "Buttons" "12"
          Option "ZAxisMapping" "4 5"
          Option "Resolution" "800"
    EndSection

```
   Note that the number of buttons is 12 even though the mouse has 10 buttons. Read on to find out why.

2. Get logitech_applet ([http://freshmeat.net/projects/logitech_applet](http://freshmeat.net/projects/logitech_applet)) from [http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz](http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz). *./autogen.sh && make && sudo make install* (or use *dpkg-buildpackage* to create a package). Create */etc/init.d/logitech-applet*:

```

    #!/bin/sh
    #
    # Set the mouse resolution to 800 and disable the cruise control
    #
    
    case "$1" in
    start)
            logitech_applet -s 800 -d
            exit 0
            ;;
    stop|restart|force-reload)
            exit 0
            ;;
    *)
            echo "Usage: $0 {start|stop|restart|force-reload}" >&2
            exit 3
            ;;
    esac

```
   Then, make it start on boot: *update-rc.d logitech-applet defaults*

3. Rearrange the buttons each time X starts by creating *~/.xinit*:

```

    xmodmap -e "pointer = 1 2 3 6 7 8 9 10 11 12 4 5"

```
4. Install the applications that will process the mouse events: *apt-get install xbindkeys xvkbd*. Last, put the actual bindings into *~/.xbindkeysrc* (the comments decribe the extra mouse buttons):

```

    #side down aka right aka forward (Page forward)
    "xvkbd -xsendevent -text "\A\[Right]""
      m:0x10 + b:6
    
    #side up aka left aka back (Page back)
    "xvkbd -xsendevent -text "\A\[Left]""
      m:0x10 + b:7
    
    #window aka tasksel (Close the current tab)
    "xvkbd -xsendevent -text "\CW""
      m:0x10 + b:8
    
    #fast down (Move to the end of the document)
    "xvkbd -xsendevent -text "\[End]""
      m:0x10 + b:12
    
    #fast up (Move to the beginning of the document)
    "xvkbd -xsendevent -text "\[Home]""
      m:0x10 + b:10

```

---

### Post by Fandu on 2005-05-22
**whiskybar:**

Did you have to install the patches to get evdev working?  If so, how did you do it??

---

### Post by Firetech on 2005-05-22
[QUOTE=Fandu]**whiskybar:**

Did you have to install the patches to get evdev working?  If so, how did you do it??[/QUOTE]
 You don't need to apply the X patches. Just make sure the evdev module is loaded with "sudo modprobe evdev"

---

### Post by fivre on 2005-06-18
[QUOTE=Firetech]You don't need to apply the X patches. Just make sure the evdev module is loaded with "sudo modprobe evdev"[/QUOTE]
 Will this allow me to use [middleclick] as Ctrl+T (new tab in Firefox)?
Or do you have to do something else?

---

### Post by TravisNewman on 2005-06-18
[QUOTE=fivre]Will this allow me to use [middleclick] as Ctrl+T (new tab in Firefox)?
Or do you have to do something else?[/QUOTE]
 that's always just worked for me. Your mouse may only be set to 2 buttons in the x config.

---

### Post by volvoguy on 2005-06-23
Hey all,

I've been using panickedthumb's instructions for getting my Intellimouse to work since the day he posted them. Since my upgrade to Breezy, things are really behaving badly and I can't figure out what/why things changed. It's kinda hard to tell what's going on but the scrollwheel now scrolls through the history in the address bar of firefox, and the back/forward buttons don't seem to do anything. 

Were there some low level changes somewhere that might have broken things? 

Thanks!

Aaron - [http://www.volvoguy.net/ubuntu/](http://www.volvoguy.net/ubuntu/)

---

### Post by TravisNewman on 2005-06-23
I haven't upgraded to breezy yet, so I have no knowledge of what it does differently. Sometime soon I will be setting up breezy, but that will be after our honeymoon, so hopefylly someone ehlps before then.

and Aaron-- I thought you had more than 3 posts.

---

### Post by volvoguy on 2005-06-23
[QUOTE=panickedthumb]I haven't upgraded to breezy yet, so I have no knowledge of what it does differently. Sometime soon I will be setting up breezy, but that will be after our honeymoon, so hopefylly someone ehlps before then.

and Aaron-- I thought you had more than 3 posts.[/QUOTE]

You know, I would have thought I'd have had more than 3 posts too. I guess that's what I get for using the mailing list directly. I drink enough espresso that I should probably have the designation "Permanently Wired'. I'm still dealing with some medical problems which is why I've been nearly silent the last few months. I've been USING Ubuntu a lot - one Hoary server, one Hoary desktop and an "I don't care if it breaks" Breezy desktop. I just haven't had much energy to work on the artwork stuff - which is really the most significant way I can contribute to things.

I'll be happy to provide any log or error files to help track this down - but for my part I don't know much more about the whole mouse config issue than what's in your HOWTO. If no one else steps up to the plate, I'll look forward to your return from your honeymoon. (btw - congrats and have a great time!)

Breezy seems to be leveling out a bit in terms of stability. It should definitely be "usable" by the time you get back. 

In the interest of learning more about a linux system in general, I've taken on another OS on my test machine - Gentoo. So far I'm not getting very far with mouse configuration there either, but perhaps my deep digging around in the system will help me figure out a solution. I'll keep everyone posted if I figure something out.

Aaron - [http://www.volvoguy.net/ubuntu/](http://www.volvoguy.net/ubuntu/)

PS - If the moderators want to move this somewhere else since it's Breezy related, that's fine. I just posted here because of the original "thumb buttons" HOWTO.

---

### Post by doans on 2005-06-24
[QUOTE=vassalle]hi, the howto works, in firefox atleast.. is there a way to make it work in nautilus ? thanks ![/QUOTE]

I know this is an old thread but I wanted to pass on my solution to get the side buttons working in Firefox and Nautilus. I have alread posted another thread about how to do it. Here is the [link.]("http://www.ubuntuforums.org/showthread.php?t=44191")

---

### Post by volvoguy on 2005-06-25
must have been a temporary bug that needed to be squashed. i just "dist-upgraded" today (June 25, 2005) and the functionality seems to have reverted to the desired state. yay! 

also, since i mentioned it previously, it's still broken in gentoo - which i didn't care for at all. yay - reclaimed hard drive space! :-)

Aaron - [http://www.volvoguy.net/ubuntu/](http://www.volvoguy.net/ubuntu/)

---

### Post by asimon on 2005-06-25
[QUOTE=volvoguy]also, since i mentioned it previously, it's still broken in gentoo [/QUOTE]
It's working fine on a ~x86 Gentoo machine of mine.

---

### Post by Cmdrfletcher on 2005-06-26
Very good!

Thank you for this. Worked right "out of the box".

I am using a Logitech MX510... \\:D/

---

### Post by kaiesh on 2005-08-25
\\:D/ 
Just like to say, that I managed to get my Logitech MX900 (bluetooth mouse with 10 buttons) working without using IMWheel. The alterations I made are as follows:

1) I edited my xorg.conf device section to read:
_*/etc/X11/xorg.conf*_
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "evdev" 
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "9 10"
        #Use: cat /proc/bus/input/devices to get YOUR 'Dev Name' and 'Dev Phys' **THEY WILL DIFFER**
        Option          "Dev Name"      "Logitech Bluetooth Mouse"
        Option          "Dev Phys"      "00:07:62:2E:6F:38"
        Option          "Resolution"    "800"
EndSection
```

Once I did this, I had to play around a bit with keymappings  :roll: , but I finally found that the following works best:
```
 xmodmap -e "pointer = 1 2 3 6 7 9 10 8 4 5"
```

That gets all the forward/back, up/down, left/middle/right buttons working - **but** I haven't managed to map the application switching button to anything *yet*.  ;-) 

**NOTE:** You can play around with xmodmap in a terminal and test the results, but if you want it to automatically happen when you load into your graphical session, you should create (or alter) the file:
```
/home/<your username>/.xinit
``` 
to include the *xmodmap* line above (or whichever one you choose).
*(note the **dot** before the file name - that keeps it hidden)*

The .xinit file simply a startup script to be executed upon interface load.

So in briefy summary:
1) Make a backup of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup_conf
``` 
2) Find out your mouse details by executing the command:
```
cat /proc/bus/input/devices
```
3) Implement the changes to the xorg.conf as detailed above, taking into account the information from **step 2**
4) Edit your .xinit file as detailed above.
5) Restart X (logout cleanly as that's always nice, then at the Login prompt hit "Ctrl-Alt-Backspace")
6) Dance!  \\:D/

---

### Post by Avarweth on 2005-09-17
I completed this guide, and it worked... after a fashion.

It seems that my scroll wheel is my "back and forward" and my left-side buttons scroll - and backwards - the "back" button scrolls down, and the "forward" button scrolls up.

What settings in what files do I need to change?

Thank you so much!

[EDIT] I found my error - I thought I'd completed the steps exactly, but was confused by step 4-1: I thought that if I logged in through a graphical interface I did not have to do that one. Once I did, no problems.

Thanks for the guide!

---

### Post by southernman on 2006-01-13
Thank You panickedthumb(sp)!!! Your a champion!

I did everything except installing imwheel, yet my forward and back button works like a charm. The only thing that doesn't work is my clickable (locking) scroll wheel. I suppose doing the imwheel steps will correct this, but I think I'll run a backup first. I'll have to look into adding universe to synaptic first though. It's always something with us new *nixers

Thanks again for the time you (and others like you) put into helping everyone!

---

### Post by jscat on 2006-02-12
Thanks, worked like a charm.

---

### Post by Vetto on 2006-02-18
exactly what i have trying to get configured for 3 days...thanks for the how-to!  works great on Kubuntu Breezy also.

---

### Post by Angry penguin on 2006-02-25
I tried this howto on my generic GE 5 button mouse and it doesnt seem to have worked. My xserver is no longer starting, it gives the following error:

"error opening security policy file /etc/xserver/SecurityPolicy FreeFontPath: FPE "/usr/shar/X11/fonts/misc" refcount is 2, should be 1; fixing."

I just recently switched to Dapper, does this have anything to do with this not working for me?

It shows my nvidia splash screen and acts like it is starting X but when it goes to start GDM it crashes.

Any suggestions?
thanks.:cry:

---

### Post by volvoguy on 2006-02-26
[QUOTE=Angry penguin]I tried this howto on my generic GE 5 button mouse and it doesnt seem to have worked. My xserver is no longer starting, it gives the following error:

"error opening security policy file /etc/xserver/SecurityPolicy FreeFontPath: FPE "/usr/shar/X11/fonts/misc" refcount is 2, should be 1; fixing."

I just recently switched to Dapper, does this have anything to do with this not working for me?

It shows my nvidia splash screen and acts like it is starting X but when it goes to start GDM it crashes.
[/QUOTE]

Hmm... That's a weird error. I don't even have a "/etc/xserver" directory on my system and an error about fonts shouldn't be caused by changing mouse settings anyway. 

I don't have a fix for you, but your problem could be Dapper and the binary Nvidia driver. I haven't been able to get that working yet (the version in the repository or the installer from Nvidia). If you switch back to the "nv" driver, does everything work as it should? 

Aaron

---

### Post by Angry penguin on 2006-02-26
Miraculously, after i told it to shutdown. my xserver started working again. My  forward and back buttons on the mouse still dont work but i'm sure glad to have my xwindows back. Oh well:-k

---

### Post by Flupke on 2006-02-27
My mx510 thumb buttons were working great in xorg 6.8 (breezy), and broke in xorg 7 (dapper).
I found the reason [here](http://www.nabble.com/Re:-ms-intellimouse-not-working-right-p2718900.html),  xmodmap is now superseded by xorg.conf "ButtonMapping" option and should not be used anymore for mapping the mouse buttons.

For the impatient, here is my actual config (xorg 7 + logitech mx510, should work for MS Intellimouse too) :
```
Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "5"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
  Option      "Resolution" "800"
EndSection
```

---

### Post by fangorious on 2006-02-28
Flupke you are my hero. This works in dapper with my 6 button Logitech M-B4A7 mouse. (although I set Buttons to 7)

---

### Post by bites on 2006-02-28
@flupke: just one post you've made, but it's one hell of a useful one!  Thanks a lot!

---

### Post by fangorious on 2006-02-28
well, at least for me, this only works for Firefox. Nautilus, Konqueror, and Epiphany all fail to recognize the thumb button. Perhaps imwheel would fix that though.

---

### Post by Flupke on 2006-02-28
Sure the imwheel tricks are still necessary for applications that do not support thumb buttons natively like firefox does.

---

### Post by vassalle on 2006-03-02
hi guys..
how do i do the imwheel trick in xorg 7.0? from the front page, i see that it involves xmodmap which is already superseeded.. 

anyone here knows how to get the side buttons to work in nautilus etc in xorg 7.0?

---

### Post by Flupke on 2006-03-03
I don't know about nautilus since I don't use it, but I tested konqueror and this imwheel config worked :

```
"konqueror"
None, Left, Alt_L|Left
None, Right, Alt_L|Right
```

Compared to what is explained in the front page, you can see that the thumb buttons are now (xorg 7 !) known as Left and Right buttons from X server, which is the way it should be.
Now you could read imwheel documentation if you want finer control on how your thumb buttons are mapped in each application, or maybe replace "konqueror" by ".*" in the example above :)

---

### Post by The J on 2006-03-07
Following the guide, I could only get the side mouse buttons working in Firefox and Nautilus.  I wanted them in Opera and so I spent more time messing with things.  Before, xmodmap would not run since it thinks I have 11 buttons.

I have a Microsoft IntelliMouse Optical 1.0A.  It has its wheel as buttons 4 and 5 and the side buttons are 8 and 9 (from xev).  Buttons 6, 7, 10, and 11 are nothing.  I got things working right by following this guide and setting xmodmap to:

```
#/bin/bash
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 "

```

I have no idea why it thinks there's 11 buttons, but I got things working in Firefox, Opera, and Nautilus using Dapper Drake AMD64.

Hopefully this will help someone with an IntelliMouse.

Edit:  I read in another post that typing **xmodmap -pp** in the terminal will tell you how the buttons of your mouse are mapped.  This might be useful.

---

### Post by Flupke on 2006-03-07
xmodmap is deprecated in xorg 7 (dapper's xorg version), see my post on the previous page :)
For making things work on opera, just see which keyboard shortcuts it uses for previous and next functions, then map them in your imwheelrc.
Refer to the man page of imwheel for more info, really simple to configure for all your apps (once the xmodmap+xorg 7 mess is gone ...)

---

### Post by pkroks on 2006-04-01
[QUOTE=panickedthumb]Have a Microsoft Intellimouse or a Logitech Mouseman? This will get you going with using the side buttons.

You can also find this document on the wiki at:
[https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons](https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons)

**Step 1:** Editing the config file:
[indent]Edit your /etc/X11/XF86Config-4 or /etc/X11/xorg.conf file so that the mouse section looks like this:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

```
Note1: The resolution option is optional, that's just for mouse accuracy.
Note2: even if you're using a Logitech Mouseman with only one thumb button, this will still work.[/indent]

**Step 2:** Installing imwheel:
[indent]Now we need to install imwheel using apt-get:
```
$ sudo apt get install imwheel
```
or by using synaptic to find and install it.[/indent]

**Step 3:** Creting the imwheel config file
[indent]Create a file called /etc/X11/imwheelrc using your favorite text editor, in this case, nano:
```
$ sudo nano /etc/X11/imwheelrc
```
and put this text in it:
```


".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right

```[/indent]

[/QUOTE]


I tried this. When I try to go back/forward. It doesn't work. The forward button acts as a right click button, i.e. the menu pops up and has all the options. 

I have an Intellimouse Explorer 4.0.

Here is my "** imwheelrc **" configuration file. 

```
# IMWheel Configuration file ($HOME/.imwheelrc or /etc/imwheelrc)
# (GPL)Jon Atkins <jcatki@jonatkins.org>
# Please read the README and/or imwheel(1) manpage for info
# and this is best operated on using vim (as I said: It's crunchy)

#
# This is only for demonstration of the priority command...
# See the other global Exclude command below for the one you want to use!
# If this is activated it will only apps that have a lower priority
# priority is based first on the priority command, then the position in this
# file - the higher the line is in a file the higher in a priority class it is
# thus for a default priority you can see that the position in the file is
# important, but the priority command CAN appear anywahere in a window's list
# of translations, and the priority will be assigned to all translations below
# it until either a new window is defined or the priority is set again.
#
#".*"
#@Priority=-1000 #the default priority is zero, higher numbers take precedence
#@Exclude
#@Repeat

# want it to type something?
# this would type "Rofl" and press Return in any window
#".*"
#,Up,Shift_L|R|-R|-Shift_L|O|-O|F|-F|L|-L|Return



# This one rule can send button events, as if you used ZAxisMapping "4 5"
# Make sure your XF86Config allows for the max buttons needed...
# otherwise the events will NOT even be generated...
#".*"
#, Up, Button4
#, Down, Button5
#, Left, Button6
#, Right, Button7
#, Thumb1, Button6
#, Thumb2, Button7
# alternatively with Button numbers
#".*"
#, Button4, Button4
#, Button5, Button5
#, Button6, Button6
#, Button7, Button7
#, Button6, Button6
#, Button7, Button7

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^mutt.*"
None,           Up,     Up
None,           Down,   Down
Control_L,      Up,     Page_Up
Control_L,      Down,   Page_Down

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^aterm"
None,           Up,     Shift_L|Page_Up
None,           Down,   Shift_L|Page_Down
Control_L,      Up,     Up
Control_L,      Down,   Down

#Thanks to Mathias Weyland <mathias@weyland-wtal.de>
"^Xplns"
None,           Up,     Left
None,           Down,   Right
Control_L,      Up,     Up
Control_L,      Down,   Down

"^kvt"
None,		Up,		Shift_L|Page_Up
None,		Down,	Shift_L|Page_Down

"^Konsole"
None,		Up,		Shift_L|Page_Up
None,		Down,	Shift_L|Page_Down

"^XMcd"
None,		Up,		C
None,		Down,	Shift_L|C

"^XMMS_Player"
Shift_L,		Up,		Right
Shift_L,		Down,	Left

"^XMMS_Playlist"
Shift_L,	Up,		Page_Up
Shift_L,	Down,	Page_Down

"^xmms"
Alt_L,		Up,		Z
Alt_L,		Down,	B
Control_L,	Up,		V
Control_L,	Down,	C

"^XATITV-GATOS"
None,       Down,	KP_Subtract
None,       Up,		KP_Add

"^Xman"
None,		Down,	F
Shift_L,	Down,	3
None,		Up,		B

"^Gvi(m|ew)"
Alt_L,	Up,		Page_Up
Alt_L,	Down,	Page_Down
Shift_L,	Up,		Control_L|Y
Shift_L,	Down,	Control_L|E
#None,		Up,		Page_Up
#None,		Down,	Page_Down
#,	Up,	Button4
#,	Down,	Button5
,	Left,	Shift_L|Left
,	Right,	Shift_L|Right
,	Thumb1,	Shift_L|Left
,	Thumb2,	Shift_L|Right

"^VIM"
Shift_L,	Up,		Control_L|Y
Shift_L,	Down,	Control_L|E
#None,		Up,		Page_Up
#None,		Down,	Page_Down

"^Eterm"
Alt_L,		Up,		Up
Alt_L,		Down,	Down
#Alt_L,   	Up,     Shift_L|Page_Up
#Alt_L,   	Down,   Shift_L|Page_Down

#"^GnomeTerminal"
#@Exclude
#@Repeat
#None,		Up,		Shift_L|Page_Up
#None,		Down,	Shift_L|Page_Down

"^NXTerm"
None,   	Up,     Shift_L|Page_Up
None,   	Down,   Shift_L|Page_Down

"^rxvt"
Alt_L,  	Up,		Shift_L|Page_Up
Alt_L,  	Down,	Shift_L|Page_Down

"^XTerm"
Alt_L,		Up,		Shift_R|Page_Up
Alt_L,		Down,	Shift_R|Page_Down
Alt_L,		Left,	Control_L|A
Alt_L,		Right,	Control_L|E
#Shift_L,	Down,	Shift_L|1

"^VMware"
@Exclude
#@Repeat

"^Mozilla-bin$"
#,	Up,	Button4
#,	Down,	Button5
#,	Left,	Alt_L|Left
#,	Right,	Alt_L|Right
#
# If you want to scroll by a few lines then uncomment these 4 lines
# and comment out the paging 4 lines below these!
#
Shift_L,	Down,	Page_Down,			1#,	1000,	1000
Shift_L,	Up,		Page_Up,			1#,	1000,	1000
#None,		Down,	Down,				7#,	1000,	1000
#None,		Up,		Up,					7#,	1000,	1000
#
# If you don't like page scrolling then comment these out and uncomment above!
#
#Shift_L,	Down,	Down,				7,
#Shift_L,	Up,		Up,					7,
#None,		Down,	Page_Down,			1,
#None,		Up,		Page_Up,			1,
# Left/Right & Thumb stuff
None,		Left,	Left,				7,
None,		Right,	Right,				7,
None,		Thumb1,	Down,				7,
Shift_L,	Thumb1,	Up,					7,
None,		Thumb2,	Up,					7,
Shift_L,	Thumb2,	Down,				7,

"^Freespace.*"
,	Up,		Y
,	Down,	X
,	Thumb1,	H
,	Thumb2,	R

"^SDL_App"
#,	Up,		Button4
#,	Down,	Button5
,	Thumb1,	Home	#many apps don't understand Button > 5
,	Thumb2, End		#many apps don't understand Button > 5

# Thanks to shewp <shewplx@pblx.net>
"^Opera" 
#@Repeat    # let qt do it
None,       Down,   Down,               4,  100,    100
None,       Up,     Up,                 4,  100,    100
None,       Thumb1, Right
None,       Thumb2, Left

"^Netscape.*"
, Thumb1, Alt_L|KP_Left
, Thumb2, Alt_L|KP_Right
#, Up, Button4
#, Down, Button5

"^Netscape"
#
# If you don't want to scroll by a few lines then comment out these 4 lines
# and uncomment the paging 4 lines below these!
#
Shift_L,	Down,	Page_Down,			1,	1000,	1000
Shift_L,	Up,		Page_Up,			1,	1000,	1000
None,		Down,	Down,				7,	1000,	1000
None,		Up,		Up,					7,	1000,	1000
#
# If you don't like page scrolling then uncomment these
# and comment out the 4 lines above!
#
#Shift_L,	Down,	Shift_L|Down,		7,	1000,	1000
#Shift_L,	Up,		Shift_L|Up,			7,	1000,	1000
#None,		Down,	Page_Down,			1,	1000,	1000
#None,		Up,		Page_Up,			1,	1000,	1000
# Left/Right & Thumb stuff
None,		Left,	Left,				7,	1000,	1000
None,		Right,	Right,				7,	1000,	1000
None,		Thumb1,	Down,				7,	1000,	1000
Shift_L,	Thumb1,	Up,					7,	1000,	1000
None,		Thumb2,	Up,					7,	1000,	1000
Shift_L,	Thumb2,	Down,				7,	1000,	1000

"^Navigator"
#Alt_L,		Down,	Alt_L|Right
#Alt_L,		Up,		Alt_L|Left
Alt_L,		Down,	Right,				10,	1000,	1000
Alt_L,		Up,		Left,				10,	1000,	1000

# Thanks to Paul J Collins <sneakums@usa.net>
"^emacs"
Shift_L,	Up,		Page_Up
Shift_L,	Down,	Page_Down
# you may need Alt instead of Meta....
None,		Down,	Control_L|Meta_L|Shift_L|parenright
None,		Up,		Control_L|Meta_L|Shift_L|parenleft

# Thanks to etienne grossmann <etienne@isr.ist.utl.pt>
"^Xftp"
,			Down,	j
,			Up,		k

".* - Pan$"
,	Left,	Control_L|Button1
,	Thumb1,	Control_L|Button1
#,	Up,	Button4
#,	Down,	Button5

# Thanks to etienne grossmann <etienne@isr.ist.utl.pt>
"^gv[ :]"
None,		Up,		Shift_L|space
None,		Down,	space

#"^Event Tester"
#@Repeat
#@Exclude
#,	Left,	Button6
#,	Right,	Button7
#,	Thumb1,	Button8
#,	Thumb2,	Button9

"^xv grab"
@Priority=1
@Exclude

"^XV.*"
None,	Down,	Tab
None,	Up,		Delete

"^Untitled"
# if using wheel fifo, you may switch these.
#,	Up,		Button4
#,	Down,	Button5
#with these
,	Up,		Page_Up
,	Down,	Page_Down
# (end of switch)
,   Thumb1, Home
,   Thumb2, End

"^No Title"
# if using wheel fifo, you may switch these.
#,	Up,		Button4
#,	Down,	Button5
#with these
,	Up,		Page_Up
,	Down,	Page_Down
# (end of switch)
,   Left, Home
,   Right, End
,   Thumb1, Home
,   Thumb2, End

#"\(null\)"
# if using wheel fifo, you may want the 2nd group
#,	Up,		Button4
#,	Down,	Button5
#,	Left, Button6
#,	Right, Button7
#,	Thumb1, Button8
#,	Thumb2, Button9
# 2nd group (old keys...)
#,	Up,		Page_Up
#,	Down,	Page_Down
#,	Left, Home
#,	Right, End
#,	Thumb1, Home
#,	Thumb2, End
# (end of switch)

# send event to the window manager when in the root window...
"\(root\)"
,	Up,		Control_L|N
,	Down,	Control_L|P
,   Thumb1,	Alt_L|Left
,	Thumb2,	Alt_L|Right

#
# Uncommment the following to exclude by default.
# Then you will have to add new apps all the time, but will retain any built-in
# wheel functionality contained in some KDE and other newer programs.
# This kinda defeats the original purpose of the program! ;)
#
#".*"
#@Priority=-1000
#@Exclude
#@Repeat

#
# These are the defaults, but note that the defaults for the right side of the
# keyboard are still handled within the program, unless you add the
# combinations desired here. (except for the None modifier of course!)
# If this section is deleted then the hardcoded defaults will be used, which
# are the same thing.
# Modifying these has global effects, but doesn't override what is above.
#
#".*"
#@Priority=-1001
#,	Up,	Button4
#,	Down,	Button5
#None,							Left,	Left
#None,							Right,	Right
#None,							Up,		Page_Up
#None,							Down,	Page_Down
#Shift_L,						Left,	Left
#Shift_L,						Right,	Right
#Shift_L,						Up,		Up
#Shift_L,						Down,	Down
#        Control_L,				Left,	Left,		2
#        Control_L,				Right,	Right,		2
#        Control_L,				Up,		Page_Up,	2
#        Control_L,				Down,	Page_Down,	2
#Shift_L|Control_L,				Left,	Left,		5
#Shift_L|Control_L,				Right,	Right,		5
#Shift_L|Control_L,				Up,		Page_Up,	5
#Shift_L|Control_L,				Down,	Page_Down,	5
#                  Alt_L,		Left,	Left,		10
#                  Alt_L,		Right,	Right,		10
#                  Alt_L,		Up,		Left,		10
#                  Alt_L,		Down,	Right,		10
#Shift_L|          Alt_L,		Left,	Left
#Shift_L|          Alt_L,		Right,	Right
#Shift_L|          Alt_L,		Up,		Left
#Shift_L|          Alt_L,		Down,	Right
#        Control_L|Alt_L,		Left,	Left.		20
#        Control_L|Alt_L,		Right,	Right.		20
#        Control_L|Alt_L,		Up,		Left.		20
#        Control_L|Alt_L,		Down,	Right.		20
#Shift_L|Control_L|Alt_L,		Left,	Left,		50
#Shift_L|Control_L|Alt_L,		Right,	Right,		50
#Shift_L|Control_L|Alt_L,		Up,		Left,		50
#Shift_L|Control_L|Alt_L,		Down,	Right,		50
#,   Thumb1, Home
#,   Thumb2, End

# vim:ts=4:shiftwidth=4:syntax=sh



".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right

```

---

### Post by pkroks on 2006-04-01
..

---

### Post by pkroks on 2006-04-01
I don't know what happened now. 

I pushed a button on my Multimedia keyboard, it was the My Documents shortcut. My computer shut down or went to sleep or something, when I switched it on, it started booting wierd. So I reset and chose which startup I wanted, I got in here, and now when I try to scroll using my mouse wheel, it's like does back and forward. 

Here is the xorg.conf file:

```
 # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```




Please help!

---

### Post by pkroks on 2006-04-01
I also went to check the imwheelrc file, it was blank. :O

So I pasted the original text that I placed in my first post on here, in the code box back in there. Please help


Edit
Damn. I just noticed this is not in the Ubuntu Breezy Badgy 5.10 Forum. I used the search result to find this. Damn. Now what...

---

### Post by Spudgun on 2006-06-06
For those trying to get this guide working in Dapper Drake, use the following in your xorg.conf instead of the original -

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ButtonMapping"         "1 2 3 6 7"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Resolution" "800"
EndSection
```

---

### Post by Ludwig7666 on 2006-08-23
lol I'm a newb still to ubuntu. It won't let me save the damn thing. I tried to change the permission in the properties but I can't. Or am I doing it all wrong?

---

### Post by watherby on 2006-09-03
I have same error:
"waiting for xserver to shut down FreeFontPath: FPE "/usr/shar/X11/fonts/misc" refcount is 2, should be 1; fixing."

no nvidia driver installed
lately updated Glib

restarted GNOME with Ctrl+Alt+BackSpace couple of times (don't know if it is relevant)

HELP!

---

### Post by QettoE on 2006-09-27
> **watherby said:**
> I have same error:
"waiting for xserver to shut down FreeFontPath: FPE "/usr/shar/X11/fonts/misc" refcount is 2, should be 1; fixing."

no nvidia driver installed
lately updated Glib

restarted GNOME with Ctrl+Alt+BackSpace couple of times (don't know if it is relevant)

HELP!

It happened to me too. Remove imwheel and then go to your /etc/X11/Xsessions.d folder and remove all files with imwheel in file name.

---

### Post by Wolfraem on 2007-04-26
Ok. I'm on Fiery now (7.04 in x86_64) and I've tried a plethora of alterations and can't seem to get this to work. I'm wondering if there's something new with the upgrade? 

This is my xorg.conf

```


Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"

        Option          "Buttons"               "7"

        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"


EndSection


```

This is my 57xmodmap

```


#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"


```

If someone could help, I would very much appreciate it :)

---

### Post by Wolfraem on 2007-04-26
Ok, I did a little more searching and found this thread: [http://ubuntuforums.org/showthread.php?t=44191]("http://ubuntuforums.org/showthread.php?t=44191")

I figured out, though, that the buttons will only work if you use our current thread's "57xmodmap" contents. So...

at step five in the above thread, using the code 

```


#bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

also, when in step 4 of the above-linked thread, read the instructions included in the app. there's a line of code that at the bottom of the file commented out. 
```
 #IMWHEEL_PARAMS='-b "0 0 8 9"'
```
Uncommenting it (as per instructed in the directions in the file) seemed to help -- I'm not sure if it was necessary or not, but my mouse now works so I'm not complaining.

Hope this is helpful for all y'all 7.04 users.

---

### Post by mdmykel on 2007-06-12
For my 5-button M$ LaserMouse 6000 I just edited the /etc/X11/xorg.conf by commenting out the existing "Configured Mouse" section and adding the code below the old section to enable my side buttons for forward in back in firefox.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

NOTE: You must be root to edit the xorg.conf file so in a terminal you should enter:
%>su 
Password:<enter your root password>
%>gedit /etc/X11/xorg.conf

After saving the edit, to load the change, you have to restart xserver by entering Ctrl-BkSp and logging back in.

---

### Post by sigmund1898 on 2007-06-14
For those of you whom own an Optical Intellimouse with 5 buttons and none of the above xorg.conf settings worked, the following settings worked for me: 

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "6 7 5"
    Option         "ButtonMapping" "1 2 3 4 5 6 7"
    Option         "Emulate3Buttons" "YES"
    Option         "Buttons" "7"
EndSection
```

I noticed that 6 and 7 were the scroll up/down for the mouse wheel, and 5 is the button in the middle, 1 2 and 3 are of course, left click, wheel click, and right click.

---

### Post by IggyGal on 2007-07-07
Help I have fallen down and can't get my mouse to do what I want.  I have tried just about everything, I know it is me not doing something right.  I'm very new to Linux and Ubuntu, I have used it for about a month and just love it.  Don't think I will ever go back to Windows. Anyway here is my problem.  I have a Logitech Cordless MouseMan and Keyboard and I need the mouse to be able to move the page up and down. Right now it backup a page. Also I would like the thumb button (only one button) to backspace.  I'm using Netscape since I could not get the 64bit firefox to install shockwave-flash. But thats another request.  My xorg.conf :
Section "InputDevice"
	Identifier 	"mouse.usb"
	Driver 		"mouse"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"Buttons" "6"
	Option 		"ZAxisMapping" "4 5"
EndSection

Thanks

---

### Post by nunyabidness on 2007-09-15
I had my mouse buttons working last week, was forced to do a reinstall due to typical noobie stupidity and since then I have not been able to get my back and forward buttons to work.  Period.  I can not even get to the point of doing it incorrectly and having the mouse wheel cause forward and back in my browser.  I have followed the instructions and examples to the "T", still no joy.  To make matters worse, each time I modified my xorg.conf input device mouse section, I would end up with a corrupted xserver and end up having to boot from the cd and restore my xorg.  I believe I have fixed that, my xorg was looking for Mouse0 and all the examples had the mouse named Configured Device or Configured Mouse, changing that to Mouse0 seems to have done the trick for not crashing my X at least.  If anyone out there has had similar problems and overcame them, would you please post what you had to do?  I have tried everything in this thread to no avail.  Thanks in advance.

---

### Post by nunyabidness on 2007-09-16
Well, in another shining example of weirdness, both buttons now work correctly for Firefox, but not nautilus, and my X is not crashing when I boot.  Didn't do anything, (that I am aware of, as I am a noobie), that I had not already attempted.  Thanks to anyone who read my plea for help.

---

### Post by jdsfl on 2007-10-22
for some reason on my logitech mx700 i cannot seem to get this to work, before the back button on my mouse worked the same as the left mouse button. now it seems to do nothing. followed the directions, and tripled checked everything. not so lucky here

---

### Post by tomsa on 2007-12-01
I somehow screwed this up, and my scroll wheel is now a forward/back button.  Naturally, being a big linux noob, I didn't understand the severity of editing my xorg.conf file, and didn't make a backup.  I would like to undo what changes I have made and stick with the default configuration (so that I can have my scroll wheel back), but I am not quite sure how to get back to it.  I'm pretty sure that Ubuntu has created a backup for me (xorg.conf~) but I'm not sure.  As I know just enough to be able to really wreck up my computer at the command line, I'd like to get your opinion on if this will work or not:

1. Remove imwheel through synaptic
2. run the command "sudo rm /etc/X11/Xsession.d/57xmodmap"
3. run the command "sudo rm /etc/X11/imwheelrc"   
4. run "dpkg-reconfigure xserver-xorg"
5. reboot and hope it worked

should that do it, or will I just screw up my computer even worse?

Please help!](*,)

---

### Post by Muscar on 2007-12-01
When i try to save the xorg.conf file it says that i don't have the right privileges to do that, but I am admin. :confused:

---

### Post by zeker on 2007-12-25
It took me all afternoon to get this to work, so I am posting here in the hopes of saving other people the time

To make a Microsoft habu gaming mouse work in KDE:

**Step 1 - have KDE see the buttons**

Change xorg.conf (/etc/X11/xorg.conf) to look like this for the mouse:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons" 	"false"
EndSection

```

note the protocol in particular, and also take out any reference to button mapping. 

**Step 2 - modmap the mouse buttons**

create a modmap file (/etc/X11/Xsession.d/57Xmodmap) that looks like this:

```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"
imwheel -k -b "0 0 6 7"
```


**Step 3 - Start the imwheel program**

In my KDE autoexec folder (~/.kde/Autostart) there is a shell script (imwheel.sh*) that lloks like this:

> #/bin/bash
imwheel -k


Then in my home directory there is a config file for the imwheel program (~/.imwheelrc) that looks like this:

```
".*"
None,Thumb1,Alt_L|Left
None,Thumb2,Alt_L|Right

```

This allows the two thumb buttons to work as forward and back in all programs.

---

### Post by -::Bas::- on 2008-01-16
To make a [COLOR="Red"]Microsoft habu[/COLOR] gaming mouse work in Gnome:

Step 1 - have Gnome see the buttons

Change xorg.conf (/etc/X11/xorg.conf) to look like this for the mouse:

First
```
 sudo gedit /etc/X11/xorg.conf 
```

Then add:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons" 	"false"
EndSection
```

note the protocol in particular, and also take out any reference to button mapping.

Step 2 - modmap the mouse buttons

create a modmap file 

```
sudo gedit /etc/X11/Xsession.d/57Xmodmap
```

and add this to the blank stuff you've just created:

```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"
imwheel -k -b "0 0 6 7"
```

Step 3 - Install the imwheel program:
```

sudo apt-get install imwheel
```

Step 4 - Autostart the imwheel program:

Go to System -> Administration -> Sessions
Click on "add", and add the imwheel program which is located in /usr/bin/imwheel

Step 5 - Let the two thumb buttons work as forward and back in all programs:

Open /etc/X11/imwheel/.imwheelrc 
```

sudo gedit /etc/X11/imwheel/imwheelrc 
```

Add this to the file and save it:
```

".*"
None,Thumb1,Alt_L|Left
None,Thumb2,Alt_L|Right
```

Now ctrl-alt-bckspc, log into your machine and you're good to go!


Thanks to Zeker who wrote most of this for KDE, I only adapted it for Gnome-users.

---

### Post by zeker on 2008-02-09
Hey! Glad to be of help.

---

### Post by reverend_HH on 2008-02-11
Ok so I'm about fed up here, I've been messing with the settings for the longest and I've gone from having my mouse wheel scroll up/down, used as the forward/back buttons, and not working at all. I've changed the settings in  57xmodmap and that doesn't seem to have an effect on the side buttons. My system always reads my back side button as mouse3 (middle click) and my forward button as mouse2 (right click). I had it working before so I know for a fact that it's possible but I had to reconfigure my xorg to default settings because it wouldn't read my graphics card. In case it matters, I'm using an MX600 (it comes with the MX3200 desktop and I've tried changing the number of buttons from 7 to 9 to 10. Please help!

---

### Post by SilentChris on 2008-04-26
Thanks a ton Zeker and -::Bas::- !

I tried other solutions for like an hour before I came to this one.  It worked perfectly.  Now I can finally navigate firefox with my side buttons =D

---

### Post by dover19 on 2008-04-28
Wow, not only did this not work but it screwed up my Ubuntu. Some Error message about not loading GNOME properly.

---

### Post by twizler on 2010-01-28
**panickedthumb THANK YOU ! YOU THE MAN!! [B] I have a usb 5 button Microsoft intelli mouse that is now working w/ scroll back / forward buttons!!!! ** WOOT WHOOT 

some of step items were a little off on my system but you got me 95 % of the way there and the rest was intuitive to figure out 
my imwheelrc  file was located @ 

/etc/X11/imwheel/imwheelrc 
and xmodmap
/etc/X11/Xsession.d/80ubuntu-xmodmap[B]

---

