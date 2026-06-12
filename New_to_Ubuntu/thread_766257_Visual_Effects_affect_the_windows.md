---
title: "Visual Effects affect the windows"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by antipax on 2008-04-25
I installed the iso of 8.04, and everything was working properly, I have a Toshiba Satellite A-10 749 with an nVidia graphics card 7300 I think, and I had fun starting the Compiz fusion and checking a couple of settings on the System > Preferences > Advanced Desktop Effects Settings.

So, the point is after I shutdown and re-connected my laptop again later, I saw the windows like this:

[IMG]http://i4.photobucket.com/albums/y113/antipax/Screenshot.png[/IMG]

They lost their outer frame, I am unable to move or resize them and the terminal window is just a white square.

When I disable the Visual Effects, I get the windows looking normal again.

I'd like to know what's going on and how can I correct it, thanks for the help in advance.

---

### Post by alejo0823 on 2008-04-25
enable window decoration in the compiz settings manager

---

### Post by antipax on 2008-04-25
Thanks for the help, but Window Decoration is already enabled on the Advanced Settings Manager. This is my first time using Ubuntu, btw.

---

### Post by warbread on 2008-04-25
Hit alt+f2 and type in:

> emerald --replace

---

### Post by Google Spider on 2008-04-25
I assume you have the driver installed.

If windows decoration is enabled then disable it, close the windows, open again and enable windows decoration. (sounds stupid but i read this trick somewhere and works for me)

also,

```
**emerald --replace**
```

---

### Post by alejo0823 on 2008-04-25
if it was ok before you started turning on and off some things try to restore the default values in preferences.

---

### Post by antipax on 2008-04-25
> **Google Spider said:**
> I assume you have the driver installed.

If windows decoration is enabled then disable it, close the windows, open again and enable windows decoration. (sounds stupid but i read this trick somewhere and works for me)

also,

```
**emerald --replace**
```

I did that, but whenever I disable Window Decoration on the Advanced Setting Manager, close all the windows and then open the Adv. Set Man. I scroll to find that Window Decoration is enabled again.

as for the emerald --replace comand I get this:

[IMG]http://i4.photobucket.com/albums/y113/antipax/Screenshot-1.png[/IMG]

---

### Post by forestpixie on 2008-04-25
You'll need to install emerald if you haven't yet and a theme for it (maybe). You can get emerlad from the repos

```
sudo apt-get install emerald
```

You can get themes from here and others
[http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=5e610c7b81941737bc6b73ffea8872f9](http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=5e610c7b81941737bc6b73ffea8872f9)

---

### Post by Google Spider on 2008-04-25
So are the windows border back? Are you able to move and resize them?

I guess you don't have emerald theme manager.

```
sudo apt-get install emerald
```

EDIT : Beaten!

---

### Post by antipax on 2008-04-25
Okay, I installed the Emerald Theme Manager. 

So I go to Themes Settings -> Themes and the list is empty.

And on Edit Themes I chose legacy 0.1

When I enable the Extra visual effects, I still don't have the window borders. I'm feeling tremendously silly here.

---

### Post by alejo0823 on 2008-04-25
do again
> emerald --replace

---

### Post by antipax on 2008-04-25
Btw, on the CompizConfig Settings Manager I reset everything back to defaults, and it didn't solve the problem either.

---

### Post by Google Spider on 2008-04-25
> **antipax said:**
> 
So I go to Themes Settings -> Themes and the list is empty.



Here's a theme
[http://gnome-look.org/content/show.php/Vista-Linux?content=42875](http://gnome-look.org/content/show.php/Vista-Linux?content=42875)

download and open with emerald theme manager

then do emerald --replace

---

### Post by antipax on 2008-04-25
I did alt+F2, typed emerald --replace and the window closed by itself, then I went to System>Appearance>Visual Effects>Extra and it still removes the window borders.

---

### Post by antipax on 2008-04-25
> **Google Spider said:**
> Here's a theme
[http://gnome-look.org/content/show.php/Vista-Linux?content=42875](http://gnome-look.org/content/show.php/Vista-Linux?content=42875)

download and open with emerald theme manager

then do emerald --replace

I did that, it saved the theme to my desktop, then I opened Emerald and imported that theme into the themes list.

Then I closed emerald and did alt+F2 emerald --replace and the window closed by itself and nothing changed. When I tried to enable the Extra visual effects, still the windows lose their borders.

I'm beginning to think it's hopeless.

---

### Post by antipax on 2008-04-25
Actually I don't know why, but Emerald doesn't seem to do anything to change the visual aspect of my desktop. What am I doing wrong here?

---

### Post by alejo0823 on 2008-04-25
dont do it with alt-f2 try in a terminal and post errors

> emerald --replace

---

### Post by SunnyRabbiera on 2008-04-25
you might be getting hiccups with desktop effects, it might be best to turn them off and restart your computer and try them again.
sometimes the desktop effects do stuff like this with certain cards.

---

### Post by Znort_Ubern00b on 2008-04-25
If you have an nvidia card...

try typing this into terminal when running metacity, then enable compiz

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

it worked for me and i had the min max and close buttons back...

---

### Post by Separ on 2008-04-25
Looks like what I get if Compiz crashes, try hitting alt-f2 and typing compiz :D

---

### Post by antipax on 2008-04-25
> **alejo0823 said:**
> dont do it with alt-f2 try in a terminal and post errors

I typed that command in a terminal window pressed enter and nothing happened, I was left looking at a blinking cursor on the line below that command.

---

### Post by Google Spider on 2008-04-25
> **SunnyRabbiera said:**
> you might be getting hiccups with desktop effects, it might be best to turn them off and restart your computer and try them again.
sometimes the desktop effects do stuff like this with certain cards.
+1

sometimes these desktop effects make me mad.

> I'm beginning to think it's hopeless.

lol I told you whatever I could. Switch off your computer and go out get some fresh air. then try again ;)

---

### Post by antipax on 2008-04-25
> **SunnyRabbiera said:**
> you might be getting hiccups with desktop effects, it might be best to turn them off and restart your computer and try them again.
sometimes the desktop effects do stuff like this with certain cards.

I have reset all the CompizConfig settings to defaults and have rebooted the computer a couple times since and still the window borders disappear when I enable Extra visual effects.

When I installed the 8.04 I installed the nVidia proprietary driver, btw.
Everything worked properly after the first install for a few hours, all the visual effects were working fine. 

After I restarted my computer a few hours later, then the problems started, I can get the rotating cube and whatnot, but the windows do not show borders or maximize and minimize buttons (of course) and I can't resize or move them.

Emerald doesn't do anything for me, I'm wondering what I did wrong, because I even tried installing the suggested theme and did the emerald --replace and nothing changed either.

---

### Post by antipax on 2008-04-25
> **Google Spider said:**
> +1
Switch off your computer and go out get some fresh air. then try again ;)

Hehe, probably the best advice so far.
I know being a n00b to Ubuntu can get some of you wiser guys rolling your eyes, but I'm really happy I took the plunge, it works so much smoother than my previous OS: Vista.

---

### Post by antipax on 2008-04-25
> **Separ said:**
> Looks like what I get if Compiz crashes, try hitting alt-f2 and typing compiz :D

Okay, THAT removed the borders of my window now. Lost maximize, minimize button, etc
I went to Appearance and disabled the Extra effects that this command apparently enabled.

---

### Post by antipax on 2008-04-25
> **Znort_Ubern00b said:**
> If you have an nvidia card...

try typing this into terminal when running metacity, then enable compiz

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

it worked for me and i had the min max and close buttons back...

what is metacity?

---

### Post by Znort_Ubern00b on 2008-04-25
try using the line of code I gave you in my previous post. I am sure it will work.

[It did here...]("http://ubuntuforums.org/showthread.php?t=751956")

---

### Post by Znort_Ubern00b on 2008-04-25
> **antipax said:**
> what is metacity?

it is default windows manager.

type 
**metacity --replace**

in terminal then type that text then:

**compiz --replace**
you should then see then window borders

---

### Post by antipax on 2008-04-25
> **Znort_Ubern00b said:**
> try using the line of code I gave you in my previous post. I am sure it will work.

[It did here...]("http://ubuntuforums.org/showthread.php?t=751956")

I got this message:

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by Znort_Ubern00b on 2008-04-25
> **antipax said:**
> I got this message:

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Ok, turn off compiz and then turn it on again. it should then show you all the min max close buttons.

---

### Post by antipax on 2008-04-25
Dude you rock.

That worked, thanks so much!

And thanks to everyone else for bearing with me.

---

### Post by Ub1476 on 2008-04-25
Make sure that the command for the Window Decoration in Compiz is set to "emerald --replace", otherwise it might use Metacity upon startup.

---

### Post by antipax on 2008-04-25
Oh damn, it seems like before, everything works properly (I even used Emerald to change the theme and it worked) I had the visual effects and everything was working smoothly, until I decided to try and see if it worked after a restart.

It doesn't, back to the same problem - no visual effects when I log in and loss of window borders when I start compiz. I'm wondering if I'm going to have to do the previous solution everytime I restart the computer so I can have the visual effects?!

---

### Post by antipax on 2008-04-25
> **Ub1476 said:**
> Make sure that the command for the Window Decoration in Compiz is set to "emerald --replace", otherwise it might use Metacity upon startup.

Could that be the problem?
How do I change it?

---

### Post by antipax on 2008-04-25
> **Znort_Ubern00b said:**
> it is default windows manager.

type 
**metacity --replace**

in terminal then type that text then:

**compiz --replace**
you should then see then window borders

I typed these two lines and everything works smoothly again.

How do I go about making sure it remains that way, after I close/restart the computer?

---

### Post by Znort_Ubern00b on 2008-04-25
try changing the first command to 
emerald --replace instead of metacity --replace

see if that works.

---

### Post by antipax on 2008-04-25
Okay, that works, and it restores my emerald installed theme. It also starts compiz with default settings (no desktop cube, but desktop wall).

The issue I'm now addressing is, that upon restart, it never keeps my configuration. It just boots into Ubuntu without any visual effects and I have to manually type those 2 commands you gave me to get them back.

I also changed the command in the compizconfig settings manager -> Window decoration, from /usr/bin/compiz-decorator to emerald --replace

like another member suggested, I think
But still, upon restart, I get regular desktop with no visual effects and have to start them manually.

Any ideas?

---

### Post by antipax on 2008-04-25
When I shutdown/restart, I also revert back to just 2 Desks instead of the 4 I chose.

Having to go emerald --replace and compiz --replace after restart is annoying at best, because then I have to check/uncheck on compizconfig the effects I want/don't want.

Any suggestions on how I can make the system remember my desktop configuration? It's a strange situation...

---

### Post by Znort_Ubern00b on 2008-04-25
the emerald --replace will use emerald as your default desktop setting.try changing that back and see what happens.

if not then,to start up with compiz as default you have a few choices.
1) write a bash script to start compiz on login. Unfortunatly I know nothing about bash scripts, someone else may be able to help you on this one.
2)Look for the compiz fusion manager(**not ccsm**, i will look for actual name when i get home)this puts an icon next to system clock and I think allows you to change the default manager. so when you log in it uses compiz by deefault.


or you could just create a launcher on your desktop that you just need to click when you log in to start compiz.
Sorry i can't be of more help, am fairly new to all this and learning as I go.

---

### Post by antipax on 2008-04-25
thank you, you've actually been very helpful.

---

### Post by joshrobinson on 2008-04-25
fusion-icon is very nice, it can start your compiz for you, with your desired window decorator, you can also use it to change from emerald, to the standard GTK decorator, or shutdown compiz and go back to metacity

```
sudo apt-get install fusion-icon
```
to run it type
```
fusion-icon
```
and you can right click it to see the settings

if you like it and want it to startup compiz for you everytime you turn the computer on,

first make sure you have no other compiz startup scripts
then
system > preferences > sessions
click add on the first tab
set the name, and command as fusion-icon

---

### Post by oodledoodle on 2008-04-25
are you using nvidia? try here [http://ubuntuforums.org/showthread.php?t=599200](http://ubuntuforums.org/showthread.php?t=599200)
post number 7. 
worked for me.

---

### Post by Ub1476 on 2008-04-25
> Make sure that the command for the Window Decoration in Compiz is set to "emerald --replace", otherwise it might use Metacity upon startup.

To be exact, open System>Preferences>Advanced Desktop Effects. Next, click on Effects>Window Decoration. Look for the command line, and change this to "emerald --replace".

If Compiz wont startup automatically with this, go to System>Preferences>Sessions and click add.

Name: Compiz-Fusion
Command: Compiz

---

### Post by Separ on 2008-04-25
You can get emerald/compiz to start with those commands on startup in System>Preferences>Sessions

Hit the add button to add to the list. and make a seperate entry for emerald --release and compiz

If it doesn't save (like mine did) then do this as a fix:

```
cd ~/.config/
rm autostart
mkdir autostart
sudo chown -R USER:USER autostart
```

Replacing USER with your username.

---

### Post by evane1890 on 2008-05-07
> **antipax said:**
> I typed these two lines and everything works smoothly again.

How do I go about making sure it remains that way, after I close/restart the computer?

thank you, you've actually been very helpful.

&#35874;&#35874;&#65292;&#36825;&#23545;&#25105;&#22826;&#26377;&#24110;&#21161;&#20102;&#12290;&#12290;:guitar:

---

