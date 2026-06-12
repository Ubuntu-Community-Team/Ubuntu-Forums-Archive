---
title: "HOWTO: 5 button mouse working on firefox (back/forward buttons)"
date: 2005-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by James Brown on 2005-04-19
Hi 
I've got it here (for Xandros): 

[http://www.adamfranco.com/?site=afranco&section=22&action=site](http://www.adamfranco.com/?site=afranco&section=22&action=site)

It works for me in Ubuntu. I've made some corrections...

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3. put the following lines in the .xsession file in your home directory:**

exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

** this don't worked for me in Ubuntu. So I made a script file called "mouse", like the following, and put it on /home/"login"/.kde/Autostart, and in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" & 
exec imwheel -k -b "67" & 
exec $REALSTARTUP

---

### Post by dyle on 2005-04-20
Thanks!  Worked for me in firefox.  Didn't read the last part so my X session crashed on me when I made the .xsession file...oops!

Anybody know how to have this work with Epiphany? I'd rather use that browser but I'm really missing this feature for my mouse (MX500)

---

### Post by dyle on 2005-04-20
Found it!

Just edited /etc/X11/xorg.conf

Option "ZAxisMapping" "6 7"
Option "Buttons" "9"

Then edited the mouse script to reflect this
 
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 " &
exec imwheel -k -b "67" &
exec $REALSTARTUP

Works with a Logitech MX500

---

### Post by Gustav on 2005-04-20
For me it was enough to do the editing of xorg.conf part.
Although I had to set the ZAxisMapping to "4 5" instead of "6 7".

So I recommend that you try without installing IMWheel and editing .session and if it still doesn't work after restart of X, do the rest of the stuff.

(I'm using a Intellimouse Explorer in Gnome)

---

### Post by Skaman on 2005-04-20
[QUOTE=dyle]Found it!

Just edited /etc/X11/xorg.conf

Option "ZAxisMapping" "6 7"
Option "Buttons" "9"

Then edited the mouse script to reflect this
 
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 " &
exec imwheel -k -b "67" &
exec $REALSTARTUP

Works with a Logitech MX500[/QUOTE]
great! I have a mx 510 (i'll try as soon as i can..)
u did all the process upthere or just edited this few lines in xorg.conf???

---

### Post by woifi on 2005-04-20
[http://www.ubuntuforums.org/showthread.php?t=3828](http://www.ubuntuforums.org/showthread.php?t=3828)

... works in hoary too

---

### Post by Gnobody on 2005-04-20
I have known about this hack for a while, but is there anyway to get the extra buttons to work with Nautilus and Konqueror?

---

### Post by woifi on 2005-04-20
[QUOTE=Gnobody]I have known about this hack for a while, but is there anyway to get the extra buttons to work with Nautilus and Konqueror?[/QUOTE]
 I want to get the buttons work with nautilus too, I'm working on that ;)

---

### Post by Skaman on 2005-04-20
[QUOTE=Gnobody]I have known about this hack for a while, but is there anyway to get the extra buttons to work with Nautilus and Konqueror?[/QUOTE]
i did it and in conqueror the buttons work great!
the only problems ar with scrolling buttons (tey go back and forward if there is the possibility to do it) and with the 9th button that simply doesnt work.....

for the rest works great!

anyway i don'use those buttons :P

---

### Post by hobnob on 2005-04-20
I have a USB Optical IntelliMouse, and only needed to edit xorg.conf as follows to get the side buttons working in Firefox. ```
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option		"ZAxisMapping"		"4 5"
```
KISS in action  :)

---

### Post by woifi on 2005-04-20
[QUOTE=Skaman]i did it and in conqueror the buttons work great!
the only problems ar with scrolling buttons (tey go back and forward if there is the possibility to do it) and with the 9th button that simply doesnt work.....

for the rest works great!

anyway i don'use those buttons :P[/QUOTE]
 and would you tell us how you solve the problem?

I found something in the old warty thread: [http://www.ubuntuforums.org/showpost.php?p=103285&postcount=57](http://www.ubuntuforums.org/showpost.php?p=103285&postcount=57)

unfortunately it works not for me with nautilus

---

### Post by Skaman on 2005-04-20
[QUOTE=woifi]and would you tell us how you solve the problem?

I found something in the old warty thread: [http://www.ubuntuforums.org/showpost.php?p=103285&postcount=57](http://www.ubuntuforums.org/showpost.php?p=103285&postcount=57)

unfortunately it works not for me with nautilus[/QUOTE]
i just followed the tutorial...
maybe with konqueror works & with nautilus no. :neutral:

---

### Post by woifi on 2005-04-21
yesterday I had the idea to simply change the nautilus shortcut for back & forward to alt-l/left alt-l/right, but it seems there are no shortcuts for going back or forward in nautilus :(

any ideas?

---

### Post by Gothic on 2005-04-21
great tip, thx!

---

### Post by dyle on 2005-04-21
[QUOTE=Skaman]great! I have a mx 510 (i'll try as soon as i can..)
u did all the process upthere or just edited this few lines in xorg.conf???[/QUOTE]

Sorry about that.  I should have made my post clearer.  Here's what i did (editing instructions from the first post)

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
**Option "Buttons" "9"**
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3.   I made a script file called "mouse.sh", like the following, and put it in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
**exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &**
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

**Also worked in Nautilus and Epiphany** once again.. on a MX 500 or similar configuration

---

### Post by vassalle on 2005-04-22
seriously, the back and forward button works for you in nautilus too ?

---

### Post by dyle on 2005-04-22
[QUOTE=vassalle]seriously, the back and forward button works for you in nautilus too ?[/QUOTE]

Yes, it does.  Just to add on it, I have my Nautlis behavior set to "Always open in browser window".  Back and forward buttons definitely work.

---

### Post by telmo on 2005-04-22
This second tutorial doesn't work for me.

I have a MX510.

---

### Post by dyle on 2005-04-23
[QUOTE=telmo]This second tutorial doesn't work for me.

I have a MX510.[/QUOTE]

Are you using the ps2 adapter or straight usb?  If you're using the ps2 adapter, try deleting the line "Identifier 'mouse.usb' in your xorg.conf.

I'm using the ps2 adapter and my actual xorg.conf looks like this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"9"
	Option		"ZAxisMapping"		"6 7"
EndSection

Hope this helps.  I'm no way an expert at linux but I managed to get this working in my computer so I'd like to help as much as I can.  Please make sure to backup your xorg.conf file just in case.

---

### Post by gopha on 2005-05-25
[QUOTE=woifi]yesterday I had the idea to simply change the nautilus shortcut for back & forward to alt-l/left alt-l/right, but it seems there are no shortcuts for going back or forward in nautilus :(

any ideas?[/QUOTE]

Same here, it does not work in nautilus.

---

### Post by oars on 2005-05-26
Like someone before said, back/forward will only work in Nautilus if it is in browser mode.  It works like a charm.

Cool thing about installing imwheel:
I switched from a 5 button mouse to a 3 button (2 buttons and scroll wheel).  I used IMwheel to make it so that clicking the scroll wheel goes back for me.  Good stuff.  Also, since I have a laptop, I made a script that I run when I have the mouse plugged in and just use the touchpad when I don't have the mouse plugged in.

---

### Post by benplaut on 2005-05-26
unfortunately, it completely messes stuff uo when you have a trackpoint with three buttons, and touchpad with two buttons, and a USB mouse with 5 buttons  :roll:

---

### Post by gopha on 2005-05-26
[QUOTE=oars]Like someone before said, back/forward will only work in Nautilus if it is in browser mode.  It works like a charm.

Cool thing about installing imwheel:
I switched from a 5 button mouse to a 3 button (2 buttons and scroll wheel).  I used IMwheel to make it so that clicking the scroll wheel goes back for me.  Good stuff.  Also, since I have a laptop, I made a script that I run when I have the mouse plugged in and just use the touchpad when I don't have the mouse plugged in.[/QUOTE]
 I got it set to browsermode and it does not work at all ;)

---

### Post by sudhashen on 2005-05-26
have a laptop/explorer 5 button intellimouse and did not need to install imwheel - just edited xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
EndSection

works ferfectly!

---

### Post by thecrimsonking on 2005-05-26
Did not work for me until i changed 
Identifier "mouse.usb" to
Identifier "Configured Mouse"

Well, it worked in FF, just not Konqueror. Changing it to "Configured Mouse" made it work in Konqueror.  Even though I am using a USB mouse.

---

### Post by pete0r on 2005-05-27
i keep trying to install IMwheel and it keeps saying:

```

pete@pete-laptop:~$ sudo apt-get install imwheel
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imwheel
pete@pete-laptop:~$

```

any ideas?

thanks

---

### Post by #Vizc@ch@ on 2005-05-27
Pete do you have the correct repositories enabled? (universe?)

Hi everyone i followed the instructions, but i don't understand how it is supposed to work, which mouse buttons do i have to click in order to go forward-back in the browser?

Thanks

---

### Post by pete0r on 2005-05-27
[QUOTE=#Vizc@ch@]Pete do you have the correct repositories enabled? (universe?)

Hi everyone i followed the instructions, but i don't understand how it is supposed to work, which mouse buttons do i have to click in order to go forward-back in the browser?

Thanks[/QUOTE]
 actually i figured that out and got it working.

when i get the extra time, i gotta get the other buttons on my mx700 working as well. at least i can use the back and forward ones now.

thanks guys!

---

### Post by rama on 2005-05-29
I followed the instructions I found at :
[https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons](https://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons)

The side buttons now work with firefox but Nautilus still does not respond. I also get an error message during gnome start up informing me that I do not have permition to execute "the file". It does not specify which file it is reffering to though. I have checked the permitions of the /etc/X11/Xsession.d/57xmodmap file they are set to 777.

Any ideas?

---

### Post by rama on 2005-05-29
[QUOTE=rama] I also get an error message during gnome start up informing me that I do not have permition to execute "the file".[/QUOTE]
To be exact the errors are :
1. Missing command to run
2. You must run this program as the root user.

I double checked the steps of the instructions I mentoined before and the files that I have created/edited... Everything is looking fine.  :roll: 
Someone?

---

### Post by Spike on 2005-06-02
[QUOTE=oars]I used IMwheel to make it so that clicking the scroll wheel goes back for me.  Good stuff.  Also, since I have a laptop, I made a script that I run when I have the mouse plugged in and just use the touchpad when I don't have the mouse plugged in.[/QUOTE]

How do you do this?

I'm trying to get clicking the scroll wheel to double click... (I'm also trying to get the wheel to scroll a screen at a time...)

ty

---

### Post by bugmenot on 2005-06-08
I have a USB MX500 which is working correctly with the 7-button ExplorerPS/2 setup mentioned above.  By "correctly," I mean that the left button, middle click, right button, scroll wheel up, scroll wheel down, back, and forward events are properly communicated to the application.  I am not using imwheel, as my browsers (firefox and opera) support buttons 6 and 7 natively.

I have experienced the phantom button press issue with the top "cruise control" button, which was mentioned in this bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=1947](https://bugs.freedesktop.org/show_bug.cgi?id=1947)

This causes every click of the button on top of the scroll wheel to produce a spurious button 6 event (back button) as well as the proper button 4 event (scroll up).

bugzilla.kernel.org is refusing connections at the moment so I am unable to find their solution; however, my question is the following: are there plans to roll this evdev patch into the ubuntu xserver-xorg package?  I am currently using the latest version (6.8.2-10).

Also, I found that the "quick switch" button maps to button #1, even if I increase Option "Buttons" past 7.  Are there plans to support this button in the X server as a distinct event?

---

### Post by aaron on 2005-07-21
Hey bugmenot, I have the same problem.

A patch was released that fixes this issue. Here is the link

[http://cvs.archlinux.org/cgi-bin/viewcvs.cgi/x11/xorg/9000_all_6.7.99.2-lnx-evdev-core-v3.patch](http://cvs.archlinux.org/cgi-bin/viewcvs.cgi/x11/xorg/9000_all_6.7.99.2-lnx-evdev-core-v3.patch) 

Although from here I'm not sure how to install the patch. If you have any directions on how to do that it would be greatly appreciated!

---

### Post by Stige on 2005-08-03
This thing lets you have your MX510 work seamessly
```

xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"

```

But there is this thing that I'm using Fluxbox and i dunno how to add that command to startup so I need to type it everytime I start X.

---

### Post by Kanbeki on 2005-08-14
[QUOTE=dyle]Sorry about that.  I should have made my post clearer.  Here's what i did (editing instructions from the first post)

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
**Option "Buttons" "9"**
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3.   I made a script file called "mouse.sh", like the following, and put it in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
**exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &**
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

**Also worked in Nautilus and Epiphany** once again.. on a MX 500 or similar configuration[/QUOTE]

I did this with an MX500 on hoary, and now the forward and back buttons on the side control scrolling up and down AND they are inverted, the scrollwheel makes me go back and forward, and the forward and back buttons on the top work..help?

---

### Post by SDutra on 2005-08-15
I cant edit xorg.conf It says that it is protected.  I can;t change the settings because it says that i am not the owner. any ideas?

---

### Post by jeremy on 2005-08-15
[QUOTE=SDutra]I cant edit xorg.conf It says that it is protected.  I can;t change the settings because it says that i am not the owner. any ideas?[/QUOTE]
 Open a terminal and do
sudo gedit /etc/X11/xorg.conf

---

### Post by theraginasian on 2005-08-24
[QUOTE=dyle]Sorry about that.  I should have made my post clearer.  Here's what i did (editing instructions from the first post)

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
**Option "Buttons" "9"**
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3.   I made a script file called "mouse.sh", like the following, and put it in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
**exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &**
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

**Also worked in Nautilus and Epiphany** once again.. on a MX 500 or similar configuration[/QUOTE]

Ok guys, if you follow this EXACT guide, you will only have to change ONE thing in order for it to work on an MX500:

change:
```
Option "ZAxisMapping" "6 7"
```
to:
```
Option "ZAxisMapping" "4 5"
```

I followed his guide (thanks a billion btw!), noticed after restarting X that my scroll wheel did funny things like back and forward in nautilus, so I changed the axis mapping, restarted X again, and it works FLAWLESSLY... better in fact in Ubuntu now than it ever does in Windows. And he's right, it works in Nautilus...

HOWEVER... im using Colony 3 so that may be a reason why. Not sure though, I literally installed and was up and running on this 4 hours ago so I claim to be NO expert just what has worked for me... Im not stupid though either I came from Arch if anyone needed or cared to know :p

EDIT: how odd, I just applied a bunch of updates through synaptic (many packages that dealt with X) and it reversed me needing to use ZAxisMapping 4 5 to what dyle had origionally, which is ZAxisMapping 6 7. Perhaps you will you just to play with it to really know if you got the update that affects this or not.

---

### Post by themadhippy on 2005-08-24
hurra it works,first the modem,know the mouse  are working fine ,however  how to i change the right buttons use? I prefer the right button to be "close" instead of "forward ". i quess its the
> None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right 
bit i need to change,however how do i input F4,as in the keyboard command  Alt+ f4

---

### Post by Delvien on 2005-10-05
this don't worked for me in Ubuntu. So I made a script file called "mouse", like the following, and put it on /home/"login"/.kde/Autostart, and in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)""


Where the heck is "sessions">"start programs"????? i see no such thing

---

### Post by ratfish on 2005-10-19
I guess you found it by now, but SESSION is under SYSTEM...PREFERENCES on your menus

---

### Post by mariux on 2005-10-20
[QUOTE=dyle]Sorry about that.  I should have made my post clearer.  Here's what i did (editing instructions from the first post)

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
**Option "Buttons" "9"**
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3.   I made a script file called "mouse.sh", like the following, and put it in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
**exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &**
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

**Also worked in Nautilus and Epiphany** once again.. on a MX 500 or similar configuration[/QUOTE]Worked on my mx500 with konqueror!
Thanks!

---

### Post by LinuxKiller on 2005-10-26
Thank you for providing the perfect way for me to kill yet another Linux install.

I can't seem to get Linux to survive more than a couple of weeks with me!

I had just managed to get the annoying UTC problem (-1 hour in Window) fixed and then I thought I would get my back and forward buttons working.

Now my linux is dead again (no desktop, only command line) :-(

Anyone know how/if I can restore things back to how they were? ... I think the whole .xsession thing broke it because there was no .xsession file in the first place to add to.

It isn't easy to re-install Ubuntu because I'll have to copy Windows off the hard drive first, format and re-partition ... unless there is a better way.

---

### Post by Big-Wayne on 2006-01-08
Greetz all,
I know this an oldish thread, but I have followed the instructions to the letter and have been successfulish, in that the thumb button works.
My scroller wheel now sends everything back\forward in nautilus and firefox. However what i would like to achieve is for the thumb button to to go back in nautilus and firefox and the scroller wheel to do exactly that....scroll webpages up and down.
My mouse is a logitech mouseman dual optical.

Any help gratefully recieved.

---

### Post by joblessjunkie on 2006-05-12
I am using a **Microsoft Intellimouse Optical USB** with the Dapper Drake beta, and the configuration can be much, much simpler than described elsewhere in this thread. You do **not** need to use imwheel or create a multitude of startup scripts if you are using this mouse.

Edit the "InputDevice" section of **/etc/X11/xorg.conf** to look like this:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

The next time you log in, the side buttons will move back and forward in Firefox, and the mouse wheel will scroll the page up and down ... just like it does in Windows.

Not to complain about software I get for free, but simple needs (buttons that work as expected on a very popular and common mouse) that turn into long, complicated forum threads are why I'll never subject my family members to a linux desktop.

How do I contribute to get this simple thing working in the next rev of Ubuntu?

---

### Post by BungaMan on 2006-05-16
I'd just like to add my mouse results to this threads just in case others run into similar problems as I did.

I have a Predator 4200 optical gamer mouse from Trust and with the following settings in xorg.conf I got firefox working using side buttons and scrolling.  In Nautilus the scrolling works but not the back and forward button.  There was no need to install imwheel.  The scroll button seems to do pasting in ff.

```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device"			"/dev/input/mice"
	Option	    "Protocol"			"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option	    "ZAxisMapping"		"4 5"
	Option		"Buttons"			"7"
    Driver		"mouse"
EndSection

```

Oh, and like the guy up here... I know the type of mouse can be detected so why isn't this mapped to a database with working settings for xorg?  Or am I missing something and is it much more complicated?  Something for the Ubuntu team to work on?

---

### Post by lobsterboy on 2006-06-03
[QUOTE=joblessjunkie]I am using a **Microsoft Intellimouse Optical USB** with the Dapper Drake beta, and the configuration can be much, much simpler than described elsewhere in this thread. You do **not** need to use imwheel or create a multitude of startup scripts if you are using this mouse.
[/QUOTE]

Thanks, jobless. Your fantastically simple solution worked like a charm to get my **Logitech Cordless Click Plus** up and running with the back/forward buttons in Firefox under Dapper -- while the HOWTO that kicks this thread off doesn't work at all for me.

---

### Post by Osamabingandhi on 2006-06-05
Thanks jobless, worked perfect for my logitec cordless mousman wheel. The only downside is that it didn't work anywhere else exept in firefox....But i can live with that, firefox is most important.:D

---

### Post by Tamale on 2006-07-19
> **Stige said:**
> This thing lets you have your MX510 work seamessly
```

xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5"

```

But there is this thing that I'm using Fluxbox and i dunno how to add that command to startup so I need to type it everytime I start X.

Thank you so much!!!  This is exactly what I need as I have an MX500 that I only plug into my laptop SOMETIMES..

by the way, in dapper 6.06 the string order that worked for me was:

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"

Cheers!

---

### Post by Explodicle on 2006-10-11
I don't remember what my mouse was on the box, but the KDE settings claim it's a MX1000 (left, right, scroll button w/ sidescrolling, 2 extra buttons). I'm running Kubuntu 6.06.

For me, what worked was 
```
exec xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11 12 13" &
```

With 4 and 5 for my Z axis mapping in xorg.conf.

I did this because xmodmap was giving me this error with only 9 buttons:
```
xmodmap:  commandline:1:  bad number of buttons, must have 13 instead of 9
xmodmap:  1 error encountered, aborting.
```

I have no idea why it's doing this, but hey, it works... kinda. I'll keep messing with it and let you folks know if I can make it shiny.

---

### Post by Explodicle on 2006-10-12
Ok, it's actually the [Logitech LX7]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2135,CONTENTID=10918"), and KDE was just guessing. And Although the forward/back buttons are working properly, the sidescroll left just does the same thing as the back button (I have it bound on the left) and the sidescroll right does nothing.

(/me continues to tinker...)

---

### Post by Explodicle on 2006-10-12
Ok, I'm done for today... I've made no progress. 
[LIST]
[*]For some reason imwheel thinks that the "Buttons" value in my xorg.conf is 4 higher than it is. So, right now I have it at "5" for my 9-button mouse, with no errors from imwheel. When I set the value in xorg.conf to "9", it thinks I have a 13-button mouse. 
[*]My sidescrolling buttons won't work correctly. The one that would sidescroll left uses the same behavior as #8, and the one that would sidescroll right does not do anything. This is the same with all of the combinations I've tried. 
[/LIST]

Here's what I've got in my xorg.conf...
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"5"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
... My imwheelrc...
```
"^Firefox"
, Up, Control_L|Shift_L|Tab
, Down, Control_L|Tab
, Left, Alt_L|Left
, Right, Alt_L|Right
, Thumb1, Alt_L|Tab
, Thumb2, Alt_L|Shift_L|Tab
```
... And my mouse script.
```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9" &
exec imwheel -k -b "89" &
exec $REALSTARTUP
```

Of course, I tried the configurations suggested on this thread first, to no avail. If anyone has any similar experiences or insights, I'd welcome any input.

---

### Post by JPDVM2014 on 2006-10-23
I had the same problem with it thinking i had 4 more buttons than i actually did. Mine was doing it even after i uninstalled imwheel. I fixed it by using  
sudo cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf .  I still can't get my side buttons to work. i followed the tutorial in this thread. They were working at one point, but my scroll wheel also went forward and back. So i gave up on this. I probably wouldn't use them that much anyway.

---

### Post by flammen on 2006-10-27
The way I got my side buttons to work was like this.  It's super easy .

Install imwheel through synaptic or apt-get

Edit your xorg.conf and add one more line to your mouse section  - Option   "Buttons"  "7"

Then open the file /etc/X11/imwheel/startup.conf  and add these two lines (make sure there are spaces in between the numbers)

IMWHEEL_START=1

IMWHEEL_PARAMS='-b "0 0 8 9"'

Restart X and you're set.  It's less complicated than the other ways and worked great for me.

---

### Post by nchase on 2006-10-27
> **flammen said:**
> The way I got my side buttons to work was like this.  It's super easy .

Install imwheel through synaptic or apt-get

Edit your xorg.conf and add one more line to your mouse section  - Option   "Buttons"  "7"

Then open the file /etc/X11/imwheel/startup.conf  and add these two lines (make sure there are spaces in between the numbers)

IMWHEEL_START=1

IMWHEEL_PARAMS='-b "0 0 8 9"'

Restart X and you're set.  It's less complicated than the other ways and worked great for me.

This appears to have worked perfectly for me. (Logitech 518 MX)

Thanks a lot!

---

### Post by zedfrugnug on 2006-10-30
I tried the first part of the howto; replacing the mousesection in /etc/X11/xorg.conf.
This worked fine for me in Dapper, but after upgrading to Edgy it kills my xserver. 

The problems with xserver is also discribed here: [http://www.ubuntuforums.org/showthread.php?t=285758&highlight=xorg]("http://www.ubuntuforums.org/showthread.php?t=285758&highlight=xorg")

The solution seems the be reinstaling xserver, but I get an error, because /etc/X11/xorg.conf has been customized.

Ofcourse I can just reinstall edgy completely, but then I still don't have my mouse buttons working properly ](*,) 
I even tried downgrading again to Dapper, but now this gives gives me the same results (dead xserver) I had in Edgy.

Has anybody tried this in Edgy?
I'd really like to get this fixed.

---

### Post by Chippendale on 2006-11-05
This worked for me. I have a 7 button Optical Intellimouse (microsoft)

```
Section "InputDevice"
      Identifier "Configured Mouse"
      Driver "mouse"
      Option "CorePointer"
      Option "Device" "/dev/input/mice"
      Option "Protocol" "ExplorerPS/2"
      Option "Buttons" "7"
      Option "ButtonMapping" "1 2 3 4 5"
      Option "ZAxisMapping" "6 7"
      Option "Resolution" "100"
EndSection
```

---

### Post by zedfrugnug on 2006-11-06
Thanks! This one doesn't kill my xserver :) 

Unfortunately the side buttons and the scroll button switched function :( 
I tried changing ZAxisMapping back to "4 5" but offcourse that just killed the sidebuttons again..

Anyone any idea?

btw
Don't wich brand my mouse is; the label only tells me it's "made in China"

---

### Post by pip on 2006-11-18
I had the same thing. Changed it to this to flip it back:

```
Option		"ButtonMapping" 	"1 2 3 6 7"
Option 		"ZAxisMapping"		"4 5"
```

---

### Post by wyntermute on 2006-12-07
THANKYOUJUNKIE~!!!!  Yes, I meant to shout there.  I've been trying solution after solution to see if i could get my M$ Intellimouse Optical trackball's extra buttons working, with no luck.... Until now~!!!  :mrgreen: This should be stickied somewhere, at least for people who're using IntellOpticals. In conclusion, joblessjunkie has made my ubuntu experience one step closer to perfect -- only 2 more things stand between me & full dewindowsization~! (dual booting now, but i spend MUCH more time in Ubuntu).. i digress.  And sorry i didn't give you credit Chippendale, but i found junkie's post before yours...

> **joblessjunkie said:**
> I am using a **Microsoft Intellimouse Optical USB** with the Dapper Drake beta, and the configuration can be much, much simpler than described elsewhere in this thread. You do **not** need to use imwheel or create a multitude of startup scripts if you are using this mouse.

<snip>

How do I contribute to get this simple thing working in the next rev of Ubuntu?

---

### Post by ilovenicotine on 2006-12-08
> **joblessjunkie said:**
> I am using a **Microsoft Intellimouse Optical USB** with the Dapper Drake beta, 

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection



PERFECT!

---

### Post by els on 2006-12-10
[SIZE="2"]This got my Logitech MX 400 working.  Thanks for the help everyone.[/SIZE]

> **joblessjunkie said:**
> ...You do **not** need to use imwheel or create a multitude of startup scripts if you are using this mouse.

Edit the "InputDevice" section of **/etc/X11/xorg.conf** to look like this:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

The next time you log in, the side buttons will move back and forward in Firefox, and the mouse wheel will scroll the page up and down ... just like it does in Windows.


---

### Post by dangerboy_ds on 2007-02-12
Thank you, mine works just fine, and i think the brand of the mouse doenst really matter as i'm using a NGS (10€) mouse and it worked in the first time, changing only the xorg file... thanks anyway, now i'd like to ask how to make the mouse behave the same in the window manager
"Nautilus" in my case.

---

### Post by dangerboy_ds on 2007-02-12
Well folks as i saidi use a NGS mouse and i'd like to leavemy code here as it seems to solve the problem  (Only with firefox) about any mouse...

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

I hope i helped  ;-)

---

### Post by hppyfngy on 2007-02-19
Hey Gang, could someone bring an old subject up to date for me (and other newbs like me?)

I have an MX700 and I really really need a back button in Firefox.  I'm also running Beryl on Edgy and don't want to monkey up my scroll wheel or middle button.  

Anyone know what will work?   ):P

---

### Post by hppyfngy on 2007-02-20
bump?

---

### Post by fromdown on 2007-02-22
This is one of those things that should just work and not require hacking files to work. Yeah linux is a good OS when it cant get the little things to work its pretty sad. On my windows and OSX machines I just plug in and all the buttons work without loading extra drivers. Loading drivers just enhances the experience. Again its only a little thing but one of the thing that frustrates me no end I should have to spend time getting this sort of stuff to work

---

### Post by gksmithlcw on 2007-02-22
> **dangerboy_ds said:**
> Well folks as i saidi use a NGS mouse and i'd like to leavemy code here as it seems to solve the problem  (Only with firefox) about any mouse...

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

I hope i helped  ;-)

This code works for my Logitech MX518 in Firefox. However, still no luck with Nautilus (as dangerboy implies). I get a scroll effect with my back and forward buttons in Nautilus. Has anyone come up with a way to make Nautilus behave?

---

### Post by nategreat on 2007-03-22
**This works with my Ez NavigMan Duo wireless keyboard & mouse desk set**

Edit the "InputDevice" section of /etc/X11/xorg.conf to look like this:

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

**THANKS A LOT!**

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

### Post by margaf77 on 2007-07-11
> **mdmykel said:**
> For my 5-button M$ LaserMouse 6000 I just edited the /etc/X11/xorg.conf by commenting out the existing "Configured Mouse" section and adding the code below the old section to enable my side buttons for forward in back in firefox.

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

This worked perfectly for my MS Intelimouse Optical

---

### Post by har5ha on 2007-07-15
> 
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

This Works  for : **[Logitech MediaPlay Cordless Mouse]("http://www.amazon.com/Logitech-MediaPlay-Cordless-Mouse-Blue/dp/B0002SAF3C")**
[B]
Note : [/B]Instead of  [Option  **"CorePointer"**] 

I have [Option  **"AlwaysCore"**] , as I am using it as secondary pointer device [ie. on a Laptop].


Thanks Everybody !!! :)

---

### Post by Chilligan on 2007-09-10
Ok so back and forward works in Firefox ... what about Konqueror or Nautilus ?

---

### Post by xunil76 on 2007-10-05
> **Chilligan said:**
> Ok so back and forward works in Firefox ... what about Konqueror or Nautilus ?

i would also like to know how to get this to work....it's working fine for me in FF now (Intellimouse Explorer 3.0), but i really like it to work everywhere

i'm still in the process of reading & searching, so forgive me if this has already been answered, and maybe post a link for others that find this thread first?

---

### Post by mizzouxc on 2007-10-16
You could always do this, and avoid IMWHEEL or any other addons:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Emulate3Buttons" "false"
Option "Buttons"         "7"
Option "ButtonMapping"   "1 2 3 6 7"
Option "ZAxisMapping"    "4 5"
EndSection

---

### Post by TearDownAllSigns on 2007-10-20
When I first installed Feisty about 2 weeks ago, I changed my xorg.conf to one similar to the above to get my M$ Intellimouse to work with FireFox. The back and forward buttons worked great with very little fuss.

Then about 5 days later without warning the back and forward buttons no longer work and don't seem to send any signal to Firefox (ie not right and left click with the side mouse buttons as on a fresh xorg.conf). I had not made any changes to the xorg.conf during this time.

I have played around a bunch with my xorg.conf using various ones in this forum but none seem to get FireFox  or Nautilus to respond to the back and forth buttons. I even got a new replacement mouse from Logitech (MX 620) and am not able to get its back and forward buttons to be noticed. IMWheel did not help either. 

Any one have a similar issue or suggestions? I've tried most everything in this thread and the HowTo Wiki for multiple button mice.

---

### Post by IHateSnow on 2007-10-20
I'm having problems with this to work in gusty. Anyone else have the forward and back working in firefox?

---

### Post by TearDownAllSigns on 2007-10-20
My mouse is now working. I did a fresh install to Gutsy and edited my xorg.conf as below and it worked without a hitch in Firefox. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option          "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

Not sure why my mouse buttons stopped working on Feisty, but as I go through setting it up to my liking if I happen to lose it again, I'm sure I'll be back.

---

### Post by twizler on 2007-10-25
IT WORKS THANK YOU Tear Down All Signs  !!! IT WORKS -- I HAVE BEEN GOING CRAZY TRYING TO FIND THE FIX. 


Edited my xorg.conf  like above --- 
Then hit 
(Crtl + Alt + Backspace) To restart my xorg.conf file.... sent me to log in screen .... logged back into Gusty and now my 5 buttons are working... Forward and back in FireFox ROCKs!!! WOOOT WHOOT

---

### Post by trmiv on 2007-10-29
TearDownAllSigns and  twizler so you both have the MX620 working?  I've been considering picking one up since it seems rather comfortable, but I haven't seen much mention of that mouse on these forums.

---

### Post by hairywombat on 2007-11-02
I'm running Gutsy and use a 5-button intellimouse with intellieye. I did what TearDownAllSigns did and that got Firefox forward and back working but not for Nautilus. What is interesting is before the modifications to Xorg.conf, XEV (run XEV at the terminal and click the buttons) was reporting that the side buttons were buttons 8 & 9. After the modifications they are 6 & 7.

---

### Post by gbendotti on 2007-11-03
This works for the Evoluent VerticalMouse 3

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "true"
    Option          "Buttons"               "5"
    Option          "ZAxisMapping"          "4 5"
    Option          "ButtonMapping"         "1 2 3 7 6"
EndSection

---

### Post by vayhemar on 2007-11-09
Worked for a Logitech MX310

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"Auto"
	Option		"Buttons"	"7"
	Option		"Emulate3Buttons" "true"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7"
EndSection
```

---

### Post by ericesque on 2007-11-10
Veyhemar's stanza worked for my Logitech cordless Click! Plus

Still doesn't work in nautilus, but I can live with that.  Fwd/Back in firefox is a must have.

---

### Post by NineseveN on 2007-11-16
> **TearDownAllSigns said:**
> My mouse is now working. I did a fresh install to Gutsy and edited my xorg.conf as below and it worked without a hitch in Firefox. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option          "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

Not sure why my mouse buttons stopped working on Feisty, but as I go through setting it up to my liking if I happen to lose it again, I'm sure I'll be back.

Sweat! :guitar:

This worked 100% in 7.10/Firefox with an IOGEAR Laser  i600. I tried a few other methods and they didn't work (one somehow managed to disable my restricted ATI drivers). Thanks a million for this post (and the multitude of others here that have made this transition so painless). I just migrated from years of using XP. Though I never had any issues whatsoever with XP myself (due to extreme diligence and a lot of knowledge of services and OS optimization on my part), Ubuntu is still, IMHO, easily 10 times better. I haven't even scratched the surface with Ubuntu either...very cool indeed.

Of course, I bought a copy of XP retail but used a corporate version to bypass activation, so technically I was cheating. ;)

---

### Post by MrLooney on 2007-11-21
> **TearDownAllSigns said:**
> My mouse is now working. I did a fresh install to Gutsy and edited my xorg.conf as below and it worked without a hitch in Firefox. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option          "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

Not sure why my mouse buttons stopped working on Feisty, but as I go through setting it up to my liking if I happen to lose it again, I'm sure I'll be back.

I did this and every other install possible. I now have it working. with above config on a Microsoft IntelliMouse Explorer 3.0 USB + PS2 compatible mouse. 

I do not know if all the others work or not. I found out that if you do not restart not ctrl + alt + Backspace the changes do not take effect. I am running the latest Ubuntu 7.10.....   Hope that helps a little.

---

### Post by tdmoore on 2007-11-22
Hobnob,

Newbie to Ubuntu and loving it...

However on your code above can you give me more detail on actual sudo commands?

Also, for some reason my right (what would be the forward button) gives me a menu including Back, Reload, Bookmark, Save Page As, Send Link etc.  Left button does not work at all.  Wheel works fine...

MS Intellimouse 1.1A USB (although using serial adapter to plug into computer).

Much appreciated in advance.

---

### Post by TearDownAllSigns on 2007-11-24
Haven't seen too much on it here, but if anyone is having mouse button issues with the Epiphany browser there is some bug info here:

[http://bugzilla.gnome.org/show_bug.cgi?id=337852]("http://bugzilla.gnome.org/show_bug.cgi?id=337852")

What I found worked for me was typing about:config in the address bar and editing the following values.

```
about:config

mousewheel.horizscrool.withnokey.action 2
mousewheel.horizscrool.withnokey.sysnumlines false
```

It will work right away so you should know quick if its going to work with your mouse.

I'm liking Epiphany so far, having had none of the memory and locking up issues that made me turn from Firefox. At least until FF3. 

PS @ trmiv: The MX620 is pretty nice, I love the mouse scroll with the ball bearings.

---

### Post by TearDownAllSigns on 2007-11-24
> **tdmoore said:**
> Hobnob,

Newbie to Ubuntu and loving it...

However on your code above can you give me more detail on actual sudo commands?

Also, for some reason my right (what would be the forward button) gives me a menu including Back, Reload, Bookmark, Save Page As, Send Link etc.  Left button does not work at all.  Wheel works fine...

MS Intellimouse 1.1A USB (although using serial adapter to plug into computer).

Much appreciated in advance.

Welcome tdmoore,

I'm guessing you are just looking for the commands for backing up and then editing  the xorg.conf file?

First back up your old one by creating a copy, the sudo password will be from your admin account which was setup in the installation:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit your xorg.conf using the gnone editor:
```
sudo gedit /etc/X11/xorg.conf
```

One I posted recently on this forum seems to work well for people on Gutsy and I have a old Intellimouse that I just plugged in and confirmed it works with it. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option          "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

Save the file and close any apps, and do a ctrl-alt-backspace to restart X-Windows (this will not prompt you with a "are you sure?" so make sure you are ready). One you log back in you should (hopefully) have back and forward buttons working. 

An important thing to note is that you only want to do changes to the mouse section of your xorg.conf at this time. Messing with the video section could lead to a nasty restart where the graphical end of you system will not load. Because of this I still have a sticky note with the following in case I boot from a nerfed xorg.conf.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
ctrl-alt-backspace
```

That will overwrite the bad one with your backup and restart you. 

Good luck in this, for some reason I had a harder time getting my mouse to work in Ubuntu than I did setting up a multiple desktop display with my TV and Monitor.

---

### Post by tdmoore on 2007-11-25
Thanks TDAS.

will give it a try...have not had any experience with the "option" portion of commands so will try to figure that out first.

Much appreciated.

---

### Post by CheShA on 2007-11-25
Thanks TDAS, works a treat for me in Gutsy with my Trust MI-4500X USB / wireless optical mouse.  Quite a crafty way of doing it too, swapping the mapping round like that!

---

### Post by MrBL on 2007-11-26
Hi, 

thx TDAS, worked perfectly in FF for me too.

If anyone's still interested in making your 5 buttons mouse work with Nautilus and many others, I just worked it out with my first gen. intellimouse, following instructions posted [here]("http://doc.ubuntu-fr.org/souris_microsoft_intellimouse_explorer") (excuse my french...) using **imwheel**.
There's [a page about it in the original doc]("https://help.ubuntu.com/community/ManyButtonsMouseHowto") but it lacks imwheelrc config examples.
You can find the config file for almost anything on [imwheel website]("http://imwheel.sourceforge.net/imwheelrc").

---

### Post by Xgen on 2007-11-26
I haven't had any problems with my Intellimouse Optical on Hardy Heron, and am using Imwheel for the middle click configuration.  I have the middle button configured to exit on all programs - except xmms which I configured differently - and the side back/forward/exit  buttons work normal in Firefox and Nautilus. I DO have the usb mouse adapted to a ps2 port...whether that makes any difference...I haven't tried it without.

---

### Post by tdmoore on 2007-11-26
Thanks Xgen,

However I am a real newb to all this command stuff OTHER than looking out for spam/trouble commands.  I have visited this site [URL="https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons"] Mouse
[/URL] however stumped at first step!  I did load imwheel however.

Need total commands - do I need to include sudo?  Don't really understand how to edit an x11 file.

Appreciate any support you can give.

---

### Post by Xgen on 2007-11-27
I'm not that good at explaining things and although I don't know what mouse you have, I will detail what I do to get my "Intellimouse Optical" fully operational. Perhaps it works with other types.
For me, GUI screens are easier: 

With IMWHEEL installed....sudo nautilus or gksudo nautilus.
     /etc->X11->imwheel->startup.conf. Change "IMWHEEL_START=1" and remove "#" from IMWHEEL_PARAMS='-b "0 0 8 9"'
     /etc/X11/Xsession.d. Create a new file called "63xmodmap".
Add:

killall imwheel
 xmodmap -e 'pointer = 1 2 3 8 9 4 5'
 BINARY=$(which imwheel)
 $BINARY -k  -b "2 9 8"

Save & exit.
Create a hidden file in your home folder called ".imwheelrc".
This is the info which I placed in mine:

"^alacarte"
None, Up, Alt_L|C

"^listen"
None, Up, Alt_L|F9

"^vlc"
None, Up, Ctrl_L|X

"^gnome-terminal"
None, Up, Shift_L |Control_L|Q

"^amarok"
None, Up, Alt_L|F4
"^firestarter"
None, Up, Alt_L|F4
"^kcolorchooser"
None, Up, Alt_L|F4
"^nvidia-settings"
None, Up, Alt_L|F4
"^beryl-manager"
None, Up, Alt_L|F4
"^frostwire"
None, Up, Alt_L|F4
"^gparted"
None, Up, Alt_L|F4
"^gnome-search-tool"
None, Up, Alt_L|F4
"^gmplayer"
None, Up, Alt_L|F4
"^frostwire"
None, Up, Alt_L|F4

"^automatix2"
None, Up, Control_L|Q
"^brasero"
None, Up, Control_L|Q
"^exaile"
None, Up, Control_L|Q
"^k3b"
None, Up, Control_L|Q
"^gedit"
None, Up, Control_L|Q
"^gxine"
None, Up, Control_L|Q
"^totem"
None, Up, Control_L|Q
"^file-roller"
None, Up, Control_L|Q
"^gimp"
None, Up, Control_L|Q
"^synaptic"
None, Up, Control_L|Q
"^rhythmbox"
None, Up, Control_L|Q

"Thunar"
None, Left, Alt_L|Left
None, Right, Alt_L|Right
None, Up, Control_L|W 

"Nautilus"
None, Left, Alt_L|Left
None, Right, Alt_L|Right
None, Up, Control_L|W 

"^xine"
None, Up, Alt_L|G
None, Down, Alt_L|F4
None, Up, Alt_L|F4

".*"
None, Up, Control_L|W
None, Up, Alt_L|Left
None, Down, Alt_L|Right

 "(null)"
None, Up, Control_L|W
None, Up, Alt_L|Left
None, Down, Alt_L|Right

Of course, the commands for the middle button can be changed...mine closes out the application. Some may be redundant/unnecessary but I haven't bothered to fine-tune it or remove dead entries. If a program doesn't respond to the middle button, I just add it to the list.
     /etc->X11->xorg.conf
My file has this info:

Section "InputDevice"
    Identifier     "IntelliMouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "9"
    Option         "ZAxisMapping" "4 5"
EndSection

Restart the computer or xserver.
It took a long time to find the right combination...wouldn't wish it on anyone....still works through all the Ubuntu versions. Hopefully, I haven't forgotten anything, as I just paste everything from other versions.

---

### Post by aaargh486 on 2007-11-27
I have some sort of Logitech mouse, and I didn't have to use imwheel. I just had to change my xorg.conf to

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

I found this out after a LOT of trying out. It's really nice that GUtsy and Feisty support my sidebuttons without (the non-existant) Logitech drivers.

---

### Post by Xgen on 2007-11-27
Yes, my mouse side buttons worked fine without imwheel too... in Firefox...although I'm not so sure about Nautilus.  But to map the middle button with the commands that I wanted I had to use imwheel.

---

### Post by jamespetts on 2007-12-10
How do I configure imwheel/xorg.conf to work with the Intellimouse Explorer 4, which has the additional tilt wheel, giving it effectively nine buttons? Just increasing the number of buttons to 9 has made the scroll wheel act like the backwards and forwards button, and not made the backwards and forwards button work...

---

### Post by BryanFRitt on 2007-12-21
I tried to do the stuff in this forum and I've got the scroll wheel on the mouse doing back and forward instead of the back and forward buttons on the mouse.
with a Logitech MX510 mouse on KUbuntu 7.10
The default set the forward and backward as a copy of the right and middle buttons,
the scroll up as scroll up, and scroll down as scroll down.
I'd like to keep everything working and just change the two buttons on the side to forward/backward in browsers.

---

### Post by jamespetts on 2007-12-21
What I eventually found helped was starting imwheel without any command line options.

---

### Post by jmgallag on 2007-12-31
Working xorg.conf mouse configuration for Microsoft USB Intellimouse, 5 button + wheel, Ubuntu 7.10.

X sees this mouse as having 7 buttons. (Wheel on this mouse does not rock left and right.)

No other config changes or other programs required. 

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 6 7 4 5" 
        Option          "ZAxisMapping"  "4 5"
EndSection

---

### Post by NineseveN on 2008-01-05
FYI, when using the Nvidia X driver, if you have Nvidia configure your xorg.conf, adding the lines suggested in this thread will cause your xorg.conf to be unusuable. Instead, simply find the mouse section and add:

> Option         "ButtonMapping" "1 2 3 6 7 4 5" to the mouse section, it should look like the following:

> [COLOR="Navy"]Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"[/COLOR]
    Option         "ButtonMapping" "1 2 3 6 7 4 5"
[COLOR="Navy"]EndSection[/COLOR]

Everything in blue is generated by default, you only need to add the button mapping option (in most cases -I'm sure there's an exception out there).

This is due to the following section added by the Nvidia config:
> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

It lists your mouse as "Mouse0" instead of "Configured Mouse" as in the other examples. Sure you could probably change the InputDevice name to Configured mouse and then add the code, but simpy adding the ButtonMapping line (Option         "ButtonMapping" "1 2 3 6 7 4 5") gives you the same thing and changes less (which is a good thing).

I banged my head against the wall with this for a few minutes before I stepped back and actually looked at what the Nvidia configuration actually changed (which is, in a word, **everything**).

Hope this helps.

---

### Post by esmerine on 2008-01-06
Hooray!
Last night I was trying to fundamentally understand how "Emulating3Buttons", "ButtonMapping", etc. works and I got it.
I have a 6-button UltraX mouse. But I wrote "Button" "7" as I didn't know if option "6" worked. And I was too lazy to try/reboot again and again :biggrin:. Now what I'm having: my sixth button that is supposed to be "Minimize/Maximize" does "Back" in firefox (the thing it did in Win without any corrections and I was used to it), wheel click when clicked on a link always opens it in a new tab (what I had in Win), in text editors it pastes. Cool.

---

### Post by Maikelv on 2008-01-08
I did what was said in the opening post. However now my mousewheel is : scrolling up : back, scrolling down : forward. 
And my side buttons don't do anything.

edit : my mouse has : 4 buttons, and a scrollwheel that can click, scroll up, down, and click to the left & right.

---

### Post by hyperair on 2008-01-11
I've got a rather interesting situation here. I'm trying out a Dell Premium USB Mouse, snippet from /proc/bus/input/devices below:
```

I: Bus=0003 Vendor=413c Product=3016 Version=1110
N: Name="Dell Premium USB Optical Mouse"
P: Phys=usb-0000:00:03.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=17
B: KEY=31f0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

```

For some strange reason, buttons 1-3, and the scroll wheel works fine, but the back button and forward button register themselves as button 2 adn button 3 respectively. =\ From all the configuration methods I've seen, not one of them shows a case like this.

Even xev shows buttons 2 and 3 pressed when I click the back and forward buttons.

---

### Post by Gigamo on 2008-01-11
For anyone having issues with this guide and an IntelliMouse Explorer 3.0 (USB), this is my Xorg section:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by Nitro Fan on 2008-03-08
> **James Brown said:**
> Hi 
I've got it here (for Xandros): 

[http://www.adamfranco.com/?site=afranco&section=22&action=site](http://www.adamfranco.com/?site=afranco&section=22&action=site)

It works for me in Ubuntu. I've made some corrections...

1. Edit /etc/X11/xorg.conf

replace

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "IMPS/2"
Option "Emulate3Buttons" "YES"
Option "ZAxisMapping" "4 5"
EndSection

with

Section "InputDevice"
Identifier "mouse.usb"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "6 7"
EndSection

2. Install IMWheel via apt

3. put the following lines in the .xsession file in your home directory:**

exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

4. put the following lines at the bottom of /etc/X11/imwheel/imwheelrc

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

5. hit CTRL+ALT+BACKSPACE to restart X and log back in. Your back/forward buttons should now work in Firefox.

** this don't worked for me in Ubuntu. So I made a script file called "mouse", like the following, and put it on /home/"login"/.kde/Autostart, and in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" & 
exec imwheel -k -b "67" & 
exec $REALSTARTUP

i am trying to do this but when I try to save the file xorg.conf I get the following error message 

[COLOR="Red"]
Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.[/COLOR]

do I need to be in aministrator or something? if so how do i do that!? (I am a total newbie to all this)

Thanks Guys

---

### Post by Gotit on 2008-03-27
> i am trying to do this but when I try to save the file xorg.conf I get the following error message


Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

do I need to be in aministrator or something? if so how do i do that!? (I am a total newbie to all this)


did you open the editor as $ sudo gedit xorg.config

If so, when you try to save it will ask you for your password.

---

### Post by tweston on 2008-03-28
Honestly, I think that the original advice to use imwheel makes for unnecessary complexity. Forget imwheel altogether. As far as I can see, most folks only really want the thumb buttons to page back and forward in firefox. To do this, at least with a microsoft intellimouse explorer 4 usb, all you need is the following in xorg.conf:

> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection


---

### Post by Adahn on 2008-03-31
The hardy Heron upgrade messed up my button mapping.
My gutsy button map (1 2 3 6 7) got the thumb buttons working.  Now the thumb buttons scroll right/left.
I'm experimenting with new mapping.

---

### Post by Marktheawesome on 2008-04-01
> **NineseveN said:**
> FYI, when using the Nvidia X driver, if you have Nvidia configure your xorg.conf, adding the lines suggested in this thread will cause your xorg.conf to be unusuable.
. . .
it should look like the following:
```
Section "InputDevice"
# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 4 5"
EndSection
```

When I tried this I still get the same problem. My side buttons are not working like they should. Right now my forward button is a right click and my back button is a paste (<control>v).

MX900 with nVidia driver.

My xorg looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"buttons"	"7"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"no"
	Option		"ButtonMapping"	"1 2 3 6 7 4 5"
EndSection
```
What am I doing wrong? It's driving me nuts not having my side buttons:(

---

### Post by energy. on 2008-04-02
> **Marktheawesome said:**
> When I tried this I still get the same problem. My side buttons are not working like they should. Right now my forward button is a right click and my back button is a paste (<control>v).

MX900 with nVidia driver.

My xorg looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"buttons"	"7"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"no"
	Option		"ButtonMapping"	"1 2 3 6 7 4 5"
EndSection
```
What am I doing wrong? It's driving me nuts not having my side buttons:(

try this

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
EndSection

```

---

### Post by Marktheawesome on 2008-04-02
the broswer buttons now do nothing. At least that is a start.
They don't left click or paste anymore but they also don't go forward or backwards.

---

### Post by Tgon on 2008-04-03
> **har5ha said:**
> This Works  for : **[Logitech MediaPlay Cordless Mouse]("http://www.amazon.com/Logitech-MediaPlay-Cordless-Mouse-Blue/dp/B0002SAF3C")**
[B]
Note : [/B]Instead of  [Option  **"CorePointer"**] 

I have [Option  **"AlwaysCore"**] , as I am using it as secondary pointer device [ie. on a Laptop].


Thanks Everybody !!! :)

I'm using a mediaplay mouse and have followed these same settings but still it wont work, do I need to change a setting somewhere that tells the computer I'm using the custom mouse profile?

Also how do I program the other buttons? can I set the media buttons to open a progam and have the volume and track skip work?

---

### Post by Marktheawesome on 2008-04-04
> **Marktheawesome said:**
> the broswer buttons now do nothing. At least that is a start.
They don't left click or paste anymore but they also don't go forward or backwards.bump. I would really like to get this issue resolved.

---

### Post by nilsglow on 2008-04-28
> **Marktheawesome said:**
> the broswer buttons now do nothing. At least that is a start.
They don't left click or paste anymore but they also don't go forward or backwards.

according to [https://bugzilla.mozilla.org/show_bug.cgi?id=355477](https://bugzilla.mozilla.org/show_bug.cgi?id=355477) the problem seems to be with firefox. it had it's mouse button mapping changed to follow the current convention (in GTK+ and Qt). now mouse buttons 6 and 7 are for horizontal scroll and 8 and 9 for back and forward.

I finally fixed my back (and forward) button in firefox by switching 6/7 with 8/9 because I actually only have 7 buttons... I did the switch with xmodmap and made it permanent by creating the file $HOME/.Xmodmap with the content:

pointer = 1 2 3 4 5 8 9 6 7

with this remapping through xmodmap I do not need ANY adjustments in xorg.conf. so my InputSection now looks like this:

Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Protocol"		"auto"
Option		"Emulate3Buttons"	"true"

I hope this helps...

---

### Post by auslander1138 on 2008-04-29
> **nilsglow said:**
> according to [https://bugzilla.mozilla.org/show_bug.cgi?id=355477](https://bugzilla.mozilla.org/show_bug.cgi?id=355477) the problem seems to be with firefox. it had it's mouse button mapping changed to follow the current convention (in GTK+ and Qt). now mouse buttons 6 and 7 are for horizontal scroll and 8 and 9 for back and forward.

I finally fixed my back (and forward) button in firefox by switching 6/7 with 8/9 because I actually only have 7 buttons... I did the switch with xmodmap and made it permanent by creating the file $HOME/.Xmodmap with the content:

pointer = 1 2 3 4 5 8 9 6 7

with this remapping through xmodmap I do not need ANY adjustments in xorg.conf. so my InputSection now looks like this:

Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Protocol"		"auto"
Option		"Emulate3Buttons"	"true"

I hope this helps...
@nilsglow

which mouse do have?

I'm still pounding my head against the wall trying to get the side buttons of my Intellimouse Exlorer (wired) working

This is what I have so far and scrolling is working again (broke that for a while) but I can't seem to get the side buttons to work no matter...

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option	   "Device"		"/dev/input/mice"
    Option	   "Protocol"		"ExplorerPS/2"
#    Option	   "ZAxisMapping"		"6 7"
#    Option         "Emulate3Buttons"	"false"
#    Option 	   "Buttons" 		"7"
#    Option         "ButtonMapping" 	"1 2 3 4 5"
EndSection

Thanks!

aus

---

### Post by panosy on 2008-05-16
OK, after A LOT of trial and error (there should be a proper manual for that), the MS intellimouse USB works (scroll with wheel AND back-for buttons in firefox) with that:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
EndSection

at least for me it does. Now the wheel doesn't work as a 3rd button, not even with 3rd button emulation, but it's good enough for a start..

---

### Post by TearDownAllSigns on 2008-05-16
I upgraded to Hardy today and among other annoyances my back and forward buttons stopped working in Firefox. I have a Logitech Wireless Laser Mouse. 

I looked at the above sited bug entry and saw the patch for it maps mouse buttons 8-9 to the back/forward commands. I was able to fix it by playing the pair 8 and 9 in the right position. I originally had "1 2 3 6 7 4 5" which worked on Gutsy, and ended up with "1 2 3 8 9 4 5 6 7". 

Here is what worked for me:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"ButtonMapping"	"1 2 3 8 9 4 5 6 7"
```

You may need to play around with placing the 8 and 9 values in your ButtonMapping to match up with the design of your particular mouse. 

I have also plugged in a USB MS Intellimouse and find that this works with the above setting also. 

Now if I could just figure out how to get rid of the black screen that now plagues my Orange Box games I'll be a happier man. Miss me some Team Fortress 2.

---

### Post by TearDownAllSigns on 2008-05-16
It seems that Hardy is a bit better than Gutsy at working without having the manually defined mappings. As auslander1138 notes, you can run the Xorg with out the last three options from my last post and get the same results. 

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
```

I'm guessing people doing a fresh install of Hardy won't be visiting this thread too much, but people who are upgrading and had to change their settings before may want to run without any manual mapping and see if that works.

---

### Post by Adahn on 2008-05-17
Option		"ButtonMapping"	"1 2 3 **8 9**"

Thank you for mentioning the firefox bug.  The changes above fixed the side buttons on my Razer Diamondback.
This has been annoying the pi$$ out of me since I upgraded.

---

### Post by Ux64 on 2008-05-17
> **TearDownAllSigns said:**
> It seems that Hardy is a bit better than Gutsy at working without having the manually defined mappings.

Thanks. Let's see if that works. Because manual mappings DIDN'T work with Hardy...

I had this stuff working fine with Gutsy but after Upgrade to Hardy it didn't work out anymore. I'll now try your suggestion.

```

#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
##     Option         "Protocol" "ImPS/2"
#    Option         "Buttons" "10"
#    Option         "ZAxisMapping" "4 5"
#    Option         "ButtonMapping" "1 2 3 6 7"
#    Option         "Emulate3Buttons" "true"
#EndSection

```

---

### Post by pannerrammer on 2008-05-17
> **Ux64 said:**
> Thanks. Let's see if that works. Because manual mappings DIDN'T work with Hardy...

I had this stuff working fine with Gutsy but after Upgrade to Hardy it didn't work out anymore. I'll now try your suggestion.

```

#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
##     Option         "Protocol" "ImPS/2"
#    Option         "Buttons" "10"
#    Option         "ZAxisMapping" "4 5"
#    Option         "ButtonMapping" "1 2 3 6 7"
#    Option         "Emulate3Buttons" "true"
#EndSection

```

Recommend you have a look at [URL="http://ubuntuforums.org/showthread.php?t=787790"]http://ubuntuforums.org/showthread.php?t=787790
[/URL]

---

### Post by prostar on 2008-06-07
Just to post what did work for me with MS Intellimouse Explorer 2.0 wireless:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"ButtonMapping"	"1 2 3 8 9 4 5 6 7"
```

---

### Post by reginak on 2008-06-15
> **gbendotti said:**
> This works for the Evoluent VerticalMouse 3


For the sake of a complete Linux newbie, could you please spell out what exactly you are mapping to each button?  I also have the VerticalMouse, and I'd like to have it the way it works in Windows, i.e.: thumb = back, left = left, middle = double-click, right = right, scroll wheel scrolls and I don't know what it does if you click on it. Probably scroll lock. I love having one-click "back" and "double-click". 

Thanks!!
Regina

---

### Post by pannerrammer on 2008-06-17
> **reginak said:**
> For the sake of a complete Linux newbie, could you please spell out what exactly you are mapping to each button?  I also have the VerticalMouse, and I'd like to have it the way it works in Windows, i.e.: thumb = back, left = left, middle = double-click, right = right, scroll wheel scrolls and I don't know what it does if you click on it. Probably scroll lock. I love having one-click "back" and "double-click". 

Thanks!!
Regina

Regina, 
The imwheel/xmodmap stuff that worked with Gutsy doesn't seem to load properly when Hardy starts up - most posts here since April are concerned with modifying xorg.conf, which is no longer necessary.

Have a look at [http://ubuntuforums.org/showthread.php?t=787790](http://ubuntuforums.org/showthread.php?t=787790) where I've tried to describe a method to help you match your buttons to actions (assuming you've got imwheel installed see esp. step 5). 

imwheel does not operate on buttons 1,2 and 3 (left, middle, right) only buttons 4 upwards. To get round this the pointer command is used to 'fool' imwheel by remapping a higher number to 1,2 or 3 - so to get the attention of your middle button you might need something like ```
pointer = 1 8 3 4 5 6 7 2 9
```  (so 2 becomes 8 and 8 becomes 2). Some remappings work better than others.

Also imwheel refers to buttons by name, so button 8 ought to be called ExtBt8 (but it might turn out to be Thumb1 or Thumb2 - there is some inconsistency!). 

Again, see step 5 in [http://ubuntuforums.org/showthread.php?t=787790](http://ubuntuforums.org/showthread.php?t=787790) to work out your optimum pointer/imwheel settings.

The .imwheelrc code for a double click is **[COLOR=DarkRed]Button1, 2[/COLOR]** ( **[COLOR=DarkRed]Button1[/COLOR]** is the left one, and **[COLOR=DarkRed], 2[/COLOR]** means twice). So, if Thumb1 is the name of your button 8 (which you've remapped to button 2)...  a line such as ```
None, Thumb1, Button1, 2
``` will be required in .imwheelrc

All the best...

---

### Post by esaym on 2008-07-11
This worked for me, microsoft usb intellimouse:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ButtonMapping" "1 2 3 8 9"
    Option         "ZAxisMapping" "4 5"
EndSection

---

### Post by Robin.Muilwijk on 2008-07-13
> **TearDownAllSigns said:**
> I upgraded to Hardy today and among other annoyances my back and forward buttons stopped working in Firefox. I have a Logitech Wireless Laser Mouse. 

I looked at the above sited bug entry and saw the patch for it maps mouse buttons 8-9 to the back/forward commands. I was able to fix it by playing the pair 8 and 9 in the right position. I originally had "1 2 3 6 7 4 5" which worked on Gutsy, and ended up with "1 2 3 8 9 4 5 6 7". 

Here is what worked for me:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"ButtonMapping"	"1 2 3 8 9 4 5 6 7"
```

You may need to play around with placing the 8 and 9 values in your ButtonMapping to match up with the design of your particular mouse. 

I have also plugged in a USB MS Intellimouse and find that this works with the above setting also. 

Now if I could just figure out how to get rid of the black screen that now plagues my Orange Box games I'll be a happier man. Miss me some Team Fortress 2.

Thanks you so much, the buttonmapping is all I had to change to get my back button working again.

---

### Post by ch_123 on 2008-07-30
Hey Folks,

In Windows and Mac software for certain mice (Kensington ones in particular come to mind), it is possible to set up mouse buttons so that pressing two of them causes a particular effect (lets say for example, pressing left and right simulataneously has the effect of middle clicking). Is it possible to emulate this in Linux?

---

### Post by Loverentiy on 2009-01-15
u 8.10, 
Objective: Functional back/forward mouse buttons in Nautilus
(x buttons working in Firefox, auto configured Xorg file by Nvidia)

```

sudo aptitude install imwheel

```
```

sudo gedit /etc/X11/imwheel/startup.conf

```
change IMWHEEL_START=0 to IMWHEEL_START=1
```

sudo gedit /etc/X11/imwheel/imwheelrc

```
# Add the following to the bottom of the existing file:
```

    ".*"
    None, **Thumb1**, Alt_L|Left
    None, **Thumb2**, Alt_L|Right
    "(null)"
    None, **Thumb1**, Alt_L|Left
    None, **Thumb2**, Alt_L|Right

```

#
on a personal note way to get a newbie to think [ubuntu-tutorials](http://ubuntu-tutorials.com/2006/12/02/imwheel-5-button-mouse-within-nautilus-ubuntu-610/)... I was wondering why my mouse wheel was navigating instead of scrolling ;)

---

### Post by amadeus266 on 2009-04-19
These 5 button mice are very common these days. Why don't we have the ability to choose which type the user has during installation, and then load the appropriate driver on startup?

---

### Post by hyperair on 2009-04-19
The default is evdev nowadays, and I think it supports 5 buttons pretty well.

---

