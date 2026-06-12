---
title: "How to run a script at startup?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-05-17
I'm trying to run a script at startup to keep my screen from blanking every 10 minutes.  The script works just fine, when I execute it manually it disables DPMS.  Getting it to run at startup is proving to be a problem though.  The script name is .dpms-off and it's located in my home directory.  Here's what I've tried (owner is my username):

1 - Placing a copy of the script file in: /home/owner/.config/autostart
This works for pidgin instant messenger, but doesn't seem to work for the script.

2 - Placing an autostart file in: /home/owner/.config/lxsession/Lubuntu
And in the autostart file putting: @/home/.dpms-off

3 - Placing an autostart file in: /home/owner/.config/openbox
And in the autostart file putting: @/home/.dpms-off

4 - Editing the autostart file in: /etc/xdg/openbox
To include @/home/.dpms-off

5 - Editing the autostart file in: /etc/xdg/lxsession/Lubuntu
To include @/home/.dpms-off

6 - Editing the autostart file in: /etc/xdg/lxsession/LXDE
To include @/home/.dpms-off

7 - Placing a copy of the script file in: /etc/xdg/autostart
And checking the desktop session settings to see if the file is listed in there, but it's not.

I'm out of ideas.  Could it be that "@/home/.dpms-off" is not correct?  I know the script is not running because I can go to terminal and type xset -q and it tells me if DPMS is enabled or disabled.  If the script were running it would be set to disabled.  When I run the script manually by double clicking on it DPMS becomes disabled.

Any suggestions?

---

### Post by Cheesemill on 2012-05-17
If the script is in your home directory then you are not calling the correct path.

The script isn't located at @/home/.dpms-off

It's actually located at /home/owner/.dbms-off

Also I'm not sure what your @ is meant to achieve?

---

### Post by ajgreeny on 2012-05-17
> **nullified_nostalgia said:**
> I'm trying to run a script at startup to keep my screen from blanking every 10 minutes.  The script works just fine, when I execute it manually it disables DPMS.  Getting it to run at startup is proving to be a problem though.  The script name is .dpms-off and it's located in my home directory.  Here's what I've tried (owner is my username):

1 - Placing a copy of the script file in: /home/owner/.config/autostart
This works for pidgin instant messenger, but doesn't seem to work for the script.
[COLOR=Red]You do not put a copy of the script in here but a desktop configuration file, ie a launcher for the script[/COLOR].

2 - Placing an autostart file in: /home/owner/.config/lxsession/Lubuntu
And in the autostart file putting: @/home/.dpms-off
[COLOR=Red]You don't need the @ prefix here, just the command to run the script.  If you copy the script to /usr/bin and make sure it is executable you can launch it simply with its name.[/COLOR]

3 - Placing an autostart file in: /home/owner/.config/openbox
And in the autostart file putting: @/home/.dpms-off
[COLOR=Red]I have no autostart file in my openbox folder here. Is it something you made yourself?[/COLOR]

4 - Editing the autostart file in: /etc/xdg/openbox
To include @/home/.dpms-off
[COLOR=Red]Can't help with this location.
[/COLOR] 
5 - Editing the autostart file in: /etc/xdg/lxsession/Lubuntu
To include @/home/.dpms-off
[COLOR=Red]This is where you need the @ prefix, but you still need the proper path for the script /home/owner/.dpms-off and if the script is not actually named .dpms-off (ie hidden with the . at the front of the name) you should remove the . in the path
[/COLOR] 
6 - Editing the autostart file in: /etc/xdg/lxsession/LXDE
To include @/home/.dpms-off
[COLOR=Red]Can't help with that location either as I don't have it[/COLOR]

7 - Placing a copy of the script file in: /etc/xdg/autostart
And checking the desktop session settings to see if the file is listed in there, but it's not.
[COLOR=Red]You do not put a copy of the script in here either but a desktop configuration file, ie a launcher for the script the same as your #1 query.[/COLOR]

I'm out of ideas.  Could it be that "@/home/.dpms-off" is not correct?  I know the script is not running because I can go to terminal and type xset -q and it tells me if DPMS is enabled or disabled.  If the script were running it would be set to disabled.  When I run the script manually by double clicking on it DPMS becomes disabled.

Any suggestions?

@ Cheesemill:  As you can see from the above, this is Lubuntu and the @ prefix is needed only in the /etc/xdg/lxsession/Lubuntu/autostart file.  But as you say, the path shown is incorrect.

I also wonder if the script name is correct or if the OP is confusing the ./ needed to run in terminal a script that's in /home/owner

---

### Post by Rodney9 on 2012-05-17
Wouldn't it be easier to turn off screen blanking in the power settings in screensaver.


For How-To's and  Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)


Rodney

---

### Post by nullified_nostalgia on 2012-05-18
> **Rodney9 said:**
> Wouldn't it be easier to turn off screen blanking in the power settings in screensaver.

Turning it off in Lubuntu doesn't do anything, it's bugged.  It will turn off screen blanking up until a reboot and then even though blanking is set to disabled it ignores the setting.

In reply to the other two comments, I was using the @ because it was the only example I had to go by, found in /etc/xdg/lxsession/Lubuntu and a couple of other locations that I've explored.  I've been using linux for less than a year so I'm still heavily in the learning process.

In reply to ajgreeny's reply to number 3, yes I placed it there myself.  It was copied from /etc/xdg/openbox, in which the comments suggested the following:
> # These things are run when an Openbox X Session is started.
# You may place a similar script in $HOME/.config/openbox/autostart
# to run user-specific things.
Just for reference, I was following the advice of this post, but it leaves out instructions on how to get it to run at startup (instructions wouldn't have helped me much anyway considering it was xubuntu the poster was using):  [http://ubuntuforums.org/showpost.php?p=11512983&postcount=25](http://ubuntuforums.org/showpost.php?p=11512983&postcount=25)

I've now followed the suggestions given in the replies, after I reboot I'll know for certain if it worked and I'll mark the thread solved if it works.  Must get some sleep though so I'll save that for the morning.

---

### Post by Rodney9 on 2012-05-18
Well on my Lubuntu 12.04 the off screen blanking in the power settings in screensaver works and stays after a reboot.

Rodney

---

### Post by nullified_nostalgia on 2012-05-18
&#65279;I've tried every suggestion in ajgreeny's reply but haven't yet gotten it to work.  I've got it down to this though:
 
In /usr/bin I've got an executable script named dpms-off (I got rid of the . in front of it so it's not hidden).  The script reads as follows:
 > #!/bin/bash
 xset -dpms
 xset s off And it works when I execute it manually.
 
In /etc/xdg/autostart I've got a launcher named (visibly) DPMS Off, and (invisibly - aka when I right click and hit "rename") dpms-off.desktop, and in leafpad it reads as follows:
 > [Desktop Entry]
 Encoding=UTF-8
 Type=Application
 Name=DPMS Off
 Name[en_CA]=DPMS Off
 Exec=dpms-off
 Comment[en_CA]=Disable Screen Blanking
 StartupNotify=trueThis now allows me to select it when I go to the Desktop Session Settings in my preferences.  Double clicking the launcher disables DPMS.


But.....it still doesn't run when lubuntu launches.  I even put a copy of the launcher in /home/owner/.config/autostart, where I also had to put a pidgin instant messenger launcher to get it to autostart, but still no luck.


Any suggestions?


Also, @Rodney9, Lubuntu 12.04 doesn't have the screen blanking bug, but I'm using 11.10 which does.  I've tried 12.04 but it's got some things about it that I don't like.  The only thing I don't like about 11.10 is the screen blanking problem, which if I can get fixed I'll be completely happy with.

---

### Post by rai4shu2 on 2012-05-18
You could just as easily have a .desktop file in ~/.config/autostart that contains:

```
Exec=xset -dpms && xset s off
StartupNotify=false
Terminal=false
Hidden=false
```

and that *should* work.

---

### Post by nullified_nostalgia on 2012-05-18
> **rai4shu2 said:**
> You could just as easily have a .desktop file in ~/.config/autostart that contains:

```
Exec=xset -dpms && xset s off
StartupNotify=false
Terminal=false
Hidden=false
```and that *should* work.
Negative, did not work.  I put a .desktop file in there named dpms-off-secondary.desktop with the following in it:
> [Desktop Entry]
Exec=xset -dpms && xset s off
StartupNotify=false
Terminal=false
Hidden=false
Didn't have an effect at all.  Do I need the [Desktop Entry] at the top of the file?  I'm not sure what that does.

Perhaps the script is actually running but it's running before the screensaver settings take effect and the screensaver settings are turning DPMS back on...

---

### Post by rai4shu2 on 2012-05-18
Okay, so maybe:

```
Exec=sleep 5 && xset -dpms && xset s off
```

---

### Post by steeldriver on 2012-05-18
just throwing these out, I haven't tried them:

1) pass consoleblank=0 on the grub GRUB_CMDLINE_LINUX_DEFAULT line

2) creating a skeleton xorg.conf with

```

Section Monitor
 .
 Option "DPMS" "off" 
 .
EndSection
```

---

### Post by nullified_nostalgia on 2012-05-18
> **rai4shu2 said:**
> Okay, so maybe:

```
Exec=sleep 5 && xset -dpms && xset s off
```
Nope that didn't do it either.  I also tried setting a 30 second sleep in another way before trying that and that didn't work either.

I also tried changing the settings so the screen goes blank after 240 minutes, but even with that setting it still blanked after 10 minutes.

When I've got the screensaver setting turned to "none", opening the screensaver settings disables dpms for some reason.  That's what I've been doing for the past few months, every time I boot up the computer I just open the screensaver settings and then close it and then I don't have to worry about it blanking.

I'm at a complete loss as to why none of this is working.  The easiest viable solution I can think of, barring somehow getting the script to run at startup, is to put a shortcut to the dpms-off script on a panel and just hitting that every time I boot up.

---

### Post by nullified_nostalgia on 2012-05-18
> **steeldriver said:**
> just throwing these out, I haven't tried them:

1) pass consoleblank=0 on the grub GRUB_CMDLINE_LINUX_DEFAULT line

2) creating a skeleton xorg.conf with

```

Section Monitor
 .
 Option "DPMS" "off" 
 .
EndSection
```
I have no idea how to do either of those.  I googled both of them and I was able to figure out how you create an xorg.conf file in the root folder, but I can't seem to create it because xorg is already running.  I have no idea how to stop it or what happens if I do.

---

### Post by rai4shu2 on 2012-05-18
How about this: Go to "Seassion and Startup" and disable the "Power Manager". You don't really need it, do you?

---

### Post by nullified_nostalgia on 2012-05-18
> **rai4shu2 said:**
> How about this: Go to "Seassion and Startup" and disable the "Power Manager". You don't really need it, do you?
Crazily enough it was already disabled.  However I went to /etc/xdg/lxsession/Lubuntu and commented it out of the autostart file, and that did the trick.

Glad that's finally over with lol.  That was a lot of work for such a simple thing.  At least I learned a lot, including how to autostart scripts, even if the one I was trying to autostart wouldn't properly autostart.

Thanks!

---

### Post by rai4shu2 on 2012-05-18
I should probably give Lubuntu another try. It sounds like it's come a long way.

---

