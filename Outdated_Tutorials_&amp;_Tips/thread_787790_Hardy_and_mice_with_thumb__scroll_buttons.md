---
title: "Hardy and mice with thumb / scroll buttons"
date: 2008-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by pannerrammer on 2008-05-09
This tutorial explains how to get the thumb buttons to work with Hardy (sometimes the thumb buttons will work with Firefox but not with Nautilus, on other installations the thumb buttons do nothing).

The widely-circulated instructions that install imwheel, then create an 63xmodmap file, etc, no longer work with Hardy (whether you do a fresh install or an upgrade from Gutsy). 

The tutorial has been tested using several mice, including Intellimouse and Logitech Nano VX.

I've divided the tutorial into several steps, some of which you might be able to skip. 




[SIZE=3][COLOR=DarkRed]**Step 1 - Undoing previous changes**[/COLOR][/SIZE]

If you've followed imwheel/xmodmap/startup.conf instructions described in other threads then this step describes how to clean/remove all the stuff you've done.

If you've never installed imwheel then you can skip this step.


[COLOR=Navy]**Re-configure xorg.conf**[/COLOR]

Make a copy of xorg.conf, just in case things go wrong 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

[B]Note: If things do go wrong and you can no longer start X, then this
```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```
will recover your original xorg.conf file. Case matters. Make a note of it before you continue![/B]

Now, edit xorg.conf with
```
gksu gedit /etc/X11/xorg.conf
```
The mouse section probably looks similar to this:
```
Section "InputDevice" 
     Identifier    "Configured Mouse"  
     Driver        "mouse" 
     Option        "CorePointer" 
     Option        "Device"    "/dev/input/mice" 
     Option        "Protocol"    "ExplorerPS/2" 
     Option        "Buttons"    "7" 
     Option        "ButtonMapping"    "1 2 3 8 9"  
     Option        "Emulate3Buttons"    "false" 
EndSection
```
Change it to this:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection
```
Save, then Quit.


[COLOR=Navy]**Re-configure the imwheel startup file**[/COLOR]

You no longer need imwheel to start as the machine boots, so
```
gksu gedit /etc/X11/imwheel/startup.conf
```
and change the setting (back) to 
```
IMWHEEL_START=0
```


[COLOR=Navy]**Delete the xmodmap file**[/COLOR]

Various threads create either 57xmodmap or 63xmodmap. Whatever, you won't need them anymore.
```
sudo rm /etc/X11/Xsession.d/57xmodmap*
```
or 
```
sudo rm /etc/X11/Xsession.d/63xmodmap*
```
(I've added the * because if you've edited more than once there will be 63xmodmap and 63xmodmap~).

OK, other than the .imwheelrc file (which you'll edit below) you should now be back where you started.


[COLOR=Navy]**Check that imwheel no longer starts**[/COLOR]

Restart your computer, then click [COLOR=Indigo]System > Administration > System monitor > Processes[/COLOR] and search for an imwheel entry - there shouldn't be one!




[SIZE=3][COLOR=DarkRed]**Step 2 - Just upgraded from Gutsy?**[/COLOR][/SIZE]

If you've upgraded from Gutsy the mouse section of the xorg.conf file isn't the same as if you'd done a fresh install of Hardy. This step makes them the same.

Skip this section if you've done a fresh install of Hardy (or just completed Step 1).

Make a copy of xorg.conf, just in case things go wrong
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

[B]Note: If things do go wrong and you can no longer start X, then this
```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```
will recover your original xorg.conf file. Case matters. Make a note of it before you continue![/B]

Now, edit xorg.conf with
```
gksu gedit /etc/X11/xorg.conf
```
The mouse section probably looks similar to this:
```
Section "InputDevice" 
     Identifier    "Configured Mouse"  
     Driver        "mouse" 
     Option        "CorePointer" 
     Option        "Device"    "/dev/input/mice" 
     Option        "Protocol"    "ExplorerPS/2" 
EndSection
```
Change it to this:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection
```
Save, Quit, then Restart your computer.




[SIZE=3][COLOR=DarkRed]**Step 3 - Which imwheel is right for you?**[/COLOR][/SIZE]

You should not skip this step.

In Gutsy it doesn't seem to matter, but in Hardy it does; imwheel can run in 2 modes, controlled by the -f (for focus) parameter. Use the wrong mode and you'll either run out of memory after 20 minutes, or your computer will fail to come out of screensaver/hibernation.

According to the imwheel documentation, the -f parameter "Forces the X event subwindow to be used instead of the original hack that would replace the subwindow in the X event with a probed focus query (XGetInputFocus)", which clears that up then!


[COLOR=Navy]**Install imwheel**[/COLOR]

If you haven't previously done so, install imwheel with ```
sudo apt-get install imwheel
```


[COLOR=Navy]**Make imwheel autostart when you log on**[/COLOR]

Create an autostart folder with ```
mkdir ~/.config/autostart
``` (don't worry if it already exists).

Then create a new autostart file with ```
gedit ~/.config/autostart/amouse.desktop
```
Copy and paste this 
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=amouse
Comment=amouse
Exec=imwheel
X-GNOME-Autostart-enabled=true
```

Save, then Quit.


[COLOR=Navy]**Find which imwheel mode to use**[/COLOR]

Restart your computer (logout/login is not enough), then click [COLOR=Indigo]System > Administration > System monitor > Processes[/COLOR] and scroll down to the imwheel entry.

If imwheel is Running, using 15-20% of processor time and eating memory then you need the -f parameter.

If imwheel is Sleeping, using 0% processor time, and using 200-300k memory, then you do not need the -f parameter.

Click on the imwheel process, then click [COLOR=Indigo]End Process[/COLOR] (and again!).




[SIZE=3][COLOR=DarkRed]**Step 4 - Quick and easy thumb buttons**[/COLOR][/SIZE]

If you're just looking for a quick and easy way to get the thumb buttons to work, if you don't want to mess with the scroll buttons, or swap buttons around then this step's for you. Thanks to Cubeist.

Do not do this step until you've done Step 3.


[COLOR=Navy]**Create and configure .imwheelrc**[/COLOR]


Create an .imwheelrc file with 
```
gedit ~/.imwheelrc
```
Copy and paste this 
```

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```


[COLOR=Navy]**Make imwheel start when you turn your computer on**[/COLOR]

Edit the autostart file you created in step 3 with 
```
gedit ~/.config/autostart/amouse.desktop
```
If you need the -f parameter, change the Exec line to: ```
Exec=imwheel -k -f -b "0 0 0 0 8 9"
```
If you do not need the -f parameter, change the Exec line to: ```
Exec=imwheel -k -b "0 0 0 0 8 9"
```

Save then Quit, and that's it. 

Logout/login and the two thumb buttons should work. 

Note: if they're the wrong way round then re-edit .imwheelrc and swap Up and Down. Save, Quit then logout/login again.




[SIZE=3][COLOR=DarkRed]**Step 5 - Troubleshooting your buttons**[/COLOR][/SIZE]

(...or, a bit more about imwheel and xmodmap)

This step provides a technique to help you work out what button does what. The aim is not to make the buttons do anything useful, just to identify a 'best mapping' between imwheel and xmodmap. You can play with the settings until you get it right!

imwheel can take control of button 'events' 4,5,6,7,8,9,10 and 11. 

imwheel reckons that:
[LIST]
[*]Buttons 4,5 represent the forward/backward scroll wheel, and calls them Up, Down
[*]Buttons 6,7 represent the left/right tilt wheel, and calls them Left, Right
[*]Buttons 8,9 represent the 2 thumb buttons, and calls them Thumb1, Thumb2
[*]Buttons 10,11 represent any extra buttons, and calls them ExtBt7, ExtBt8
[/LIST]

imwheel is unable to do anything to button 'events' 1, 2 or 3 (left, middle and right click). 

In an ideal world imwheel numbers and your mouse button 'event' numbers would match... but with some mice they don't.  Which is where xmodmap comes in - it enables you to renumber/remap the buttons.


[COLOR=Navy]**Configure an experimental .imwheelrc**[/COLOR]

Edit your .imwheelrc file with 
```
gedit ~/.imwheelrc
```
Copy and paste this for initial testing
```

".*"
None, Up, U
None, Down, D
None, Left, L
None, Right, R
None, Thumb1, 1
None, Thumb2, 2
None, ExtBt7, 7
None, ExtBt8, 8
```
When you click various buttons in a text editor (below) the mouse will type U,D,L,R,1,2,7,8 

Once you know which button does what you can re-edit .imwheelrc to do something more useful.

The None at the beginning of each line means 'just the mouse button' (ie. without a modifier)... See man imwheel for more, but you can set up the Thumb button, Alt+Thumb, Ctrl+Thumb, etc.

In many guides the codes are repeated under the entry "(null)". I've not (yet) found any instance where this is needed.


[COLOR=Navy]**Testing your buttons**[/COLOR]

Essentially, we're trying to identify which button on the mouse corresponds to Up, Down, Left, Right, Thumb1, Thumb2, ExtBt7, ExtBt8 (though you may not have them all).

Start the Text editor (in Accessories)

In Terminal:

If you need the -f parameter, copy and paste this: ```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"; imwheel -k -f -b "4 5 6 7 8 9"
```
If you do not need the -f parameter, copy and paste this: ```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"; imwheel -k -b "4 5 6 7 8 9"
```

[LIST]
[*]The ; lets you do multiple commands in one go.
[*]The xmodmap command sets up a pointer array with 9 buttons. Notice that I've added all 9 - adding less creates an warning/error, as does repeating the same number twice.
[*]The imwheel command means that when button4 is pressed the matching action in .imwheelrc happens, etc. The -k stops any running instances of imwheel.
[/LIST]
Click into the Text editor and click away. On my mouse both thumbs but only one of the scroll buttons work with the above settings.

Press the up-arrow in Terminal to re-edit the command. 

The variant below works best for me (in the xmodmap command I've swapped the 4-5 and the 6-7 pairs). It gives me control over forward-scroll, backward-scroll, small-thumb and big-thumb.
```
xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9"; imwheel -k -f -b "4 5 6 7 8 9"
```

If you don't want to muck about with the scroll wheels, and just want to grab the thumb-buttons then try the following variant (the 0 means imwheel does not take control of button events 4,5,6, and 7, so only 'events' 8 and 9 are processed).
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"; imwheel -k -f -b "0 0 0 0 8 9"
```

Changing 8 9 to 9 8 will swap the thumbs 
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8"; imwheel -k -f -b "0 0 0 0 8 9"
```
You could do this in either the xmodmap or the imwheel command, but not both or you're back where you started!

If you're left handed and only want to swap the left and right buttons try this
```
xmodmap -e "pointer = 3 2 1 4 5 6 7 8 9"; imwheel -k -f -b "0 0 0 0 8 9"
```

Assuming this works for you ;) make a note of the modmap and imwheel numbers because they're needed in the step 7.




[SIZE=3][COLOR=DarkRed]**Step 6 - What do you want your buttons to do?**[/COLOR][/SIZE]

Making your mouse buttons type U,D,L,R, etc isn't all that handy. 

The .imwheelrc file enables you to make the thumb buttons (usually) do something special. For instance they might be set to mean 'copy' and 'paste' in the OpenOffice Wordprocessor, and Next/Prev in Firefox/Nautilus. A couple of examples:
[LIST]
[*]If your mouse responds by typing L and R when you click the thumb buttons, replace L and R with [COLOR=Indigo]Alt_L|Left[/COLOR] and [COLOR=Indigo]Alt_L|Right[/COLOR] ...this lets you scroll to next/previous in Firefox, Nautilus, etc
[*]If your mouse responds by typing 1 and 2 when you click the thumb buttons, replace the 1 and 2 with [COLOR=Indigo]Control_L|c[/COLOR] and [COLOR=Indigo]Control_L|v[/COLOR] ...the thumb buttons will work as copy and paste
[*]Fed up double-clicking? Replace the thumb button action with [COLOR=Indigo]Button1, 2[/Indigo] and a single click of the thumb button will be a double-click (note the [COLOR=DarkGreen]**, 2**[/COLOR] which means do Button1 twice)
[/LIST]
[COLOR=Indigo]Alt_L[/COLOR] means the left Alt key, [COLOR=Indigo]Control_L[/COLOR] means the left Control key (so you can guess what _R does!)


[COLOR=Navy]**Configure .imwheelrc**[/COLOR]

Edit the .imwheelrc file with 
```
gedit ~/.imwheelrc
```
Replace the test letters with a more appropriate action.

To test the changes you make to .imwheelrc ...save, then re-run your preferred variant of the [COLOR=Indigo]xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9"; imwheel -k -f -b "4 5 6 7 8 9"[/COLOR] command in Terminal.




[SIZE=3][COLOR=DarkRed]**Step 7 - Configuring your mouse with imwheel and xmodmap**[/COLOR][/SIZE]

Assuming that you've now got .imwheelrc as you want it (Step 6), we need to make imwheel/xmodmap start when you login.


[COLOR=Navy]**Create a .Xmodmap file**[/COLOR]
```
gedit ~/.Xmodmap
```
Copy and paste this
```

pointer = 1 2 3 4 5 6 7 8 9

```
Replace the pointer numbers so they match what you wrote down in Step 5. Notice that you don't need the xmodmap -e bit. Save, then Quit.


[COLOR=Navy]**Make imwheel start when you turn your computer on**[/COLOR]

Edit the autostart file you created in step 3 with 
```
gedit ~/.config/autostart/amouse.desktop
```
If you need the -f parameter, change the Exec line to: ```
Exec=imwheel -k -f -b "0 0 0 0 8 9"
```
If you do not need the -f parameter, change the Exec line to: ```
Exec=imwheel -k -b "0 0 0 0 8 9"
```

Replace the imwheel numbers so they match what you wrote down in Step 5. 

Save, then Quit, and that's it. 

Logout/login and you'll be asked what to do with the .Xmodmap file you created. Click on it then Add (so it appears on the left), then ok. Your new mouse setting should work.




[SIZE=3][COLOR=DarkRed]**Further information**[/COLOR][/SIZE]
You can do the same thing as the .config/autostart stuff by clicking [COLOR=Indigo]System > Preferences > Sessions > Add[/COLOR])

According to [http://bugzilla.gnome.org/show_bug.cgi?id=314800]("http://bugzilla.gnome.org/show_bug.cgi?id=314800") we can expect a fix sometime soon, but as the bug was first reported in Aug 2005 don't hold your breath.

Some threads covering ATI graphics drivers suggest that xserver-xgl needs to be installed. This caused my working imwheel setup to fail! On Hardy, uninstalling xserver-xgl didn't affect my graphics and imwheel worked once more.

---

### Post by linux4me on 2008-05-20
I have an Intellimouse Explorer USB/PS2 mouse that's hooked up via PS2 connection.

I had all the buttons working in Gutsy just by setting the following in /etc/X11/xorg.conf:
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons"       "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping"  "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

I never installed imwheel before.

After I upgraded to Hardy, the entries above are still in xorg.conf, but I no longer have the thumb buttons working in Firefox or Nautilus. (They never did work in Nautilus, but they worked in Firefox.)

I followed Method 1 of the instructions and except for having to create the folder/file autostart/amouse.desktop first before Gedit would let me save to it, it all went smoothly.

I restarted and confirmed in System->Administration->System Monitor->Processes that imwheel is there, and it says it's "sleeping", but I still don't have working thumb buttons in Firefox.

Is there something else I need to do or some way I can troubleshoot this?

---

### Post by pannerrammer on 2008-05-21
Hi linux4me.

First, edit your /etc/X11/xorg.conf so it looks like this
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
#    Option         "Buttons"       "7"
#    Option         "ButtonMapping" "1 2 3 6 7"
#    Option         "ZAxisMapping"  "4 5"
#    Option         "Emulate3Buttons" "true"
EndSection
```
The # simply makes the line a comment. Then reboot the pc so the new config is active. The lines you've commented out don't appear at all when you do a new install of Hardy.

You might have created the amouse.desktop file in the wrong place because the .config/autostart folder should already exist (because it's where your Sessions stuff (like Evolution notification) is. Check amouse.desktop is listed in Sessions by clicking System > Preferences > Sessions (if not you can click Add - the command is ```
imwheel -k -f -b "0 0 0 0 8 9"
``` and the rest is amouse).

Does this help?

---

### Post by Chokkan on 2008-05-21
One of the surprising things I found with my fresh install is that my thumb buttons worked 'out of the box' with my Cordless Desktop MX3000 mouse.

---

### Post by pannerrammer on 2008-05-21
> **Chokkan said:**
> One of the surprising things I found with my fresh install is that my thumb buttons worked 'out of the box' with my Cordless Desktop MX3000 mouse.
Hi Chokkan.
Do your thumb buttons work with Nautilus, or just Firefox?
Regards, pannerrammer

---

### Post by linux4me on 2008-05-21
> **pannerrammer said:**
> 
First, edit your /etc/X11/xorg.conf so it looks like this
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
#    Option         "Buttons"       "7"
#    Option         "ButtonMapping" "1 2 3 6 7"
#    Option         "ZAxisMapping"  "4 5"
#    Option         "Emulate3Buttons" "true"
EndSection
```
The # simply makes the line a comment. Then reboot the pc so the new config is active. The lines you've commented out don't appear at all when you do a new install of Hardy.


Hooray! Commenting out those lines worked perfectly! Thanks pannerrammer!

I can't explain the issue with the folder autorun and saving the amouse file. I can confirm that it does appear in sessions, and I do use Evolution, but there wasn't an autostart folder in /home/<my account name>/.config. Very strange.

---

### Post by wild_oscar on 2008-05-31
I got my MS Intellimouse working correctly with the following configuration in .imwheelrc:

```
".*"
#None, Up, Alt_L|Left
#None, Down, Alt_L|Right
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

I commented the Up and Down lines and got:
- scroll wheel scrolls correctly in Nautilus and Firefox
- Thumb buttons correctly go back/forward in Nautilus and FF

---

### Post by linux4me on 2008-05-31
I should mention I decided to switch from 32-bit Hardy to 64-bit, and did a clean install of 64-bit Hardy.

My Intellimouse Explorer (PS2), including the wheel and thumb buttons,  worked without any tweaking on my part at all, and imwheel was not required.

I don't know if it was the clean install or a difference with 64-bit, but I am happy.

---

### Post by skinnie on 2008-06-06
I have a microsoft intellimouse 1.1a and it works out of the box in hardy (in "explorer" and firefox (in feisty I needed to edit the xorg.conf), althought  in opera it doesn't work...it is needed to instal imwheel?
any tips?
I am using hardy 64bit.

---

### Post by pannerrammer on 2008-06-06
> **skinnie said:**
> I have a microsoft intellimouse 1.1a and it works out of the box in hardy (in "explorer" and firefox (in feisty I needed to edit the xorg.conf), althought  in opera it doesn't work...it is needed to instal imwheel?
any tips?
I am using hardy 64bit.

Hi skinnie.

When Hardy was released Firefox recognised the thumb buttons because of coding in Firefox (not because of the coding in Hardy).  Similar coding is promised for the back/forward buttons in Nautilus - I presume you mean Nautilus, not "explorer" :) 

But I don't think that will extend to OpenOffice or Opera, etc.

I did a fresh install of hardy 64bit today and uploaded all the updates, but the thumb buttons still don't work (for me) in Nautilus without imwheel. So, to get Opera to respond to the thumb buttons I'd guess you need imwheel too.

pannerrammer

---

### Post by marklid on 2008-06-07
> **wild_oscar said:**
> I got my MS Intellimouse working correctly with the following configuration in .imwheelrc:

```
".*"
#None, Up, Alt_L|Left
#None, Down, Alt_L|Right
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

I commented the Up and Down lines and got:
- scroll wheel scrolls correctly in Nautilus and Firefox
- Thumb buttons correctly go back/forward in Nautilus and FF

Worked a treat, thanks to the posters in this thread !

---

### Post by reginak on 2008-07-05
Hardy? Gutsy? Sleepy? Do I feel Dopey? A neighbor installed Ubuntu for me, just a few weeks ago. I am not a geek (although I wanted Linux partly because I miss being able to tell the computer exactly what I want, sick of GUI Windows). The CD he left says Ubuntu 8.04 i386. How do I know if I have Hardy or Gutsy? 

Thank you

---

### Post by reginak on 2008-07-05
> **pannerrammer said:**
> See man imwheel for more

How does one "see man imwheel"?  Does that mean the manual for imwheel?  Is it online? 

TIA
Regina

---

### Post by skinnie on 2008-07-05
> **reginak said:**
> Hardy? Gutsy? Sleepy? Do I feel Dopey? A neighbor installed Ubuntu for me, just a few weeks ago. I am not a geek (although I wanted Linux partly because I miss being able to tell the computer exactly what I want, sick of GUI Windows). The CD he left says Ubuntu 8.04 i386. How do I know if I have Hardy or Gutsy? 

Thank you
If it is 8.04 it is hardy..a simple google search would have told you that.

---

### Post by linux4me on 2008-07-05
> **reginak said:**
> How does one "see man imwheel"?  Does that mean the manual for imwheel?  Is it online?

The manuals for most things are already on your machine. You can access the one for imwheel by going Applications->Accessories->Terminal, then typing:
```
man imwheel
```
and pressing Return.

You navigate the manual using the Page Up and Page Down keys, and type "Q" when you're done to quit the manual.

---

### Post by reginak on 2008-07-05
Thank you, Skinnie & Linux4me. This is making my brain hurt! I should stick to the Absolute Beginners forum, but I've got this daggone fancy Evoluent Vertical Mouse, and I want it to work!

I did step 5 ... 
The left button works as advertised.
The middle button acts as right-click (doesn't type anything, it just brings up the menu with undo, etc.)
The right button acts as Thumb1 (types a 1)
Up and down scroll are fine
I have no sideways scrolls
The thumb button (there's only 1 on this mouse) works as Thumb2

So I want to make the middle button act as double-click instead of right-click. You say that is Button 1, 2.  I want to make the right button act as the right button instead of as Thumb 1. And I want to make the thumb button (now mapped as Thumb2) act as "back" in Firefox (Alt_L|Left).

Help?

---

### Post by BLTicklemonster on 2008-07-05
One of the confusingest how tos I've seen yet. I don't think I want my buttons working in nautilus bad enough to attempt this again.

---

### Post by reginak on 2008-07-06
OK ... I know, that was too lazy of me. I should experiment with it myself, and figure it out. After all, it's just the mouse -- I still have the touchpad, so if I totally screw up the mouse it's not like I'll be paralyzed, right? OK, here goes ..... I will report back!

](*,)
Regina

---

### Post by reginak on 2008-07-06
Hey ... it works! Woohoo, I have my double-click and my browser-back buttons!  Yay! and thank you!

I made the xmodmap order = 1 2 6 4 5 9 7 3 8
and the imwheelr is 
".*"
None, Up, Up
None, Down, Down
None, Left, Button1, 2
None, Right, R
None, Thumb1, Alt_L|Left
None, Thumb2, 2
None, ExtBt7, 7
None, ExtBt8, 8

Too bad imwheel doesn't seem to recognize clicking the wheel, I'd map it to Alt_L|Right. But I didn't have that in Windows either, so I am not complaining!

Thank you pannerrammer!

---

### Post by reginak on 2008-07-06
Ugh, I take it back. Double-click isn't working.

---

### Post by L a r r y on 2008-07-06
I have a lead-foot finger on the right mouse button.  In Ubuntu 8.04, I have this very undesirable jump to the top or to the end of the document I am scrolling through, using left-clicks on the up-arrow or down-arrow at each end of the scrollbar, when my right finger decides to lay down on the right button.

I have a couple thumb buttons on my Rocketfish 2.4GHz wireless laser mouse that don't do anything in Linux, so I have reassigned the right mouse button to the top thumb button, and the top thumb button to the right mouse button.  The new right mouse button does nothing when I lay my heavy finger on it.  The bottom thumb button is a double-click button now.

I found from this tutorial that my /etc/X11/xorg.conf file contained some useless configuration stuff now, left over from my upgrade from 6.06.  I removed everything from the mouse configuration section, leaving ```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

``` 
with no ill effects.  My ~/.Xmodmap contains ```
pointer = 1 2 8 4 5 6 7 3 9
```
There I just switched position 3 with position 8 to do the right-click-Thumb1 swap.

My  ~/.config/autostart/amouse.desktop contains```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=amouse
Comment=amouse
Exec=imwheel -k -b "0 0 0 0 0 9"
X-GNOME-Autostart-enabled=true
```

That activates the lower thumb button in imwheel, which I have configured for double-click in  ~/.imwheelrc thusly:```
".*"
None,Thumb2,Button1,2
```
My hearty thanks to the author of this fine tutorial!

---

### Post by Harpz on 2008-08-18
> **wild_oscar said:**
> I got my MS Intellimouse working correctly with the following configuration in .imwheelrc:

```
".*"
#None, Up, Alt_L|Left
#None, Down, Alt_L|Right
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

I commented the Up and Down lines and got:
- scroll wheel scrolls correctly in Nautilus and Firefox
- Thumb buttons correctly go back/forward in Nautilus and FF

This one worked a treat, i can scroll back/Forward in Nautilus and Firefox with my IntelliMouse Optical.

Dose anyone know how to get it to double click with the wheel? (the wheel has a click as well as a scroll up and down function) at the moment it pastes whatever I've highlight when i wheel click a location in a text editor. 

It opens a link i click on in Firefox in new tab (this is right) but in win if i wheel clicked it would allow me to shoot up and down the page.

Im mainly after a double click in Nautilus

Is it possible?
Thanks in advance
Mike

---

### Post by faheyd on 2008-08-18
> **pannerrammer said:**
> This tutorial explains how to get the thumb buttons to work with Hardy (sometimes the thumb buttons will work with Firefox but not with Nautilus, on other installations the thumb buttons do nothing).

.....

Some threads covering ATI graphics drivers suggest that xserver-xgl needs to be installed. This caused my working imwheel setup to fail! On Hardy, uninstalling xserver-xgl didn't affect my graphics and imwheel worked once more.

Unfvcking believable that a user has to go through all that shite to get a 5 button mouse to work. I've been using linux since 1994 and this has always bugged the hell out of me.  WHY CAN'T a simpler method be found within the mouse driver itself for xwindows....

If they can get  a damn graphics tab to work, a simple 5 button mouse should be easy.

---

### Post by jimgeroul on 2008-11-09
I'm using Ubuntu 8.10 intrepid now.. and i'm using the "Trust MI-7700R wireless laser mouse" witch has 11 buttons.
buttons 1,2,3 well known.
buttons 4,5 it's the wheel, scroll up down
buttons 6,7 also wheel buttons left and right
buttons 8,9 thumb button and
button 10,11 (extra buttons) zoom in-out buttons

The problem is that i cant have these two last buttons get recognized. is it because of the imwheel?? it can only recognize 9 buttons?? Does anyone know how can i enable them?

I can't use btnx because it does not detect the mouse at all (i think because i'm on ubuntu 8.10)

any suggestion??

---

### Post by pannerrammer on 2008-11-10
Hi jimgeroul. 

I have 5 fingers/thumbs on my left hand and 5 more on my right, totalling 10. What do you use to press your 11th button? :twisted:

imwheel can take control of button 'events' 4,5,6,7,8,9,10 and 11 - have you tried step 5 on the first page of this tutorial to capture events 10 and 11? 

Most of my instructions only go up to button 9, so you'll need to modify them for all 11, similar to
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8 10 11"
imwheel -k -f -b "0 0 0 0 8 9 10 11"
```I did read that btnx and 8.10 don't like each other.

I've installed 8.10 and this method still works fine for my old MS Intellimouse, and for my new wireless MS laser mouse 7000 (which was expensive, is uncomfortable to use, and keeps losing its wireless signal!).

> **jimgeroul said:**
> I'm using Ubuntu 8.10 intrepid now.. and i'm using the "Trust MI-7700R wireless laser mouse" witch has 11 buttons.
buttons 1,2,3 well known.
buttons 4,5 it's the wheel, scroll up down
buttons 6,7 also wheel buttons left and right
buttons 8,9 thumb button and
button 10,11 (extra buttons) zoom in-out buttons

The problem is that i cant have these two last buttons get recognized. is it because of the imwheel?? it can only recognize 9 buttons?? Does anyone know how can i enable them?

I can't use btnx because it does not detect the mouse at all (i think because i'm on ubuntu 8.10)

any suggestion??

---

### Post by jimgeroul on 2008-11-11
Hi pannerrammer,

I've tried the step you said but my ExtBt7 and ExtBt8 still don't respond. I also tested other combinations such as:
```

~$ xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8 10 11"
   Warning: Only changing the first 11 of 32 buttons.
~$ imwheel -k -b "0 0 0 0 10 11"
   INFO: imwheel(pid=6073) killed.
   INFO: imwheel started (pid=6175)
   Unrecognized wheel action in config. Ignoring action.
   ExtBt7
   Unrecognized wheel action in config. Ignoring action.
   ExtBt8

```

or
```

xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8 10 11"
imwheel -k -b "0 0 0 0 10 11 8 9"

```

wich has the same result.. Thumb button's output was 7 and 8
and ExtBt7 and ExtBt8 did not work at all.. :(

The problem is that the system doesn't even know they exist... ^^
I tried running xev, all other buttons responded, these two didn't.

As btnx is concerned, it didn't work when i was on ubuntu 8.04 too. It could not detect the mouse at all!

---

### Post by pannerrammer on 2008-11-17
Hi jimgeroul.

If your buttons are not being seen by xev then I guess it's unlikely that imwheel can see your mouse events either (but I've now gone beyond my technical ability!).

I spent quite a long time deciphering (trying to) the info in the imwheel manual (man imwheel), there are several options/areas I didn't explore cos I didn't need them - have a look for yourself.

Also, in several areas in the imwheel manual it shows things like this
 ```
KeySym   IMWheel Input  Real Mouse
              ------   -------------  ----------
              Button1  (none)         Left Mouse Button
              Button2  (none)         Middle Mouse Button
              Button3  (none)         Right Mouse Button
              Button4  Up             Mouse Wheel Up
              Button5  Down           Mouse Wheel Down
              Button6  Left           Mouse Wheel Left
              Button7  Right          Mouse Wheel Right
              Button8  Thumb1         Side Mouse Button 1 (left/up)
              Button9  Thumb2         Side Mouse Button 2 (right/down)
              Button10 ExtBt7         Extra Mouse Button 1
              Button11 ExtBt8         Extra Mouse Button 2
              etc.
```The interesting bit is the word 'etc.' - I know this will be a bit of a chore, but maybe imwheel handles events all the way up to button 32. Dunno, might be worth filling in all the blanks and giving it a try.

pannerrammer

---

### Post by PhonicLynx on 2008-12-15
I have something else I want to do. I set up my buttons in Windows to have button 6 and 7 (left and right scroller) to make them press Ctrl-Shift-Tab and Ctrl-Tab, respectively. This allows me to use the tabs in Mozilla and switch between them quickly because I check alot of sites at once and like to flip between them back and forth.

How would I set up the config files to reflect this.. its kinda handy in alot of different programs too

:popcorn:

ps 10 and 11 I am using Crtl-F4 and Alt-F4.. close mini window.. and close app.

---

### Post by webbdawg on 2008-12-20
I got my son running Ubuntu on his amd sempron 2300. We are using a MS wireless 3000 keyboard / mouse w3 buttons.

The three buttons are theleft, right and the wheel button. Right now the wheel button acts just like the left click. 

I want the wheel button the be the trigger the "Back" in a browser.

Any ideas on that?? Thanks

---

### Post by jimgeroul on 2008-12-22
you can do this by editing/creating the "~/.imwheelrc" file. Look post about imwheel! That should do.

---

### Post by BLTicklemonster on 2008-12-26
Well all I have to say is that I'm a bit miffed that Firefox knows exactly what to do with my mouse, but Gnome or Ubuntu don't. Firefox goes forward and backward just fine when I hit my buttons. Seems like Ubuntu would come out of the box working already with mice that have forward and back buttons.

---

### Post by BLTicklemonster on 2009-02-16
> **wild_oscar said:**
> I got my MS Intellimouse working correctly with the following configuration in .imwheelrc:

```
".*"
#None, Up, Alt_L|Left
#None, Down, Alt_L|Right
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```

I commented the Up and Down lines and got:
- scroll wheel scrolls correctly in Nautilus and Firefox
- Thumb buttons correctly go back/forward in Nautilus and FF

that setting works exactly right for me with a logitech mx310

---

### Post by Lampi on 2009-06-15
After reading the [wiki]("https://help.ubuntu.com/community/ManyButtonsMouseHowto") and this thread I'm now sure how I can map my thumb buttons to page up / page down

Right now they are recognized by xev as button8 and button9, I can assign them in opera and they work.

But I'd like to assign them globally to page up/down keystroke, so I don't have to configure every application. Can this be done or do I have to set up imwhell entries for every application I want to use with thumb buttons?

For example: what about Open Office? How do I assign Pageup/pagedown there?

Edit: Got it!

~$ cat .imwheelrc
```
".*"
None, Thumb1, Prior
None, Thumb2, Next
```
works in OpenOffice, Firefox, Opera

---

### Post by tobybot on 2009-07-08
I'm using the Evoluent vertical mouse, and I got mine working as I wanted, so I thought I'd throw this in here.

I used xinput, like this:

First, I opened up a terminal window and typed this to find out what the mouse is called:
```
xinput list
```It came back with:
"Evoluent Vertical Mouse 2"    id=5    [XExtensionPointer]

so I did this to get the current button mappings:
```
xinput get-button-map "Evoluent Vertical Mouse 2"
```It returned this:
 1 2 3 4 5 6 7 9 8 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10

Weirdly, it claims to have 32 buttons. Whatever. I want my mouse to act like this:
Thumb Button: back
Top Button: left click
Scroll Wheel Button: double click
Middle Button: right click
Bottom Button: forward

So after some fooling around, I found that this is what I wanted:
```
sudo xinput set-button-map "Evoluent Vertical Mouse 2" 1 2 3 4 5 6 7 9 8 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10
```I switched 8 and 9, since on my mouse, those are thumb and bottom button. It works. YMMV, but if you're having trouble, just swap two numbers at a time (and swap them back if you get the wrong ones) until you find the buttons you're looking for.

hope that's helpful to someone!

---

### Post by Takaian on 2009-09-13
I am trying to currently do something very similar to this, but instead of mapping the very simple and over-explained function to Forward/Back to my Thumb buttons, I really would like to know the value or command to map my Thumb2 button to "middle click". I don't know what I would enter into my imwheelrc other than:

".*"
None, Thumb2, __________

The underscores signify the command I need help with to activate that function to middle click.  Any help given is appreciated. (For reference, my xorg is:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

)

---

