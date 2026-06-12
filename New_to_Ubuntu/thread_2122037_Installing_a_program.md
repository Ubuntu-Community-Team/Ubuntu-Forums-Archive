---
title: "Installing a program"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by mmcl26554 on 2013-03-03
Since my 3 cats like to join in when I am on the computer I was looking for a program I could activate with a few key strokes and lock the keyboard.   I did find one for windows and it works great.   I have actually found one for linux also and have downloaded but because I am so new to Ubuntu I just don't know what to do next.   I make contact with the author and he send me some instructions but I still need help. Below are excerpts of his directions:


No worries Michael I'll see if I can help you out. I think I have a Ubuntu VM somewhere around the place that I can play with. Off the top of my head though, you will need the following software installed. I don't know the Ubuntu package names for these but I should be able to get back to you with that later.

Perl
 Gtk version 2
 Perl module Gtk2 (in ubuntu, this might be called perl-gtk2 or just perl-gtk or even gtk-perl or GtkPerl)

That's it, if you can install those things then you have all the rewuirements. But I wrote it a long time ago, so it is possible that Ubuntu only has gtk 3 now. In that case you may be able to just edit the script (you can edit it with a text editor) and change all occurrences of Gtk2 to Gtk3.

To run the script, it needs to be flagged as executable . you can do this in linux like this:

cd /home/your-username/downloads/ (or where ever you saved it)
 chmod a+rx lock-keyboard-for-baby.pl (or whatever your file is called)

Then you can run it by typing :
 ./lock-keyboard-for-baby.pl

and see if it works.


So how do I find out if I have Perl module Gtk2?

---

### Post by darkcrimson on 2013-03-03
```
instmodsh
```
Then at the cmd? prompt
```
l
``` -that's a lowercase L.

Hope this helps!

---

### Post by mmcl26554 on 2013-03-03
Perl is listed but I don't know about the gtk2 so do I assume that is not installed?  BTW, thank you for helping!
Michael

---

### Post by d4m1r on 2013-03-04
What's the name of the program, where did you download it from, and what's the file extension (ex: .exe)?

---

### Post by frup on 2013-03-04
Does CTRL + ALT + L achieve what you want?

---

### Post by mmcl26554 on 2013-03-04
Here is the website for the program:  [http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm](http://csincock.customer.netspace.net.au/lock-keyboard-for-baby.htm)

---

### Post by drmrgd on 2013-03-04
Pretty simple.  There's nothing to install but the Perl Gtk2 libraries.  Open up a terminal window and install the perl GTK2 libraries:

```
sudo apt-get install libgtk2-perl
```

Once that's you can just run the script following the author's instructions.  In short, copy the program into a text editor and save it somewhere.  Then, make the program executable:

```
 chmod +x <yourprogram>
```

Then you can run it from the terminal with:

```
 ./path/to/your/program/ 
```

You could get fancier with it and create a launcher or something too if you wanted.

---

### Post by stinkeye on 2013-03-04
I don't know how the script works for you, but when the keyboard is locked 
I can't move windows with the mouse.

In unity I create a launcher which uses xinput to disable and enable my input device.

eg Get the ID of your device...
```
xinput -list
```

```
[COLOR="#008000"]glen@Quantal:~$[/COLOR] **xinput -list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Honey Bee  Nostromo SpeedPad2           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Honey Bee  Nostromo SpeedPad2           	id=8	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Headset           	id=10	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=[COLOR="#FF0000"]12[/COLOR]	[slave  keyboard (3)]
----

```
My keyboard ID=[COLOR="#FF0000"]12[/COLOR]

Create a .desktop file. Run in terminal ...
```
gedit ~/.local/share/applications/Catwalk.desktop
```
Copy and paste this into gedit.
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Catwalk
Comment=disable enable keyboard
Exec=/usr/bin/xinput --disable [COLOR="#FF0000"]12[/COLOR]
Icon=[COLOR="#FF8C00"]/home/glen/Desktop/Scratch_cat_large.png[/COLOR]
Categories=Utility;

Actions=enable;

[Desktop Action enable]
Name=Enable Keyboard
Exec=/usr/bin/xinput --enable [COLOR="#FF0000"]12[/COLOR]
OnlyShowIn=Unity;
```
Edit the file to use [COLOR="#FF0000"]your keyboard id[/COLOR]
and the [COLOR="#FF8C00"]path to an icon[/COLOR].

Save the file.
Open the dash and type in "catwalk" and drag to the launcher.
Left click to disable the keyboard and right click to bring up the quicklist to enable.

It would be better to use a toggle on/off script but I don't
know how to get the disabled/enabled status of the keyboard.

---

### Post by deadflowr on 2013-03-04
stinkeye's post is pretty well spot on.
However run this in a terminal:
```
chmod + x [COLOR=#000000][FONT=Ubuntu Mono] ~/.local/share/applications/Catwalk.desktop[/FONT][/COLOR]
```

so the .desktop file is executable, or else the file will open the text editor (most likely).
Or right-click>properties>permissions>check run as executable.

---

### Post by stinkeye on 2013-03-04
> **deadflowr said:**
> stinkeye's post is pretty well spot on.
However run this in a terminal:
```
chmod + x [COLOR=#000000][FONT=Ubuntu Mono] ~/.local/share/applications/Catwalk.desktop[/FONT][/COLOR]
```

so the .desktop file is executable, or else the file will open the text editor (most likely).
Or right-click>properties>permissions>check run as executable.

Hi there deadflowr,
a .desktop file doesn't need to be executable unless you want to place it on the desktop,
whereby its being handled by nautilus when you click on it.

---

### Post by mmcl26554 on 2013-03-06
I thank all who are contributing to this little project for me.   Being an absolute beginner with Ubuntu my confidence level is low but my desire to make it work is high.  I think I can put this all together and make it work but let me outline what I want to accomplish with this program.   The similar Windblows program will activate when you type ctl+alt+L and deactivate when you type "unlock"  This works really well, so when I see a cat heading toward me I quickly press ctl+alt+l just before she lands on the keyboard.   All is well and when she leaves I type the "unlock" and I'm back to work.   I do remember setting up the 3-key entry for "Keepass" to enter a username and password and I would like to do that with this program (like windblows).   I have the program downloaded so I guess the next thing to do would be to text edit it so it will execute but I sure would like to be able to get it to activate and deactivate like the windblows version.   So if some more of you can offer specific directions I can follow that would be great!

Michael

---

