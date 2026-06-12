---
title: "HOWTO: Transparent borderless pop-up gnome-terminal"
date: 2005-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2005-06-02
**[COLOR="Red"]This guide is obsoleted. Please refer to [this one]("http://www.ubuntuforums.org/showthread.php?t=81727") instead. [/COLOR]**

at last i've figured out a way to do this. there are still some glitches / shortcomings though, but i'm hoping to smooth those out with the responses to this thread. [EDIT: The 0.60-1 version of Alltray has a --sticky option which makes the target application appear on all workspaces, so we no longer need devilspie or any other window matching function.]


1) download and install [alltray](http://alltray.sourceforge.net/). 

2) set up a new profile in gnome-terminal. i'll call the profile name "tterm" here, you call it whatever you fancy. edit the profile with the following options: uncheck the "show menubar by default in new terminals" option in the "general" tab, in the "effects" tab choose "transparent background" and set transparency level as you like, and in the "scrolling" tab, disable the scrollbar.

3) create a launcher with the following command:
```
alltray --borderless --sticky "gnome-terminal --window-with-profile=tterm"
```
theoretically you can add a --geometry option to the line to determine where the window will pop up, but i haven't got this to work. maybe it's an alltray issue; gnome-terminal just won't obey my orders while launching with alltray. if you want to fiddle with this you can find the x window server geometry specification in the manpage for x; i find it easier to just move the window to wherever i want it to stay, since it has to be done just once per session.

4) double click the launcher, position the window, click the tray icon, and viola.

[COLOR="Red"][EDIT: The below section is outdated and I'm keeping it here for the sake of not losing context in the replies. It's safe to ignore.][/COLOR]
[SIZE="1"]now my major complaint with this method: i just can't get devilspie to hide gnome-terminal from the task list and workspace pager, and put it in all workspaces. in short devilspie won't recognize gnome-terminal at all with neither the window_title nor the application_name properties. i've tried setting different titles, without luck. maybe this has something to do with the "(AllTray)" suffix added by alltray? 

this is not a biggie though, because this method is meant to provide a pop-up terminal, and since the tray icon is always fixed on the panel there's no real need to make it appear in all workspaces. and the task list item only appears when the terminal is up, so it doesn't take up space all the time. so, not to get bugged by these issues, close down the terminal when you're done with it, and open it again when you need it; it just takes a click  :smile: 

hope you find this useful. and devilspie hackers: help me sort the minor quirk out![/SIZE]

---

### Post by keffo on 2005-06-03
may we have a little eye-candy shot?

---

### Post by xristos on 2005-06-03
Very nice . Worked out of the box !

---

### Post by benplaut on 2005-06-03
[QUOTE=keffo]may we have a little eye-candy shot?[/QUOTE]

please?  :-P

---

### Post by xristos on 2005-06-03
Here it is...

---

### Post by benplaut on 2005-06-03
[QUOTE=xristos]Here it is...[/QUOTE]

SWEET!!!

i'm installing right now!  :grin:

<<EDIT>>

another screenie:

[[IMG]http://img96.echo.cx/img96/4720/terminalclear9ca.th.png[/IMG]](http://img96.echo.cx/my.php?image=terminalclear9ca.png)

this thing is awesome!

---

### Post by allforcarrie on 2005-06-03
I would get to confused.... but it does look nice.=D>

---

### Post by 23meg on 2005-06-03
i set mine up to work on the upper right hand corner, since that's where my notification area lies, and thus the icon is placed there, so i can just click the icon to show/hide the terminal, and it drops down just under the pointer. see the attached screenshot.

---

### Post by benplaut on 2005-06-03
[QUOTE=23meg]i set mine up to work on the upper right hand corner, since that's where my notification area lies, and thus the icon is placed there, so i can just click the icon to show/hide the terminal, and it drops down just under the pointer. see the attached screenshot.[/QUOTE]

screenshot...  :roll:  (never mind, there now  ;-) )

you mean like this?

[[IMG]http://img95.echo.cx/img95/1711/second8sp.th.png[/IMG]](http://img95.echo.cx/my.php?image=second8sp.png)

---

### Post by 23meg on 2005-06-03
yes, like that.. can you not see my screenshot? that's weird.

---

### Post by benplaut on 2005-06-03
[QUOTE=23meg]yes, like that.. can you not see my screenshot? that's weird.[/QUOTE]

caught your post before the edit... got it now  ;-)

---

### Post by 23meg on 2005-06-03
ok, must be fine after reuploading. 

here's a reminder for those who may not be aware of it: you can hit alt and drag any window to move it without needing a title bar; this helps with placing borderless windows where you want. you can change this behavior in system / preferences / windows.

---

### Post by mike998 on 2005-06-03
[QUOTE=23meg]ok, must be fine after reuploading. 

here's a reminder for those who may not be aware of it: you can hit alt and drag any window to move it without needing a title bar; this helps with placing borderless windows where you want. you can change this behavior in system / preferences / windows.[/QUOTE]

My God, Man....  Do you know how long I have been looking for this?
Thank you !

---

### Post by DFreeze on 2005-06-03
Nice looks!

This one is for xristos: How did you get your upper panel completely transparent? I'm looking for a way to get that too!

---

### Post by ubuntu_demon on 2005-06-03
it's nice!

too bad it's not real transparant. When I have it above firefox I see my wallpaper (and not firefox) through it.

---

### Post by 23meg on 2005-06-03
is it possible to have "real transparency" for any window with xcompmgr? not that i'd make use of it, just wondering.

---

### Post by xristos on 2005-06-03
[QUOTE=DFreeze]Nice looks!

This one is for xristos: How did you get your upper panel completely transparent? I'm looking for a way to get that too![/QUOTE]
Right click on the panel ---> properties

---

### Post by benplaut on 2005-06-03
[QUOTE=xristos]Right click on the panel ---> properties[/QUOTE]

and then hope that your applets don't get in the way  :roll:

---

### Post by pdk001 on 2005-06-03
oh awsome, i will try it right away

---

### Post by pdk001 on 2005-06-03
double click the launcher, position the window, click the tray icon, and viola. <--this meaning?

---

### Post by banditti on 2005-06-04
I get the following, what am I doing wrong?

(gnome-terminal:8603): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by 23meg on 2005-06-04
when + where exactly are you getting this?

---

### Post by mattack on 2005-06-05
Wow! This is sweet! Thanks.
What's the syntax for the --geometry option to determine where the window pops up?

---

### Post by 23meg on 2005-06-05
type "man x" and scroll down to the title "geometry specification".

---

### Post by mattack on 2005-06-05
[QUOTE=23meg]type "man x" and scroll down to the title "geometry specification".[/QUOTE]
 I did that, but like you I can't get a terminal to open up anywhere but the upper left hand corner...
I wonder how other folks got it to open in other places.

---

### Post by infinito on 2005-06-05
[QUOTE=23meg]i set mine up to work on the upper right hand corner, since that's where my notification area lies, and thus the icon is placed there, so i can just click the icon to show/hide the terminal, and it drops down just under the pointer. see the attached screenshot.[/QUOTE]
 What command do you use to put the terminal on the upper right corner??
I use: gnome-terminal --geometry=-0+0, but alltray overrides this...

---

### Post by 23meg on 2005-06-05
that's right, this must be an alltray problem. it's not difficult to just alt+click anywhere in the gnome-terminal window to move it anywhere you like though. if you want a visual cue as to the exact size of the window (since it's borderless), just right click and choose "show menubar" and close down the menubar later when you're done with it.

---

### Post by Sionide on 2005-06-05
Funky little HOWTO, I like it very much. Hooray for eye candy!

---

### Post by infinito on 2005-06-05
[QUOTE=23meg]that's right, this must be an alltray problem. it's not difficult to just alt+click anywhere in the gnome-terminal window to move it anywhere you like though. if you want a visual cue as to the exact size of the window (since it's borderless), just right click and choose "show menubar" and close down the menubar later when you're done with it.[/QUOTE]
 I reported a bug on Alltray project site, so I hope this will be fixed soon.

---

### Post by ante0 on 2005-06-05
[QUOTE=23meg]ok, must be fine after reuploading. 

here's a reminder for those who may not be aware of it: you can hit alt and drag any window to move it without needing a title bar; this helps with placing borderless windows where you want. you can change this behavior in system / preferences / windows.[/QUOTE]

Hah, i was just about to post this ALT+drag thing, oh well, now i dont need too  :grin:

---

### Post by lizardking on 2005-06-06
So the geometry sintax  does not work i have this however:
```
alltray --borderless "gnome-terminal --window-with-profile=bg --geometry 120x25-170-300 --zoom 0.9" 
``` 

Only a problem **i Have save the code up in the Gnome session starter** with other apps (gdesk gnome clipoard etc) **but alltry is running but not displayed**...
This is the program running:
[IMG]http://www.iacopomasi.net/session.png[/IMG] 
**[SIZE=3]But in the gnome tray there is not a terminal icon...[/SIZE] ** ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by 23meg on 2005-06-06
did you try assigning a different "order" number to it? this usually solves such problems.

---

### Post by lizardking on 2005-06-06
[QUOTE=23meg]did you try assigning a different "order" number to it? this usually solves such problems.[/QUOTE]
I prove a lot of order..Now i have** 150** in the way that gnome tray is already on when alltry started

---

### Post by XDevHald on 2005-06-06
Nice trick, and someone might want to tell the owner of [http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)  that there faq link has a "g" instead of a "q" for faq :p

---

### Post by X3N on 2005-06-08
I've just compiled this on x86_64 ( obviously as the i386 binary is 32bit ) .
One thing that caught me out was that ./configure doesn't fail when it should. libxmu-dev (which provides /usr/X11R6/include/X11/Xmu/WinUtil.h )  package is needed to "make" this program. (you'll find it in the repisitories)

---

### Post by Sionide on 2005-06-10
Hm, I still can't get this to start when I login, I've set the order to 150 - is that still too low?

---

### Post by simonkitch on 2005-06-10
[QUOTE=23meg]i set mine up to work on the upper right hand corner, [/QUOTE]

How do you do that? Mine defaults to the left.

---

### Post by lizardking on 2005-06-10
[QUOTE=Sionide]Hm, I still can't get this to start when I login, I've set the order to 150 - is that still too low?[/QUOTE]
me too same problem

---

### Post by 23meg on 2005-06-10
hmm that is an alltray issue as well, perhaps.

---

### Post by jebe on 2005-06-13
hi,

as the author from alltray i can may help out here a little :)

*Session managament is not (yet) supported. make a bash script with the program you would like to start and add this script to "Additional startup programs"

*to use the geometry stuff, use the geometry option provided by alltray
(version >0.54)

*--borderless option will not work with 0.54 version anymore
(only if the program support it native) maybe i find a solution to add it again


@ XEN and BB: thanks i will correct this ,)


jebe

---

### Post by lizardking on 2005-06-14
[QUOTE=jebe]hi,

as the author from alltray i can may help out here a little :)

*Session managament is not (yet) supported. make a bash script with the program you would like to start and add this script to "Additional startup programs"

jebe[/QUOTE]
Can you post the script?

---

### Post by Sionide on 2005-06-14
Something along the lines of;

```

#!/bin/bash
alltray --borderless "gnome-terminal --window-with-profile=trans"
```

Save as 'term.sh' and add that to your sessions.

---

### Post by SpEcIeS on 2005-06-14
[QUOTE=23meg]at last i've figured out a way to do this. there are still some glitches / shortcomings though, but i'm hoping to smooth those out with the responses to this thread.

1) download and install [alltray](http://alltray.sourceforge.net/).the debian sid package works with ubuntu.

2) set up a new profile in gnome-terminal. i'll call the profile name "tterm" here, you call it whatever you fancy. edit the profile with the following options: uncheck the "show menubar by default in new terminals" option in the "general" tab, in the "effects" tab choose "transparent background" and set transparency level as you like, and in the "scrolling" tab, disable the scrollbar.

3) create a launcher with the following command:
```
alltray --borderless "gnome-terminal --window-with-profile=tterm"
```
theoretically you can add a --geometry option to the line to determine where the window will pop up, but i haven't got this to work. maybe it's an alltray issue; gnome-terminal just won't obey my orders while launching with alltray. if you want to fiddle with this you can find the x window server geometry specification in the manpage for x; i find it easier to just move the window to wherever i want it to stay, since it has to be done just once per session.

4) double click the launcher, position the window, click the tray icon, and viola.

now my major complaint with this method: i just can't get devilspie to hide gnome-terminal from the task list and workspace pager, and put it in all workspaces. in short devilspie won't recognize gnome-terminal at all with neither the window_title nor the application_name properties. i've tried setting different titles, without luck. maybe this has something to do with the "(AllTray)" suffix added by alltray? 

this is not a biggie though, because this method is meant to provide a pop-up terminal, and since the tray icon is always fixed on the panel there's no real need to make it appear in all workspaces. and the task list item only appears when the terminal is up, so it doesn't take up space all the time. so, not to get bugged by these issues, close down the terminal when you're done with it, and open it again when you need it; it just takes a click  :smile: 

hope you find this useful. and devilspie hackers: help me sort the minor quirk out![/QUOTE]
Is this the dev-snap, 0.54, or the 0.51 deb package you are referring to? I am having difficulties moving the terminal using 0.51, so now I am building the 0.54 version. :) Otherwise it is a really nice feature. :)

Edit:
Uh..  never mind..  I guess it helps when I read all of the posts.  :roll:

---

### Post by luiska on 2005-06-15
Hi

Here is the command for my terminal:

alltray  --borderless "gnome-terminal --window-with-profile=tterm --geometry=135x42+30+200"

Makes it full screen

Luiska

---

### Post by SpEcIeS on 2005-06-15
[QUOTE=luiska]Hi

Here is the command for my terminal:

alltray  --borderless "gnome-terminal --window-with-profile=tterm --geometry=135x42+30+200"

Makes it full screen

Luiska[/QUOTE]
Thanks for the help, but I am not having much luck with the --geometry option. The terminal will, if geometry is applied, will only be located in the upper left corner and stretched down to the bottom of the screen. :?  I have tried different combinations, but same or none desirerable results occur.

Currently I am using 0.51 deb package, however I did compile the 0.54 version, but the borderless option does not seem to work. Upon this discovery it was removed and the latter version applied. Other than that, 0.54 is a nice application.

What do I need to do to make my terminal box, using 0.51, in the upper right corner and say 120x53? After spend a lot of time trying different things out and coming up with the same results, I have concluded I do not know what I am doing, or --geometry simply does not work properly in the alltray application.  :smile:

---

### Post by dkitty on 2005-06-15
I haven't had much luck with geometry options either. However, the first window I open is automatically centered on the desktop. I imagine there's an option somewhere that sets how/ where windows are positioned on the desktop by default when they first open. Anyone know what that option might be or how to access it?

By using Sionide's (may I call you CN?) bash file startup thang I've been able to assure that the transparent terminal is the first window.

[QUOTE=Sionide]Something along the lines of;

```

#!/bin/bash
alltray --borderless "gnome-terminal --window-with-profile=trans"
```

Save as 'term.sh' and add that to your sessions.[/QUOTE]

Once I had term.sh I hid it away so I wouldn't putz with it. I selected "View > Show Hidden Files" from Nautils and stashed term.sh it in the .Gnome2 folder in my home directory. I then made the bash file executable.

```
chmod +x /home/tara/.Gnome2/term.sh
```

Now the terminal icon shows up in the panel via alltray when I start a session and is automatically set to the center of my desktop. Screenie below... thought be warned that my background/ wallpaper isn't work safe.  :grin:

---

### Post by luiska on 2005-06-15
Hi

I got it to look like I wanted it by trail and error, opened and closed that terminal about 200 times.....

geometry=135x42+30+200

I understand it as follows: 
135x42 is the size and +30+200 is the postition.

Although I must admit that it still rather seem to be adding right to the top left corner. 

Luiska

---

### Post by Sionide on 2005-06-15
I just move it each time to the middle of the screen heh Alt+Drag works wonders. It remembers that position til next time I reboot but that's no big problem. Perhaps I'll figure it out one day!

---

### Post by jebe on 2005-06-15
[QUOTE=luiska]Hi

I got it to look like I wanted it by trail and error, opened and closed that terminal about 200 times.....

geometry=135x42+30+200

I understand it as follows: 
135x42 is the size and +30+200 is the postition.

Although I must admit that it still rather seem to be adding right to the top left corner. 

Luiska[/QUOTE]

you can move the window to the desired position and then call

 xwininfo | grep "geometry"

this will output the geometry string.

note: alltray --geometry option only works with positive values


jebe

---

### Post by SpEcIeS on 2005-06-15
Yeah, I do not believe that the positioning options work, but the sizing of the terminal seems to work. It would seem that using the ALT+ dragging the terminal is the only option to position it. Looks nice though.  :smile:

---

### Post by Sionide on 2005-06-26
[QUOTE=jebe]you can move the window to the desired position and then call

 xwininfo | grep "geometry"

this will output the geometry string.[/QUOTE]

Wow! That worked... Great!!!

Ok, so now I have the terminal starting up when I login, but I also need it to automatically quit before the system shuts down, the reason is because Gnome/whatever treats it as an open terminal and that's all and next time I boot up or log back in, it starts up the alltray terminal AND another terminal.

Hrm...

---

### Post by royg1234 on 2005-06-26
[QUOTE=benplaut]SWEET!!!

i'm installing right now!  :grin:

<<EDIT>>

another screenie:

[[IMG]http://img96.echo.cx/img96/4720/terminalclear9ca.th.png[/IMG]](http://img96.echo.cx/my.php?image=terminalclear9ca.png)

this thing is awesome![/QUOTE]

Is there a way to get real transperency?  The way it works now seems like it just draws the desktop background as the app's background.

---

### Post by Sionide on 2005-06-26
Surely that's better?? If it was "really" transparent, you might have your Firefox window underneath with a load of text and then your terminal is text so you'd be trying to read one lot of text with another lot right underneath - which is very difficult. Having it transparent this way just [gives your terminal a cool background.](http://www.sionide.net/gallery/albums/pics/Screenshot_001.png)

---

### Post by Bicky on 2005-06-28
is there a way to run alltray as demon ?

---

### Post by infinito on 2005-06-28
[QUOTE=Bicky]is there a way to run alltray as demon ?[/QUOTE]
 You should run it from your gnome session. Just add the command you want to the gnome session startup programs. I think this is wgat you want...

---

### Post by bored2k on 2005-06-29
This is a very nice trick. Alltray definitely improves my desktop's usability (terminal + nautilus allways in tray = hands down awsome).

---

### Post by piedamaro on 2005-06-29
I came up with this hack: I use xmacro to move the terminal in place after it pops up. Here is the script:
```
#!/bin/sh

alltray -s -x "gnome-terminal --window-with-profile=translucent"&
sleep 3
echo -e "KeyStrPress Alt_L \n
        KeyStrPress F7 \n
        KeyStrRelease F7 \n
        KeyStrRelease Alt_L \n
        KeyStrPress Shift_L" | xmacroplay :0
for i in `seq 1 3`; do
        echo -e "KeyStrPress Right \n
                KeyStrRelease Right \n" | xmacroplay :0
done
echo -e "KeyStrRelease Shift_L \n
        KeyStrPress Return \n
        KeyStrRelease Return \n" | xmacroplay :0
exit 0

``` 

You can see the result in the attached sample video cap. Enjoy :)

---

### Post by dolny on 2005-06-29
Hmm... here's mine, normal - transparent, borderless gnome-terminal without HOWTO: [http://www.echostar.pl/~dolny/ubu/zrzut17.jpg](http://www.echostar.pl/~dolny/ubu/zrzut17.jpg) - I'm using KDE, but can't do the same with Konsole (the borders stay on their place even though I choose to hide them).

One's again, link: [http://www.echostar.pl/~dolny/ubu/zrzut17.jpg](http://www.echostar.pl/~dolny/ubu/zrzut17.jpg)

---

### Post by Skel on 2005-07-02
piedmara awesome hack make smy terminal turninto a transparent on.. how can i get this to start at starup  along with alltray i cant seem to get Nohup Alltray & to stick...

---

### Post by piedamaro on 2005-07-02
As you can see I use simply:
alltray "gnome-terminal...." &
and it seems to work :)

---

### Post by niels2005 on 2005-07-04
hey very nice desktop
and then I saw the little skype icon on your panel,
how did you get it there ?
sorry i am newbie
niels

---

### Post by jebe on 2005-07-04
hi,

i made a new allltray release. --geometry and --borderless option should work fine now

[http://alltray.sourceforge.net/downloads.html](http://alltray.sourceforge.net/downloads.html) (dev snap)

alltray "gnome-terminal --window-with-profile=test" -x -g +700+50


jebe

---

### Post by raakken on 2005-07-15
why is the launcher created? what does it do? it went transparent before I installed the launcher

---

### Post by jago25_98 on 2005-07-20
I have kde with ctrl+return set to open new term and alt+x for run dialog

---

### Post by nickless on 2005-07-20
Ahhh this is just too nice :D
One little thing interessts me thought. Is there, like a command or something like that, to toggle showing the window and hiding it? I would love to just push a button to toggle this :)

---

### Post by bored2k on 2005-07-20
[QUOTE=][/QUOTE]
 You just "push" or click on the icon tray and it goes away.. I believe.

---

### Post by nickless on 2005-07-20
Yeah I click, but I want to use the keyboard :) , thats what I meant with "push a button"

---

### Post by jebe on 2005-07-21
[QUOTE=nickless]Yeah I click, but I want to use the keyboard :) , thats what I meant with "push a button"[/QUOTE]

no not yet possible

---

### Post by jebe on 2005-07-21
to dock gnome-terminal without being visible for a moment:


alltray "gnome-terminal --disable-factory --window-with-profile=test" -x -g +700+50

this will open a gnome-terminal with his own process (not attached to the first terminal)


jebe

---

### Post by Shwiing on 2005-08-02
Well I am kinda getting annoyed with this fix, here are some things I would really like help on.

1) How do I get it to run when I open a session and pop up on my screen?
   - I tried adding it to system->preferences->sessions->startup programs but never worked

2) How do I keep it below all other windows?

3) How do I delete my current startup because I saved it once on shutdown and it will never change.

Thanks

---

### Post by dkitty on 2005-08-02
1) Look [two pages earlier in this thread](http://www.ubuntuforums.org/showpost.php?p=214410&postcount=45) to have the borderless, transparent terminal load in alltray at the beginning of a session.

2) I'm not sure exactly what you mean. Maybe check the [HOWTO: Terminal for desktop background](http://www.ubuntuforums.org/showthread.php?t=36811) thread.

3) Check the [Gnome login fails](http://www.ubuntuforums.org/showthread.php?t=33165) thread.

---

### Post by Shwiing on 2005-08-02
[QUOTE=dkitty]1) Look [two pages earlier in this thread](http://www.ubuntuforums.org/showpost.php?p=214410&postcount=45) to have the borderless, transparent terminal load in alltray at the beginning of a session.

2) I'm not sure exactly what you mean. Maybe check the [HOWTO: Terminal for desktop background](http://www.ubuntuforums.org/showthread.php?t=36811) thread.

3) Check the [Gnome login fails](http://www.ubuntuforums.org/showthread.php?t=33165) thread.[/QUOTE]

1) thats what i've been trying, but after fiddling with it, got it to work.

2) still cant find out a way to make it a permanent bottom window.

3) thanks that helped a lot!

---

### Post by dkitty on 2005-08-02
1) What did you do differently to add it to a session Schwiing? I'm all curious now.

2) I'm still not quite sure what you mean by having the terminal as a permanant bottom window. Do you mean at the bottom of the screen (on the y axis) or do you mean positioned behind all other windows that show up (on the z axis)?

3) Kew. At least I could help with one out of three.  ^_^

---

### Post by Shwiing on 2005-08-02
[QUOTE=dkitty]1) What did you do differently to add it to a session Schwiing? I'm all curious now.

2) I'm still not quite sure what you mean by having the terminal as a permanant bottom window. Do you mean at the bottom of the screen (on the y axis) or do you mean positioned behind all other windows that show up (on the z axis)?

3) Kew. At least I could help with one out of three.  ^_^[/QUOTE]

1) Forgot to add sh to the command in the session: sh /location/term.sh

2) I meant the second thing you said, that its positioned behind all other windows

---

### Post by PsyberOneZero on 2005-08-03
I've got an interesting problem, I've got a dual monitor setup and I want the term on the 2nd screen.  I've got the geometry but I cant get it to start on the 2nd display. any help?

---

### Post by jebe on 2005-08-04
[QUOTE=PsyberOneZero]I've got an interesting problem, I've got a dual monitor setup and I want the term on the 2nd screen.  I've got the geometry but I cant get it to start on the 2nd display. any help?[/QUOTE]


i have no dual monitor so i can not do/test this

cu jebe

---

### Post by Heli0s on 2005-08-04
I cant seem to get the --borderless option to work, and i dont get an icon any where. But i also dont get an error :S

---

### Post by seanroth on 2005-08-05
Oh, this is great! Worked perfectly. :)

---

### Post by myha on 2005-08-09
[QUOTE=luiska]Hi

Here is the command for my terminal:

alltray  --borderless "gnome-terminal --window-with-profile=tterm --geometry=135x42+30+200"

Makes it full screen

Luiska[/QUOTE]
 \\:D/ It works now....   \\:D/ 
thanks!

---

### Post by manicka on 2005-08-09
[QUOTE=Heli0s]I cant seem to get the --borderless option to work, and i dont get an icon any where. But i also dont get an error :S[/QUOTE]
 An icon should appear in your systray

---

### Post by atilasendil on 2005-08-09
thanks a lot for all posts :-)
made my way through reading all again and again :-)
sorry for being a noob but :
although --geometry works generally how do I get it to open at exact top-right corner?
I open my cool transparent borderless terminal and move it to top-right and do:
*$ xwininfo | grep "geometry"*
and get :
* -geometry 80x24-0+25*
but when I try :
*alltray --borderless "gnome-terminal  --disable-factory --window-with-profile=tterm --geometry 80x24-0+25"*
it opens at :
[I]$ xwininfo | grep "geometry"
  -geometry 80x24-10+25[/I]

anyone with same problem ?

---

### Post by Razman on 2005-08-18
I do not get anything, when I click on the launcher, it looks like a window appears, very briefly and then disappears.

I then ran the command in a term window...(though the error may be due to window being open?)
what I get run...

# alltray --borderless "gnome-terminal --window-with-profile=tterm"

and I get the following
> Alltray: no system tray/notification area found.
I will wait........ I have time....

In the meantime you may add a system tray applet to the panel.

any ideas why this happens?
Thanks.

---

### Post by manicka on 2005-08-19
[QUOTE=Razman]
any ideas why this happens?
Thanks.[/QUOTE]

Do you have a systray (notification area) running on your panel? If not, add one.

---

### Post by Razman on 2005-08-19
[QUOTE=manicka]Do you have a systray (notification area) running on your panel? If not, add one.[/QUOTE]
 Ok... I did that.

This is the error now.
> :~$ alltray --borderless "gnome-terminal --window-with-profile=tterm"

** ERROR **: file gnome_theme.c: line 194 (parse_theme): assertion failed: (theme_name)
aborting...
Aborted


---

### Post by manicka on 2005-08-19
I'm only guessing. What happens if you temporarily change your gnome theme (say to the default) and try to run it again?

---

### Post by Razman on 2005-08-19
[QUOTE=manicka]I'm only guessing. What happens if you temporarily change your gnome theme (say to the default) and try to run it again?[/QUOTE]
 Same thing! :(

but!
When I switched back to the "Human" theme... it is now working!

Thanks!!

---

### Post by arnieboy on 2005-08-19
This is what I have done: installed the latest alltray autopackage from [http://alltray.sourceforge.net/downloads.html](http://alltray.sourceforge.net/downloads.html) and I use the following command:
```
alltray --geometry 500x300+220+200 --borderless "gnome-terminal --hide-menubar --window-with-profile=tterm"
```
works perfectly for me!

---

### Post by myha on 2005-08-20
Hi!

Can anyone tell me how to disable xcompmngr for certain window?
I have desktop terminal and it drops shadow, and it kinda bothers me, so i would like to have just this window without xcompmngr effects.

Thank you,
Miha

---

### Post by 23meg on 2005-08-21
wow, the new alltray release fixed another major issue with this method for me: now i can drag and drop files from nautilus into the borderless terminal window and the URI gets pasted on the prompt immediately! with the former release this didn't work when the window was borderless. i recommend everyone to upgrade to 0.60 just for this conveinence. thanks a lot jebe.

---

### Post by bionnaki on 2005-08-23
hello. I am trying to install alltray, but I am running into some trouble.

> Preparing to replace alltray 0.60-1 (using alltray.debian_0.60-1_i386.deb) ...
Unpacking replacement alltray ...
dpkg: dependency problems prevent configuration of alltray:
 alltray depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing alltray (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alltray 

so, what should I do?
thanks!

---

### Post by arnieboy on 2005-08-23
[QUOTE=bionnaki]hello. I am trying to install alltray, but I am running into some trouble.

 

so, what should I do?
thanks![/QUOTE]
go to [http://alltray.sourceforge.net/downloads.html](http://alltray.sourceforge.net/downloads.html) and download alltray-0.60.x86.package and install it.  its an autopackage. it will install flawlessly and  wont bother u with dependencies which the deb package will since its looking for the latest lib files which ubuntu doesnt have currently in its repos.

---

### Post by bionnaki on 2005-08-23
thanks!

what a cool installation.
works like a charm.

---

### Post by arnieboy on 2005-08-23
[QUOTE=bionnaki]thanks!

what a cool installation.
works like a charm.[/QUOTE]
hey u are welcome :)

---

### Post by twodogs on 2005-08-27
ok, this is really cool.  i just installed Ubuntu 3 days ago and it rocks.

I downloaded Altray. but how do I install it. In windows, I would just click icon.
Do I install Altray in the terminal with 'sudo apt-get install...?'

Thanks for your help.

---

### Post by manicka on 2005-08-27
[QUOTE=twodogs]ok, this is really cool.  i just installed Ubuntu 3 days ago and it rocks.

I downloaded Altray. but how do I install it. In windows, I would just click icon.
Do I install Altray in the terminal with 'sudo apt-get install...?'

Thanks for your help.[/QUOTE]
 In a terminal, change to the directory you downloaded the deb to, then

sudo dpkg -i alltray.ubuntu_0.60-1_i386.deb

---

### Post by elgx on 2005-09-05
why does it give me this answer? look here:

> elena@elena-ubuntu:~$ alltray --borderless "gnome-terminal --window-with-profile=tterm"
Failed to read gconf file /home/elena/.gconf/apps/metacity/general/%gconf.xml: Apertura del file "/home/elena/.gconf/apps/metacity/general/%gconf.xml" fallita: No such file or directory
*** parsing theme failed ! oh oh ***
elena@elena-ubuntu:~$

can i solve it somehow, installing sth missing (via synaptic or via the shell, it's all accepted ^^)?
thank you, it is a nice trick!

---

### Post by jebe on 2005-09-07
[QUOTE=elgx]why does it give me this answer? look here:



can i solve it somehow, installing sth missing (via synaptic or via the shell, it's all accepted ^^)?
thank you, it is a nice trick![/QUOTE]

start "gconf-editor" go to "/apps/metacity/general" change the Theme to another.
...or wait for a new release tomorrow ;)

jebe

---

### Post by pinoyskull on 2005-09-28
nice one, i like it a lot :)

---

### Post by kingsidy on 2005-10-03
this thing is cool. here is mine. it goes well with my mac os theme
[ATTACH]2688[/ATTACH]

---

### Post by DREMA on 2005-10-06
[QUOTE=myha]Hi!

Can anyone tell me how to disable xcompmngr for certain window?
I have desktop terminal and it drops shadow, and it kinda bothers me, so i would like to have just this window without xcompmngr effects.

Thank you,
Miha[/QUOTE]

Does anybody have the answer for this ???
Tnks

---

### Post by Mustard on 2005-10-07
I'm getting a dependency error.  Apparently my libc6 is not a high enough version.

```
mustard@slave:~$ sudo dpkg -i alltray.debian_0.60-1_i386.deb
Selecting previously deselected package alltray.
(Reading database ... 61892 files and directories currently installed.)
Unpacking alltray (from alltray.debian_0.60-1_i386.deb) ...
dpkg: dependency problems prevent configuration of alltray:
 alltray depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing alltray (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alltray
mustard@slave:~$

```

I try installing libc6 and I get this...

```
mustard@slave:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  alltray: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mustard@slave:~$

mustard@slave:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  alltray
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 158kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 61905 files and directories currently installed.)
Removing alltray ...

mustard@slave:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
mustard@slave:~$


```

Here is my source.list

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

---

### Post by brt on 2005-10-07
the howto didn't work for me too because i use breezy on an AMD64,
i had to compile it from source:

this installs the compiler and needed libraries:
```
sudo apt-get install build-essential libgtk2.0-dev
```

download, compile and install:
```
cd /tmp
wget http://puzzle.dl.sourceforge.net/sourceforge/alltray/alltray-0.62.tar.gz
tar -xzf alltray-0.62.tar.gz
cd alltray-0.62
./configure
make
sudo make install
```

and everything works!! wohooo :D

---

### Post by ztrikker on 2005-10-07
This is my first post so be gentle :) 

I got the geometry to work perfectly i used this command line to put the window in the lower corner of my 1600x1200 display 

**alltray --show --geometry 750x460+850+715 --borderless "gnome-terminal --window-with-profile=tterm" **

Using the geometry setting in gnome-terminal wasn't working properly for me so i forced the geometry with the all try command and that did the trick, plus it doesnt minimize when i launch it.

---

### Post by delaguer on 2005-10-11
thanks for the HowTo. works great! 

del :cool:

---

### Post by 23meg on 2005-10-21
i've just tried using this method with the transset utility of the x composite extension to get **real** transparency as opposed to the pseudo-transparency of gnome-terminal, and it looks very cute. see the attached screenshot.

---

### Post by 23meg on 2005-10-22
now i'm trying to get this working in xfce with gnome-panel, but alltray just won't appear in the notification area. can anyone replicate this in xfce?

---

### Post by kroiz on 2005-10-28
when running ```
alltray --borderless --sticky "gnome-terminal --window-with-profile=tterm"
```

I get
```
profile=tterm"
Failed to read gconf file /home/kroiz/.gconf/apps/metacity/general/%gconf.xml: Failed to open file '/home/kroiz/.gconf/apps/metacity/general/%gconf.xml': No such file or directory
*** parsing theme failed ! oh oh ***

```

I dont have a directory called metacity.
btw I use breezy.

---

### Post by 23meg on 2005-11-15
[COLOR="Red"]This guide is obsoleted. Please refer to [this one]("http://www.ubuntuforums.org/showthread.php?t=81727") instead.[/COLOR]

---

