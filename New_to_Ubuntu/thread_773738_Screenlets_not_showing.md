---
title: "Screenlets not showing"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by cartisdm on 2008-04-29
I have screenlets installed and it has it's bugs here and there but overall I really like it.  My problem is I can't get the widgets to appear on my other desktop after a reboot.  I have the following options checked under the Window Option:

Lock
Widget
Sticky
Keep Below.

If I uncheck Sticky, then recheck it it will then put that widget on the othe desktops (just like I want).  Then after a reboot it places them back to display only on the first desktop.  What am I missing?

---

### Post by cartisdm on 2008-04-29
Anybody?

---

### Post by dangerpl on 2008-04-29
If you use Gdesklets, they will show on all your desktops.

---

### Post by PinkFloyd102489 on 2008-04-29
Lock and stick the screenlet.

---

### Post by cartisdm on 2008-04-29
> If you use Gdesklets, they will show on all your desktops

I tried gDesklets but they were really buggy for me and got on my nerves.  I couldn't ever get the weather to even display...

> **PinkFloyd102489 said:**
> Lock and stick the screenlet.

Don't I already have that checked? or do you mean something else....?

---

### Post by cartisdm on 2008-05-03
*bump*

---

### Post by other guy on 2008-05-03
Do they show in sessions? So it can load after you start the user account. There is a spot you can tick to have them automagically start with the user. Unless you found a bug unique to you.


In Gnome:

System | Preferences | Sessions

You should see the session instance of the Screenlet.. you want There can be a few depending how many your are firing off.

In my session for example, I have 

Screenlets Daemon
/usr/share/screenlets-manager/screenlets-daemon.py

I might be wrong assuming it is not starting with your user.

You might have to manually edit the config file for the screenlet so it keeps the settings. If it does work starting up correctly. I had to manually edit the file for my monitor screenlet so it stayed under.

---

### Post by cartisdm on 2008-05-03
Yea I just checked the Sessions and they all are set up to start on boot.  And within the Screenlets settings the Autostart is checked as well

---

### Post by other guy on 2008-05-03
Ok, next poke at the issue.


Navigate to your home folder. Make sure hidden files are shown. One of two ways. Easy way is to use Crtl+H. Or you can simply tick hidden files in the view menu.


Ok next step that you can see hidden files. Go to the .screenlets folder. You will see your active screenlets there. look for the file(s) called config.ini.

The dot in front of any folder or file means it is hidden. :D

That is when you open it in the text editor and set each value you want to True or False. Make your changes, save and check your work.


If you need more details. Please by all means ask.

---

### Post by bnl on 2008-05-03
I have the same problem.  If i log out and back in, my screenlets are gone.  I can go to the screenlets manager and click the "restart all screenlets" and they'll be back, but they won't stick to all desktops even though they say "Sticky".  If i uncheck and then check the box again, it works.

My config.ini looks like this:
[Options]
show_in_tray=True

Why aren't there any of the screenlets listed?


And on a related note about settings not being saved on log out/in, how do i keep the screenlets to appear on both the widget layer and the regular layer?  I got it to work by opening two of the same screenlet and setting one to be treated as a widget and then deleting that screenlet.  The other screenlet of the same type now appears on both layers.  Of course, after i log out and back in, the settings are lost and they only remain on the regular layer.

Thanks!

---

### Post by other guy on 2008-05-03
Since I have no ssiue. Producing the same bug as you. Lets move to another directory and look for the specific options you seek. :D

Same thing as post #9 above. Make hidden files visible. bla bla bla..

Lets move to:

/home/*Your_User*/.config/Screenlets/

This will show all your screnlets and the configs' for them. Even for each instance of it.

As exmaple:

I want to modify the momometer I have spawned. Actually three of them. So each one will have to be modified uniquely.

My file(s) will look like this..   .. Roughly....

/home/other_guy/.config/Screenlets/Manometer/default

Manometer1.ini  Manometer2.ini  Manometer3.ini

Now since I have some minor variances between each instance each one has. How about I show Manometer1.ini as a rough example.  I can tweak as  I see fit or have need for each screenlet I use or want to use.


** Manometer1.ini**
opacity=0.7
scale=0.7
theme_name=Monochrome White
show_info=Temperature: Core 1:      +34°C  (high =   +85°C)
is_sticky=True
cLabel_color=1.0,1.0,1.0,1.0
cLabel_text=Core1
draw_buttons=False
keep_above=False
lock_position=True
is_dragged=False
keep_below=True
y=796
x=1184
skip_taskbar=True


So roughly following my previous post's instructions. Just move to the new directory and see if that fixes ya'll up.


If not, I will still be glad to help out and offer assistance.

---

### Post by bnl on 2008-05-03
In .config/Screenlets/Clock/default/Clock2.ini, i have:

scale=1.5
theme_name=station
is_sticky=True
keep_above=True
lock_position=True
keep_below=False
y=57
x=1205
time_offset=-7


So it says that it is "Sticky" as expected, but it's not appearing on other desktops.  When i uncheck and check "Sticky", it works again.  Thoughts?

Thanks for your help.

---

### Post by other guy on 2008-05-03
Maybe delete that file and start afresh??

I know some settings can be buggy. I cannot reproduce that same issue as you. Yes, I am a screenlets fan also.


If need be. I can spawn an instance on my machine with all the settings and post up the result. Then you could edit out what you want and do not want.. First please backup your file(it should by itself anyways) and then delete it to see if it helps you./  Sometimes a fresh start fixes things. When setting the settings. Please try to use the full GUI for each Instance. Not the context menu options.

:popcorn:

---

### Post by bnl on 2008-05-04
I really wanted to figure this one out, so i decided to try to fix it myself.  In /usr/shared/pyshared/screenlets/__init__.py, edit line # 952 from:

try: self.window.show()

to

try: self.window.show(), self.window.hide(), self.window.show()

That seems to make things work.  I'm going to send this to the Screenlets people to see if this is an actual bug (it's been confirmed by others on this thread) and if this is a principled fix vs. just a hack.

---

### Post by Hells_Dark on 2008-05-08
Same problem here with the nowplaying screenlet.

i'd like to try the bnl tips but my line 959 is :
```
item.show()
```
so..

---

### Post by dark_harmonics on 2008-05-08
I have had problems where i have to uncheck the keep-above option on my laptop constantly on an RSS feeder. It does get rather annoying.

---

### Post by Golem XIV on 2008-05-08
What version of Screenlets are you running? The one in the repositories is old (0.0.12) and there is a new one that came out (0.1.1).  You can find it on [GetDeb]("http://www.getdeb.net/app/Screenlets").  Just download the .deb file appropriate to your system and double-click on it to install.  Just to be on the safe side, purge the previous installation.

---

### Post by diplomat.x on 2008-05-10
Okey, so seems like i am not alone. 

Absolute similar problem with me. I set everything up and i am damn sure i tick all the locks and sticky options but everytime i restart, they are gone. If i open screenlet and click restart all screenlets, they are all at new locations. Now i cant keep editing screenlets everytime i start my computer...
Things werent the same in gutsy....

I will try what "other guy" has suggested and post here the outcome.

---

### Post by nynoah on 2008-05-10
actually this is just a little quirk to the screenlets program.  If you modify the screenlet do all the things that you want to do to it.  Then close it.  Open up the screenlets manager, relaunch the one you just closed make sure before launch it that the box for "auto start on login" is checked.  It should work with all the settings that you just changed.  I don't know why it is like this, but this is how I work around it.  BE sure not to DELETE SCREENLET.........you want to just "quit this screenlet"

let me know if that helps or if you need more help.

Noah

---

### Post by diplomat.x on 2008-05-11
> **nynoah said:**
> actually this is just a little quirk to the screenlets program.  If you modify the screenlet do all the things that you want to do to it.  Then close it.  Open up the screenlets manager, relaunch the one you just closed make sure before launch it that the box for "auto start on login" is checked.  It should work with all the settings that you just changed.  I don't know why it is like this, but this is how I work around it.  BE sure not to DELETE SCREENLET.........you want to just "quit this screenlet"

let me know if that helps or if you need more help.

Noah


Tried it. Followed steps u said. Restarted and same problem, screenlet didnt start and when i manually started it was again placed improperly. 
In sys>pref>sessions, karamba, screenlets are all ticked....:(

Thanks for getting involved and trying to help.

---

### Post by MrGrey1 on 2008-08-06
Hey, had similar problems with not staying sticky and screenlets reloading in wrong place, upgraded to latest screenlet manger and now problems seem to have been solved. The latest manager is not in the repos...
Try here if your still having problems: [http://www.getdeb.net/release/2748](http://www.getdeb.net/release/2748)

:)

---

