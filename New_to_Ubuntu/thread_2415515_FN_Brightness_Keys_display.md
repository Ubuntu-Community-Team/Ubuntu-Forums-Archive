---
title: "FN Brightness Keys display"
date: 2019-03-27
forum: New to Ubuntu
---

### Post by licondam on 2019-03-27
**Staff Note**

Spam text removed. The post started as an apparently innocent question, but which was probably a copy-paste from somewhere. The spammer then replaced the original text with spam text some weeks later, after several members had responded to the original text.

I'll close the thread and leave in situ rather than jailing the whole thread and having to pm several forum members explaining why their posts are in spamalot.

---

### Post by TheFu on 2019-03-27
Each flavor of Ubuntu uses a different DE. Each DE has different methods to assign actions to keyboard events. A DE would be from one of these choices, 
* LXDE
* LXQt
* Mate
* Unity
* Gnome2
* Gnome3
* KDE
* Cinnamon
and a few others.

There are also ways to run Ubuntu without any DE, like I do.  These have either a Window Manager-only setup, WM, or they are a server, which doesn't have any GUI.
Window Manager choices are many. Too many to list.  I use openbox or fvwm, but those aren't the most popular.

Anyways ... nobody can help without knowing which DE or which WM you are running.   Lacking that, the Ubuntu Desktop Guide for your specific flavor and release is the guess [https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en)  You can setup brighter and dimmer keyboard keys to call xbacklight.

---

### Post by Kevin McCready on 2019-04-02
DE is Desktop Environment. How do I know what DE I have?
I also want to lower the brightness at night.

---

### Post by ajgreeny on 2019-04-02
You can install **redshift** to reduce screen brightness automatically on your system dependent on your global position.

To find what DE you're using run command
```
echo "Desktop:	$DESKTOP_SESSION"
``` which will immediately respond with something like *ubuntu, xubuntu, kubuntu*, etc etc.

---

### Post by Kevin McCready on 2019-04-02
ta for that
I'm running mate apparently
but redshift is predicated on GMT
is there a way to give me control at any time?

---

### Post by ajgreeny on 2019-04-02
Look for the following in your ~/.config/redshift.conf file and make changes there for the location; mine is set for my position in UK.
```
; Set the location-provider: 'geoclue', 'gnome-clock', 'manual'
; type 'redshift -l list' to see possible values
; The location provider settings are in a different section.
location-provider=manual

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values
; 'randr' is the preferred method, 'vidmode' is an older API
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings
; e.g. 'redshift -l manual:help'
[manual]
lat=52
lon=-1.5
```

---

### Post by Kevin McCready on 2019-04-03
I can't seem to open the config file.
```

locate redshift
/usr/share/app-install/desktop/redshift-gtk:redshift-gtk.desktop
/usr/share/app-install/icons/redshift.svg
/usr/share/icons/Mint-Y/apps/16/redshift.png
/usr/share/icons/Mint-Y/apps/22/redshift.png
/usr/share/icons/Mint-Y/apps/24/redshift.png
/usr/share/icons/Mint-Y/apps/256/redshift.png
/usr/share/icons/Mint-Y/apps/32/redshift.png
/usr/share/icons/Mint-Y/apps/48/redshift.png
/usr/share/icons/Mint-Y/apps/64/redshift.png
/usr/share/icons/Mint-Y/apps/96/redshift.png

```

---

### Post by ajgreeny on 2019-04-03
The configuration file for redshift is in your home at **/home/*username*/.config/redshift.conf** not in the root filesystem.

You may need to enable seeing hidden files and folders to get to the file so use **Ctrl+H** to do that, search for that file and edit it manually

---

### Post by Kevin McCready on 2019-04-03
it's not there.
the locate command shows it's not there

---

### Post by ajgreeny on 2019-04-03
Have you actually run redshift yet?
If not the file will not be present, but it should be there once you have run it, so try command **redshift-gtk** and see if the file then appears.

---

### Post by Kevin McCready on 2019-04-03
When I tried to run redshit and redshift-gtk I got the same error message:
Failed to run Redshift
Trying location provider `geoclue2'...
Unable to connect to GeoClue.
Unable to get location from provider.

---

### Post by ajgreeny on 2019-04-04
It looks as if you are from New Zealand but that redshift is unable to find your location and is therefore failing.

I have attached an edited version of my redshift.conf file below with "manual location" setting, ie. with latitude and longitude for NZ which you can adjust for your specific location in NZ if you wish.
I have also changed the adjustment method from **vidmode** to **randr** which is now the better option in most cases.

Save my version as a text file, rename it as **~/.config/redshift.conf** in your home then try starting redshift again.
A version of the configuration that works should allow the application to start.

---

### Post by TheFu on 2019-04-04
BTW, it is common for config files not to pre-exist.  The user is expected to create them from scratch with many tools.  It is just the location, name and correct contents inside any file that matters.  Often, there is a system-wide example file to be copied over, but just as often, the program has *reasonable defaults* which are used when no config file is found to override those built-in settings.

I've seen people coming from other OSes struggle with this idea.

In short, if there isn't a config file of the correct name, in the correct place, and you need one, then MAKE IT.

---

### Post by Kevin McCready on 2019-04-04
Thanks. It didn't work. I renamed and put the file into the ~/.config then I ran redshift-gtk and got this:
```

redshift-gtk
/usr/lib/python3/dist-packages/redshift_gtk/statusicon.py:32: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GLib, GObject
/usr/lib/python3/dist-packages/redshift_gtk/statusicon.py:35: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator

(redshift-gtk:11176): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed


```
When I ran redshift (without gtk) I just got a blinking cursor in the terminal.

---

### Post by ajgreeny on 2019-04-05
Well, now I am baffled.

I have installed redshift on four computers in my household , all running either Xubuntu-18.04, Lubuntu-18.04, or Ubuntu-mate-18.04, and it is working fine on all of them.

Can I double check that you installed redshift from the standard repos as normal and that it is not from some other source.

Can you also check to see that redshift is not running as I also get the **(redshift-gtk:11176): Gdk-CRITICAL** error like you but the application is running fine.
Check your situation with ps aux | grep redshift and you may see output similar to
```
~$ ps aux | grep redshift
193:username   17723  1.8  0.5 503912 42188 ?        Sl   11:33   0:00 /usr/bin/python3 /usr/bin/redshift-gtk
194:username   17724  0.3  0.0  64064  3072 ?        S    11:33   0:00 /usr/bin/redshift -v
196:username   17738  0.0  0.0  14428  1056 pts/0    S+   11:33   0:00 grep -n --color redshift

``` which means it is running.
If you see only something like my third line with grep in the output redshift is not running; that is the grep process itself looking for redshift.
Look also for the redshift icon in your panel (see screenshot) which when clicked gives you information about the current settings for redshift.

---

### Post by Dennis N on 2019-04-05
You can also start redshift and set location and color with a single command placed in your startup applications. redshift-gtk and geoclue are not required. Also with this method, no configuration file is used. 

```
redshift -l latitude:longitude -t day:night
```

Example: set for Phoenix, Arizona, USA
look up latitude and longitude with google: 33 N, 112 W
default color settings are: day 5500K night 3700K (from redshift man page)

```
redshift -l 33:-112 -t 5500K:3700K

```
S latitude and W longitude values are expressed as negative numbers. 
a lower K temp gives more reddish hue for night. Adjust to your liking.

There are more options on the man page.

---

### Post by Kevin McCready on 2019-04-05
Thanks guys
Yes redshift-gtk is running.
I don't care about the lat and long. All I want is to adjust the brightness when I feel like it. I can't seem to do this without it flickering all the time every second or so.
```

 redshift-gtk -b .4
/usr/lib/python3/dist-packages/redshift_gtk/statusicon.py:32: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GLib, GObject
/usr/lib/python3/dist-packages/redshift_gtk/statusicon.py:35: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator

```
then it cycles rapidly between bright and dark.

---

### Post by Kevin McCready on 2019-04-05
OK
Cancel that last post.
Solved now. Whew. 
I think I had both versions (redshift and redshift-gtk) running in separate terminals and they were fighting. Hee hee.
Thanks for your help.

---

### Post by ajgreeny on 2019-04-06
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by Kevin McCready on 2019-04-06
I can't mark it solved. Perhaps because I didn't start the thread.

---

### Post by TheFu on 2019-04-07
> **Kevin McCready said:**
> I can't mark it solved. Perhaps because I didn't start the thread.

Ah ... so you hijacked another persons thread.  Bad form and bad form for us not to notice. Boo on everyone.

---

### Post by ajgreeny on 2019-04-08
Mea culpa!

I didn't notice either, and the OP has not come back so we have no idea if he's been following these discussions.

---

