---
title: "unity-greeter theme for lightdm"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jbicha on 2011-07-13
A unity-greeter theme for lightdm has been uploaded and is currently not installed by default and has to be manually enabled even after installation. It's still a work-in-progress but I think it's already an improvement over the current greeter (which was never intended to be the final 11.10 version).

Via Robert Ancell:
> Uploaded the first version into Oneiric! It's in the **unity-greeter** package, and you can play around with it using ```
/usr/lib/lightdm/unity-greeter --test-mode
``` or if you're particularly brave use it as your login screen by setting *greeter-theme=unity* in */etc/lightdm/lightdm.conf*

---

### Post by jbicha on 2011-07-13
Yes, definitely still a work in progress. There's all sorts of buttons in the top right that will break things. As an example, it's possible to launch Banshee from the greeter which isn't a particularly good idea.

---

### Post by lucazade on 2011-07-13
I was looking for that command to switch greeter.. going to try!

---

### Post by fjgaude on 2011-07-13
Wow, the trial unity-greeter is certainly eye catching... each user gets a different background... that should get a few users of Mac or Win to switch over, eh? <smile>

---

### Post by Starks on 2011-07-13
that's pretty awesome

---

### Post by CreativeReach on 2011-07-14
Love it!

---

### Post by ricsi-pontaz on 2011-07-17
Here is a video of the new theme:

[http://youtu.be/uM6UYPMyJ4g](http://youtu.be/uM6UYPMyJ4g)

---

### Post by pulpo69 on 2011-07-17
is there a language chooser in the new theme, i couldn't see it in the video.

---

### Post by MacUntu on 2011-07-17
> **pulpo69 said:**
> is there a language chooser in the new theme

No.

---

### Post by CaptainMark on 2011-07-17
should this be available as standard, ive run synaptics updates yet i dont have a /usr/lib/lightdm/unity-greeter

---

### Post by sgage on 2011-07-17
> **CaptainMark said:**
> should this be available as standard, ive run synaptics updates yet i dont have a /usr/lib/lightdm/unity-greeter

No, it's a new package, so you don't pick it up on and update - you need to specifically install it...

---

### Post by VinDSL on 2011-07-17
I likey...  :)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-17-jul-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-17-jul-2011.png")[/INDENT]

---

### Post by rburkartjo on 2011-07-18
okay and how would you do as jb said
"or if you're particularly brave use it as your login screen by setting greeter-theme=unity in /etc/lightdm/lightdm.conf"
tks

---

### Post by Anduu on 2011-07-18
> **rburkartjo said:**
> okay and how would you do as jb said
"or if you're particularly brave use it as your login screen by setting greeter-theme=unity in /etc/lightdm/lightdm.conf"
tks

I too would like to know...I took a peek at the lightdm.conf and it seems a tad cryptic as there are a couple of places to modify greeter values.

---

### Post by TrueJournals on 2011-07-18
That should go in the [seat-0] section of /etc/lightdm/lightdm.conf

---

### Post by VinDSL on 2011-07-18
> **rburkartjo said:**
> okay and how would you do as jb said
"or if you're particularly brave use it as your login screen by setting greeter-theme=unity in /etc/lightdm/lightdm.conf"
tks

Install the theme:
```

$ sudo apt-get install unity-greeter

```

Edit lightdm.conf
```

$ sudo gedit /etc/lightdm/lightdm.conf

```

Change this:
```

[LightDM]
#xserver=default-xserver
#default-xserver-command=
#authorization-directory=/var/cache/lightdm/authority
#log-directory=/var/log/lightdm
[B][COLOR="Red"]theme-directory=/usr/share/lightdm/themes 
theme-engine-directory=/usr/lib/lightdm[/COLOR][/B] 
#default-greeter-theme=
#cache-directory=/var/cache/lightdm
#xsessions-directory=/usr/share/xsessions
#default-xsession=
session-wrapper=/etc/lightdm/Xsession
minimum-vt=7
seats=seat-0

```

And, this:
```

[seat-0]
[B][COLOR="Red"]vt=0
greeter-theme=unity[/COLOR][/B]
#greeter-user=lightdm
#session=gnome
#default-user=bob
#default-user-timeout=5
#default-user-session=
#pam-service=lightdm
#display-number=2
#xserver=
#xdmcp-manager=
#xdmcp-port=177
#key=0x0123456789ABCD

```

And, this:
```

[GuestAccount]
**[COLOR="Red"]enabled=false[/COLOR]**
username=guest
setup-script=/usr/share/lightdm/guest-session/guest-session-setup.sh
cleanup-script=/usr/share/lightdm/guest-session/guest-session-cleanup.sh

```

Save & restart.


To test / take screenshots / make videos, et cetera:
```

$ /usr/lib/lightdm/unity-greeter --test-mode

```

That's all I did...  :)

---

### Post by CaptainMark on 2011-07-18
i tried this, is it just these 2 lines to change, im still booting to un-themed lightdm

---

### Post by godhika on 2011-07-18
Dont forget to uncomment at least the line with greeter-theme - that did the trick for me ( i guess - had to go through some trial and error ;) )

---

### Post by VinDSL on 2011-07-18
> **CaptainMark said:**
> i tried this, is it just these 2 lines to change, im still booting to un-themed lightdm
Sorry for being rudimentary, but...

Have you installed the theme?

```

$ sudo apt-get install unity-greeter

```

---

### Post by lonniehenry on 2011-07-18
Or are you using the grub from the oneiric install or are you using one from another partition like I am doing.

---

### Post by CaptainMark on 2011-07-18
Yeah ive got the package and its a single boot rig, do these lines have to go after [seat - 0] this isn't the case here, ill move it around, trial and error

---

### Post by VinDSL on 2011-07-18
I'll just post the whole lightdm.conf file here:

```

#
# General configuration
#
# xserver = X server to run (FIXME)
# default-xserver-command = Default X server command (FIXME)
# authorization-directory = Directory to store X authorization files
# log-directory = Directory to log information to
# theme-directory = Directory to load themes from
# theme-engine-directory = Directory to load theme engines from
# default-greeter-theme = Default greeter theme to use
# cache-directory = Directory to cache to
# xsessions-directory = Directory to find X sessions
# default-xsession Default X session to use
# session-wrapper = Program to run sessions through
# minimum-vt = First VT to run displays on
# seats = list of seats to start displays on
#
[LightDM]
#xserver=default-xserver
#default-xserver-command=
#authorization-directory=/var/cache/lightdm/authority
#log-directory=/var/log/lightdm
theme-directory=/usr/share/lightdm/themes 
theme-engine-directory=/usr/lib/lightdm 
#default-greeter-theme=
#cache-directory=/var/cache/lightdm
#xsessions-directory=/usr/share/xsessions
#default-xsession=
session-wrapper=/etc/lightdm/Xsession
minimum-vt=7
seats=seat-0

#
# X server configuration
# layout = ServerLayout to use
# config-file = Configuration file to use
#
#[default-xserver]
#command=/usr/bin/X
#layout=
#config-file=

#
# Seat configuration
#
# vt = Virtual terminal to start on (0-n)
# greeter-theme = Greeter theme
# greeter-user = User to run greeter process as
# session = Default session
# default-user = Username of default user to log in as
# default-user-timeout = Delay before logging in in seconds (use 0 for automatic login)
# pam-service = PAM service to use
# display-number = Display number to use (overrides automatic display number selection)
# xserver = X server to use
# xdmcp-manager = XDMCP manager to connect to
# xdmcp-port = XDMCP UDP/IP port to communicate on
# key = Authentication key to use
#
[seat-0]
vt=0
greeter-theme=unity
#greeter-user=lightdm
#session=gnome
#default-user=bob
#default-user-timeout=5
#default-user-session=
#pam-service=lightdm
#display-number=2
#xserver=
#xdmcp-manager=
#xdmcp-port=177
#key=0x0123456789ABCD

#
# User manager configuration
#
# load-users = true if can provide user list to greeter
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserManager]
#load-users=true
#minimum-uid=500
#hidden-users=nobody nobody4 noaccess
#hidden-shells=/bin/false /usr/sbin/nologin

#
# Guest account configuration
#
# enabled = true if guest account is enabled
# username = username of guest account
# setup-script = script to be run to setup guest account
# cleanup-script = script to be run to cleanup guest account
#
[GuestAccount]
enabled=false
username=guest
setup-script=/usr/share/lightdm/guest-session/guest-session-setup.sh
cleanup-script=/usr/share/lightdm/guest-session/guest-session-cleanup.sh

#
# XDMCP Server configuration
#
# enabled = true if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
[xdmcp]
#enabled=true
#port=177
#key=0x0123456789ABCD

```

Not a lot of changes, from the default, so it should be a drop-in...  ;)

---

### Post by sgage on 2011-07-18
VinDSL,

How do you get the nice picture of the cherry and all? I'm getting the unity greeter, but with a plain background (little dots). Can you get any picture you want in the background?

[Edit: When I run unity-greeter --test I see the cherry background, but not when run "for real".]

---

### Post by CaptainMark on 2011-07-18
aah it works now and it looks sweet, i cant wait for more themes and the polished finished product, i too would like to alter the backgrounds,
also the tiny bar which has a clock on it (top right) appears light grey and has no buttons, where as the the test-mode is dark like the default taskbar colour with sound and power options on it, has everyone got the same problem?


EDIT: Second impressions are not so good, had to change back as im finding it too unstable to use and keep getting logged out after anything between 10 seconds to 5 minutes, usually the former

---

### Post by MacUntu on 2011-07-18
You probably should not alter the 'vt' value. Having this point to something wrong caused a lot of problems in the past.

---

### Post by Roo79x on 2011-07-18
First off thank you to VinDSL followed your instructions and it works a real treat... 

+1 for info on changing the background please 

@CaptainMark the tiny bar which has a clock on it (top right) appears light grey and has no buttons, where as the the test-mode is dark like the default taskbar colour with sound and power options on it... <<<< mine is the same also

but I'm still very happy to just being able to have the changed theme :)

[EDIT!!!] I just changed the image warty-final-ubuntu.png in /usr/share/backgrounds {found an image I wanted to use that was the same dimensions as the original warty-final-ubuntu.png renamed it to warty-final-ubuntu.png} then copied my new image to /usr/share/backgrounds [a quick note though warty-final-ubuntu.png is actually a .jpeg] and now lightdm is using my new image

---

### Post by MonolithImmortal on 2011-07-18
> **Roo79x said:**
> 
[EDIT!!!] I just changed the image warty-final-ubuntu.png in /usr/share/backgrounds {found an image I wanted to use that was the same dimensions as the original warty-final-ubuntu.png renamed it to warty-final-ubuntu.png} then copied my new image to /usr/share/backgrounds [a quick note though warty-final-ubuntu.png is actually a .jpeg] and now lightdm is using my new image

Hmmm, That doesn't seem like a good solution to me. Sure it works, but I have to remove the default Ubuntu wallpaper. Surely there's a way to to select which image lightdm uses as the background. Has anyone figured out how to set up the background switching that's displayed in the test mode?

---

### Post by Roo79x on 2011-07-18
yeah I know it aint the best way lol...  but it worked and I hate the default wallpaper... I the default backed up so when someone shows a better way I can change it back.

---

### Post by QQi on 2011-07-18
/usr/share/lightdm/themes/unity/index.theme

[theme]
name=Unity
description=Unity Greeter
engine=unity-greeter
session=gnome
[COLOR="Red"]background-image=bg.jpg[/COLOR] *[COLOR="DarkGreen"]//maybe help[/COLOR]*


and in /usr/share/lightdm/themes/example-gtk-gnome have gtkrc maybe can change the panel theme

---

### Post by MonolithImmortal on 2011-07-18
> **QQi said:**
> /usr/share/lightdm/themes/unity/index.theme

[theme]
name=Unity
description=Unity Greeter
engine=unity-greeter
session=gnome
[COLOR=Red]background-image=bg.jpg[/COLOR] *[COLOR=DarkGreen]//maybe help[/COLOR]*

Already tried. I added the picture I wanted to the unity folder and added that line to the index.theme. Still no change.

---

### Post by meborc on 2011-07-19
> **MonolithImmortal said:**
> Already tried. I added the picture I wanted to the unity folder and added that line to the index.theme. Still no change.

i have no experience in this but it might be that only images with correct resolution get shown... but i might be wrong

---

### Post by moore.bryan on 2011-07-19
I'm having some issues with the default de selected; unity-greeter seems to default to unity 2d even though that's not set in *any* file. Huh?

Oh, and the renaming warty image works to change background for me.

---

### Post by TrueJournals on 2011-07-19
Looks like per-user background images are currently hard-coded into unity-greeter.  For non-test-mode, these are hard-coded to null, so right now, there's no way to configure the per-user backgrounds.

---

### Post by sgage on 2011-07-19
> **TrueJournals said:**
> Looks like per-user background images are currently hard-coded into unity-greeter.  For non-test-mode, these are hard-coded to null, so right now, there's no way to configure the per-user backgrounds.

Well, that's good to know! I'll stop beating my head against the wall trying to find a solution :KS

---

### Post by Gremlinzzz on 2011-07-19
Nice now they should work on there wallpaper.something Ubuntu related not trees or rock or blurred colors.come to think of it i,v never seen a tux related default wallpaper in Ubuntu.:)

---

### Post by Roo79x on 2011-07-19
> **Gremlinzzz said:**
> Nice now they should work on there wallpaper.something Ubuntu related not trees or rock or blurred colors.come to think of it i,v never seen a tux related default wallpaper in Ubuntu.:)

I agree

check this one out it's my favourite comes in a few different colours too...

[HTML]http://planet.awn-project.org/?p=6320[/HTML]

---

### Post by seeker5528 on 2011-07-20
> **TrueJournals said:**
> Looks like per-user background images are currently hard-coded into unity-greeter.  For non-test-mode, these are hard-coded to null, so right now, there's no way to configure the per-user backgrounds.

Per-user background images does not compute. :confused:

I could see using '~/.face' (small image file) to allow users to change the face image that shows next to their name on the login screen. If there was a splash screen I could see allowing a per-user image for that. But the amount of time from login until your wallpaper is set doesn't seem so great that there really needs to be a per-user background in between.

Later, Seeker

---

### Post by moore.bryan on 2011-07-20
Can anyone confirm/explain the bug where Unity2D is the default login for unity-greeter, even though it's not set in any file?

---

### Post by mc4man on 2011-07-20
> **moore.bryan said:**
> Can anyone confirm/explain the bug where Unity2D is the default login for unity-greeter, even though it's not set in any file?
I can say in the short time I used it to log in that it pays no attention to ~/.dmrc
Here it would always default to the top entry, "Gnome" (session - gnomeshell), irregardless of whether gnomeshell was installed

It is a 0.1 release, not intended to all that functional

---

### Post by moore.bryan on 2011-07-20
It's as fully functional as I expect it to be right now, but I find it interesting "GNOME" is the only shell selection I can find in any config file, but Unity2D is the default... I wonder where lightdm is getting its "marching orders."

---

### Post by Bowmore on 2011-07-20
I can confirm it as a first time issue. After changing it i.e to *unity* it seems to work properly here. And yes, the session is stored in the *~/-dmrc* file. Actually this (Session) is the only item that is used by lightdm in this file. At the moment *Session=gnome* represents the *unity* session but there is work going on to change that to *Session=unity*.

---

### Post by TrueJournals on 2011-07-20
> Per-user background images does not compute
What do you mean? Have you run the greeter in test mode? You'll notice that each user is given their own background image when you scroll to their name.

---

### Post by moore.bryan on 2011-07-20
> **Bowmore said:**
> I can confirm it as a first time issue. After changing it i.e to *unity* it seems to work properly here. And yes, the session is stored in the *~/-dmrc* file. Actually this (Session) is the only item that is used by lightdm in this file. At the moment *Session=gnome* represents the *unity* session but there is work going on to change that to *Session=unity*.
Sorry for being thick, but does this mean setting ```
Session=unity
``` in ~/.dmrc will make it default into Unity?
What's the deal with the 2D setting?

And, as a side-question, would it be fine for me to get rid of 2D--since it's useless to me--or is that "hard-wired" into Oneiric right now?

---

### Post by mc4man on 2011-07-20
> **moore.bryan said:**
> Sorry for being thick, but does this mean setting ```
Session=unity
``` in ~/.dmrc will make it default into Unity?


session=gnome means Ubuntu (unity3d
session=gnome-shell
session=ubuntu-2d

> I wonder where lightdm is getting its "marching orders." 
As far as the session list I'd guess from what's in /usr/share/xsessions/ (the .desktops

---

### Post by Bowmore on 2011-07-20
> **moore.bryan said:**
> Sorry for being thick, but does this mean setting ```
Session=unity
``` in ~/.dmrc will make it default into Unity?Nope.

Atm the following is due in ~/.dmrc:
[I]Session=gnome (for unity)
Session=ubuntu-2d
Session=gnome-classic
Session=gnome-shell[/I]

You select the session at login, i.e clicking the "star" in the upper right corner.

Here's the bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/803519](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/803519)

> **moore.bryan said:**
> What's the deal with the 2D setting2D is the default Ubuntu fallback. Remember though that the unity-greeter is just a mockup and hardcoded right now.

> **moore.bryan said:**
> And, as a side-question, would it be fine for me to get rid of 2D--since it's useless to me--or is that "hard-wired" into Oneiric right now?Well, it's not hardcoded but unity-2d package is part of ubuntu-desktop.

---

### Post by moore.bryan on 2011-07-20
I can confirm that ```
Session=gnome
``` defaults to Unity2D for me, **not** Unity3D as expected. Back to the drawing board!

---

### Post by Bowmore on 2011-07-20
Hmm, do you have full 3D support, check with
```
/usr/lib/nux/unity_support_test -p
```
If so try to login using session Ubuntu 2D, then logout again and select Ubuntu and login.

If I got it right I had to do something like this the first time to make it work with the unity-greeter.

---

### Post by moore.bryan on 2011-07-20
> **Bowmore said:**
> Hmm, do you have full 3D support, check with
```
/usr/lib/nux/unity_support_test -p
```
Fully supported.

[quote=Bowmore]
If so try to login using session Ubuntu 2D, then logout again and select Ubuntu and login.[/QUOTE]
Did this and it didn't "set" Unity3D; rather, I *now* have to login *twice* to get in.

Thanks! ;-)

---

### Post by seeker5528 on 2011-07-20
> **TrueJournals said:**
> What do you mean? Have you run the greeter in test mode? You'll notice that each user is given their own background image when you scroll to their name.

I wasn't seeing it, but I figured out I had a dyslexic moment on the number of dashes to use. I understand now. I think it's a waste, but I understand. ;)

I did have the thought that the greeter should just use what each user has selected as their wallpaper, but after thinking some more I thought... hmmm... that could be a little scary for some people, probably better not to go there. :P

Later, Seeker

---

### Post by moore.bryan on 2011-07-21
Well, now I'm not longer having to double login, but I still can't get Ubuntu as the default session; Ubuntu2D is always the default.

I've played around with /etc/lightdm/lightdm.conf and set the default session as "gnome," but that doesn't even work.

:-(

Bug filed:
[https://bugs.launchpad.net/unity-greeter/+bug/814235]("https://bugs.launchpad.net/unity-greeter/+bug/814235")

---

### Post by sgage on 2011-07-21
> **moore.bryan said:**
> Well, now I'm not longer having to double login, but I still can't get Ubuntu as the default session; Ubuntu2D is always the default.

I've played around with /etc/lightdm/lightdm.conf and set the default session as "gnome," but that doesn't even work.

:-(

Bug filed:
[https://bugs.launchpad.net/unity-greeter/+bug/814235]("https://bugs.launchpad.net/unity-greeter/+bug/814235")

I am set to auto-login at boot, and lightdm boots me into Unity. If I log out, the default session for logging back in is Gnome Shell! What a world!

---

### Post by moore.bryan on 2011-07-21
Hmm... I guess autologin is "overriding" the unity-greeter's settings.

---

### Post by mc4man on 2011-07-21
When you get to the login screen there is a little 'wheel' icon in the top r. corner of login window

It lists the available sessions based on the display names of the .desktops in  /usr/share/xsessions and at least here is ordered alphabetically,  as in -

Gnome -(gnome-shell
Ubuntu -(unity
Ubuntu 2D

You have to pick one each time you login unless the enabled one is what you want
Here it always has Gnome selected so the default would be gnome-shell, to get unity I select Ubuntu each time

Edit : didn't see your autologin comment , was posting...

If you are picking Ubuntu and getting ubuntu-2d then you've either messed with something you shouldn't have  or you're being thrown back to unity-2d for lack of proper 3d support, real or otherwise

---

### Post by moore.bryan on 2011-07-21
> **mc4man said:**
> When you get to the login screen there is a little 'wheel' icon in the top r. corner of login window
Thanks, mc4man, I got this one under control.

> **mc4man]You have to pick one each time you login unless the enabled one is what you want[/quote]
That's just it said:**
> If you are picking Ubuntu and getting ubuntu-2d then you've either messed with something you shouldn't have  or you're being thrown back to unity-2d for lack of proper 3d support, real or otherwise
Sorry I didn't make myself clear... when I *select* "Ubuntu" I *am* logged-in to Unity3D and when I select "Ubuntu2D" it puts me into Unity2D. Once again, my issue is with ~/.dmrc not being parsed and the default Unity3D selected. It's not a *huge* deal to have to select which session each time, but it is enough of a PITA to irritate... and, besides, that not what lightdm *should* do. That's why I reported the bug. :-)

---

### Post by mc4man on 2011-07-21
> when I select "Ubuntu" I am logged-in to Unity3D and when I select "Ubuntu2D" it puts me into Unity2D. Once again, my issue is with ~/.dmrc not being parsed and the default Unity3D selected. It's not a huge deal to have to select which session each time, but it is enough of a PITA to irritate... and, besides, that not what lightdm should do.
That will certainly be coming with a future release.
I wasn't sure we we taking about the same 'default'

( While I was using it (the greeter), I wasn't using gnome-shell
So rather than have to pick Ubuntu each time I simply made Ubuntu the first listed choice so it was the one the greeter had enabled and would log in to without picking

---

### Post by moore.bryan on 2011-07-21
> **mc4man said:**
> That will certainly be coming with a future release.
I wasn't sure we we taking about the same 'default'

( While I was using it (the greeter), I wasn't using gnome-shell
So rather than have to pick Ubuntu each time I simply made Ubuntu the first listed choice so it was the one the greeter had enabled and would log in to without picking

How'd you make Ubuntu the first listed choice? If I could do *that*, it'd at least irritate me less. 

:-)

---

### Post by mc4man on 2011-07-21
> How'd you make Ubuntu the first listed choice? If I could do that, it'd at least irritate me less. 
That would depend on the order - top to bottom that they are listed in the login.

What I posted above is the order on a fresh install, there are only 3
Gnome
Ubuntu
Ubuntu 2D

I'm guessing you might have an older install where the order is
Ubuntu 2D
Ubuntu
whatever

There are 2 ways - one is to mv the .desktop listed above Ubuntu to a .bak, then it won't show up at all

The way to move lower in the list is to mv the .desktop to a new .desktop name

So what does this show?
ls /usr/share/xsessions/

And what is the order in the login drop down?

---

### Post by seeker5528 on 2011-07-21
> **mc4man said:**
> I'm guessing you might have an older install where the order is
Ubuntu 2D
Ubuntu
whatever


There doesn't seem to be any sanity there.

Personally I would have expected the default to be whatever you get when  you stop all the display managers and type 'startx' at the command line, but even that doesn't seem to be the case.

GDM and KDM list the sessions in alphabetical order, GDM indicates Ubuntu is the default, KDM doesn't give a visible indication of what is the default but indicates which session was last used.

LXDM and LightDM don't list the sessions in alphabetical order, and the order the sessions are listed are different from each other.

For me LigthDM lists Openbox at the top of the list, LXDM lists LXDM, then Openbox.

If I type 'startx' at the command line, then I get a Gnome session with Gnome shell. I suspect that is because the alternative for 'x-session-manager' is set to '/usr/bin/gnome-session'. OK, I used galternatives to change the 'x-session-manager' alternative to '/usr/bin/startlxde' and I get an lxde session when I type 'startx', so when doing that it must first look at 'x-session-manager' then if it doesn't find it fall back to 'x-window-manager'.

The interesting thing is if I reboot, sometimes it will log me into a Unity/Ubuntu session without having to select it first.

Later, Seeker

---

### Post by mc4man on 2011-07-21
> There doesn't seem to be any sanity there.
Can't quite see any either
On an older install where the list was 
Ubuntu 2D
Ubuntu
Ect.
Ect.

I moved Ubuntu to the top by 

```
sudo mv /usr/share/xsessions/ubuntu-2d.desktop  /usr/share/xsessions/2dunity.desktop
```

On newer where it was
Gnome
Ubuntu
Ubuntu 2d
```
sudo mv /usr/share/xsessions/gnome-shell.desktop  /usr/share/xsessions/gshell.desktop
```
Note - keeping the 'display' names of the .desktops the same (Name=
> If I type 'startx' ....

If you look in the various .desktops the Exec= line shows why - 
Gs is - Exec=gnome-session
Ubuntu is - Exec=gnome-session --session=ubuntu
ect,

---

### Post by Bowmore on 2011-07-21
I my cases, one Oneric originating from a Natty install and another being a fresh alpha2 installation they both respect the session setting in the .dmrc file. I also tested by changing the session manually in .dmrc after a login and rebooted and those cases worked as expected too.

Could it be a fallback issue, ubuntu3d to ubuntu2d initially or does it happen when selecting gnome shell or gnome fallback as well?

---

### Post by seeker5528 on 2011-07-21
> **Bowmore said:**
> I my cases, one Oneric originating from a Natty install and another being a fresh alpha2 installation they both respect the session setting in the .dmrc file. I also tested by changing the session manually in .dmrc after a login and rebooted and those cases worked as expected too.

It was working fine for me before I switched to the unity greeter, even after I switched it gave me the Ubuntu session, it worked until I updated this morning, but I don't see anything in the updates that seems like a likely suspect to me so I'm assuming for the moment that it was coincidental. 

> Could it be a fallback issue, ubuntu3d to ubuntu2d initially or does it happen when selecting gnome shell or gnome fallback as well?

My .dmrc file says 'Session=gnome', is this going off the name of the .desktop file or the 'Name=' line that is in the .desktop file?

Later, Seeker

---

### Post by mc4man on 2011-07-21
Ultimately this is just fool around stuff - it will work as intended.
My older install, due to an non fixable  kernel issue is a fresh  natty immediately upgraded to O around A2
The new install is from the 19th on different hardware

The are some significant differences between the 2, in this regard the only thing the same is the unity greeter always defaults to the top of the list. (~.dmrc ignored

But then again I've got some things maybe most others don't see - for instance atm most of the modal windows have no window decoration
So I'm gathering there could be a wide variation between anybody's install and someone else's

> My .dmrc file says 'Session=gnome', is this going off the name of the .desktop file or the 'Name=' line that is in the .desktop file?
Session= in ~/.dmrc points to the <whatever>.desktop which runs the Exec= in that .desktop

Edit: to show
in my new install when I pick "Gnome" I login to GS and this is the .dmrc (this is the install I mv'ed to  gshell.desktop

> [Desktop]
Session=gshell

---

### Post by seeker5528 on 2011-07-21
If I choose other, then type my username and password,I get the Ubuntu session, or I am assuming at this point whatever the last used session was.

EDIT: After logging in to a Lubuntu session, and logging out, choosing other still goes to Ubuntu instead of the last used session, even if I type the username first, then bring up the list.

Later, Seeker

---

### Post by mc4man on 2011-07-21
> **seeker5528 said:**
> If I choose other, then type my username and password,I get the Ubuntu session, or I am assuming at this point whatever you last used session was.
 
Later, Seeker
I believe 'other' does something a little different, don't exactly know, -  based on the still current bug about first time login where you need to use other once (more in reference to the default  lightdm and greeter.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/809890](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/809890)

Post 6 gives some info

---

### Post by seeker5528 on 2011-07-21
> **mc4man said:**
> based on the still current bug about first time login where you need to use other once (more in reference to the default  lightdm and greeter.

For me using the gtk-gnome greeter theme, it always crashes the greeter if I don't choose other at the login screen.

Later, Seeker

---

### Post by mc4man on 2011-07-21
> using the gtk-gnome greeter theme, it always crashes the greeter if I don't choose other at the login screen.

Maybe a fresh install would improve, maybe not.
For better or worse I'll probably do one at least once a week till beta
I see there is a new unity/nux upgrade, so if that doesn't improve my modal deco issue then I'll see if tommorrows iso fresh is any better.
I don't think there is any guarantee that an update will always fix  something that's gone a bit south

---

### Post by moore.bryan on 2011-07-21
None of the possibilities listed above do anything for me. In fact, renaming the .desktop files and then specifying that name in ~/.dmrc causes no shell to load at all.

---

### Post by seeker5528 on 2011-07-22
> **mc4man said:**
> Maybe a fresh install would improve, maybe not.

I never re-install unless the situation gets pretty extreme. Which typically would be hard drive failure or something that caused significant file/file system corruption.

Things may not always work like they do if you did a fresh install, but they still need to work, and the problems still need to be sorted out, whether it's something you have installed that may not get installed in a fresh install or some configuration that gets carried over as-is that should get updated.

Not to say you shouldn't do a fresh install, it all depends on your goals/priorites in testing, patience, maybe in some cases how stubborn/masochistic your are, etc...

Later, Seeker

---

### Post by CaptainMark on 2011-07-22
is this being included into 11.10 at standard btw??

---

### Post by moore.bryan on 2011-08-06
Has anyone else noticed unity-greeter being ignored after the latest round of updates?

---

### Post by VinDSL on 2011-08-06
> **moore.bryan said:**
> Has anyone else noticed unity-greeter being ignored after the latest round of updates?
Yes.

I returned from holiday 7 days ago - performed a massive update (more than 100 were waiting) - and unity-greeter hasn't worked since.

I was growing tired of it anyway, so I haven't tried to resurrect it.

---

### Post by moore.bryan on 2011-08-06
Well, at least it's not just me then! :-)

---

### Post by CaptainMark on 2011-08-06
no the package has been altered and the config files have been moved too, ive not got /etc/lightdm/lightdm.conf

---

### Post by moore.bryan on 2011-08-06
> **CaptainMark said:**
> no the package has been altered and the config files have been moved too, ive not got /etc/lightdm/lightdm.conf

I still have that config file... Where would the new config file be, if not in/etc/lightdm?

---

### Post by CaptainMark on 2011-08-06
i dont know, i installed the unity-greeter package on a fresh install a few days ago and just dont have this file i have these```
mark@desktop:~$ list lightdm.conf
/usr/share/doc/lightdm/lightdm.conf
/var/lib/dpkg/info/lightdm.conffiles
/var/lib/dpkg/info/lightdm.config
/etc/init/lightdm.conf

```

---

### Post by moore.bryan on 2011-08-06
> **CaptainMark said:**
> ```
mark@desktop:~$ list lightdm.conf
/usr/share/doc/lightdm/lightdm.conf
/var/lib/dpkg/info/lightdm.conffiles
/var/lib/dpkg/info/lightdm.config
/etc/init/lightdm.conf

```
What's this "list" command?
;-)

---

### Post by CaptainMark on 2011-08-07
ah thats just a lazy shortcut i made to save on typing, it runs```
find / -iname "*lightdm.conf*" 2>/dev/null
```

---

### Post by moore.bryan on 2011-08-07
I like it! Would you mind sharing the script?

---

### Post by klim8 on 2011-08-07
```

$ dpkg -S lightdm.conf

lightdm: /usr/share/doc/lightdm/lightdm.conf
lightdm: /etc/init/lightdm.conf
lightdm: /etc/lightdm/lightdm.conf

```

Much faster.

---

### Post by sgage on 2011-08-07
> **klim8 said:**
> ```

$ dpkg -S lightdm.conf

lightdm: /usr/share/doc/lightdm/lightdm.conf
lightdm: /etc/init/lightdm.conf
lightdm: /etc/lightdm/lightdm.conf

```

Much faster.

$ locate lightdm.conf

Fast as lightning :KS

---

### Post by lucazade on 2011-08-07
> **sgage said:**
> $ locate lightdm.conf

Fast as lightning :KS

you need this before :)

sudo updatedb
locate lightdm.conf

---

### Post by CaptainMark on 2011-08-08
it pretty basic but i find it helpful depending on what you are searching for ```
#!/bin/bash 

string=$1

if [ -z $string ]; then
	echo "Search criteria missing"
else
	find / -iname "*$string*" 2>/dev/null 
fi

```i then just put a symlink to it /bin
i had a specific reason for not using locate when i scribbled it down, something to do with the order of the output

---

### Post by moore.bryan on 2011-08-08
Thanks, CaptainMark. I also usually use locate, but the sudo updatedb can become a hassle if I've installed lots of programs recently, as is often the case running Oneiric.

sgage, that's also an elegant solution... I'm not sure how dpkg slipped my mind!

---

### Post by moore.bryan on 2011-08-09
Perhaps adding to the strangeness of what's happening... /usr/share/lightdm/themes/ no longer contains any reference to unity-greeter. I've also noticed /etc/init/ now has a lightdm.conf file, but it looks nothing like the "correct" one.

[http://pastebin.com/U4HDkcz5](http://pastebin.com/U4HDkcz5)

---

### Post by mc4man on 2011-08-11
At least here, updated, you can swicth to the unity greeter from cli if desired, though I still prefer the gtk one
Noting a restart is reqir. and the unity greeter is still lacking one
```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```
And when your sick of it to return

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

---

### Post by CaptainMark on 2011-08-11
unity-greeter has now been enabled by default and runs reasonably well, next step is waiting for the user unique backgrounds to be included

---

### Post by moore.bryan on 2011-08-11
> **mc4man said:**
> 
```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```
This worked for me.

> **CaptainMark said:**
> unity-greeter has now been enabled by default and runs reasonably well, next step is waiting for the user unique backgrounds to be included
It was not enabled by default for me; I had to use the above line to get it to work...

---

### Post by CaptainMark on 2011-08-11
perhaps did you alter the config files before the update? i had the package unity-greeter installed but had not altered any configs and when i booted yesterday i was greeted by unitys theme. 
oh well youve still got the theme, it looks cool, i cant wait for custom themes to start arriving,

i just hope its not another change like pidgin being switched for empathy, the reasons canonical chose that change sort of fizzled away,

---

### Post by moore.bryan on 2011-08-11
I hadn't changed anything, AFAIK, but it's possible. I also find the unity-greeter much better than "stock."

You can change the background by renaming whatever image you want to "warty-final-ubuntu.png" in /usr/share/backgrounds. I know it's a dirty fix, but it works...

---

### Post by moore.bryan on 2011-08-11
Spoke too soon. After a full restart, not just a log-out, unity-greeter doesn't show up. Nice.

EDIT:
Spoke to soon about speaking too soon... after eleven reboots, unity-greeter is now default. I wonder what the hell that was all about.

---

