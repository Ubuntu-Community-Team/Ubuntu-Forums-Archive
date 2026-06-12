---
title: "Replace metacity by xfwm4"
date: 2005-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by theine on 2005-11-10
Since metacity became the default window manager for gnome, I've always been bugged by the absence of some very useful features such as edge resistance towards other windows and vertical/horizontal maximization. The latter is actually somewhat implemented, but in a poor way, and [appearently]("http://bugzilla.gnome.org/show_bug.cgi?id=81704"), the developers of metacity don't seem to see a desperate need for properly implementing the above features anytime soon.

Fortunately, there are alternatives to using metacity as window manager under Gnome. For a while I was using [Openbox]("http://icculus.org/openbox/"), which is great but I always had minor issues with it (e.g. the Gnome panels stayed visable when watching a video in fullscreen mode with VLC), so I kept looking and found xfwm4, which is the default window manager under [XFCE]("http://www.xfce.org"). xfwm4 works absolutely fabulous for me, and it fits very nicely into Gnome since it also uses GTK. For anybody interested in trying it out, here's how to set it up under Gnome...

First, make sure the universe repository is enabled and then do
```

sudo apt-get install xfwm4 xfce4-mcs-manager

```
Next, edit /usr/bin/gnome-wm and add xfwm4 to the entry line that already contains openbox, i.e.
```

sudo sed -i "s/openbox)/openbox|xfwm4)/" /usr/bin/gnome-wm

```
Last thing to do is to set the WINDOW_MANAGER environment variable so that Gnome is aware of it. This can be accomplished by
```

echo export WINDOW_MANAGER=/usr/bin/xfwm4 >> ~/.gnomerc

```
Done. Next time you log into Gnome, xfwm4 should manage your windows.

Setting the WINDOW_MANAGER environment variable won't have any effect if you saved your Gnome session at some point in the past. In that case, /usr/bin/gnome-wm isn't even invoked anymore when you log into Gnome. The solution is to either
```

rm ~/.gnome2/session

```
and start over with the default Gnome session next time you log in, or save a new session after doing the ```

killall metacity && xfwm4

```
routine. Thanks to the posters in this thread for pointing this out.

To adjust the settings for xfwm4, execute
```

xfce-setting-show

```
If you would like to do this with /usr/bin/gnome-window-properties (System -> Preferences -> Windows) you need to write a little .desktop file:
```

theine@cosmo:~$ cat /usr/share/gnome/wm-properties/xfwm4.desktop
[Desktop Entry]
Name=Xfwm4
Exec=xfwm4

# name we put on the WM spec check window
X-GNOME-WMName=Xfwm4

# our config tool
ConfigExec=xfce-setting-show
theine@cosmo:~$

```
Could be that you need to execute
```

sudo /etc/init.d/readahead start

```
before Gnome will be aware of xfwm4's configuration tool. The above .desktop file is identical to the one from the openbox package apart from the substitution openbox -> xfwm4.

---

### Post by LaSSarD on 2005-11-11
thanks, i've been looking for this for ages :D

---

### Post by sailor420 on 2005-11-11
Is there an easy way to uninstall this, ie revert back to metacity should things not work?

---

### Post by LaSSarD on 2005-11-11
hey theine, now i had the opportunity to test it and it doesn't work at all :(
metacity is still running, no xfwm4 :(

---

### Post by majikstreet on 2005-11-11
I'd like to see a screenshot, if possible.

---

### Post by samwyse on 2005-11-11
Is there a way to start the Gnome Run Dialog using xfwm4? xfrun is slow to start.

---

### Post by Bitmastro on 2005-11-12
yes, but it's a bit tricky, I don't know if there are better solutions..
you must install openbox by synaptic or by doing```
sudo apt-get install openbox
```in a command line.
then run xfce-setting-show and go to the window manager settings (it should be in the bottom left corner)
Open the keyboard tab, and click "add" to create a new keybinding theme.
In the command shortcuts windows double-click on xfrun4 and write this command "gnome-panel-control --run-dialog".
It should work now
bye

---

### Post by samwyse on 2005-11-12
^ Thanks, works perfectly.

---

### Post by theine on 2005-11-12
[QUOTE=sailor420]Is there an easy way to uninstall this, ie revert back to metacity should things not work?[/QUOTE]

Yes, just export WINDOW_MANAGER=/usr/bin/metacity in ~/.gnomerc or delete that line all together.

---

### Post by theine on 2005-11-12
[QUOTE=LaSSarD]hey theine, now i had the opportunity to test it and it doesn't work at all :(
metacity is still running, no xfwm4 :([/QUOTE]

Check /usr/bin/gnome-wm if the entry for xfwm4 looks OK. Also, try
```

echo $WINDOW_MANAGER

```
and see whether it says xfwm4. If not, check ~/.gnomerc

---

### Post by theine on 2005-11-12
[QUOTE=majikstreet]I'd like to see a screenshot, if possible.[/QUOTE]

[http://www.nordita.dk/~theine/images/Screenshot.png](http://www.nordita.dk/~theine/images/Screenshot.png)

---

### Post by majikstreet on 2005-11-12
that's good looking!

-m

---

### Post by manicka on 2005-11-12
I like this alot, but I've lost some handy keyboard shortcuts like hitting PrintScrn and alt-PrintScrn to take snapshots. Any way to get them back. I'm a bit of a novice with xfce.

---

### Post by manicka on 2005-11-12
[QUOTE=manicka]I like this alot, but I've lost some handy keyboard shortcuts like hitting PrintScrn and alt-PrintScrn to take snapshots. Any way to get them back. I'm a bit of a novice with xfce.[/QUOTE]

Okay, so a workaround is to create some custom launchers on the panel, but I'd really like to add some of these keyboard shortcutsback in

---

### Post by curtis on 2005-11-12
[QUOTE=manicka]I like this alot, but I've lost some handy keyboard shortcuts like hitting PrintScrn and alt-PrintScrn to take snapshots. Any way to get them back. I'm a bit of a novice with xfce.[/QUOTE]

Same here, I miss my keyboard shortcuts to show the desktop and open a terminal.
Wierd thing is I still have one of my keyboard shortcuts working (CTRL + ALT + L to lock screen)

---

### Post by manicka on 2005-11-12
[QUOTE=curtis]Same here, I miss my keyboard shortcuts to show the desktop and open a terminal.
Wierd thing is I still have one of my keyboard shortcuts working (CTRL + ALT + L to lock screen)[/QUOTE]
Yes, and alt-f2 works as well. There must be away to configure some more

---

### Post by henriquemaia on 2005-11-12
[QUOTE=manicka]I like this alot, but I've lost some handy keyboard shortcuts like hitting PrintScrn and alt-PrintScrn to take snapshots. Any way to get them back. I'm a bit of a novice with xfce.[/QUOTE]

You can try to install xbindkeys and included it in you session startup programs.

Under a terminal, write:

```
sudo apt-get install xbindkeys xbindkeys-config
```

after that, go to (on the gnome-panel) System/Preferences/Sessions and add it to the Startup Programs tab.

Then run ```
xbindkeys-config
``` and make your configurations.

During that same session you're in, run ```
xbindkeys
``` to get the shortcuts working.

Next time you reboot, you'll have your shortcuts available, since xbindkeys is starting up automatically.

Hope this helps.

---

### Post by manicka on 2005-11-13
Thanks henriquemaia :)

---

### Post by manicka on 2005-11-13
One more thing I've noticed that is a killer for me. 

I use klipper. When klipper runs with xfwm4 as the window manger, it's icon doesn't appear in the systray, just two lines. If I fiddle around and click in just the right spot, klipper's menu appears, so it's still running, but it's to fiddly to use on a permanent basis.

This is the only thing stopping me from changing over to xfwm4. I wish gnome had something comparable to klipper.

Edit: The only thing stoppping me is an inane dependence on klipper, a program I use when I need to copy 3 or 4 things to the clipboard and then use them in another doc. Tomboy can do this for me just as effectively and probably a bit better in my context.

Combining xfwm4 with the latest clearlooks patch has given me the nicest desktop I've had in ages. I think I'll post a screenie in the gallery. :D

---

### Post by Bitmastro on 2005-11-13
Just to repeat myself, to configure the shortcuts you can also run xfce-setting-show, go to window manager settings (bottom left corner), keyboard and add the command you need
"gnome-screenshot" and press "Print"
"gnome-screenshot --window" with alt+print
"xfce4-taskmanager" with Control+Alt+Delete
"gnome-terminal" with Control+Alt+T
"gnome-panel-control --run-dialog" with Alt+F2
and so on..
I still don't know how to show the desktop :-(

---

### Post by manicka on 2005-11-13
[QUOTE=Bitmastro]Just to repeat myself, to configure the shortcuts you can also run xfce-setting-show, go to window manager settings (bottom left corner), keyboard and add the command you need
"gnome-screenshot" and press "Print"
"gnome-screenshot --window" with alt+print
"xfce4-taskmanager" with Control+Alt+Delete
"gnome-terminal" with Control+Alt+T
"gnome-panel-control --run-dialog" with Alt+F2
and so on..
I still don't know how to show the desktop :-([/QUOTE]

Geez, missed that one. :oops: 

I should read threads more closely. Thanks

---

### Post by magnusbb on 2005-11-13
I would really like to have this one, but I can't get it to work. I have done all said in the instructions, and the echo command reports that xfwm4 is the exported as an environment variable.

However, Metacity is still running, and it's still the window manager in GNOME. I can't even see the xfwm4 process in "top".

Here's my /usr/bin/gnome-wm, in case there is something wrong with that:

> #!/bin/sh

# The user can specify his prefered WM by setting the WINDOW_MANAGER
# environment variable.
#
# If this is not set, we search a list of known windowmanagers and use
# the first one that is found in the users's PATH
#
# This script has been heavily modified to support Debian's
# alternatives system.

# sm-client-id value
SMID=
# default-wm value
DEFWM=

#read in the arguments
GET=
for n in "$@" ; do
  case "$GET" in
    smid)
      SMID=$n
      GET=
      ;;
    defwm)
      DEFWM=$n
      GET=
      ;;
    *)
      case "$n" in
        --sm-client-id)
          GET=smid
          ;;
        --default-wm)
          GET=defwm
          ;;
      esac
      ;;
  esac
done

if ! which "$WINDOW_MANAGER" > /dev/null; then
  # Get --default-wm
  if which "$DEFWM" > /dev/null; then
    WINDOW_MANAGER=$DEFWM
    if [ "$WINDOW_MANAGER" = x-window-manager ]; then
      WINDOW_MANAGER=`readlink /etc/alternatives/x-window-manager 2>/dev/null`
    fi
  # if nothing is found, first use metacity
  elif [ -x /usr/bin/metacity ]; then
    WINDOW_MANAGER=/usr/bin/metacity
  elif [ -x /usr/bin/sawfish ]; then
    WINDOW_MANAGER=/usr/bin/sawfish
  else
    WINDOW_MANAGER=`readlink /etc/alternatives/x-window-manager 2>/dev/null`
  fi
fi

# If no window manager can be found, we default to xterm

if [ -z "$WINDOW_MANAGER" ] ; then
  echo "WARNING: No window manager can be found."
  WINDOW_MANAGER=`readlink /etc/alternatives/x-terminal-emulator 2>/dev/null`
fi

# If there is no xterm, they're really screwed.
if [ ! "$WINDOW_MANAGER" ]; then
  echo "ERROR: No window manager and no xterm!"
  exit 1
fi

# Now create options OPT1 and OPT2 based on the windowmanager used
OPT1=
OPT2=
if [ ! -z "$SMID" ] ; then
  case `basename $WINDOW_MANAGER` in
    sawfish|sawmill|metacity)
      OPT1=--sm-client-id=$SMID
      ;;
    openbox|xfwm4)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
    enlightenment|twm)
      OPT1=-clientId
      OPT2=$SMID
      ;;
    fvwm|fvwm2)
      OPT1=--clientid
      OPT2=$SMID
      ;;
    lwm)
      OPT1=-s
      OPT2=$SMID
      ;;
    #FIXME: add all other windowmanagers here with their proper options
  esac
fi

exec "$WINDOW_MANAGER" $OPT1 $OPT2

echo "ERROR: No window manager could run!"
exit 1


---

### Post by manicka on 2005-11-13
[QUOTE=magnusbb]I would really like to have this one, but I can't get it to work. I have done all said in the instructions, and the echo command reports that xfwm4 is the exported as an environment variable.

However, Metacity is still running, and it's still the window manager in GNOME. I can't even see the xfwm4 process in "top".

Here's my /usr/bin/gnome-wm, in case there is something wrong with that:[/QUOTE]

An obvious question is did you log out and back in again. 

What do the contents of ~/.gnomerc look like. 

There should be one line in it's content:

export WINDOW_MANAGER=/usr/bin/xfwm4

---

### Post by magnusbb on 2005-11-13
I did log out and in again, yes.

The contents of my ~/.gnomerc is exactly the line you posted, and that line only.

Is there something with my current session starting Metacity, or what?

---

### Post by neuschnee on 2005-11-13
Try backing up/deleting "~/.gnome2/session" ... then relog and try.

If session gets saved it fixes on metacity instead of gnome-wm.

---

### Post by ubuntu_demon on 2005-11-15
So does the speed of the "final product" more resemble that of xfce4 or more that of gnome (on a pc where you notice the difference) ?

---

### Post by theine on 2005-11-15
[QUOTE=ubuntu_demon]So does the speed of the "final product" more resemble that of xfce4 or more that of gnome (on a pc where you notice the difference) ?[/QUOTE]

It'll definately resemble the overall speed of Gnome.

---

### Post by ubuntu_demon on 2005-11-16
[QUOTE=theine]It'll definately resemble the overall speed of Gnome.[/QUOTE]
did you try ? (I'm not on gnome right now)

---

### Post by theine on 2005-11-16
[QUOTE=ubuntu_demon]did you try ? (I'm not on gnome right now)[/QUOTE]

No, I didn't. There's so much talk about Gnome being slow and why that is and I don't know what to believe, but I'm fairly sure that it's not due to the window manager.

---

### Post by LaSSarD on 2005-11-16
[QUOTE=theine]Check /usr/bin/gnome-wm if the entry for xfwm4 looks OK. Also, try
```

echo $WINDOW_MANAGER

```
and see whether it says xfwm4. If not, check ~/.gnomerc[/QUOTE]
the entry for xfwm4 looks ok on /usr/bin/gnome-wm, see:
```
if [ ! -z "$SMID" ] ; then
  case `basename $WINDOW_MANAGER` in
    sawfish|sawmill|metacity)
      OPT1=--sm-client-id=$SMID
      ;;
    openbox|xfwm4)
      OPT1=--sm-client-id
      OPT2=$SMID
      ;;
```
but now, that's strange:
```
:~$ echo $WINDOW_MANAGER
/usr/bin/xfwm4
```
it looks perfect, but metacity is already running (perfectly, no strange errors)

---

### Post by theine on 2005-11-16
> but now, that's strange:
```
:~$ echo $WINDOW_MANAGER
/usr/bin/xfwm4
```
it looks perfect, but metacity is already running (perfectly, no strange errors)

As neuschnee pointed out, you probably saved your Gnome session at some point. Try backing up/deleting ~/.gnome2/session and then log out of Gnome and back in again.

---

### Post by jadugarr on 2005-11-17
[QUOTE=neuschnee]Try backing up/deleting "~/.gnome2/session" ... then relog and try.

If session gets saved it fixes on metacity instead of gnome-wm.[/QUOTE]

I had the same problem when i first tried this.  Deleting your session file fixes this.

---

### Post by j_baer on 2005-11-17
Thanks for this how-to. 

I started here but decided to load the xubuntu packages to get all of xfce. I put it on top of my existing gnome install which allows me to switch back if required.

Works great !!!

I thought the "rox" file manager wasn't as strong as nautilus so I run nautilus instead {no problems}.

Anyone waiting on the next "gnome" should give xfce a try.

Thanks again ...

---

### Post by theine on 2005-11-17
[QUOTE=jadugarr]I had the same problem when i first tried this.  Deleting your session file fixes this.[/QUOTE]

Thanks, added this to the howto.

---

### Post by LaSSarD on 2005-11-17
it works perfect now, thanks a lot :D
now i'm just looking for all the metacity keybindings to import to xfwm4
well, they're here:

conf editor > /apps/metacity/global_keybindings
conf editor > /apps/metacity/keybinding_commands
conf editor > /apps/metacity/window_keybindings

but they're not "complete", there are some variables like "show desktop" instead of the proper command...

---

### Post by jadugarr on 2005-11-20
Does anyone know what the command is to open the Applications menu; alt+f1 default in gnome?

---

### Post by Bitmastro on 2005-11-21
install openbox
```
sudo apt-get install openbox
```
then the command is
```
gnome-panel-control --main-menu
```

---

### Post by jadugarr on 2005-11-21
[QUOTE=Bitmastro]
```
gnome-panel-control --main-menu
```[/QUOTE]

Thanks for the command.  There is an odd quirk when that command is used as xfce-keyboard-shortcut.  Instead opening the Applications menu it just hilights the menu and will not open a menu until you move the mouse over one of the other menu's (Places, System).  The command works normally from a terminal.  Maybe it has something to do with focus stealing protection? (wild guess).

It isn't a big deal though because I rarely use that shortcut and using the run dialog is faster anyway. :)

---

### Post by jadugarr on 2005-11-21
Here is another screenshot of xfwm4 in action.  [http://www.deviantart.com/deviation/25500214/](http://www.deviantart.com/deviation/25500214/)

---

### Post by angrykeyboarder on 2005-11-22
[quote=theine]Since metacity became the default window manager for gnome, I've always been bugged by the absence of some very useful features such as edge resistance towards other windows and vertical/horizontal maximization. The latter is actually somewhat implemented, but in a poor way, and [appearently]("http://bugzilla.gnome.org/show_bug.cgi?id=81704"), the developers of metacity don't seem to see a desperate need for properly implementing the above features anytime soon.[/quote]

I guess since I don't know what "edge resistance towards other windows and vertical/horizontal maximization" means, I've had nothing to miss. ;-)

---

### Post by jadugarr on 2005-11-22
[QUOTE=angrykeyboarder]I guess since I don't know what "edge resistance towards other windows and vertical/horizontal maximization" means, I've had nothing to miss. ;-)[/QUOTE]
Edge resistance is when you are moving windows, they sort of snap to the edges of other windows, panel, or edge of screen when you get close to them.  The vertical/horizontal maximization will only resize you window to full veritical or full horizontal ... keeping the previous size of the other value.  You can think of it as hotdog (vertical) and hamburger (horizontal) folding techniques where the original piece of unfolded paper is regular full maximization. 
These features are usefull if you like to view several windows at a time, and helps you arrange them neatly and quickly.

---

### Post by angrykeyboarder on 2005-11-22
[quote=jadugarr]Edge resistance is when you are moving windows, they sort of snap to the edges of other windows, panel, or edge of screen when you get close to them. The vertical/horizontal maximization will only resize you window to full veritical or full horizontal ... keeping the previous size of the other value. You can think of it as hotdog (vertical) and hamburger (horizontal) folding techniques where the original piece of unfolded paper is regular full maximization. 
These features are usefull if you like to view several windows at a time, and helps you arrange them neatly and quickly.[/quote]

Aah, OK, now I understand.  However, that's not something I'd even use if I did have it. :-)

Thanks for the info.

---

### Post by jadugarr on 2005-11-22
It's one of those things that you'll only notice/miss if you have used a window managers or applications that support this in the past. :)

---

### Post by angrykeyboarder on 2005-11-22
[quote=jadugarr]It's one of those things that you'll only notice/miss if you have used a window managers or applications that support this in the past. :)[/quote]

Perhaps. But there are a number of features in Metacity and Kwin that I probably don't use either.  I guess I'm boring in that regard. ;-)   And "minimalist" Window Managers like *box annoy me.  It's almost like they go out of thier way to be difficult.

I remember when GNOME dumped Sawfish for Metacity and how that upset many.  Sawfish had more "features" but you needed to manually tweak configuration files to get them.  And besides, I always felt it was ugly.  I just took a gander at [thier web site]("http://sawmill.sourceforge.net/") and I still think it's ugly. ;-)

---

### Post by foxy123 on 2005-11-22
I mostly use xfce, so I enjoy xfwm4 anyway. However I need sometimes to log in to Gnome and thought that would be nice to have xfwm4 there as well. So I followed the guide and xfwm4 seems to be running. The prolem is I cannot now log out. I have to use Alt-Ctrl+Backspace to leave Gnome.

Any idea how to fix it? Also I would like to make sure that it is xfwm4, which causes the problem, so how I put metacity back?

---

### Post by jadugarr on 2005-11-22
[QUOTE=foxy123]So I followed the guide and xfwm4 seems to be running. The prolem is I cannot now log out. I have to use Alt-Ctrl+Backspace to leave Gnome.

Any idea how to fix it? Also I would like to make sure that it is xfwm4, which causes the problem, so how I put metacity back?[/QUOTE]

What exactly does it do when you try and log out?  Metacity may still be running if you didn't delete your ~/.gnome2/session file which could be causing problems.  

To change back to metacity just edit the ~/.gnomerc file and remove the line (or comment out) that contains xfwm4.

---

### Post by foxy123 on 2005-11-22
[QUOTE=jadugarr]What exactly does it do when you try and log out?  Metacity may still be running if you didn't delete your ~/.gnome2/session file which could be causing problems.  

To change back to metacity just edit the ~/.gnomerc file and remove the line (or comment out) that contains xfwm4.[/QUOTE]
when I click on Log Out everything freezes, that's all. I rolled back to metacity and everything worked. Then I tried again put xfwm4 and it freezes again. Maybe it is because I use xfce from svn, I do not know.

---

### Post by Niomi on 2005-11-22
Thanks! Metacity had problems with the resolution I was running but xfwm works well with it. It also loads much faster.

I know it is possible to install clearlooks (I heart clearlooks!!) on xfwm but I believe it involves compiling the source code, something I haven't done before. I thought I could ask if there was a hold-the-newbie's-hand way to do it? Or perhaps compiling isn't as difficult as it sounds?

---

### Post by jadugarr on 2005-11-22
[QUOTE=Niomi]
I know it is possible to install clearlooks (I heart clearlooks!!) on xfwm but I believe it involves compiling the source code, something I haven't done before. [/QUOTE]
Since your still in gnome you still use your gtk-themes (listed as controls in theme manager).  There are xfwm themes that are similar to metacity themes or complete ports.  Many are available in the xfwm4-themes package in universe (apt-get).  No compiling necessary.  

For more xfwm4 themes you can look at [www.xfce-look.org](www.xfce-look.org).

---

### Post by raublekick on 2005-11-22
just tried this out. i have xfce installed, but i was never too into it. i do love the easy desktop switching ability though.

however, there's some things in metacity that i like more, and xfwm doesn't seem to be any faster.

oh well, at least i tried it out :)

---

### Post by henriquemaia on 2005-11-23
> [SIZE="0"][INDENT]There are things in xfwm that I like more and things and just miss too much on metacity. 

One of the things I miss is the lack of show desktop keyboard shortcut. I also noticed a bug with the combination of gnome Notification Area 2.12.1 + xfwm... some icons don't appear there. Native gnome and alltray icons do appear, but kde's don't (kmail and amarok). They are there, but they kind of get behind the others.

I even tried to use a combination of gnome+xfwm+xfce4-panel, using its notification area. This worked fine (in respect to the icons on the notification area), but the lack of show desktop shortcut kind of make it hard to use. I use the desktop a lot, like a big table where I put things to work them, and when you get your desktop crowded with windows, it's not very practical to do without this (I know I can use the show desktop button on xfce4-panel, but again, this is not the solution I want).

The greatest things I liked on xfwm is that gnome looks a bit faster and I can have a lot of shortcut keys for all kind of programs. 

I read somewhere that show desktop shortcut is on the todo list of xfce. When this happens, I definitely go for it.

Anyway, this tutorial works great. And I enjoyed the xfwm+gnome experience.

Thanks for this one!
[/SIZE][/INDENT]

This is not valid anymore. Please read post below.

---

### Post by henriquemaia on 2005-11-25
Well, the things I dislike most on metacity were really bugging me. As such, I reverted to the solution of using gnome + xfwm4 + xfce4-panel. 

What about the show desktop shortcut? Well... I was not being very clever before. Now I use the shortcuts to different workspaces. One of them is just for showing the desktop, with no windows. This works almost like the real thing. 

Now I'm a happy xfwm4 user. 

Things I like most on xfwm4 (update):
-Looks faster (have not done any benchmarking, but my personal experience tells me so).
-Better window placement and distribution
-Works better with alltray (alt+f4 does not closes the application, but simply hides it to the tray. With metacity, the app is closed, which makes me use the mouse more than I want to).
-If you open an extremely large folder by mistake on nautilus (like trash, when it's completely full) and you click close, the window closes almost immediately, as opposite to metacity, where nothing happens for some time (what is comprehensible but not pratical in every situation) and finally asks you if you want to kill the application. When this happens and you answer yes, it kills nautilus, desktop and other windows, which is completely unnecessary.

These are good reasons to stay with xfwm4.

Nice tutorial, works great and presents you with a good solution to quit metacity.

---

### Post by rjwood on 2005-11-26
this is loading really-really slow when I log in.

---

### Post by lucas on 2005-11-26
Why not replace gnome with xfce instead? :)

edit: added screenshot

---

### Post by kairu0 on 2005-11-28
Just followed the HOWTO and got xfwm running in Gnome. The performance is much better in terms of draw time, resizing, dragging, etc. Thanks guys!

---

### Post by The Warlock on 2005-11-28
I switched, and I like it, but there's one thing bugging me. If you go into System ->Preferences->Windows, it tells you "Cannot start the preferences application for your window manager. Window manager "Xfwm4" has not registered a configuration tool". Now, I know that "xfce-setting-show xfwm4" is the configuration tool, but how do I "register" it or whatever? It seems like an easy problem to fix; I just don't know how.

---

### Post by mcwtlg on 2005-11-28
I have not tried this yet, but I wanted to give some input to those newer linux converts (like myself) who are not happy with Gnome/Metacity performance.  I recently dumped Gnome completely and started using XFCE/XFWM4.  I like learning new things and this experiment was a lot of fun.  I will admit that it was a bit frustrating to use it at first, but it did not take long to see the benefits of XFCE/XFWM4.

The newest PC in the house is still running Windows XP (The wife is a hard sell on Linux for the main box), but the 2 other machines are both running Breezy.  One of those will get the Gnome/XFWM4 test soon.

My Linux boxes - 

U-Serv - (400 mhz Celeron, 512 meg RAM, 8 meg Matrox Millinium II video card, 1-18 gig HD, 1-6 gig HD, 1-4.5 gig HD) -- FTP, SSH, and Web Servers.
U-Lap - (650 mhz Pentium 3, 256 meg RAM, 8 meg ATI Rage P/M Mobility, 1-18 gig HD) -- Media Box

Breezy on older hardware (with ample RAM) works just fine.  Tweaking will help it to run faster.  I think, no I am certain, that that both machines run better on Linux than Windows,

I still have tons of questions, but these forums help quite a bit.  This is the first place that I have seen that does not seem to mind "dumb questions" (simply because there are none) from noobs (like myself) and flaming is just about non-existant.  This is a very good group.

Heck, the advice I have gotten from this forum has allowed me to use U-Lap to watch my sci-fi dvd's in the comfort of my bed, rather than turning on the entertainment center  I just plug in the headphones and I can enjoy full screen video < 1280X768 >.

---

### Post by theine on 2005-11-28
[QUOTE=rjwood]this is loading really-really slow when I log in.[/QUOTE]

Double-check whether you properly modified /usr/bin/gnome-wm so that xfwm4 is asigned a client ID from Gnome's session manager upon login.

---

### Post by theine on 2005-11-28
[QUOTE=The Warlock]Now, I know that "xfce-setting-show xfwm4" is the configuration tool, but how do I "register" it or whatever? It seems like an easy problem to fix; I just don't know how.[/QUOTE]

I added information on how to do this.

---

### Post by mcwtlg on 2005-11-29
Well, I did the XFWM replace (for Metacity) on the laptop and I was very happy.  I guess I was in the wrong directory or made a typo since I did not have .one of the files in the right directory, but once I moved it over, it worked like a charm.  Looks good and runs well.

I am glad it did, since this morning I went to turn on the ftp/file/web server and the PS was making a horrible noise (which finally quit) and Breezy hung right after decompressing the kernel.

Oh well, another project :D   I am wondering if the kernal is hosed.  If so, could I boot to a live Ubuntu CD and fix it...I hope so.

---

### Post by kairu0 on 2005-12-04
[QUOTE=theine]I added information on how to do this.[/QUOTE]

Just tried it. It works great!

---

### Post by HeartBT on 2005-12-20
OK, I'm game to try this, but I just need to know, will xfwm4 unroll, (or unshade) a window on focus?  I don't want to have to click on it to get it to unroll.  That one little niggling feature is all I really want out of a window manager.  Pinning is nice, but not required, themes are great, but I can usually find an acceptable one, but auto unrolling (as I like to call it) I just have to have.

---

### Post by kairu0 on 2005-12-21
I believe xfwm can't do that.

---

### Post by HeartBT on 2005-12-21
Nope it can't.  Great job on the how to, BTW.  worked slick.  I've decided that the best way to get what I want from KDE window manager, in Gnome, is to steal the KDE window manager.  Kwin is now running under Gnome.  Now I'm a happy camper, I just always thought that Kwin was so integrated into KDE it could'nt run under gnome, but so far so good.

---

### Post by kairu0 on 2005-12-21
[QUOTE=HeartBT]Nope it can't.  Great job on the how to, BTW.  worked slick.  I've decided that the best way to get what I want from KDE window manager, in Gnome, is to steal the KDE window manager.  Kwin is now running under Gnome.  Now I'm a happy camper, I just always thought that Kwin was so integrated into KDE it could'nt run under gnome, but so far so good.[/QUOTE]

Did setting that up require any special configuration? I'd like to see a screenshot, too, if you don't mind. It's very tempting.

---

### Post by Neo40 on 2005-12-21
It's nice but unfortunately it doesn't switch desktops on mouse scroll on empty desktop space. It works with mouse on desktop switcher, but not on desktop. Or I'm missing something...?

---

### Post by manicka on 2005-12-21
[QUOTE=kairu0]Did setting that up require any special configuration? I'd like to see a screenshot, too, if you don't mind. It's very tempting.[/QUOTE]

yes, I'd like to know how you did that as well

---

### Post by kairu0 on 2005-12-21
[QUOTE=manicka]yes, I'd like to know how you did that as well[/QUOTE]

I just tested it under XFCE by following the Enlightened XFCE HOWTO, substituting "enlightenment" for "kwin" is all. It worked very well. However, I quickly went back to xfwm because it added a good 5 seconds to my login time.

---

### Post by manicka on 2005-12-21
[QUOTE=kairu0]I just tested it under XFCE by following the Enlightened XFCE HOWTO, substituting "enlightenment" for "kwin" is all. It worked very well. However, I quickly went back to xfwm because it added a good 5 seconds to my login time.[/QUOTE]

Yes, but heartBT says that it can be done in gnome...

---

### Post by HeartBT on 2005-12-22
There is some playing around to do yet.  LIke I cannot get the configuration screen up when I click on the configure window settings popup.  The advanced works, and there have been no major problems yet since I've done it.  I fear that configuration is going to have to be by hand, since I don't want to install all of KDE just for it's control applet, and that appears what I have to do.  Other than that, it works.

Oh, apt-get install kwin
and then 

nohup kwin --replace &

and you should be running kwin under gnome.  

Just a reminder, I am a linux USER not programmer, expert, geek, anything.  I stumble around in the dark till I bump into something that sparks.  I know just enough outside a GUI to get me into trouble.  This one just worked, and honestly I'm shocked it did, but I'm still playing with it.

---

### Post by HeartBT on 2005-12-22
OK, an update.  I fully installed kde, and i can configure window settings with the control panel.  ( sudo apt-get install kubuntu-desktop ) I'm pretty sure that just KDE-base should net the same results without all the extra baggage of the whole desktop.  I'll do that later once I'm done learning how this is gonna work.

The transparency for kwin seems to not work in this configuration, however, there is still something else drawing my desktop.  It's not nautilus, as I have unchecked the draw desktop setting.  I have no menu's on desktop click either. 

BTW, the nohup command is a temporary way to do this, and I thought it prudent to not make a full out change until I was sure that the bugs were out and that it would work, I'm pretty sure that it can be made permanent in the GDM.  Poofyhairguy has a thread for enlightenment under gnome which is where I will start if/when I want to go permanent with this.

---

### Post by HeartBT on 2005-12-22
OK, here's the way, seems to work peachy.  on a fresh install of ubunto, I did a failsafe terminal, edited /etc/apt/sources.list and removed the commented lines.  then apt-get update, and apt-get upgrade.  

Installed kde core ( apt-get install kde-core ) and then exited.
logged into kde from the menu, kde did it's little setup thing and I logged out.  Login to gnome, I did not make it the default when it asked, opened a terminal and did the nohup kwin --replace &
metastrocity exited and kwin came up.  logged out and checked save settings.  Logged back in again, (I was not asked for default, so it was still set for last, I assume) and gnome started up, with kwin running.

---

### Post by theine on 2006-01-15
[QUOTE=HeartBT]Login to gnome, I did not make it the default when it asked, opened a terminal and did the nohup kwin --replace &
metastrocity exited and kwin came up.  logged out and checked save settings.  Logged back in again, (I was not asked for default, so it was still set for last, I assume) and gnome started up, with kwin running.[/QUOTE]

Actually, instead of the "nohup kwin --replace", etc. procedure, you can also set the WINDOW_MANAGER environment variable to kwin instead of xfwm4 (as in my original post), i.e.

```
echo export WINDOW_MANAGER=kwin >> ~/.gnomerc
```

This is a bit cleaner IMHO.

Regards,
Tobi

---

### Post by detyabozhye on 2006-01-29
I really like it, I'm using it now, but it seems to be a bit slow while dragging windows. Anybody know why?

---

### Post by kairu0 on 2006-01-29
[QUOTE=detyabozhye]I really like it, I'm using it now, but it seems to be a bit slow while dragging windows. Anybody know why?[/QUOTE]

If you drag windows on top of the wallpaper, then the application thats drawing it has to work harder. Are you using Nautilus or xfdesktop for your wallpaper?

---

### Post by detyabozhye on 2006-01-29
I'm using Nautilus, but it's ok over the desktop, it gets kinda slow over Opera, I think it was faster when I had the composite manager on, but I disabled it because it messed with my DVD playback.

---

### Post by papercuts on 2007-04-20
It's strange that there hasn't been a post for more than a year now in here.

anyway I tried this tutorial a few weeks ago with Edgy and everything worked great. Now I have Feisty and there is a problem. The effect works alright but the splash screen hangs on too long. So I login into and while I start applications the splash screen is still there. It goes away after a while. My guess is that it's loading some stuff. I don
t know what though. I went to the Sessions settings and tried to see what else it's loading. I took out Network Manager, but that didn't help.

Any ideas what might be wrong here?

---

### Post by SuSUntu on 2007-05-07
> **papercuts said:**
> It's strange that there hasn't been a post for more than a year now in here.

anyway I tried this tutorial a few weeks ago with Edgy and everything worked great. Now I have Feisty and there is a problem. The effect works alright but the splash screen hangs on too long. So I login into and while I start applications the splash screen is still there. It goes away after a while. My guess is that it's loading some stuff. I don
t know what though. I went to the Sessions settings and tried to see what else it's loading. I took out Network Manager, but that didn't help.

Any ideas what might be wrong here?

The step in the original HOWTO post which says to change the "/usr/bin/gnome-wm" file using this 'sed' command:

```

sudo sed -i "s/openbox)/openbox|xfwm4)/" /usr/bin/gnome-wm

```

is **no longer valid** because the gnome-wm file is different now.

For Feisty, you can run this modified 'sed' command:

```

sudo sed -i "s/openbox/openbox|xfwm4/" /usr/bin/gnome-wm

```

so that the original text:

```

    openbox|enlightenment|e16)

```

becomes

```

    openbox|xfwm4|enlightenment|e16)

```

Or, you can simply make the changes by directly editing the file using a text editor such as 'gedit'.

That should fix the symptoms you describe.

---

### Post by sanraj83 on 2007-05-10
> **papercuts said:**
> It's strange that there hasn't been a post for more than a year now in here.

anyway I tried this tutorial a few weeks ago with Edgy and everything worked great. Now I have Feisty and there is a problem. The effect works alright but the splash screen hangs on too long. So I login into and while I start applications the splash screen is still there. It goes away after a while. My guess is that it's loading some stuff. I don
t know what though. I went to the Sessions settings and tried to see what else it's loading. I took out Network Manager, but that didn't help.

Any ideas what might be wrong here?


Thanks! I too have the same problem. But unfortunately the long waiting for the splash happens only in ubuntu. I have ubuntu and gentoo sharing the same home and same settings for all the applications. In Gentoo the loading is very quick with the splash taking no time at all. Any one has any clues ? I was thinking it was my problem ( I mean I was doing some thing really stupid :( ) .. Any ideas ?

---

### Post by SuSUntu on 2007-05-12
> **sanraj83 said:**
> Any ideas ?

Yeah.

---

### Post by Evocati on 2007-07-23
Hi.

I did evrything like in this post and its working very nice, but after rebooting metacity is starting as default. What i must do to make xfwm4 default ?

Sorry for my english.

---

### Post by Canesfan2020 on 2007-07-23
edit - nm

---

### Post by dozersmasher on 2008-05-15
> **sailor420 said:**
> Is there an easy way to uninstall this, ie revert back to metacity should things not work?

```
sudo sed -i "s/xfwm4)/xfwm4|openbox)/" /usr/bin/gnome-wm
echo export WINDOW_MANAGER=/usr/bin/metacity >> ~/.gnomerc
```

---

### Post by darthmob on 2009-10-30
Anyone else having problems with this on 9.10?

No matter what I do it doesn't want to start with xfwm4 as window manager on my clean install. I tried all the suggestions in this thread except deleting the gnome session file which I don't find. There's no ~/.gnome2/session.

//EDIT:
Getting frustrated with metacity I installed enlightenment (e16). And now when I start enlightenment/gnome it starts with xfwm4 as I wanted it to all the time. I don't know what was wrong but it works now and that's fine with me.

---

