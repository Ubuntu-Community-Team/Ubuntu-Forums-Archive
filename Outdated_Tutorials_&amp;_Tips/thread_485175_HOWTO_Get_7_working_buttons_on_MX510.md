---
title: "HOWTO: Get 7 working buttons on MX510"
date: 2007-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by BobLand on 2007-06-26
This works for my MX510 running fiesty 7.04
Users report that the following mouse devices also work:
   *LogiTech G5
   *LogiTech wireless Media Play
   *MX600 cordless laser
   *MX610 laser

backup xorg.conf naming the backup with an identifier such as date, name, pets name...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.<my_backup_name>
```

edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

copy this code over your existing mouse code
the red indicates code that makes this all work
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        [COLOR="Red"]Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"[/COLOR]
EndSection
```

with this mouse and fiesty, the auto protocol is recommended
the ZAxixMapping tells the wheel to emulate the up/down scroll/cruise buttons
the order of the mapping is crucial - see below

save your changes
```
ctrl-s
```

close the file
```
ctrl-q
```

restart X
```
Ctrl+Alt+Backspace
```

The screen will go black for a second or 2 then you'll see a message about running local scripts. This may happen very quickly or it may take anywhere between a few seconds or minutes. You will be placed back at the login screen.  If you haven't done this before, don't worry about losing this page.  Open FF (don't know if this works with other browsers) and click Restore Session.  It will take you back to this page.

That's it! Done!
Now, test the changes

```
login
```

Open a browser window and open a few urls in the same tab.
Test all of your buttons.

The only ones that don't work (for me) are the second button from the bottom of the wheel and pressing the wheel to get smooth scrolling, but I'm working on that one.

The button mapping is as follows:
```
1 - left click
2 - middle click/scroll up/scroll down
3 - right click
4 - button above the wheel: scroll up
5 - button directly below the wheel: scroll down
6 - lower side button: go back
7 - upper side button: go forward
8 - the zen button: nothingness
```

Seems like the order of buttons in the mapping is crucial. If you just run 1 2 3 4 5 6 7 you won't get all the buttons to work. However, if this is a setting that is unique to particular computers then you should try different orders until you get them all to work.

If this is a dismal failure then restore your backup. You did make a backup, didn't you?
```
sudo cp /etc/X11/xorg.conf <my_backup_name> /etc/X11/xorg.conf
```

06/27/2007 - After reinstalling fiesty, I enabled this code for the mouse.  I found that when button 4, scroll up, was pressed at the top of a page it would become button 6, which is "go back."  I test this with xev to confirm.  I didn't see this on the pre-reinstall.  Let me know if you experience this problem.

bobland

---

### Post by KubuntuKilledMe on 2007-06-27
I can report that this howto works to enable the Back/Forward buttons on the Logitech G5 mouse as well with no modifications.

Thank you very much for your contribution, BobLand.

---

### Post by gnychis on 2007-06-28
worked perfect for me also!

thanks!

---

### Post by Brewster123 on 2007-07-06
Worked well on a Logitech wireless "Media Play" mouse too. Not interested in all the media buttons themselves but sorely missed the forward and backward buttons. Now they work great! 

Thanks!!!

---

### Post by WolfHeart on 2007-07-08
Thanks mate, now all my buttons work, i have an mx510 so now i can finally use it for what its worth :D 

However, you are right about button 4 becoming button 6 when reaching the top of the page. very annoying, but i hardly use those buttons anymore due to the fact they are worn out :)

Thanks again for a very good guide :)

---

### Post by Coopish on 2007-07-08
When i follow this guide my X wont start again. 

Is there other things you can try to make it work also? 
(kinda new to ubuntu)

---

### Post by crjackson on 2007-07-08
> **BobLand said:**
> This works for my MX510 running fiesty 7.04

backup xorg.conf naming the backup with an identifier such as date, name, pets name...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.<my_backup_name>
```

edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

copy this code over your existing mouse code
the red indicates code that makes this all work
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        [COLOR="Red"]Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"[/COLOR]
EndSection
```

with this mouse and fiesty, the auto protocol is recommended
the ZAxixMapping tells the wheel to emulate the up/down scroll/cruise buttons
the order of the mapping is crucial - see below

save your changes
```
ctrl-s
```

close the file
```
ctrl-q
```

restart X
```
Ctrl+Alt+Backspace
```

The screen will go black for a second or 2 then you'll see a message about running local scripts. This may happen very quickly or it may take anywhere between a few seconds or minutes. You will be placed back at the login screen.  If you haven't done this before, don't worry about losing this page.  Open FF (don't know if this works with other browsers) and click Restore Session.  It will take you back to this page.

That's it! Done!
Now, test the changes

```
login
```

Open a browser window and open a few urls in the same tab.
Test all of your buttons.

The only ones that don't work (for me) are the second button from the bottom of the wheel and pressing the wheel to get smooth scrolling, but I'm working on that one.

The button mapping is as follows:
```
1 - left click
2 - middle click/scroll up/scroll down
3 - right click
4 - button above the wheel: scroll up
5 - button directly below the wheel: scroll down
6 - lower side button: go back
7 - upper side button: go forward
8 - the zen button: nothingness
```

Seems like the order of buttons in the mapping is crucial. If you just run 1 2 3 4 5 6 7 you won't get all the buttons to work. However, if this is a setting that is unique to particular computers then you should try different orders until you get them all to work.

If this is a dismal failure then restore your backup. You did make a backup, didn't you?
```
sudo cp /etc/X11/xorg.conf <my_backup_name> /etc/X11/xorg.conf
```

06/27/2007 - After reinstalling fiesty, I enabled this code for the mouse.  I found that when button 4, scroll up, was pressed at the top of a page it would become button 6, which is "go back."  I test this with xev to confirm.  I didn't see this on the pre-reinstall.  Let me know if you experience this problem.

bobland

[SIZE="2"][B]@Bobland

I followed your guide and it did get my side buttons working for forward/back.  None of the other buttons (aside from left/right click) do anything.  What am I doing wrong here?[/B][/SIZE]

---

### Post by RLembke on 2007-07-09
Also works with MX600 laser cordless mouse.  Thanks!

---

### Post by BobLand on 2007-07-11
Coopish,
When you say your X wont start, are you forced on the command line?  What are you doing to recover?  If you have the patience, restore the InputDevice section in xorg.conf and change each parameter one at a time until you find the line that doesn't work.  I would start in order, that is, 
```
Option          "Protocol"              "auto"
```
If that works then proceed to the next line, and so on.

Also try the process I outlined below to verify your buttons are read correctly.  Are you sure that nothing else was changed in your xorg.conf?  This is a very fussy file and the slightest change can put you in the dark ages.  Make sure you have a clean, unchanged, original xorg.conf lying around somewhere.  Never touch it, just copy it.  Create a backup directory
```
sudo mkdir /etc/X11/backed_up_original_conf <or whatever name suits you>
```
Copy the clean xorg.conf to the backup directory
```
sudo cp /etc/X11/xorg.conf /etc/X11/backed_up_original_conf <whatever>/xorg.conf.original
```
You want to rename this file so you don't inadvertently change it.

Let me know how this works for you.

crjackson
Try this.  Open a terminal and type in```
 xev
```  This program will test each button on your mouse.  A window will open with a box.  Place your cursor in the box.  On my system I can use the full window.  This program will track everything your mouse can do.  Note that it will display ALL movement so when you go test your buttons, the slightest movement will remove the parts we are looking for.  It will look pretty hairy at first but after a few tries you'll get the hang of it.

Press the buttons that are not working.  In the terminal you will see a lot of code that displays events.  You want to find the **ButtonPress** event, not the ButtonRelease event.

Look for the code in red
```
ButtonPress event, serial 29, synthetic NO, window 0x4a00001,
    root 0x156, subw 0x4a00002, time 951412529, (41,48), root:(1491,96),
    state 0x10, **[COLOR="Red"]button 1[/COLOR]**, same_screen YES
```

Write down the button numbers for all button presses.  You may have to create a different mapping.  If this is the case, make the appropriate change to the ButtonMapping in the xorg.conf.  

If this still doesn't work, let me know and we'll try something else.

bobland

---

### Post by crjackson on 2007-07-12
**Bobland**

> crjackson
Try this. Open a terminal and type in
Code:

 xev

This program will test each button on your mouse. A window will open with a box. Place your cursor in the box. On my system I can use the full window. This program will track everything your mouse can do. Note that it will display ALL movement so when you go test your buttons, the slightest movement will remove the parts we are looking for. It will look pretty hairy at first but after a few tries you'll get the hang of it.

Press the buttons that are not working. In the terminal you will see a lot of code that displays events. You want to find the ButtonPress event, not the ButtonRelease event.

Look for the code in red
Code:

ButtonPress event, serial 29, synthetic NO, window 0x4a00001,
    root 0x156, subw 0x4a00002, time 951412529, (41,48), root:(1491,96),
    state 0x10, button 1, same_screen YES

Write down the button numbers for all button presses. You may have to create a different mapping. If this is the case, make the appropriate change to the ButtonMapping in the xorg.conf.

If this still doesn't work, let me know and we'll try something else.

bobland

[B]When I press the scroll up button it reports as button 2 - When I press the scroll down button it reports nothing.  When I press the wheel button down it report button 2.  When I press the focus/app button it reports button 2.  Nothing was red.

All other buttons work as normal.[/B]

---

### Post by slughappy1 on 2007-07-12
It also worked for my MX610 laser mouse

---

### Post by thanius on 2007-07-13
I there! I followed the guide, managed to get my MX510 to work - though not flawlessly. All buttons work as they should, except for the UP-button above the scrollwheel. It does scroll up when pressed, but after releasing the button it does a BACKSPACE (Or ALT_LEFT or Back-in-browsing-history, or wtf).

xev reports the button 4 upon pressing down and button 6 upon releasing the button.

How to fix?

---

### Post by BobLand on 2007-07-13
crjackson,
xev interprets mouse events and passes them to your application.  If it doesn't see the event then you may need to remap the ButtonMapping.  

Does the mouse work in a pure Windows environment, that is to say, not an emulator or vm?  If you can, try to borrow a friend's mouse and test it with xev.   

You could also try going to a local store buying a mouse.  If it doesn't work then return it for a refund but make sure the store will allow you to do that.  

When you press all the buttons, what is the highest number returned?  Are the ButtonPress numbers sequential or is there a skip?  Perhaps, this button mapping doesn't work for your mouse and you need a different one.  It's not hard to change, just tedious.

If that still doesn't work then I'd venture to guess it may be a faulty mouse.

Keep me posted on your progress,
bobland

---

### Post by crjackson on 2007-07-13
> **BobLand said:**
> crjackson,
xev interprets mouse events and passes them to your application.  If it doesn't see the event then you may need to remap the ButtonMapping.  

Does the mouse work in a pure Windows environment, that is to say, not an emulator or vm?  If you can, try to borrow a friend's mouse and test it with xev.   

You could also try going to a local store buying a mouse.  If it doesn't work then return it for a refund but make sure the store will allow you to do that.  

When you press all the buttons, what is the highest number returned?  Are the ButtonPress numbers sequential or is there a skip?  Perhaps, this button mapping doesn't work for your mouse and you need a different one.  It's not hard to change, just tedious.

If that still doesn't work then I'd venture to guess it may be a faulty mouse.

Keep me posted on your progress,
bobland

The mouse with all buttons work perfectly under windows.  Tested on 3 machines.

The highest number returned is 7.

Left Click = 1
Right Click =3
Wheel Click = 2
Wheel Scroll up = 4
Wheel Scroll dn = 5
Cruse Up = 6
Cruse Dn = nothing
Forward click = 7
Back click = 6
Event Focus button click = 2

The mouse works fine on all windows computers.

---

### Post by BobLand on 2007-07-13
thanias,
What you reported is a minor bug that is unique to this mouse and perhaps others.  Nothing much to do about it unless the driver is updated in a later version.

Does this behavior happen if the scroll up button is anywhere but the top?  One thing to try is not releasing at the top but move/scroll down just a bit before releasing.

Let me know if that works.

bobland

---

### Post by thanius on 2007-07-13
Nopes.

"It hurts pretty much around the bloody spot."

In other words, anywhere I click the button it goes backwards.

---

### Post by BobLand on 2007-07-13
thanius,
The problem seems to be related to the fact that the ButtonPress is 4 but the ButtonRelease is 6.  ButtonPress 5 releases on 2.  Since that is a scrolling wheel I'm assuming the driver sees it as a stationary 2 so the it doesn't move.  Does this behavior display in all programs?

My ButtonPress 4 / Release on 6 only goes back at the top of the screen.  In the middle or bottom it behaves as expected.

Try changing the button mapping.  Perhaps, you'll hit the right combination.  We're pretty much stuck with what is returned by xev unless you want to try and reprogram the driver.

Sorry.  Maybe someone will see this thread and know exactly how to fix this.  Keep your fingers crossed.

bobland

---

### Post by BobLand on 2007-07-13
Here's what I've observed and can only conclude that there is a bug in the driver for this mouse.

left click:         
ButtonPress 1 state 0x10  ButtonRelease 1 state 0x110 - consistent

wheel pressed down:  
ButtonPress 2 state 0x10  ButtonRelease 2 state 0x210 - consistent

right click:      
ButtonPress 3 state 0x10  ButtonRelease 3 state 0x410 - consistent

wheel up/scroll up:       
ButtonPress 4 state 0x10  ButtonRelease 4 state 0x810 - consistent (button not pushed down)

wheel down/scroll down:  
ButtonPress 5 state 0x10  ButtonRelease 5 state 0x1010 - consistent (button not pushed down)

side button forward:
ButtonPress 6 state 0x10  ButtonRelease 6 state 0x10 - consistent (side button)

side button backwards:
ButtonPress 7 state 0x10  ButtonRelease 7 state 0x10 - consistent (side button)

*scroll up button (above wheel):
ButtonPress 6 state 0x10  ButtonRelease 6 state 0x810 while held down, on actual release state 0x10 - consistent is this anomalous behavior

scroll down button (below wheel)
ButtonPress 5 state 0x210 ButtonRelease 5 (still held down) state 0x1210 - on actual release state 0x210 button 2 - no noticeable behavior change.

* the scroll up button's behavior is not consistent.  When I changed the mapping by leaving out the last 6, restarted, the button behaved for about 3 minutes then reverted to the behavior as experience by thanius.  When I changed it back to the original, again, it displayed normal behavior but after about 5 button presses, it reverted to inconsistent behavior.

My conclusion is there is a bug in the driver and we will have to live with this.  I'll try to post this to the proper people.

Thanks for your patience,
bobland

---

### Post by goonies on 2007-07-14
I have a mx600.  With this configuration I am left with 5 buttons that dont work.  the 2 left and right side buttons of the scroll wheel (to scroll left and right by using the scroll wheel).  and the 3 zoom buttons + - and 100%.  Has anyone ever got these buttons to work?

---

### Post by BobLand on 2007-07-14
goonies,
You may want to contact the poster in message #8.  He has an MX600 and has reported success with this process.

bobland

---

### Post by AdrianOfTyriel on 2007-07-17
has there been any luck getting the zen button (8 i believe) working?

---

### Post by BobLand on 2007-07-17
As far as I know, LogiTech will not offer any assistance to Linux programmers regarding programming mouse buttons.  What we are able to use at this moment is through the efforts of the programming community to solve this problem.

As far as I know, button 8 is still in orbit over Mars.

bobland

---

### Post by AegisTalons on 2007-07-19
Just wanted to say thanks and that it worked perfectly. I also want to say that I have a Logitech MX 518 Optical Mouse.

---

### Post by ubuntuforums on 2007-08-12
Thank you, worked partly for my Logitech Cordless Click! Plus.  Mouse4 and Mouse5 now work for forward and back.  But for some reason now when I push the scroll button to the left it functions as back (rather than scrolling left), but pushing to the right does nothing.  Mouse3 does nothing, and the top mouse button (mouse6?) doesn't do anything either.  Mouse1, Mouse2, and scrolling up and down works as usually.

---

### Post by wrongo on 2007-08-12
My mouse is the "IntelliMouse USB and PS/2 Compatible," and bobland's codes made BACK and FORWARD buttons work, but yeah, "smooth scroll" still doesn't work, i.e., "Button 2" shows up in the "xev" window but has no functionality

Smooth scroll is a MUST for reading down long webpages "hands-free"

Any ideas?

---

### Post by ubuntuforums on 2007-08-13
Option 1:  Get a bigger monitor so you can fit the entire webpage on screen.  
Option 2:  Decrease font size so you can fit the entire webpage on screen. :D

---

### Post by wrongo on 2007-08-13
UbuntuForums, are you serious? "Get a bigger monitor?" I've got thick skin, but that feels cavalier of you. Do not underestimate the power of wrongo! Long ago was it that I learned how to change mere font size. Recall, won't you, that this thread concerns configuring mouses in ubuntu, and please, address the issue. Perhaps you are afraid of the mighty Smooth Scroll? In that case, Smooth Scroll challenges UbuntuForums to a duel! Will the mighty UbuntuForums answer the challenge? Are there any Ubuntu users who know the power and majesty of Smooth Scroll?

Is this thing on?

I'm trying to get my screen to scroll down smoothly by pressing on the wheel, having my mouse pointer turn into a little circle with UP and DOWN arrows on it depending on if I move my mouse up or down; and if I move it up (above the little circle, mind you) then the page magically begins to move upward and will continue to move upward until I make it stop. The same is true for, wouldn't you know it, if I click the wheel, get the circle (with the UP and DOWN arrows) and move the mouse down. Guess what? The screen begins smoothly scrolling down. And the farther down I move my mouse (and then leave it alone) the faster the screen automatically scrolls down.

I tell you this after three successful months of my present Ubuntu install; and I come to these forums because, otherwise totally satisfied, yet the magnificent Smooth Scroll was available in my old operating system, whose name I cannot bring myself to mention, but whose initials were X and P.

There, now are you ready to discuss Smooth Scroll yet, or would you like to tell me how to remove CAPS LOCK or NUM LOCK or some other rudimentary computing skill - perhaps you want to share your ALT+TAB technique for switching between windows. I mean, my god! Were you just out of coffee when you wrote that post? I love you, but puh-leeze!

Jerit

---

### Post by ubuntuforums on 2007-08-13
You smell.  In Firefox do the following:  Edit > Preferences > Advanced, now check off auto-scrolling. :)

---

### Post by pt123 on 2007-08-14
I can't get buttons 4 or 5 working, and most likely 6 & 7. Tried xev and when I use the buttons 4 or 5 it doesnt pick it up. I have a 510 mouse.

In xorg.conf it is slightly different 
it had this for device:
Option          "Device" "/dev/psaux"

---

### Post by pt123 on 2007-08-14
I am also using Loco to get the resolution to 800.

---

### Post by Soren on 2007-08-15
Just wanted to say thank you! This worked beautifully with my Logitech MX900 Bluetooth mouse. :)

---

### Post by ushi_cz on 2007-09-06
Hi ppl!

I have MX510 and I've tried xev to recognize the buttons. The same problem as you with scrollUp button. When it is released, it throws "button 6 event". I hope somebody will fix that.

But I would like to ask you if somebody knows how to change number of lines in the setup of the scroll buttons (number 4 and 5). I used to use these buttons in windows as page up and page down, this setup is more useful for me. Or it could be as a scroll with more lines than just a three lines. Like this I can more quickly browse the documents. If somebody knows pls advise me.
Thanks...

---

### Post by kcjeffery on 2007-10-04
I appreciate the first post as it got my MX510 mouse *close* to working. I found the following changes were necessary to get the up scroll button working.

Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 8 9 10 4 5"

---

### Post by mattigras on 2007-10-04
**ATTENTION BLUETOOTH USERS:  ** A couple hours after writing this I came home and rebooted my laptop with my bluetooth mouse switched off and X would not start. I replaced ```
Option  "CorePointer"
``` with ```
Option "SendCoreEvents"  "true"
``` in my "InputDevice" Section below and now X starts even if my mouse is turned off. (I followed the [Ubuntu Bluetooth page]("https://help.ubuntu.com/community/BluetoothSetup") and edited my */etc/default/bluetooth* to make it connect automatically). When I turn the mouse on, Kubuntu detects it and automatically starts using it, but my horizontal scrolling is reversed because it didn't run my Xmodmap script (near the bottom of this post). I'm going to try and see if there's a way to configure the bluetooth daemon to run a bash script when it connects to my mouse to map my buttons correctly, and post my findings as soon as possible. Once I get everything working nicely I think I'm gonna re-post this as its own howTo. please give me feedback!

The rest of this post should still be fine for non-bluetooth mice users.....




> **AdrianOfTyriel said:**
> has there been any luck getting the zen button (8 i believe) working?
If it worked for me it should work for you:

I started using this [HowTo]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons"), but pretty much just ended up reading man pages.

The  xorg "mouse" driver currently only supports up to 7 buttons, so to get your 8th (or more in my case) button working, you need to use the "evdev" driver, which supports up to 24 buttons.  

My Bluetooth mouse (labeled Dell DH421, but really a re-branded Logitech) has 9 buttons (4-way scroll wheel and 2 side buttons). Before the steps below, my normal primary, secondary and ternary buttons, and vertical scrolling worked; and my side buttons registered as another set of secondary and ternary buttons, but my horizontal scrolling wasn't recognized.  After the steps I took below, so far all 9 show up correctly in *xev*, but currently the 2 side buttons (8 and 9) don't actually do anything in KDE. I'm sure I can get them to do something interesting using step 6 of that HowTo, but i don't care that much at the moment.

Here are my steps so far:

As always, make a back-up in case you break something:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Now, evdev comes pre-installed in Feisty, you just need to tell it to load the module.  I added a line to the "Module" Section of xorg.conf: 
```

Section "Module"
	Load	"i2c"
	.
	.
[B]	Load	"evdev"
[/B]EndSection

```

Then found my mouse in the output of *cat /proc/bus/input/devices*
```
I: Bus=0005 **Vendor=046d Product=b004** Version=7515
N: **Name="Logitech Bluetooth Mouse"**
P: Phys=00:15:83:F0:DB:0C
S: Sysfs=/class/input/input7
H: Handlers=mouse2 event7 ts2
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
```

Then I edited my InputDevice section to use the evdev driver instead of the mouse driver. I left the Identifier and the "CorePointer" options the same, but changed the driver and deleted the mouse driver's options to make room for evdev options:  
```

Section "InputDevice"
	Identifier	"Configured Mouse"
[B]	Driver		"evdev"
[/B]	Option		"CorePointer"
[B]	Option		"Name"			"Logitech Bluetooth Mouse"
	Option		"vendor"		"046d"
	Option		"product"		"b004"
[/B]EndSection

```
I'm pretty sure it would work without the "Name", "Vendor" and "Product" Options, but I'm on my laptop so the bt mouse is the 2nd pointing device, and I just wanted to be safe.

Save the file, Ctrl+Alt+BackSpace, and cross your fingers.

After restarting X, all buttons showed up in xev (yay!) but scrollwheel-left(button 7) was scrolling right, and scrollwheel-right(button 6)was scrolling left. No problem, I opened up a terminal and used xmodmap to switch the buttons:
```
xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9"  
```
And that made them work right. It gave me some error about changing only 9 of 12 buttons, but It's definitely a 9 button mouse. If you don't want the extraneous error, this does the exact same thing as far as I can tell:
```
xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12"  
```

Then I saved it so that it switches those buttons every time X starts and I'm done:
```
echo -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12\n" > ~/.Xmodmap
```

So right now, this is what my buttons do:
```
1: (left) primary click
2: (middle) ternary click
3: (right) secondary click
4: (wheel-up) scroll up
5: (wheel-down) scroll down
6: (wheel-left) firefox:History-Back, scroll left in everything else
7: (wheel-right) firefox:History-Forward, scroll right in everything else
8: (thumb-back) registers with X, but not assigned yet
9: (thumb-forward) registers with X, but not assigned yet
```

I'm pretty sure that this will work for any mouse that you can lay your hands on. Please tell me if this gets that Zen button working!

---

### Post by crjackson on 2007-10-24
Any updates as to how well all this works on Gutsy?

---

### Post by dlpfmVfH on 2007-10-25
I´m running gutsy with my mx510 mouse, with all buttons enabled with this xorg.conf:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "Device"    "/dev/input/mx510"

where /dev/input/mx510 is a link to /dev/input/event3

---

### Post by crjackson on 2007-10-25
> I´m running gutsy with my mx510 mouse, with all buttons enabled with this xorg.conf:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "Device"    "/dev/input/mx510"

where /dev/input/mx510 is a link to /dev/input/event3

Okay, if I cut and past this into my xorg.conf as shown, will it work or do I need to do something additional with:

> where /dev/input/mx510 is a link to /dev/input/event3

---

### Post by mattigras on 2007-10-25
> **aboe said:**
> I´m running gutsy with my mx510 mouse, with all buttons enabled with this xorg.conf:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "Device"    "/dev/input/mx510"

where /dev/input/mx510 is a link to /dev/input/event3

Did you already know about evdev or did you try it after looking at my post? I'm just trying to see if I actually helped someone

---

### Post by crjackson on 2007-10-25
> **mattigras said:**
> Did you already know about evdev or did you try it after looking at my post? I'm just trying to see if I actually helped someone

Well, I still don't know about it, can you throw me a bone.  Can I cut and past the code above and make it work or what else must I do?

Nevermind, I read above about it.  Seems like it may be beyond my skill level to get going....

---

### Post by boast on 2007-10-29
First, is linux not capable of detecting mouses during installation and adding the neccesary configs to xorg?

Second, how can I get this working with nautilus or w/e its called?

Third, in windows clicking the middle button creates a circle with arrows pointing in all directions, so you can move the screen around, instead of going sidebar and scroll bar till you get the spot. In firefox, nothing happens. In opera, middle clicking with something highlighted just searches it in google.

thanks for your efforts.

---

### Post by mattigras on 2007-10-30
> **crjackson said:**
> Well, I still don't know about it, can you throw me a bone.  Can I cut and past the code above and make it work or what else must I do?

Nevermind, I read above about it.  Seems like it may be beyond my skill level to get going....

You won't be able to just straight copy and paste that code. Well, you will, but you'll have to change one word.Type ```
cat /proc/bus/input/devices
``` and then find your mouse and it's event handler. Here is what mine looked like. My mouse's event is in bold:
```
I: Bus=0005 Vendor=046d Product=b004 Version=7515
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:15:83:F0:DB:0C
S: Sysfs=/class/input/input7
H: Handlers=mouse2 **event7** ts2
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
```
Then paste this over the mouse section in your xorg.conf, changing the part in bold to match your mouse from above. It will always be "event" and then a number:
```

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"evdev"
	Option 		"Device" 	"/dev/input/**event7**"
EndSection

```
I think that should get it working. Post back if you have any problems


> **boast said:**
> First, is linux not capable of detecting mouses during installation and adding the neccesary configs to xorg?

Second, how can I get this working with nautilus or w/e its called?

Third, in windows clicking the middle button creates a circle with arrows pointing in all directions, so you can move the screen around, instead of going sidebar and scroll bar till you get the spot. In firefox, nothing happens. In opera, middle clicking with something highlighted just searches it in google.

thanks for your efforts.
First, as far as I know, Linux only has auto mouse detection to the point that it can detect your mouse and detect if you have a scroll wheel. If you have a fancy mouse with lots of buttons then you need to configure it yourself.

Second, I don't know too much about Nautilus b/c I'm a KDE user.

Third, in Firefox, try going "Edit"->"Preferences", then "Advanced." On the "General" Tab, select the 3rd checkbox, which should be labelled "Use autoscrolling." Alternatively or in addition, you could use the ["All-in-One Gestures" Firefox Add-on]("https://addons.mozilla.org/en-US/firefox/addon/12"). In the Options for All-in-One Gestures,choose "All-in-One Autoscroll" in the "Middle Button Scrolling: Select" section. That should make your mouse behave like a Windoze mouse in firefox. I can't help you with Opera b/c I've never used it.

---

### Post by boast on 2007-10-30
> **mattigras said:**
> 

Third, in Firefox, try going "Edit"->"Preferences", then "Advanced." On the "General" Tab, select the 3rd checkbox, which should be labelled "Use autoscrolling." Alternatively or in addition, you could use the ["All-in-One Gestures" Firefox Add-on]("https://addons.mozilla.org/en-US/firefox/addon/12"). In the Options for All-in-One Gestures,choose "All-in-One Autoscroll" in the "Middle Button Scrolling: Select" section. That should make your mouse behave like a Windoze mouse in firefox. I can't help you with Opera b/c I've never used it.

cool, thanks.

---

### Post by rexless on 2007-11-01
Greets.
The simple changes worked for me as well.  All I did was edit the:

sudo su
vi /etc/X11/xorg.conf
 
Changed the mouse lines to look like:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "auto"
        Option          "Buttons"       "7"
        Option          "ZAxisMapping"  "4 5"
        Option          "ButtonMapping" "1 2 3 6 7 4 5 6"
EndSection

CTRL-ALT-Backspace and login.  Lovely.  Just lovely.

---

### Post by dlpfmVfH on 2007-11-02
> **mattigras said:**
> Did you already know about evdev or did you try it after looking at my post? I'm just trying to see if I actually helped someone

I used evdec, since dapper, so I already knew about it,
but in gutsy it is working without any additional stuff in xorg.

---

### Post by Stigern on 2007-11-05
> This is UDO Version 6.4.1 for Linux
Copyright (c) 1995-2001 by Dirk Hagedorn
Copyright (c) 2001-2004 by The UDO community
UDO is Open Source (see [http://www.udo-open-source.org](http://www.udo-open-source.org) for further information).

######## errors, warnings and notes:


What I get at running sudo gedit :S

---

### Post by boast on 2007-12-01
im using an mx510, and button 8 shows up on xev; 

i want to control compiz scale with button 8, and since I have scale as f12, I set .xbindkeysrc with ```
"xvkbd -text "\[F12]""
        m:0x10 + b:8

``` but it only works at random times; sometimes I press it and nothing happens- continuously pressing it, it will occasionally work

---

### Post by endo666 on 2007-12-01
hay just to let the OP know this guide worked for me with a Mx518 in ubuntu 7.10

---

### Post by marcusklaas on 2007-12-09
Thanks dawg. It worked instantly, couldn't get it working myself. I still don't grasp why the buttons have to be mapped in that order though :( oh well, guess I don't have to. Thnx

---

### Post by Tom Brokaw on 2007-12-19
This mostly worked on my MX510 as well, which is also going through my Linksys KVM.  The extra buttons work in Firefox, but the back and forward (4 ad 5, I believe) move the scrollbar in Nautilus instead of navigating folders.  Good enough though.

---

### Post by mevans336 on 2008-03-19
Scratch that, all is well!

---

### Post by lacrias on 2008-05-08
I just updated to Hardy 8.04 with Firefox 3 beta 5 and my buttons didn't work, even after following this guide (which worked wonderfully with firefox 2!!)

I did some researching and found this:

[http://support.mozilla.com/en-US/kb/Mouse+buttons+do+not+work+as+Back+and+Forward](http://support.mozilla.com/en-US/kb/Mouse+buttons+do+not+work+as+Back+and+Forward)

Apparently the buttons firefox use to go back and forwards were switched from 6 7 to 8 9. If you goto that link it shows you how to set up the about:config to fix this problem.

Hope this helps :)

---

### Post by mortem on 2008-05-21
lacrias saves the day!

---

### Post by Alien.col on 2008-06-26
lacrias i luv u man...

---

### Post by ryth on 2008-09-01
This worked great minus the "scroll up" button sending out a "back button" signal at the end, very irritating.

Another problem I have run into is that now my mouse scrolling is slow and inconsistent at best.  A lot of the time scrolling the wheel results in no page movement up or down, or when it does it may go 2-3 lines and then stop even though I continue to use the scroll wheel.

Anyone else encountering this problem?

---

### Post by SnowPunk98 on 2008-09-06
I got everything working but the scroll up button (above the wheel) is also sending be back a page.

---

### Post by FokkerCharlie on 2008-09-28
Hello!

I have a Logitech Cordless Optical Trackman, and it seems to be quite a similar setup to the MX510.

I have this in my xorg.conf:

```
Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"evdev"
	Option 		"Device" 	"/dev/input/event10"
	Option 		"Buttons" 		"10"
	Option		"ZAxisMapping"		"4 5"
	Option 		"ButtonMapping" 	"1 2 3 6 7 8 9 10 4 5"
EndSection
```

Which works fine, apart from when using the scroll buttons (not wheel), xev reports something slightly strange.  It seems to think that when I use the 'up' button, I am holding button 9, and pressing button 4 repeatedly, then releasing 9.  The down button is similarly mapped to 10 and 5.  A rudimentary workaround is to add this to .xbindkeysrc:

```
#Workaround for cruise up/dn buttons mapped as 9 and 10:
"/usr/bin/xvkbd -xsendevent -text "\""
    m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\"" 
    m:0x0 + b:10
```

Which worked OK in Gutsy, but doesn't seem to cut it in Hardy.  It seems that for some reason, btn 9 is mapped to 'forward' in  FF now.  If anyone has a clever idea, I'd love to hear it.

Cheerio
Charlie

---

### Post by Setheus on 2009-04-16
Worked great with my MX 510 + Kubuntu Intrepid. :) 
Thanks!!

---

