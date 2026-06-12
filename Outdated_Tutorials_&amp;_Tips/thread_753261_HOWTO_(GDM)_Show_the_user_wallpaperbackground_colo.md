---
title: "HOWTO: (GDM) Show the user wallpaper/background color, while logging in"
date: 2008-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kirsis on 2008-04-12
**EDIT: An improved, multi-user friendly version available on page 3. Clickity:**
[http://ubuntuforums.org/showthread.php?p=5427233#post5427233]("http://ubuntuforums.org/showthread.php?p=5427233#post5427233")
-----------------------------------


One of my pet peeves with GDM has been that after logging in, it always turns the screen to a certain color (default = light brown, though this can be changed).

I feel that showing the users wallpaper or the users background color, while starting up the session, feels more polished. Here's how to achieve it, if you feel the same way:

1) We need the install the package xloadimage, which contains the app 'xsetbg'

```

sudo aptitude install xloadimage

```

2) Create the script that will set the background immediately after entering your username/password: 

```

sudo gedit /etc/gdm/PostLogin/Default

```

Paste the following code in this file:

```

#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
# Extract the wallpaper filename
WALLPAPER="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="picture_filename".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"

# Check if the wallpaper file exists. If yes - draw it, if no - use primary background color
if [ -e "$WALLPAPER" ] && [ -f "$WALLPAPER" ] ; then
	xsetbg -onroot "$WALLPAPER"
else
	
	PRIMARY_COLOR="`cat ~/.gconf/desktop/gnome/background/%gconf.xml | sed -n -e 'N
s/^[ \t]*<entry name="primary_color".*\n[ \t]*<stringvalue>\(.*\)<\/stringvalue>.*$/\1/ip'`"
	xsetroot -cursor_name left_ptr -solid "$PRIMARY_COLOR"
fi

exit 0


```

(P.S. If you have a tiled background, add the '-tile' switch to the line that executes 'xsetbg')

This script will check for a wallpaper setting, and use 'xsetbg' to draw it to the root window. If a wallpaper image does not exist, it will fill the screen with the desktop background color.


Don't forget to make this script executable:

```

sudo chmod +x /etc/gdm/PostLogin/Default

```

Now the only step left is to remove the /etc/gdm/PreSession/Default file. This is the file that sets the root window color and it executes after the PostLogin file, so just move it out of the way:

```

sudo mv -v /etc/gdm/PreSession/Default /etc/gdm/PreSession/Default.bak

```

There you go. Now while logging in you should be seeing your background color/wallpaper, instead of the gdm background color.

**Problems**

There are three problems that this script doesn't or can't handle. 

1) If you use a gradient as your desktop background, it will not be displayed. The screen will be filled with just one color (the primary color in the gradient)

2) If your wallpaper is scaled to fit, I suggest you resize it so that it matches your desktop as this script will not do that for you. You can, in theory, use the '-background'  switch, coupled with '-border black', '-smooth' and (for png's) '-gamma 2.0', but I've found that 'xsetbg' can't properly scale to fit a lot of images (depending on their resolution, it may leave empty vertical/horizontal space at the edges) and the quality of scaled images is sub-par. I suggest you just resize the wallpaper to fit your resolution in GIMP.

3) If you use desktop effects then at one point the desktop might turn black. I haven't figured out yet, how to avoid this.





There you go, I hope this is useful for somebody :)
(Tested on Hardy Heron, but should work on older versions too.)


**Update: Instructions on how to reverse the modifications**

If for some reason the script isn't working out for you (due to the black screen problem or for whatever other reason), you can revert the effect with:

```

sudo rm /etc/gdm/PostLogin/Default
sudo mv /etc/gdm/PreSession/Default.bak /etc/gdm/PreSession/Default

```

The first line deletes the file that sets the background and the other line restores the original gdm script.

---

### Post by aashay on 2008-04-14
> **kirsis said:**
> 
Don't forget to make this script executable:

```

sudo chmod +x /etc/gdm/PreSession/Default

```

 Shouldn't this be the PostSession file?

---

### Post by kirsis on 2008-04-14
Damn, ADHD strikes again :)

The PostLogin/Default file has to be executable, thanks for catching that

---

### Post by Eclipse. on 2008-04-14
I have been looking for something like this for ages.

I even asked for something simliar to be intergrated into gutsy at the time.:)

Thanks.

---

### Post by liquid circuit on 2008-04-14
Worked perfectly (after I resized my wallpaper to my resolution, as you suggested)!!!  I have compiz enabled, and the graphical blinks/redraws are minimal (using a ATI Radeon 9200).

---

### Post by kirsis on 2008-04-15
Glad you like it, guys :)

The compiz effect differs from PC to PC. For me the screen turns black for a few seconds, but for my buddy, who is also using this trick + compiz, the screen doesn't turn black at any point.

---

### Post by MeURi on 2008-04-15
I'm running Hardy, and I already get this "effect" out of the box, by just setting the login background as my desktop background (speaking of colors)

Instead, following your how-to just gives me a black screen until gnome is fully loaded :?

Btw: I too noticed that compiz turns the background black, but it happens just sometimes

---

### Post by kirsis on 2008-04-15
Setting the log in screen background to your desktop doesnt work as nicely for multiple users on one computer. This way every user sees his/her wallpaper + you dont have to think about matching gdm themes/backgrounds :)

It's odd that you got a persistent black screen. Is your desktop background color set to black (if its not using a wallpaper)? It appears to me that xsetbg fails to find your wallpaper and instead sets your desktop to the primary background color.

If your background color is not black, then it must be some external effect, because AFAIK if xsetbg failed, you should be seeing what you always saw before it.


At any rate, you can revert to your previous configuration with:

```

sudo rm /etc/gdm/PostLogin/Default
sudo mv /etc/gdm/PreSession/Default.bak /etc/gdm/PreSession/Default

```

---

### Post by gsiliceo on 2008-04-15
Why is this nasty hack needed when in feisty the wallpaper worked right?

---

### Post by subru77 on 2008-04-15
Worked for me like a dream :P

---

### Post by kirsis on 2008-04-16
> **gsiliceo said:**
> Why is this nasty hack needed when in feisty the wallpaper worked right?

Well if the wallpaper works just right for you, then why are you in this thread in the first place? Obviously it doesn't work "just right" for everybody. 

> Worked for me like a dream :P

Glad to hear that :)

---

### Post by MeURi on 2008-04-16
@ kirsis:

I have #59798E as desktop solid color (no gradients), and the same for login background. I also use a wallpaper, which is mainly #59798E colored - see [here]("http://interfacelift.com/wallpaper/details.php?id=946") :-)

Since I'm the only user for the computer, I have no problems with the multi-user issue you pointed out. And I reverted back to my 'previous settings' as soon as I noticed the black screen.

Thanks for the how-to, anyway. I'll investigate the black screen issue when I have multiple users logging in ;-)

---

### Post by gsiliceo on 2008-04-16
> **kirsis said:**
> Well if the wallpaper works just right for you, then why are you in this thread in the first place? Obviously it doesn't work "just right" for everybody. 



Glad to hear that :)

Im using gutsy... i need this hack just like everybody else using gutsy, in feisty worked without touching a thing okay?

---

### Post by kirsis on 2008-04-16
MeURi, sorry it didn't work out for you. 




> **gsiliceo said:**
> Im using gutsy... i need this hack just like everybody else using gutsy, in feisty worked without touching a thing okay?

Fair enough, but if you waltz in the thread and all your feedback amounts to calling this a "nasty hack", then don't be surprised if my response is a bit sharp.

---

### Post by MeURi on 2008-04-17
No problem at all ;-)

Hardy does it (except for the background image, as far as I noticed) out of the box, so, in the end, I'm not complaining :-P

Anyway it's a nice "nasty hack" for those who are still on older versions of Ubuntu. I'll signal this post to some friends of mine :-)

---

### Post by Eclipse. on 2008-04-18
EDIT: Talking rubbish  nvm.

---

### Post by PaulFXH on 2008-04-22
I just tried this in Gutsy on my MacBook (C2D) but didn't get any change to the drab login screen.
However, when the desktop appeared, the background showed as tiled for 4-5 seconds before filling the screen.
AFAIK, I followed the guide exactly and no error messages were received.
Anybody know what might be wrong here?

---

### Post by janfsd on 2008-05-04
Thanks for this howto, it works in Hardy.

---

### Post by dwitkin on 2008-05-13
Hello. Just wanted to say that I also experience the screen turning black at a certain point, but it doesn't appear to be a Compiz issue. I read earlier in this thread that the thinking was the screen turns black due to Compiz, so I uninstalled Compiz. I still get the same black screen issue in this order: (1) I get the wallpaper, as expected, almost immediately after entering my pasword; (2) about 10 seconds later, I get a completely black background but I can see the panels and a few programs that show windows as they start up (note: my login / background color is set to Brown, I believe, not black); (3) About 10 seconds later, I get the wallpaper again.

Any other ideas on how to address the issue?

Thanks.

---

### Post by amoore on 2008-05-13
Ubuntu really needs to impalement slickboot!

---

### Post by dwitkin on 2008-05-13
> **dwitkin said:**
> Hello. Just wanted to say that I also experience the screen turning black at a certain point, but it doesn't appear to be a Compiz issue. I read earlier in this thread that the thinking was the screen turns black due to Compiz, so I uninstalled Compiz. I still get the same black screen issue in this order: (1) I get the wallpaper, as expected, almost immediately after entering my pasword; (2) about 10 seconds later, I get a completely black background but I can see the panels and a few programs that show windows as they start up (note: my login / background color is set to Brown, I believe, not black); (3) About 10 seconds later, I get the wallpaper again.

Any other ideas on how to address the issue?

Thanks.

Ignore my post above about Compiz not being the issue. I must have not fully re-booted before or something. In any case, Compiz is uninstalled and I am no longer experiencing the black screen issue... So, I guess Compiz is the culprit.

Aside from the black screen interaction with Compiz, this hack works great. Thanks.

---

### Post by peakpc on 2008-05-18
This trick works very well for me in Hardy with compiz-fusion it even works with webiulder (background picture changer so I have a differnt desktop every hour) I just had to make sure that all my desktop photos were sized to 1280X800 (laptop screen size):) now I have to pick out a new splash screen...as the old one was geared to blend in with the black screen I had before (got rid of the ugly brown color a while back):)

---

### Post by hollerith on 2008-05-18
I'm having a problem with gnome is obscuring the rootwindow with the desktop background.  I turned off nautilus show_desktop and I still see the wallpaper specified in Appearance Preferences/Backgrounds. This hack for setting the rootwindow with xsetroot or xloadimage or xscreensaver-getimage doesn't work for me as they all behind the wallpaper. Is there a gdm setting 'use real root window not a virtual one'.  How you guys don't have this problem?

---

### Post by peakpc on 2008-05-19
Hey Kirsis this how to works great, Is there a way to get the current background (mine changes) to be directed to the gdm login screen? maybe some modification of your code in the background area of the greeter's .xml file?  any help would be appreciated.:)

---

### Post by peakpc on 2008-06-17
I have given this some further thought and have some new questions?

Can this script be modified to run before the GDM login?

Can the background image in the Login be made transparent (png instead of jpg)? 

I don't understand everything your script is doing exactly,:) yet. but I do like it!

---

### Post by kirsis on 2008-06-17
peakpc:

It's possible to make the script run before GDM, most things are on GNU/Linux systems :) Don't think GDM'd honor transparency in a background PNG, though. 

If you want it to set the background of your GDM login screen, your best bet would be to run it before GDM (as an init script, thus - as root), extract the path to the background image as in this script (though you'd have to manually specify the user, whose background should be chosen) and make a link between that image and the background image of your GDM theme.

This would break, though, if you'd change your GDM theme (as it'd likely look for the background elsewhere and you'd have to adjust the script)

Probably not worth the hassle :)

---

### Post by mike-uk on 2008-07-12
kirsis - first of all I would like to thank you for your solution; It worked perfectly:)
Excuse my ignorance but is it possible to have the compiz-fusion splash appear during this period:confused:
Just looking for something animated.
mike-uk

---

### Post by vexorian on 2008-07-21
This doesn't seem to be working for me, out of the box that is, I noticed that script is run by root, not by my user, so it wasn't getting any background file and it was placing a primary_color that was totally different from mine, I had to use "sudo -u myUserName" It works, but it won't work for multi user...

Edit: GDM  documentation to the rescue!

This version of the script should work on more situations (aka when there are many users and each has a different wallpaper), for example if root's wallpaper is different to what you really want... Hey, at least you don't have to manually add and remove -tile when you change that option of your wallpaper...

```

#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#

# gdm always runs PostLogin as root, the USER variable is set to point out the user name.
# that, and sudo are enough to get the correct configuration.

# Extract the wallpaper filename
WALLPAPER=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/picture_filename)
# Extract the picture option (important so we know if -tile should be used)
MODE=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/picture_options)
# Extract the primary_color (in case the wallpaper image cannot be used)
PRIMARY_COLOR=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/primary_color)

# Check if the wallpaper file exists. If yes - draw it, if no - use primary background color
if [ -e "$WALLPAPER" ] && [ -f "$WALLPAPER" ] ; then

    # if mode is "wallpaper", use the -tile option
    if [ "$MODE" = "wallpaper" ]; then
        xsetbg -tile -onroot "$WALLPAPER"
    else
        xsetbg -fullscreen -onroot "$WALLPAPER"
    fi
else
    xsetroot -cursor_name left_ptr -solid "$PRIMARY_COLOR"
fi

exit 0
```

A lot of thanks since I only needed to do small tweaks to the script to make it work, the rest are things that I wouldn't be able to know that existed, like the whole utility to draw on the background and the GDM scripting. My desktop quality of life has improved a lot now that the background is loaded just after you make a succesful login.

---

### Post by kirsis on 2008-07-21
That's pretty cool, vexorian. Updated the first post to point to here.

edit: odd, though, that it was ran by root. '~' should've worked in PostLogin

---

### Post by vexorian on 2008-07-21
Well, I don't know, but GDM's documentation actually says postlogin is run for root. This doesn't explain how ~ has worked for so many people...

It seems [xsetbg -onroot "$WALLPAPER"] needs to change to [xsetbj -fullscreen -onroot "$WALLPAPER"]

---

### Post by itsjareds on 2008-08-30
I have a widescreen monitor and my background was scaled to fit by default, I was able to fix the scale problem by adding the -center option.

```
xsetbg -onroot -center "$WALLPAPER"
```

It does blink black for about two seconds right before it loads the desktop completely, but that happened before. Might just be my computer.

---

### Post by clemyeats on 2008-11-08
Hi, 

Just a quick note to share my experience with GDM. I needed to tweak /etc/gdm/PostLogin/Default for a completely different reason. Anyway, I noticed that the new GDM (coming with Gnome 2.24) interprets $USER as root while it used to interpret it as the user's username. $HOME still points to the user's home though. So that change in behavior comes from Gnome and it might explain why the original version of your tutorial worked for so many users and not for Intrepid users anymore. 

Also, Default won't run if you're missing that initial !#/bin/sh line, even if you've made the file executable. I've learnt that the hard way and your new version of this tutorial just gave me the answer (thanks :)). 

Good luck, 
Clem.

---

### Post by clemyeats on 2008-11-08
Actually, $USER being root might have had something to do with the missing /bin/sh line ;)

---

### Post by sarah.fauzia on 2008-12-31
Is there any way to make this work in Openbox? I followed the instructions, but I still get Openbox's default grey background for a split-second before the my background loads (by my gnome settings, not by the script, for I imagine if the script was working, I wouldn't see the default grey background after login first). I'm running Ubuntu Intrepid (in an Openbox-only session).

---

### Post by tad1073 on 2008-12-31
The easiest way to use your own wallpaper is to uncompress the gdm theme, edit it by adding the background you want, then recompressing it.

---

### Post by sertse on 2009-03-05
thanks for the tutorial.

Is there are way to do it on something that isn't going gnome? The script if I'm reading it correctly, refers to where gnome places the picture, and whether gnome see it as tiled and it's stuff accordingly. 

The script "works" for me in fluxbox, well... I changed the last line about primary color to force it to show a particular image, but that's not flexible for multiuser, (ok for me, since I'm the only user on this comp) nor elegant. (Since the code is really reading "this doesn't exist" else "this doesn't exist" else...force show image XYZ)

I wonder what happens if the pic isn't there, now that I changed the fallback..

Anyways, back to the good, my login is pretty seemless now, especially as my gdm has the same background as my desktop...

---

### Post by IceBadger on 2009-03-29
> **vexorian said:**
> 

```

#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#

# gdm always runs PostLogin as root, the USER variable is set to point out the user name.
# that, and sudo are enough to get the correct configuration.

# Extract the wallpaper filename
WALLPAPER=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/picture_filename)
# Extract the picture option (important so we know if -tile should be used)
MODE=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/picture_options)
# Extract the primary_color (in case the wallpaper image cannot be used)
PRIMARY_COLOR=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/primary_color)

# Check if the wallpaper file exists. If yes - draw it, if no - use primary background color
if [ -e "$WALLPAPER" ] && [ -f "$WALLPAPER" ] ; then

    # if mode is "wallpaper", use the -tile option
    if [ "$MODE" = "wallpaper" ]; then
        xsetbg -tile -onroot "$WALLPAPER"
    else
        xsetbg -fullscreen -onroot "$WALLPAPER"
    fi
else
    xsetroot -cursor_name left_ptr -solid "$PRIMARY_COLOR"
fi

exit 0
```


This script was not working for me at all, so I took a good look at it.

Apparently I did not have 'xsetbg' installed, so it would not set the background.

You will need to run:

```
sudo apt-get install xloadimage
```

After this is installed, the script worked like a charm.

---

### Post by IceBadger on 2009-03-29
I am having the black screen problem too.  The wallpaper will switch, instead of a plain color.  Then before the top panel is drawn the screen turns black.  Happens at the same time the login sound stars.

This can be avoided if visual effects are turned off:
```
System > Preferences > Appearance > Visual Effects == None
```

Has anyone found a solution yet?  It ruins the seamless transition.

---

### Post by Jayce. on 2009-03-29
omg thanks so much worked like a charm :) finally been waiting for a while for this cheers.

---

### Post by 565Customz on 2009-11-02
does this work with karmic?  i cant seem to save that script file

---

### Post by drewlong on 2010-01-08
Hi i'm running Mint 8 and couldn't get this to work, the script saved ok and no blank screens etc it just didn't pull through my background. I'm not sure if it's a Karmic thing or a mint thing ... any idea's please ?

---

### Post by nick_goodfate on 2010-01-08
[http://gnome-look.org/content/show.php/desktop+background+as+xsplash+%2B+gdm?content=114984](http://gnome-look.org/content/show.php/desktop+background+as+xsplash+%2B+gdm?content=114984)

---

### Post by drewlong on 2010-01-08
Great thanks Nick ... makes it all nice and polished ... for the first time ever the boot, through login, through desktop load now appears joined up rather than a series of disjointed apps handing over control as they execute.

Note:-
1) By the time you get to this you will probably have executed the scripts at the start of this post .... remember to back it out BEFORE trying Nick's method. I didn't ...

2) The script on page 1 runs fine with Mint 8 but not the later multiuser script ... page 3 I think it was.

---

