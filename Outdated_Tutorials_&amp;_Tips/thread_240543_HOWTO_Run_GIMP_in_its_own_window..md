---
title: "HOWTO: Run GIMP in its own window."
date: 2006-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by neko18 on 2006-08-21
First make sure you have all the needed stuff:
```
sudo apt-get install xnest metacity gimp
```

Now run this command to test it:
```
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp --display :1
```
You may like to change the "1024x690" to something that better fits your screen.

If it works, you may edit your GIMP menu shortcuts to reflect that command.

Here's a screenshot:

---

### Post by BLTicklemonster on 2006-09-05
Could I get an example of this edit command you speak of? I like this.

---

### Post by pufuwozu on 2006-09-05
That's a really good idea. Thanks.

---

### Post by BLTicklemonster on 2006-09-05
Hmmm, like perhaps I ought to create a launcher on my desktop, and use that command? I'd like it if I could make it so it would do that if I right click an image and choose open with gimp, but hey, no problem with it otherwise!

Again, I really like this, thanks for posting it.

---

### Post by simplyw00x on 2006-09-05
> I'd like it if I could make it so it would do that if I right click an image and choose open with gimp, but hey, no problem with it otherwise!

Rename /usr/bin/gimp to /usr/bin/gimp_bin, then make a new file:
```
#!/bin/bash
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp_bin --display :1
```

save this file as /usr/bin/gimp

---

### Post by sharperguy on 2006-09-05
> **simplyw00x said:**
> 
save this file as /usr/bin/gimp

youl also have to run
```

sudo chmod +x /usr/bin/gimp

```

And you'll have to be an admin of course.

---

### Post by DC@DR on 2006-09-05
We could try also GIMPshop, which is a improved version of GIMP: [http://www.gimpshop.net/](http://www.gimpshop.net/) --> it also open GIMP as a whole window, which makes us feel smth Photoshop-alike.

---

### Post by %hMa@?b&lt;C on 2006-09-05
wow, that plus gimpshop is really excellent@!!!!

---

### Post by BLTicklemonster on 2006-09-05
> **simplyw00x said:**
> Rename /usr/bin/gimp to /usr/bin/gimp_bin, then make a new file:
```
#!/bin/bash
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp_bin --display :1
```

save this file as /usr/bin/gimp
Isn't there some chown command or something I have to run first to have permission to alter the file? (if not for that, then for any others, and what is the command, I really need it for something else, also thanks)

---

### Post by BLTicklemonster on 2006-09-05
Okay, I did it, but now it opens the window, but not gimp.

---

### Post by Toxicity999 on 2006-09-07
The command your looking for is:
sudo chown username:usergroup /dir/dir/file.xyz
You DON'T need to do this to edit a text file. a simple sudo gedit or sudo nano will do there. use chown with caution.

But anyway a complete walkthrough for what they were jsut talking about to run like this by default:
sudo cp /usr/bin/gimp /usr/bin/gimp_old
sudo rm /usr/bin/gimp
sudo gedit /usr/bin/gimp

Past this into the file:
#!/bin/bash
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp_bin --display :1 Now you just need to make it executable with:

sudo chmod +x /usr/bin/gimpNow just run things as normal should work assuming they had it right I was just compiling it for everyone :)

---

### Post by argie on 2006-09-08
Hey, I like this. I just got it working nicely.

GIMP seems to look a little different though.

---

### Post by BLTicklemonster on 2006-09-09
Okay, I have already dorked out ubuntu and had to reinstall it because I chowned /usr, so I'm not about to do that again. 

Please, instead of blurting out something experienced users understand, would you please walk this moron through renaming /usr/bin/gimp please?

I have /home/ticklemonster/gimp which works fine. I have a link to it on my desktop, but I'd like to have my actual link under graphics to be the windowed version which I just created, and keep my desktop free to clutter up with other useless stuff.

Thank you. Sorry about the rant.

*edit:

tee hee hee 

> **Toxicity999 said:**
> The command your looking for is:
sudo chown username:usergroup /dir/dir/file.xyz
You DON'T need to do this to edit a text file. a simple sudo gedit or sudo nano will do there. use chown with caution.

But anyway a complete walkthrough for what they were jsut talking about to run like this by default:
sudo cp /usr/bin/gimp /usr/bin/gimp_old
sudo rm /usr/bin/gimp
sudo gedit /usr/bin/gimp

Past this into the file:
#!/bin/bash
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp_bin --display :1 Now you just need to make it executable with:

sudo chmod +x /usr/bin/gimpNow just run things as normal should work assuming they had it right I was just compiling it for everyone :)

obviously looking up is highly underated. Thank you!


Bah, sorry, nope, still openning like before, no window around it. I did exactly what you said.

---

### Post by BLTicklemonster on 2006-09-09
Not only does that open like always, now the one I made before doesn't work, it just brings up an empty window with no gimp in it.

---

### Post by mynimal on 2006-09-09
Here's the command for it to use your GTK theme, instead of that ugly default. Now I just need a way to change that background.

```
Xnest :1 -ac -name GIMP -geometry 1280x960 & metacity --display :1 & gnome-settings-daemon --display :1 & gimp --display :1
```

---

### Post by berserker on 2006-09-09
> **Toxicity999 said:**
> 
sudo mv /usr/bin/gimp /usr/bin/gimp_**bin**
sudo gedit /usr/bin/gimp

Past this into the file:
#!/bin/bash
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp_bin --display :1

Notice the changes (/usr/bin/gimp_old is now /usr/bin/gimp_bin and cp is now mv to save a step).  Should work now.

---

### Post by berserker on 2006-09-09
> **mynimal said:**
> Here's the command for it to use your GTK theme, instead of that ugly default. Now I just need a way to change that background.

```
Xnest :1 -ac -name GIMP -geometry 1280x960 & metacity --display :1 & gnome-settings-daemon --display :1 & gimp --display :1
```

Any idea on how to do that for KDE?

---

### Post by BLTicklemonster on 2006-09-09
> **berserker said:**
> Notice the changes (/usr/bin/gimp_old is now /usr/bin/gimp_bin and cp is now mv to save a step).  Should work now.

Bah, still out of the box.

---

### Post by garybrlow on 2006-09-09
How about XFCE/Xubuntu? Could it work too? :)

---

### Post by mynimal on 2006-09-10
> **berserker said:**
> Any idea on how to do that for KDE?
Not off the top of my head, but check the startup applications. It's probably one of those that need to be running to draw Qt.

---

### Post by mjpatey on 2006-09-10
Wow, amazing!  But I can't seem to make a launcher for it.  I optimized the window size to perfectly fit my desktop (very convenient), and your command worked perfectly.

But when I create a launcher using the exact same command, it does nothing.  I even checked "Open in Terminal" thinking it would help, but to no avail.

Anybody know how to make a launcher work?

---

### Post by timas on 2006-09-13
KDE user here, works like a charm!

After going through the above steps I did:

Right click the launcher you desire to edit, find the command it executes.. for me it said 'gimp-remote-2.2 %U' which I changed to 'gimp'

voila!

---

### Post by Emanuel Felipe on 2006-09-29
Nice.. :D 

note.. for Xfce users:
[B]
:~$ sudo apt-get install xnest gimp
:~$ Xnest :1 -ac -name GIMP -geometry 1024x690 & xfwm4 --display :1 & gimp --display :1[/B]

theres no need for metacity...

---

### Post by TooRight on 2006-12-22
Anyone have any idea how to male it work on Kubuntu with Beryl? This looks sooo handy, i'd love to get it going!! :D

---

### Post by BLTicklemonster on 2006-12-22
Unless something has changed, gimpshop and this as well just look to me to be basically just a window that covers your desktop and holds all the elements of gimp in it for you. Hardly any improvement if you ask me.

Here's what I do:
[http://ubuntuforums.org/showpost.php?p=1631680&postcount=66](http://ubuntuforums.org/showpost.php?p=1631680&postcount=66)

---

### Post by shane2peru on 2008-01-29
Ok, this was a good idea, however everytime the main window looses focus everything becomes grey, and I have to run my mouse over every single thing to get it back, very annoying.  See the screenshot to see what I mean.  It is a bit of annoyance, any ideas would be appreciated.  Thanks.

Shane

---

### Post by zami on 2008-07-02
> **shane2peru said:**
> Ok, this was a good idea, however everytime the main window looses focus everything becomes grey, and I have to run my mouse over every single thing to get it back, very annoying.  See the screenshot to see what I mean.  It is a bit of annoyance, any ideas would be appreciated.  Thanks.

Shane
I'm having this exact same issue.  If anyone know what causes this or how to fix it, please do share.  

I was so pleased when I got Xnest going, too.

-zami

---

### Post by supaneko on 2009-08-26
Sorry for thread digging but after a Google search this turned up and proved rather useful. :)

I am having one issue though... Segmentation fault. If I work too fast the program crashes. I also tried to command to use the Gnome theme but that caused the program to run in a continuous crashing loop which eventually forced me to hit the reset button because the CPU usage went haywire.

Any ideas on why this might be? Occasionally I have to restart the program because the mouse cursor does not seem to work.

---

### Post by supaneko on 2009-08-26
> c0llisi0n@neonekob0x:~$ gimp
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed (2)                                        
(EE) config/hal: NewInputDeviceRequest failed (2)                                        
(EE) config/hal: NewInputDeviceRequest failed (2)                                        
Xlib:  extension "RANDR" missing on display ":1.0".                                      
Xlib:  extension "RANDR" missing on display ":1.0".                                      

(gimp_bin:13202): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4000b5 (Toolbox)                                                                                                         
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.                                                                                                             
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x400067 (GNU Image )                                                                                                      
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.                                                                                                             
Xlib:  extension "RANDR" missing on display ":1.0".                                                           
lcms: skipping conversion because profiles seem to be equal:
 sRGB IEC61966-2.1
 sRGB built-in

(gimp_bin:13202): Gtk-WARNING **: Attempting to store changes into `/home/c0llisi0n/.recently-used.xbel', butfailed: Failed to rename file '/home/c0llisi0n/.recently-used.xbel.VIV8YU' to '/home/c0llisi0n/.recently-used.xbel': g_rename() failed: Operation not permitted

(gimp_bin:13202): Gtk-WARNING **: Attempting to set the permissions of `/home/c0llisi0n/.recently-used.xbel',but failed: Operation not permitted
Xlib:  extension "RANDR" missing on display ":1.0".

(gimp_bin:13202): Gtk-WARNING **: Attempting to store changes into `/home/c0llisi0n/.recently-used.xbel', butfailed: Failed to rename file '/home/c0llisi0n/.recently-used.xbel.NV06YU' to '/home/c0llisi0n/.recently-used.xbel': g_rename() failed: Operation not permitted

(gimp_bin:13202): Gtk-WARNING **: Attempting to set the permissions of `/home/c0llisi0n/.recently-used.xbel',but failed: Operation not permitted
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x400067 (tech rackm); these messages lack timestamps and therefore suck.
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Resource id in failed request:  0x0
  Serial number of failed request:  167390
  Current serial number in output stream:  167395
gimp_bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':1'.

(script-fu:13237): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error


That is the print-out from the terminal from when I run gimp to when it crashes (and it seems to crash early on almost every time).

---

### Post by sami89 on 2010-05-23
> **neko18 said:**
> First make sure you have all the needed stuff:
```
sudo apt-get install xnest metacity gimp
```Now run this command to test it:
```
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp --display :1
```You may like to change the "1024x690" to something that better fits your screen.

If it works, you may edit your GIMP menu shortcuts to reflect that command.

Here's a screenshot:
How to undo this i wrote those command it works but i want everything back.

---

