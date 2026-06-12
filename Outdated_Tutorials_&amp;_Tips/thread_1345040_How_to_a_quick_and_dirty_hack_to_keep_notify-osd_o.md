---
title: "How to: a quick and dirty hack to keep notify-osd out of your hair"
date: 2009-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by ChrisCamacho on 2009-12-03
<rant> skip to the close of the rant tag if you just want to get hacking!!!

I used to **really** hate notify-osd (the little pop up bubble that contrives to get it the way of window close widgets on maximized windows) I know its click through but its still distracting!

Worst still if you're in the habit of having a thin strip of an IM client on the right hand side and nearly maximised application windows to the left of it, the notification bubble always seems to get in the way and is defiantly distracting. (Its usually spamming you with IM messages which a flashing pidgin task bar button used to do just fine without getting in the way...)

What really irked was that there is no decent configuration options, and unless I'm laboring under a misapprehension the developers seem to think they know better than me, how **my** machine should be configured... 

I can't believe theres plans to ape windows and have the bubble originate in the bottom right hand corner, if the sys tray goes there in a later version of windows I mean Ubuntu its real face palm time...!

</rant>

I decided for me personally the best solution would be to have the origin in the bottom left of the screen where there are usually less important things going on.  I was going to properly implement South-West Gravity but in the end I did a very nasty and quick hack, why? well I'm seriously thinking of reimplementing notify-osd with a system of output plugins, off the top of my head I can think of several better solutions than an intrusive bubble... and an xml file for colours and timings is defiantly needed and no I *really* dont care about Ubuntus specs its **MY** machine (damn that was a rant again!)

So on with the dirty hack

create a sub directory to working in and grab the source to notify-osd with the following command

**apt-get source notify-osd**

once its done its thing cd into the directory it creates and run

**./configure**

you might have to do this a number of times installing any missing -dev packages it finds are missing

once you have all the needed -dev packages installed and configure has done its thing cd into the src directory

load stack.c into your favorite text editor and search for the following function

**stack_get_slot_position**

you should be at roughly line 885 ish, now skip down to the end of the routine somewhere after approx line 970+

just before the final closing curly brace ( } ) of the function add the following code

	
[B]    Defaults* d;
    d = self->defaults;
    *x=0;
    *y=defaults_get_desktop_height (d)-*y-EM2PIXELS (5 ,d);
}[/B] //<-- this is the very end of the function

basically all this does is set the position to the very left and inverts the Y value (in effect) so you'll want to turn off the strange East gravity setting if you were trying it out.

save the file and run

**make**

assuming all is well run

**sudo make install**

log out and then back in and the notification bubble should now be sulking in the bottom left corner...

happy hacking!

---

### Post by h!v on 2009-12-14
To get needed dependencies for packet you can use
```

sudo apt-get build-dep notify-osd

```

Moreover, in source code for Jaunty I didn't find any such function you quoted. File "stack.c" is about 720-ish lines too.

Cheers

---

### Post by IllegalCharacter on 2009-12-14
You could also remove them altogether:
```
cd /usr/share/dbus-1/services
sudo mv org.freedesktop.Notifications.service org.freedesktop.Notifications.service.disabled
```

---

### Post by WindPower on 2009-12-14
Kubuntu wins on this one :D [Check it out](http://uppix.net/d/9/7/639a23477c8a357116fc36e11d369.png):
[img]http://uppix.net/d/9/7/639a23477c8a357116fc36e11d369.png[/img]

---

### Post by clhodapp on 2009-12-14
I suggest some improvements to your procedure (edited):

Run:
```
sudo apt-get install devscripts build-essential
apt-get source notify-osd
```Make your changes. I personally just made the notifications shorter by changing the definition of DEFAULT_ON_SCREEN_TIMEOUT in defaults.c then run:

```
sudo apt-get build-dep notify-osd
debuild
```Install deb in directory above root of source, then run

```
sudo echo -e "Package: notify-osd\nPin: version 0.0.24-0ubuntu1\nPin-Priority: 1001" > /etc/apt/preferences
``` to stop the package from being updated and your changes from being overwritten.  Obviously, you need to correct the version to be whatever the current version is when you make your changes.  Also, this is pretty hackish, since you should really *not* be just changing the code for an exisiting debian source package, but should rather be making your own version of the package.

---

### Post by PhilMize on 2009-12-15
> **clhodapp said:**
> 
I personally just made the notifications shorter by changing the definition of DEFAULT_ON_SCREEN_TIMEOUT in defaults.c then run:




What is it you changed to make it disappear faster? I don't know code or anything. all I see is 

> 
gint
defaults_get_on_screen_timeout (Defaults* self)
{
	gint on_screen_timeout;

	if (!self || !IS_DEFAULTS (self))
		return 0;

	g_object_get (self, "on-screen-timeout", &on_screen_timeout, NULL);

	return on_screen_timeout;
}


I don't see how to edit that to make the notification not stay on so long...:(

---

### Post by clhodapp on 2009-12-25
Search for #define DEFAULT_ON_SCREEN_TIMEOUT .  The number after it is the time for it to stay on the screen in milliseconds.  Also, if you want to be able to close all current/pending notifications immediately, it seems to be safe to run killall notify-osd (it comes back up when needed), so you should be able to bind a keyboard shortcut run that command.

---

### Post by gradinaruvasile on 2009-12-25
I just installed the old style (standard gnome) notification daemon:

```
sudo apt-get install notification-daemon
```

and replaced the notify-osd vith the notification-daemon's executable (link):
first backup the notify-osd:

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-default
```

then link the notification-daemon's executable:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

kill the notify-osd so that on reload to be replaced with the notification-daemon:

```
killall -9 notify-osd
```

From now on, the notifications are displayed in the old style. There is the notification-properties program that lets you select the popup location (corners).

---

### Post by Snowjack1 on 2010-01-18
@clhodapp and ChrisCamacho: Thanks for these pointers, notify-osd was really starting to drive me nuts too.

---

### Post by tgalati4 on 2010-01-18
Growl on Mac Tiger 10.4.x seems to work properly:  the notification shows up in the upper left corner--offset so you can see the close-window icons.  Then each notification is offset below the current one so they don't overlap--helpful when several things fire off notifications at the same time.

It would be nice if Ubuntu's OSD notification followed this default behavior.

Update:  I followed clhodapp's method of rebuilding the package.  I needed to offset the bubbles so I could see the side scroll bars and the minimize/maximize icons.  I did the following:

Make a backup of defaults.c
cp defaults.c defaults.bak

Modified the following values:  Was 0.5f which is too close to the top and side.

#define DEFAULT_BUBBLE_VERT_GAP       2.5f
#define DEFAULT_BUBBLE_HORZ_GAP       2.5f

Then built the package going up one directory from src and using clhodapp's instructions:

sudo apt-get build-dep notify-osd
debuild

Then:

sudo su

echo -e "Package: notify-osd\nPin: version 0.9.11-0ubuntu3\nPin-Priority: 1001" > /etc/apt/preferences

dpkg -i notify-osd_0.9.11-0ubuntu3_i386.deb

Now my notification bubbles are still in the upper right, but offset enough that I can still control the windows underneath.  At least that's one fix.  Thanks clhodapp.

According to the wiki, [https://wiki.ubuntu.com/NotifyOSD#position](https://wiki.ubuntu.com/NotifyOSD#position), there's a lot of work going on for Lucid, but I doubt there will be a backport since they are changing a lot of the notification framework.  The new version will probably break for us running Jaunty.

---

### Post by SilverWave on 2010-04-26
> **clhodapp said:**
> I suggest some improvements to your procedure (edited):

  ...I personally just made the notifications shorter by changing the definition of DEFAULT_ON_SCREEN_TIMEOUT in defaults.c then ...


**Thanks for that, this whole issue is strangely intriguing :-) **

I have created a PPA and it has a notify-osd that is set to 3secs not 10secs.

[B][notify-osd – Now with 70% Less Annoy :-)]("http://silverwav.wordpress.com/2010/05/08/notify-osd-now-with-70-less-annoy/")

[/B] Its amazing how much that changes my appreciation of the notifications... I have found the annoyance is mainly based on them being on screen too long.


> sudo  add-apt-repository ppa:silverwave/apps-0
> **Lucid**

These work for me and my environment...



---

