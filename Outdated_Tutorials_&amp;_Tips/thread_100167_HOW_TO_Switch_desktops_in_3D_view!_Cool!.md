---
title: "HOW TO: Switch desktops in 3D view! Cool!"
date: 2005-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by anil_robo on 2005-12-07
First, make sure you have all the repositories and 3D support enabled!
 
1. Open a terminal window, type:
```
sudo apt-get install 3ddesktop
``` press enter
2. 3ddesktop should be installed.
3. you can type 3ddesk and press enter in terminal to run this. (Use arrow keys to change desktops, enter to select that desktop)
 
You'll see something like this:
 
[IMG]http://img215.imageshack.us/img215/4049/3ddesktop7tx.jpg[/IMG]
 
You can switch between desktops by:
1. Using the up and down arrow keys
2. Using the right and left arrow keys
3. Using the mouse scrolling wheel.

**How to make a desktop launcher for 3d desktop:**

1.Right click on an empty area in the taskbar, and click "add to panel"
2. Double click "custom application launcher"
3. Name: 3D Desktop changer
    Comment: My cool 3D Desktop changer (or whatever you like)
    Command: 3ddesk
    Make sure you have "run in terminal" unchecked.
If you want, you can select an icon by clicking on "no icon" button.
4. CLick OK

To run 3ddesktop switcher, just click on the icon you just made on the panel.

**How to assign the windows key to 3ddesktop:**

1. ```
gconf-editor
``` 2. Navigate to apps/metacity/keybinding_commands
3. Choose an empty command (I chose Command_1), double click, set value to 3ddesk
4. Now navigate to apps/metacity/global_keybindings in gconf-editor
5. Find Run_command_1 (or whichever command you chose in step3 above), double click it, set value to Super_L
6. Close gconf-editor
7. Check by pressing your windows key. It should start 3ddesktop.

**Tips:**
1. If the screens come up grey when you first run it, you probably do not have 3ddesktop daemon (3ddeskd) running. So you have to pass a command from terminal manually:
```
3ddesk --acquire=100
```  
2. 3ddesktop has many display modes. Try these:
```
3ddesk --mode=linear --nozoom
``` ```
3ddesk --view=slide
``` ```
3ddesk --view=linearzip
``` 
Other command-line options are:

     --version         Display version information
     --view=xxx        Uses the options from the view in 3ddesktop.conf
     --mode=xxx        Sets the arrangement mode
                        (one of carousel, cylinder, linear, viewmaster,
                         priceisright, flip, or random)
     --acquire[=#]     Grab images for all the desktops by cycling thru
                        (sleep for x millisecs at each screen for refresh)
     --acquirecurrent  Grab image for current desktop
     --nozoom          Disable the zoom out
     --changespeed     Set the rotation speed
     --zoomspeed       Set the zoom speed
     --gotoright       Goto the desktop to the right
     --gotoleft        Goto the desktop to the left
     --gotoup          Goto the desktop to the up
     --gotodown        Goto the desktop to the down
     --goto=#          Goto specified column (deprecated)
     --gotocolumn=#    Goto specified column
     --gotorow=#       Goto specified row
     --dontexit        Don't exit after a goto
     --stop            Stop 3ddesktop (kill 3ddeskd daemon)
     --reload          Force a reload of 3ddesktop.conf
     --noautofun       Don't Automatically turn on Fun Mode
     --revmousewheel   Reverse the mousewheel
     --swapmousebuttons Swap the mousebuttons
     --altmousebuttons Use alternate mousebuttons scheme
     --justswitch      Just switch desktops and acquire without graphics


This is great for people who have not got xgl working yet! Enjoy! :cool:

---

### Post by astronerd on 2005-12-08
Couldnt get it to work following your directions...   Nothing happens when I click on the icon that is made.  Is there something else you forgot to add?

---

### Post by BoneyOne on 2005-12-08
Works pretty neatly....only problem I had is that some of the screens came up green until I went to the manually first....*shrugs* oh well.

---

### Post by dabear on 2005-12-08
It would be cool if you could figure out how to link the 3ddesk command to a short key, e.g. ctrl + shift + 2 or similar.

---

### Post by jr.gotti on 2005-12-08
> Works pretty neatly....only problem I had is that some of the screens came up green until I went to the manually first....*shrugs* oh well.

Use '3ddesk -acquire' first (maybe add it to your startup?) and it will take a snapshot of all your desktops. This will eliminate that small, yet rather unattractive problem. :D

> It would be cool if you could figure out how to link the 3ddesk command to a short key, e.g. ctrl + shift + 2 or similar.

This is quite possible, to do it just...

Go to System Tools > Configuration Editor.

Open apps > metacity > keybinding commands.

Double click on command_1, and in the value field, enter '3ddesk' (no quotes).

Now, go to apps > metacity > global keybindings and double click on "run command_1."

In the value enter your keyboard shortcut. I used <Control><Alt>P, but use whatever suits you...

Now, delete the custom launcher he told you to make in the original post...it's useless. :P

Hope I helped,
-Jason

By the way, I think he forgot to mention, you have to have your graphics card drivers installed and OpenGL working for this to function correctly.

EDIT 2: What is with the Windows XP Bliss wallpaper?! I'm not hating or anything...but people that use linux tend to customize a LITTLE more than that. Lol. Run over to [http://www.deviantart.com](http://www.deviantart.com) and grab a nice desktop. (Sorry, I had to say something about it...)

---

### Post by Zeroedout on 2005-12-08
[quote=astronerd]Couldnt get it to work following your directions... Nothing happens when I click on the icon that is made. Is there something else you forgot to add?[/quote]

You need to install the drivers for your video card so opengl will work.

---

### Post by gabhla on 2005-12-08
You need to install the drivers for your video card so opengl will work.

This installed fine...I just have same problem mentiond above by someone else, I click on the icon - nothng happens.  At the risk of sounding dumb..how do I determine which drivers I need, then how do go about installing them?

---

### Post by anil_robo on 2005-12-08
I posted this on HOW-TO and it takes a long delay before they approve my post. So I've posted it in general too, so that I can update this frequently. See the updated post here: [http://ubuntuforums.org/showthread.php?t=100169](http://ubuntuforums.org/showthread.php?t=100169)

---

### Post by benplaut on 2005-12-08
look at the manpage for some info... it's possible to "3ddesk --move-left" or something... you can set custom commands for pretty much anything

---

### Post by anil_robo on 2005-12-08
[quote=pixelPOET]Use '3ddesk -acquire' first ...[/quote]
Thanks! I didn't know that! :D

> EDIT 2: What is with the Windows XP Bliss wallpaper?! I'm not hating or anything...but people that use linux tend to customize a LITTLE more than that. Lol. Run over to [http://www.deviantart.com]("http://www.deviantart.com") and grab a nice desktop. (Sorry, I had to say something about it...)

Actually I was trying to make Ubuntu look and feel like Windows XP... someone in the forums asked for it - but I couldn't really do that with the bootup screen! That's about it! And thanks for deviantart link. I stopped using that quite some time back, glad you reminded me again! :D

---

### Post by domino on 2005-12-14
This is a nice feature. Unfortunately I had to remove it because it studders my scrolling and window dragging. The CPU peeks to 50% every 2 seconds also.

---

### Post by spockrock on 2005-12-18
nifty little program, works great......

---

### Post by onesojourner on 2005-12-19
[QUOTE=domino]This is a nice feature. Unfortunately I had to remove it because it studders my scrolling and window dragging. The CPU peeks to 50% every 2 seconds also.[/QUOTE]

my cpu is hitting a high every couple seconds too. any one have any ideas as to why? this is cool but I can't have it doing that.

---

### Post by anil_robo on 2005-12-19
[quote=domino]This is a nice feature. Unfortunately I had to remove it because it studders my scrolling and window dragging. The CPU peeks to 50% every 2 seconds also.[/quote] 
Most likely, you're using this with --acquire option (as suggested by someone else in this thread). This option forces 3ddesk to acquire a screenshot of each of your desktops first by cycling through them, and then starts the program. Try running 3ddesk from a terminal without any options, and you'll be fine.

If you don't like that high cpu usage, you "have to" disable --acquire option.

The 3Ddesktop saves its preferences in /etc/3ddesktop/3ddesktop.conf. Backup this file, and edit it as per your liking! :D If you're uncomfortable with editing conf files, you can still get a workaround:

1. open a terminal window, and type **3ddesk --stop**. Press enter. This stops 3ddesktop daemon.
2. Now restart the 3ddesktop daemon in the fastest mode: in the terminal, type **3ddeskd --fastest** and press enter. Please note you should run 3ddeskd for this step, not 3ddesk.
3. Now your 3ddesktop is configured to run in the fastest graphic mode. Test it by typing **3ddesk** in the terminal and pressing enter.
4. Still having problems? You have problems with your 3d graphics hardware. Locate help for installing and enabling 3d support for your graphic card from these forums - do a search! :D

---

### Post by aptsonic on 2005-12-20
[QUOTE=pixelPOET]Use '3ddesk -acquire' first (maybe add it to your startup?) and it will take a snapshot of all your desktops. This will eliminate that small, yet rather unattractive problem. :D



This is quite possible, to do it just...

Go to System Tools > Configuration Editor.

Open apps > metacity > keybinding commands.

Double click on command_1, and in the value field, enter '3ddesk' (no quotes).

Now, go to apps > metacity > global keybindings and double click on "run command_1."

In the value enter your keyboard shortcut. I used <Control><Alt>P, but use whatever suits you...

Now, delete the custom launcher he told you to make in the original post...it's useless. :P

Hope I helped,
-Jason

By the way, I think he forgot to mention, you have to have your graphics card drivers installed and OpenGL working for this to function correctly.

EDIT 2: What is with the Windows XP Bliss wallpaper?! I'm not hating or anything...but people that use linux tend to customize a LITTLE more than that. Lol. Run over to [http://www.deviantart.com](http://www.deviantart.com) and grab a nice desktop. (Sorry, I had to say something about it...)[/QUOTE]

thanks a million for this post...

---

### Post by FLeiXiuS on 2005-12-20
When running 3ddeskd you may want to include --acquire=30.  This will tell 3ddesktop to collect an image of each workspace.  This way none of the screens come up gray.

---

### Post by RaptorRaider on 2006-02-03
Is anyone else experiencing performance problems with 3ddesktop?

On my system, 3ddesktop takes up 200Mb of RAM and seems to entirely hang the system for 0.2 seconds every 2 seconds or so; it doesn't stop until I kill 3ddesk.

---

### Post by poofyhairguy on 2006-02-03
[QUOTE=RaptorRaider]Is anyone else experiencing performance problems with 3ddesktop?

On my system, 3ddesktop takes up 200Mb of RAM and seems to entirely hang the system for 0.2 seconds every 2 seconds or so; it doesn't stop until I kill 3ddesk.[/QUOTE]


Tell us more about your system (full specs please).

---

### Post by RaptorRaider on 2006-02-03
The Ubuntu-installation itself is still very clean.
Most important hardware specs:

Athlon 64 3400+ (S754)
X800 Pro ViVo @ XT PE
2x 512MB PC3200 "Infineon Original"
MSI K8N Neo Platinum
Creative Audigy 2 ZS

ATI's drivers? :neutral:

---

### Post by Virogenesis on 2006-02-03
no probs here  works great looks great cheers

6600GT 
2600+ Sempron
756mb pc2100

---

### Post by jr.gotti on 2006-02-03
[quote=aptsonic]thanks a million for this post...[/quote]

no problem, just trying to help. :]
-jason

---

### Post by arnieboy on 2006-02-03
[QUOTE=FLeiXiuS]When running 3ddeskd you may want to include --acquire=30.  This will tell 3ddesktop to collect an image of each workspace.  This way none of the screens come up gray.[/QUOTE]
any idea how to have a different background for each workspace on Gnome? I have heard about devilspie doing it but any more trivial method?

---

### Post by cutOff on 2006-02-03
[QUOTE=arnieboy]any idea how to have a different background for each workspace on Gnome? I have heard about devilspie doing it but any more trivial method?[/QUOTE]
Do you know [Wallpapoz]("http://wallpapoz.sourceforge.net/")??

---

### Post by arnieboy on 2006-02-03
[QUOTE=cutOff]Do you know [Wallpapoz]("http://wallpapoz.sourceforge.net/")??[/QUOTE]
Nopes I didnt know about it but looks good and will give it a try. thanks.

---

### Post by javaTard on 2006-02-03
Installed fine, reading up on installing my driver for my video card. 
Does anyone use this on the 64 bit version of 5.10? That is what I am running now

---

### Post by zenwhen on 2006-02-03
This thing is actually pretty cool.

---

### Post by jerome bettis on 2006-02-03
excellent, works great over here.  i started 3ddeskd in the sessions thing as suggested above, that made it work a lot better.  i had to change the texture to 256 in the config file for a little more speed (intel i915 32mb = SLOW)

but this is awesome and it actually works!  thanks

---

### Post by Subbu.exe on 2006-02-04
I Installed it, But I Cant Make it to Run!

> subbu@Subbu:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

subbu@Subbu:~$

I Use Nvidia 6800 Vanilla 128MB, I Have Installed the Drivers from nvidia.com,
All Opengl Games Work! (Quake3, Doom3, PPracer).

Whats the Problem?

---

### Post by happyponcho42 on 2006-02-04
How did you take a screenshot while in the 3d desktop mode?  The printscreen which works when a desktop is selected doesn't seem to work while in the 3d desktop mode -- I'm trying to take a screenshot of what it looks like on my computer.

EDIT - ksnapshot (sudo apt-get install ksnapshot) did the trick :)

---

### Post by endersshadow on 2006-02-05
For fun, try:

```
3ddesk --view=bigmoney
```

It's Price Is Right style!

Great HowTo!

---

### Post by jr.gotti on 2006-02-05
if your like me, you'd hate the default green of the digits. you can change that by editing the 3ddesktop.conf file.

```
sudo vim /etc/3ddesktop/3ddesktop.conf
```

and scroll down until you see the default configuration

```
view         default    ## this is the default if no --view specified
zoom         on
show_digit   on
digit_size   100
digit_color  green
use_breathing false
```

change these to fit your personal preferences...

i personally turn off the digits, (change show_digit to off, duh...) and turn breathing on...it pulsates the light on the desktops.

if you have a faster processor you can turn on "fastest"...this makes the animation smoother...

instead of throwing everything in default, you can follow this same format and make your own views at the end of the file...

have fun!!

heres mine.

```
view         default    ## this is the default if no --view specified
zoom         on
show_digit   off
digit_size   100
digit_color  green
use_breathing true
fastest        on
```

-jason

---

### Post by PandabeaR on 2006-02-05
L33T! it works PERFECT :)

---

### Post by vbmaster on 2006-02-26
I'm loving this one:

view         default   ## this is the default if no --view specified
mode	     cylinder
dontexit     on
zoom         nozoom
show_digit   off
digit_size   100
digit_color  green
use_breathing false

---

### Post by abyssspecter on 2006-03-05
Omg, this is the coolest thing ive seen in a while.

it works perfectly for me, thanks!

but, one question, how do you add more windows? I see that on the screen shot  you have more than 4, and id like to do that.

---

### Post by anil_robo on 2006-03-06
[quote=abyssspecter]Omg, this is the coolest thing ive seen in a while.

it works perfectly for me, thanks!

but, one question, how do you add more windows? I see that on the screen shot  you have more than 4, and id like to do that.[/quote]

3ddesktop will show all the desktops you have. So if you have 10 desktops, 3ddesktop will show you 10 of them. If you have 5, it will show 5.

To change the number of desktops, you can right click on any desktop ("workspace") icon in the panel, choose preferences and then set how many do you want.

---

### Post by anil_robo on 2006-03-06
[quote=happyponcho42]How did you take a screenshot while in the 3d desktop mode?  The printscreen which works when a desktop is selected doesn't seem to work while in the 3d desktop mode -- I'm trying to take a screenshot of what it looks like on my computer.

EDIT - ksnapshot (sudo apt-get install ksnapshot) did the trick :)[/quote]

Yes that is an option. For GNOME users, they can use:
```
 gnome-screenshot --delay=5
```
Of course, you need to have it installed (installed by default - or use sudo apt-get install gnome-screenshot) and then use the command:
```
gnome-screenshot --delay=5
```
You can set the delay to any number of seconds you want (I have set it to 5 seconds in the above command)

---

### Post by bluevoodoo1 on 2006-03-09
This is great! Finally got a video card that can handle this sort of stuff and I love it!

---

### Post by ronmarley1 on 2006-03-09
Man, how did I live this long without this?  Woo Hoo!

---

### Post by _simon_ on 2006-03-10
is there a way to map this program to a key?

Ideally i'd like to press the windows key and get this to work...

---

### Post by jr.gotti on 2006-03-10
From my earlier post

>  Go to System Tools > Configuration Editor.
 
 Open apps > metacity > keybinding commands.
 
 Double click on command_1, and in the value field, enter '3ddesk' (no quotes).
 
 Now, go to apps > metacity > global keybindings and double click on "run command_1."
 
 In the value enter your keyboard shortcut. I used <Control><Alt>P, but use whatever suits you...


Hope I helped,

-Jason

---

### Post by Coolit on 2006-03-10
Excellent post! Its quite easy to get up and running thanks to this guide. 

PixelPOET I've mapped keys thanks to your post but I'd like to map the windows key as its unused, do you know what the tag is for this, <win> ?

Thanks :mrgreen:

---

### Post by Coolit on 2006-03-10
I've found the bind for the left windows key <mod4> but it doesnt work on its own so I've bound it to leftwin+z, <mod4>z

:)

---

### Post by binjajer on 2006-03-10
Looks like that with the dapper dev release, the 3ddesk will become outdated... no really, you don't know the power in your desktop until you try compiz and XGL...

---

### Post by n1gke on 2006-03-12
This is just great.
I am using a three button mouse. The center button, what I just discovered, is actually the wheel between the two main buttons. I didn't know it was a clickable button.

I did have to install the additonal drivers for the VooDoo 3D FX card, cool, and easy too using Synaptic and searching string voodoo.

Following the instructions as laid out, and selecting an appropriate icon, it landed on the bottom task bar, which is what I had chosen. I have four task bars, one for each edge of the screen.

Using the left button on the mouse brought in the 3D display mode when clicking on the icon one time.

Okay, so far so good.

I have allocated ten desktops. Each desktop is running multiple applications.

I discovered I can rotate the display either using the wheel of the mouse, up/down, or by using the left/right buttons accordingly.

By rotating the desktops on the screen and choosing one, I then discovered by click the wheel, which is a button, it will select the screen that is front and center of the displayed screens.

This is just too good to be true really.

Hang on, I need to take a depp breath and pour more coffee !

Okay. Back.

With a desktop open, and the desire to switch to another desktop, I click the 3D icon once, using the left mouse button, this returns display of all ten desktops in rotation mode, sweet. 

There is one anomaly, or deviation from common rule.

Although I have allocated ten desktops, when rotating the 3D display and it goes past the ninth desktop, the next one is numbered 1. Not good.

That can be fixed though I'm sure.

Another anomaly is. Once I have all ten desktops loaded in the 3D display, it forgets them. More about that later, okay.

For the most part, this is way too cool. Just super. 

Enough said and many thanks for the informations on how to do it !

---

### Post by DBO on 2006-03-20
this cool, but mine goes wonky... it just starts switching back and forth between desktops and I cant get out of it short of switching over to a console and killing its task.  Anyone else had this problem?

EDIT - After disabling the random movement (set the delay to a huge number), I dont experience the problem anymore.

---

### Post by DCJoeDog on 2006-03-20
clear concise instructions, and got it up and runnig in short order, thank you very much

---

### Post by Absolute on 2006-03-20
Amazing feature, thanks for the How To!

One question though; I have 4 monitors, each with their own sessions.  3ddesk only works within the monitor that I started the daemon on.  Even executing the task on another monitor starts the switcher on the monitor it was started on.

Is there a way to have 3ddesk apply to all sessions, or at least to bind different keys to different sessions?

Thanks!

---

### Post by nealklomp on 2006-03-26
awsome thanks.

---

### Post by Bigga on 2006-04-12
I'm a total n00b and got that working! Ain't Ubuntu great!?:-D

---

### Post by Josh M on 2006-04-14
This is a fun little app, thanks for the How-To.

---

### Post by x5452 on 2006-04-14
what exctly is the 3d desktop thing? I saw some screen shots, like the first post with three windows open, are those actual windows that just like rotate or something when you pick one to work in? or is it just a background type thing?

---

### Post by x5452 on 2006-04-19
ok so i have it installed, and i have a little icon i made to activate 3d desktop, but how to you make stuff appear in the other windows?  when i click it, my screen draws back, and i see the one i had, and three other ones blank...  what do you do with those?  also, i saw some screenshot where the 3d thing was a cube..can this do that?

---

### Post by anil_robo on 2006-04-19
[quote=x5452]ok so i have it installed, and i have a little icon i made to activate 3d desktop, but how to you make stuff appear in the other windows?  when i click it, my screen draws back, and i see the one i had, and three other ones blank...  what do you do with those?  also, i saw some screenshot where the 3d thing was a cube..can this do that?[/quote]

The other screens appear blank because you have not told 3ddesktop to grab them periodically. You can do so by changing the commandline for launcher to:

```
3ddesk --acquire=100
```

This cycles through all the available desktops, acquiring their screenshots at 100 millisecond intervals, and then starts 3ddesktop. However, it may eat up much system resources.

Let me know if it works.

---

### Post by x5452 on 2006-04-20
is there a way to, and i hope this doesnt sound stupid, but say on my current desktop i have a background pic, with a certain gkrellm theme ect.. can I click the 'workspace switcher' to a second workspace and put a different background, theme ect.. and have them stay like that?  so when i click the 3D button and they all slide back to choose the desktop/workspace, that i can pick between different backgrounds and theme one?  Does this make any sense or am I crazy??  :mrgreen:

---

### Post by anil_robo on 2006-04-20
[quote=x5452]is there a way to, and i hope this doesnt sound stupid, but say on my current desktop i have a background pic, with a certain gkrellm theme ect.. can I click the 'workspace switcher' to a second workspace and put a different background, theme ect.. and have them stay like that?  so when i click the 3D button and they all slide back to choose the desktop/workspace, that i can pick between different backgrounds and theme one?  Does this make any sense or am I crazy??  :mrgreen:[/quote]

You're making sense, at least to me.

What you're saying is a feature built-into KDE, but GNOME does not support this. However, there are some extra utilities which make this possible. I'm sorry I can't remember off-hand, but a little googling will get you there. That question was answered somewhere on these forums too.

---

### Post by illuzion on 2006-04-20
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

what should i do?

---

### Post by NakedGreekStatue on 2006-04-21
I got the same output as above. help?

---

### Post by anil_robo on 2006-04-21
[quote=NakedGreekStatue]I got the same output as above. help?[/quote]

Did you guys fiddle with XGL? Do you have 3D acceleration activated? I'm sorry I have limited competency in these areas - please google or search on these forums to check if your 3d acceleration is set up properly.

As a check, you can boot using live cd, and check if 3ddesktop works from there.

---

### Post by anil_robo on 2006-04-21
[quote=x5452]what exctly is the 3d desktop thing? I saw some screen shots, like the first post with three windows open, are those actual windows that just like rotate or something when you pick one to work in? or is it just a background type thing?[/quote]

3D desktop is an app that simply animates the switching of workplaces in Linux. It does not rotate actual windows or workspaces in its truest sense (XGL does that, 3ddesktop doesn't).

If you're looking for wobble effects and other spectacular 3d effects, you probably need XGL. I have resorted to 3d desktop because I couldn't configure XGL on my machine :mrgreen:

It's relatively easy to try out 3ddesktop - it won't break your system. But failed XGL tries have left my system broken totally, twice.

---

### Post by surfgeek on 2006-04-22
[QUOTE=endersshadow]For fun, try:

```
3ddesk --view=bigmoney
```

It's Price Is Right style!

Great HowTo![/QUOTE]

This is the best......:p

---

### Post by pompeyjohn on 2006-05-07
with regard to the question, is it possible to assign a different background to specific workspaces...

[QUOTE=anil_robo]
What you're saying is a feature built-into KDE, but GNOME does not support this. However, there are some extra utilities which make this possible. I'm sorry I can't remember off-hand, but a little googling will get you there. That question was answered somewhere on these forums too.[/QUOTE]

.... I cant find the answer!! can someone help please?

thanks

---

### Post by anil_robo on 2006-05-07
[quote=pompeyjohn]with regard to the question, is it possible to assign a different background to specific workspaces...
.... I cant find the answer!! can someone help please?

thanks[/quote]

You have few options to choose from:

1. Use KDE, and set different backgrounds for different workspaces.
2. Use Wallpapoz with Gnome ([http://www.gnomefiles.org/app.php?soft_id=104](http://www.gnomefiles.org/app.php?soft_id=104))


That's it for now. If I come to know anything else, I'll add it here. Have a great wekeend!

---

### Post by Xploit on 2006-05-10
[QUOTE=RaptorRaider]Is anyone else experiencing performance problems with 3ddesktop?

On my system, 3ddesktop takes up 200Mb of RAM and seems to entirely hang the system for 0.2 seconds every 2 seconds or so; it doesn't stop until I kill 3ddesk.[/QUOTE]

I got the same exact thing as you.  CPU usage also sits at 50% till I turn off 3ddesktop.  Using the ati 8.24.8 drivers.

System:  
Dell inspiron E1505
1.8ghz core duo
ati x1300 

Like I mentioned in another thread.  After I installed the new drivers.  My xorg.conf file shows 2 drivers for graphics. [Here]("http://ubuntuforums.org/showthread.php?t=172616") is the link to the post regarding that problem.  I wonder if this can cause any graphic "slowness"

---

### Post by oskvaz on 2006-05-13
No problems. It works great!!!

Athlon XP 2600
1 Gb RAM
nvidia GE Force fx5000

---

### Post by nieck on 2006-05-14
pff can't get it to work with the key-binding.
done everyting in the howto but when i press the windows-key nothing happend tryed also other key-bindings but it is not working:( 

what i'm i doing wrong ?? some settings ??

---

### Post by EdThaSlayer on 2006-05-14
Thanks! I kinda already downloaded this 3d desktop but didnt know the terminal commands! Thanks again!

---

### Post by AndreasHansen on 2006-05-15
i have a problem when i try to start 3ddesktop:
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

ive downloaded the lastest drivers for my videocard.
what is wrong and how do i fix it?

---

### Post by AndreasHansen on 2006-05-16
ok i got this problem now:
hansen@ubuntu:~$ 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddesk)

what is wrong?

---

### Post by nieck on 2006-05-18
i think your missing the libGL.so.1 lib.
so check off its on your system en cop too the /lib dir.

---

### Post by bon on 2006-05-19
have a few problems it gives this error - 
bon@Benz:~$ 3ddesk
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

bon@Benz:~$


this is my xorg.conf i was thinking it should have something in the device section for glx but not sure

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

---

### Post by Xploit on 2006-05-19
how do you set xbindkeys so it becomes a service, so that it automatically starts up everytime.

Also, is there a way to use --acquire in the config file, instead of manually typing "3ddesk --acquire" every single time I start the daemon.

---

### Post by blakegrover on 2006-05-23
I have a Dell Inspiron 9300 with the ATI X300 Mobility card and when I run 3ddesk to switch it locks up xorg and I have to switch to a terminal and kill 3ddeskd

the error it gives me is 

fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!


any help ?  I also have problems with fliipscreen3d screensaver with same error message

using the latest ati driver

Blake

---

### Post by blakegrover on 2006-05-25
Just so everyone who has a Dell Inspiron 9300 with the ATI card and wants 3ddesktop to work I just installed the latest ati driver  8.25.18 and it works great!!!!

---

### Post by galileon on 2006-06-06
hi all,
just installed dapper 64 on my newly built pentium d (2 * 3ghz), 1 gig ram etc

got it to work with a hotkey F4, but could not get the --acquire bit to run at startup - it looks like its loading in system>preference>session>startup and current session, but the others are still grey until i run the acquire bit in a terminal....

i've fixed that by assigning 3ddesk --acquire to another hot key - F3, but does anyone know why the startup bit isn't working?

cheers,

galileon

---

### Post by onesojourner on 2006-06-06
[QUOTE=galileon]hi all,
just installed dapper 64 on my newly built pentium d (2 * 3ghz), 1 gig ram etc

got it to work with a hotkey F4, but could not get the --acquire bit to run at startup - it looks like its loading in system>preference>session>startup and current session, but the others are still grey until i run the acquire bit in a terminal....

i've fixed that by assigning 3ddesk --acquire to another hot key - F3, but does anyone know why the startup bit isn't working?

cheers,

galileon[/QUOTE]

most of you might want to do the xgl/compiz instead of this. I have it installed on my 1.9 p4 and it runs better than 3ddesktop over did. 3ddesktop was always eating 10-20% of my cpu at idle. compiz doesnt seem to use any. =D>  compiz is "thefuture"... :rolleyes:

---

### Post by cajunaggie on 2006-07-16
Oooh! Shiney! But on a serious note, is there a way to map the windows key so that it runs 3ddesktop --acquire=X followed by 3ddesktop? In other words, two commands, sequentially?

---

### Post by Stirfry on 2006-07-16
Thanks it worked with no problem at all . Thanks much

---

### Post by kdragon on 2006-07-18
> 3ddesk --acquire=100
bash: 3ddesk: command not found

Help me.it cant run in my laptop
my laptop is GRZ530:p4 2.4G,512mb,7500 16mb vga

---

### Post by anil_robo on 2006-07-19
> **kdragon said:**
> Help me.it cant run in my laptop
my laptop is GRZ530:p4 2.4G,512mb,7500 16mb vga

1. Make sure you have all the repositories enabled. To do so, open your repositories file as root:
```
sudo gedit /etc/apt/sources.list
```
and remove the # signs before all the "deb" lines. Once you're done, save and close the file. Then, open a terminal window and enter this:
```
sudo apt-get update
```
Then you should have 3ddesktop in your repositories, ready to be installed.
2. To actually install 3d desktop, type this in a terminal window:
```
sudo apt-get install 3ddesktop
```
Watch the terminal window for any errors. If any, report them here.
3. Once you have installed the package 3ddesktop, you can run it by the command:
```
3ddesk
```

Regarding the hardware question, I was running this app very smoothly on a dell inspiron 1.73GHz, 1GB RAM. Yours should run fine too.

Hope it helps. Do let me know if any problems arise.

---

### Post by meney on 2006-07-31
ok, first of all I have to say this is AMAZING! I love it. Only one rough spot. Right after I installed 3ddesk, it worked super. After loggin-out and back in, I am all of a sudden getting an error.

Heres what its telling me when I type 3ddesk:

> 
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.


It was working perfect before my logout... what must I do now? Please help! :sad:

Edit: I did a restart and it seemed to fix the problem, not sure what prompted it in the first place though...

---

### Post by geektron on 2006-08-02
> **DCJoeDog said:**
> clear concise instructions, and got it up and runnig in short order, thank you very much

Ditto here. Thanks for the How To!

---

### Post by blent07 on 2006-08-14
pretty sweet stuff. of course, i had to try it.

I installed it, added it to my launch menu, ran it. It was sweet.

Of course, I'm not networked to anything.... so the other three screens are blank... 

Still makes you feel pretty cool, though. ;)

---

### Post by jr.gotti on 2006-08-15
When is this thread going to die...no disrespect to the develpment that went into this, but XGL/Compiz blows this to pieces...

---

### Post by Ramses de Norre on 2006-08-15
Not everyone likes/is able/wants to run XGL/Compiz..

---

### Post by Ice1532 on 2006-09-04
I just installed 3ddesktop and it work well but then i restarted my comp and i get an error message from it 
this is what i get:

ice@ice-Alchemy:~$ 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

and then i do what is tellsm me and i get this:

ice@ice-Alchemy:~$ 3ddeskd
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.

its a cycle... what is glXIsDirect??? any thoughts would help!!

---

### Post by Ice1532 on 2006-09-05
nvm i got it to work... dont know how but i got it to work

---

### Post by _savior_ on 2006-09-09
Hi,

> ice@ice-Alchemy:~$ 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration. Exiting.
Daemon started. Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

I get the same error. I think I have found out when this happens. I use XFCE (but I have also confirmed this in Gnome), and I added "3ddeskd --acquire=100" to "Autostarted Applications", so that it starts each time I log in to XFCE.

So when I first log in, it works fine. Then I press Ctrl+Alt+Backspace (or log out), and log in again. NOW I get the error above. I do not know why, but maybe it has something to do with 3ddeskd. It remains there after a logout, and possibly this causes problems with -- yeah, with what? I do not know exactly what happens if I press Ctrl+Alt+Backspace. Does the x server restart, or what? I tried to trace what happens (meddling with init scripts, including x11-common), but it does not seem to restart... Anyway, if I kill 3ddeskd before I log out (or execute 3ddesk --stop), it works on the next login, too!

So now I am looking for a way to kill the daemon process if I log out from XFCE or Gnome. Is there a way to do this?

Savior

---

### Post by jimmygoon on 2006-09-09
3ddeskd &
3ddesk

---

### Post by Melcar on 2006-09-09
Awesome.  I must confess that after a while the only reason I was still using XGL was because of the rotating desktop.  This option is much better suited for my laptop.

---

### Post by Not the man I once was on 2006-09-25
Greetings,

Firstly thank you for the How To Tutorial, it's absolutely excellent and I'm going to use it to configure my system. I'd like to know if this is at all BETA or Unstable software, as I've looked at the entry in the Synaptic Package Manager and it displays the Version available as "0.2.9-5.1Ubuntu1" and I don't under any circumstances install BETA software on my system for obvious reasoning.
I have an up-to-date NVIDIA GPU Driver installed and no previous system issues and I'd rather not resort to installing XGL if possible as I realise that this software is experimental and there are obvious risks associated with this although am I correct in stating that Ubuntu 6.06 "Dapper Drake" uses X.ORG 7.0?

Advice is most appreciated.

Regards,

Not the man I once was

---

### Post by anil_robo on 2006-09-25
> **Not the man I once was said:**
> I'd like to know if this is at all BETA or Unstable software, as I've looked at the entry in the Synaptic Package Manager and it displays the Version available as "0.2.9-5.1Ubuntu1" and I don't under any circumstances install BETA software on my system for obvious reasoning.
The [official website of 3ddesktop]("http://desk3d.sourceforge.net/") doesn't mention if it is a beta. Not every software that has version number less than 1.0 is a beta, and not every beta software has a version number less than 1.0. Beta versions are those that are still incomplete, in testing phase, and final tweaks are required before they can be passed on to the community. For example, Windows Vista was in Beta for quite some time, but GNU/Linux is not in Beta technically.

In a nutshell, 3ddesktop is safe in my opinion, but if you have more doubts, feel free to [contact the author of 3ddesktop.]("http://desk3d.sourceforge.net/feedback.php")

Further reading: 
[http://en.wikipedia.org/wiki/Beta_software](http://en.wikipedia.org/wiki/Beta_software)

---

### Post by Not the man I once was on 2006-09-28
Greetings,

I hadn't gotten time to browse the Author's SourceForge Web site but I managed to do so today and I'd like to notify everyone that this software application is currently listed as BETA and as such I'm not going to be installing it on my Primary Ubuntu installation for obvious reasons. I don't know why this wasn't noticed by anyone but browsing the SourceForge Project Web Page lists this as BETA.

Unfortunately I'm going to delay installing it until the Final build is released and relevant issues have been resolved before considering installing this application which in my opinion, given the gorgeous effect it boasts, is unfortunate.

Regards,

Not the man I once was

---

### Post by Melcar on 2006-10-03
> **Not the man I once was said:**
> Greetings,

I hadn't gotten time to browse the Author's SourceForge Web site but I managed to do so today and I'd like to notify everyone that this software application is currently listed as BETA and as such I'm not going to be installing it on my Primary Ubuntu installation for obvious reasons. I don't know why this wasn't noticed by anyone but browsing the SourceForge Project Web Page lists this as BETA.

Unfortunately I'm going to delay installing it until the Final build is released and relevant issues have been resolved before considering installing this application which in my opinion, given the gorgeous effect it boasts, is unfortunate.

Regards,

Not the man I once was


I have been using 3ddesk for a while now and the only complaint I have is that it always fails to acquire the desktop images at bootup, situation which is fixable by simply adding "3ddesk --acquire=100" to the session manager so it starts at every login.
One question... how do you map the Windows key to activate the desktop switcher under **_Kubuntu_**?  Any help would be appreciated.

---

### Post by meissen on 2006-10-11
I keep getting the error:

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

I have the libGL, and I tried:
brian@brian-laptop:/usr/lib$ glxinfo | grep "direct rendering"
direct rendering: No

Does this mean I can't do this with my Dell Inspiron E1505, ATI X1400 video card?

---

### Post by Leed on 2006-11-16
Runs great, but only when started with the sudo command.

without it says "demon started" but is not running.

with the command an error appears, but 3ddesk works fine
[FONT="Arial"]*libGL warning: 3D driver claims to not support visual 0x5b*[/FONT]

This is a problem because it prevents me from using the command in the session startup. If possible I'd like to avoid having to type in the whole thing after every boot

---

### Post by Leed on 2006-11-17
found a solution

create file

/etc/X11/gdm/PostLogin/Default

and insert code
```
#!/bin/sh
/usr/bin/3ddeskd --acquire 30
```

The acquire doesn't really work, screens are still gray until fist usage, but that doesn't really bother me.

---

### Post by aliyanage on 2006-11-18
Hi,

just wanted to ask whether this also works when having installed XGL, does XGL has any affect on this?

regards
aliyanage

---

### Post by comradexiactura on 2006-11-20
this looks really cool. i followed all of the directions and im getting an error  this is what happens:

basilio@basilio-desktop:~$ 3ddesk --acquire=100
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

im not sure what i should do any suggestions, thank you in advance.

---

### Post by meekon5 on 2008-10-13
This is great. I sat in the office giggling like a ten year old when I got this working.

---

### Post by durand on 2008-10-13
> **meekon5 said:**
> This is great. I sat in the office giggling like a ten year old when I got this working.

You do realise that this thread has been dead for nearly 2 years?
There is a neat effect in ubuntu which you can get by enabling desktop effects at System > Preferences > Appearance and going to the desktop effects tab.

---

### Post by ingridseynhaeve on 2009-09-01
Hi anil_robo,

I have worked on your trick but there is some problem occured during this trick.
When i try to switch to the 3D view desktop, the graphics not installed error appeared.
How can i solved it? Have you any idea about it? please, show me the way to solve the problem.

---

### Post by Bölvaður on 2009-09-01
> **ingridseynhaeve said:**
> Hi anil_robo,

I have worked on your trick but there is some problem occured during this trick.
When i try to switch to the 3D view desktop, the graphics not installed error appeared.
How can i solved it? Have you any idea about it? please, show me the way to solve the problem.
hmm....

**THIS THREAD IS 4 YEARS OLD **(this is in all caps but might be automatically changed)

There is no way that person will see your post unless if you are extraordinary lucky person wearing a necklace of 4 leaf clovers.

What you really want to do is abandon the idea to use this old program and look closer to what you already have (if you have a decent graphic card and a working driver, it is important the driver is working)

System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects (make sure they are on, but you do not need to put them to extra) 
Now click[ this link]("apt:compizconfig-settings-manager") or go into add/remove and search for CompizConfig settings manager.
Now go to System&#8594;Preferences&#8594;CompizConfig settings manager

Find 3d cube or what ever it is called. There are many interesting settings to play with.

---

