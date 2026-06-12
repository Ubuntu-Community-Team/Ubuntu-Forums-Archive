---
title: "LightDM to the default display manager for Oneiric"
date: 2011-06-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-08
Here is some info for LightDM in Oneiric.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

**What is LightDM?**
LightDM is a display manager. The most user visible aspect of the display manager is the login screen, however it also manages the X servers and facilitates remote logins using the XDMCP protocol. It is proposed to be the display manager in Ubuntu 11.10 (Oneric) replacing GDM which has been the display manager since the beginning. See the blueprint for more details.

The switch will mean two main things for Ubuntu users:

There will be a new login theme that better matches Unity. This is being designed and developed during the Oneric cycle. Until then a simple GTK login screen will be used.
There will be configuration changes for system administrators. Your feedback on how LightDM compares to GDM is very important, please file bugs and help out if there are features that are important to you.
Testing LightDM
Oneiric is scheduled to use LightDM by default in Alpha 2
You can install it by running:
```
sudo apt-get install lightdm lightdm-greeter-example-gtk
```

Running LightDM by default
If you have LightDM as your default display manager then it will just be there when you boot!
To switch the default run:
```
sudo dpkg-reconfigure lightdm
```

---

### Post by MacUntu on 2011-06-08
Where's the webkit greeter (there was one in the PPA IIRC)? Being able to theme the greeter using HTML/CSS is awesome. :D

---

### Post by jppr on 2011-06-08
Works fine :popcorn:

---

### Post by Harry33 on 2011-06-08
OK, now LightDM is the default diplay manager in Oneiric.

The latest meta package (ubuntu-meta 1.227) adds lightdm and drops gdm and gdm-guest-session from ubuntu-desktop.

> ubuntu-meta (1.227) oneiric; urgency=low

  * Refreshed dependencies
  * Added lightdm to desktop
  * Removed gdm from desktop
  * Removed gdm-guest-session from desktop-recommends

---

### Post by paul_in_london on 2011-06-08
Hmm. This is a bit weird.

I originally started using **lightdm** in Natty and it was working ok. Now and again I had to revert to **gdm** though. I had also been using this ppa:

```
https://launchpad.net/~robert-ancell/+archive/lightdm
```

but that ppa is now apparently obsolete.

At some point, **lightdm** stopped working on my two OO installs but it was still ok in my Arch install. Or maybe this happened before I upgraded to OO. I can't remember now.

When I tried re-enabling **lightdm** again last night OO was only booting to a blank screen so I just assumed it was broken and/or incompatible with something else in my setups without investigating any further and went back to **gdm**.

It now seems I must have forgotten to install or reinstall **lightdm-greeter-example-gtk** because I've just realised that **lightdm-greeter-example-gtk** was not installed on my OO VM @ work (**lightdm** itself was already installed) and when I installed that as well and re-enabled **lightdm** it was fine. :)

Btw, the Robert Ancell page on launchpad says:

> Please use [https://launchpad.net/~lightdm-team/+archive/ppa](https://launchpad.net/~lightdm-team/+archive/ppa)

so maybe I'll try adding that.

---

### Post by dino99 on 2011-06-08
My first break: cant log , i get the " oh something wrong have happened, please logout and try again" message

But neither lightdm or gdm, lxdm can log me in :( ; have tried each choice to log.

---

### Post by MacUntu on 2011-06-08
AFAIK that message comes from the session and has nothing to do with the greeter. They should give it blue background, though. >:****)

---

### Post by ronacc on 2011-06-08
I installed it in oneric via synaptic and it added the greeter as a "recommends"  , maybe that needs to be changed to a "depends" since unless you have "consider recommends as dependencies " enabled it wont be added automaticly .

---

### Post by paul_in_london on 2011-06-08
> **ronacc said:**
> I installed it in oneric via synaptic and it added the greeter as a "recommends"  , maybe that needs to be changed to a "depends" since unless you have "consider recommends as dependencies " enabled it wont be added automaticly .

@ronacc: Thanks for mentioning this.

Most of the time I use **aptitude** to install and update things (sometimes with the **--without-recommends** option depending on what I want, especially when I'm doing a minimal install), but I can't remember if I did that when I installed **lightdm**.

The only times I really use **synaptic** are (a) when running **aptitude full-upgrade** looks as if it's going to break things and I might look to see what **synaptic** would want to do or maybe (b) to purge obsolete packages/residual configuration files. 

Anyway, nice to see that it's working on the VM. Will find out later if it works for real. :)

---

### Post by 3vi1 on 2011-06-08
After installing lightdm and rebooting.  I managed to hang my Unity session on login (not sure why - I've been using KDE for the past couple of weeks, so that part's probably unrelated).  At any rate, I was stuck at a screen with just my wallpaper.

So I ctrl-alt-1'd to a terminal and did 'sudo service lightdm restart', as I normally do with GDM and KDM to kill goofed up sessions and get back to the login.

The lightdm service was stopped and restarted... but no login session ever appeared.  The wallpaper from the hung session stayed.

I tried it twice, same results.

---

### Post by 3vi1 on 2011-06-08
K - found a couple of problems.

When I use lightDM instead of GDM and boot into my KDE desktop, there are two differences:

[LIST]
[*]~/bin is not automagically added to my path.
[*]The KDE 'leave' menu tab does not have the shutdown or reboot options.
[/LIST]

Switching back to GDM or KDM gets ~/bin added to my path at login.

EDIT:  Found the relevant bug on Launchpad.  Please mark it as affecting you if you think this is annoying:  [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315)

---

### Post by portis on 2011-06-08
Lightdm seems not support fingerprint authentication.
So I'll stay with gdm.

---

### Post by Harry33 on 2011-06-08
> **paul_in_london said:**
> Hmm. This is a bit weird.

I originally started using **lightdm** in Natty and it was working ok. Now and again I had to revert to **gdm** though. I had also been using this ppa:

```
https://launchpad.net/~robert-ancell/+archive/lightdm
```

but that ppa is now apparently obsolete.
...


LightDM with greeters are in official repos of Oneiric and Natty too.
So no need to use PPA's.

---

### Post by sparker256 on 2011-06-08
No luck for me. Get a black screen with pointer or cursor.

I did a ctrl+alt+F1 to enter the command
```
 sudo dpkg-reconfigure gdm
``` 
which got my login back after a reboot.

 I got today updates using
```
 sudo aptitude update && sudo aptitude safe-upgrade
```
The following was installed
```
 
lightdm 0.3.7-0ubuntu1
lightdm-greeter-example-python-gtk 0.3.7-0ubuntu1

```
Added and all is well
```
lightdm-greeter-example-gtk 0.3.7-0ubuntu1
```
Thanks Bill

---

### Post by Starks on 2011-06-08
[http://mjg59.livejournal.com/136274.html](http://mjg59.livejournal.com/136274.html)

The criticism begins.

---

### Post by lucazade on 2011-06-08
> **Starks said:**
> [http://mjg59.livejournal.com/136274.html](http://mjg59.livejournal.com/136274.html)

The criticism begins.

..and Bryce Harrington replied to these Matt's critics in Ayatana ML:

"Boiling Matt's post down this is what I'm reading:

  1. NIH
  2. It doesn't start a GNOME session
  3. Doesn't have arbitrary shiny stuff like slidy effects
  4. Auto-update when users are created or deleted
  5. Accessibility functionality UI
  6. Gratuitously drawing a clock
  7. Handle power policy via gnome-power-manager rather than via upower

#1 yeah but whatever.  #2 seems like a feature unless proven otherwise.
#3 who cares.  #4 ok, fair point, seems minor though.  #5 important, but
I think already under development.  #6 yeah right.  #7 huh?

Anyway, I greatly respect mjg59 but find this particular post not very
constructive."

[https://lists.ubuntu.com/archives/ubuntu-desktop/2011-June/003095.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2011-June/003095.html)

We'll see...

---

### Post by MacUntu on 2011-06-08
> **Starks said:**
> The criticism begins.
Check your calendar! :P

It's either a win or a fail. A fail is not the end of the world (we obviously survived Xsplash)...

---

### Post by ronacc on 2011-06-08
I think his point is "when you set out to reinvent the wheel don't be surprised when it ends up round" .

---

### Post by Harry33 on 2011-06-08
In order to have a working lightdm you must install both these packages (in Ubuntu):
- lightdm
- lightdm-greeter-example-gtk

The package lightdm-greeter-example-python-gtk is not necessary.

---

### Post by 23dornot23d on 2011-06-08
I have them installed - the LightDM greeter sits between the two monitors on a dual monitor 
system .....

---

### Post by jwcalla on 2011-06-08
i feel a little queasy about the state and future of gnome

it seems like whenever users have legitimate criticisms (like "yo dude, you took away our remote desktop login option") their response is typically "oh well tough crap good luck with your life".

Maybe after awhile it began to grate a bit on the folks at canonical.

---

### Post by TerminX on 2011-06-08
LightDM really seems to need some work before it's ready for primetime.  It's completely screwed when you're using an NVIDIA multi-monitor setup with TwinView (everything is centered across the two monitors whereas GDM is smart enough to throw the actual login dialog on the primary monitor), and it doesn't seem to automatically restart itself when you Alt+SysRq+k.  I'll definitely be sticking with GDM for now.

---

### Post by MacUntu on 2011-06-08
> **TerminX said:**
> LightDM really seems to need some work before it's ready for primetime.  It's completely screwed when you're using an NVIDIA multi-monitor setup with TwinView (everything is centered across the two monitors whereas GDM is smart enough to throw the actual login dialog on the primary monitor), and it doesn't seem to automatically restart itself when you Alt+SysRq+k.  I'll definitely be sticking with GDM for now.

You are using pre-pre-pre-production software and you're complaining about it not being ready for prime time? Seriously?

---

### Post by TerminX on 2011-06-08
I'm complaining that LightDM is nowhere near complete enough to even be considered as the default login manager in a major distro at this point in time.

Something like a login manager is far too important a piece of the system to be actively developed concurrently with the distro's development cycle.   It leaves very little or no time for the kind of thorough testing something like this realistically should have.  Using "pre-pre-pre-production software" for such an important part of the system is the problem in the first place.

I think we would be a lot better off if the development continued as it is now but the actual adoption of it was deferred until Ubuntu 12.04 or so.

---

### Post by seeker5528 on 2011-06-08
> **lucazade said:**
> 
Anyway, I greatly respect mjg59 but find this particular post not very
constructive."

As a Gnome centric response to the [proposal in the Gnome mailing list](http://mail.gnome.org/archives/desktop-devel-list/2010-October/msg00226.html) he was responding to....>   Let's go back to the comparisons of code size. LightDM's simple GTK greeter is about 1000 lines of code. gdm's greeter is almost 20,000. Some of this is arbitrary shiny stuff like the slidy effects that occur, but a lot of it is additional functionality. For example, some of it is devoted to handling the interface with AccountsService so gdm can automatically update when users are created or deleted. Some of it is providing UI for accessibility functionality. Some of it is drawing a clock, which I'll admit may be a touch gratuitous.....makes sense.

Relative to what the [Light Display Manager](https://launchpad.net/lightdm) and [Blueprint](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-desktop-n-display-manager) pages indicate.

[quote]The entirety of LightDM's design is based on a false premise

Doesn't make so much sense to me.

And...
>  For example, one of the reasons gdm starts a local gnome session is that it wants gnome-power-manager to be there to handle power policy.

That begs the question in my mind.... Why is Gnome using something that requires a gnome session to handle a system wide policy? That sounds like pointing out a bad idea to justify another bad idea to me. 

Is Upower only able to provide system wide power management control, without a way to store system wide power management policies?

Later, Seeker

---

### Post by wnelson on 2011-06-08
lxdm is so much lighter on resources that lightdm! Easier to configure also.

---

### Post by 23dornot23d on 2011-06-09
With Lightdm active ..... 

I have not been able to log out or power off from the desktop
replaced it with another desktop manager and I can now .....

---

### Post by ronacc on 2011-06-09
I tried lightdm for a couple of days with no major problems , I didn't really push it hard . The only things I noticed were that I lost my timed login and had to log in manualy and I could not select the type of session at log in . I was running it on an up to date onerick 64bit with gnome-shell , my specs Amd64X2 4600 , 4 gig mem , nvidia 7600gs , samsung monitor .

---

### Post by Harry33 on 2011-06-09
> **ronacc said:**
> I tried lightdm for a couple of days with no major problems , I didn't really push it hard . The only things I noticed were that I lost my timed login and had to log in manualy and I could not select the type of session at log in . I was running it on an up to date onerick 64bit with gnome-shell , my specs Amd64X2 4600 , 4 gig mem , nvidia 7600gs , samsung monitor .

I have LightDM in my 64-bit Oneiric setup, fully updated (except the newest glib2.0) with Gnome-shell.
And I can choose the session from LightDM login screen.

---

### Post by 23dornot23d on 2011-06-09
> **Harry33 said:**
> I have LightDM in my 64-bit Oneiric setup, fully updated (except the newest glib2.0) with Gnome-shell.
And I can choose the session from LightDM login screen.

I had the latest too - but mine was 32 bit ..... it would let me into my sessions and either of the users ok ...

It just would not let me exit nicely out of them ...... ;)

Update - ( might be Gnome-Shell that wont allow the logout - shutdown - just read another user had a similar problem )
Although thinking about this .... I changed to gdm and it was ok ...... but I also downgraded Gnome-Shell too .....

---

### Post by ronacc on 2011-06-09
> **Harry33 said:**
> I have LightDM in my 64-bit Oneiric setup, fully updated (except the newest glib2.0) with Gnome-shell.
And I can choose the session from LightDM login screen.

you're right , sometimes I can be rather stupid , I was looking in all the wrong places for the selection:(

---

### Post by seeker5528 on 2011-06-09
> **23dornot23d said:**
> Update - ( might be Gnome-Shell that wont allow the logout - shutdown - just read another user had a similar problem )
Although thinking about this .... I changed to gdm and it was ok ...... but I also downgraded Gnome-Shell too .....

I couldn't log out from Lubuntu either while using lightdm.

In addition to that opening a terminal window and typing ```
sudo stop lightdm
``` resulted in a complaint that 'no such service exists' or some words to that effect, in spite of the fact that when no display manager is running I can type 'sudo start lightdm' to start lightdm. 

Doing 'SysReq'+'K' resulted in output to the monitor being killed so with no visual clues as to what was going on I did 'SysReq'+'B' to reboot.

From the Lubuntu shutdown/logout screen, choosing reboot does work, I'm guessing shutdown would work too.

I did find '~/.xprofile' wasn't being sourced, I figured this bug report was probably close enough.....

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315)

... and added myself as being affected.

Later, Seeker

---

### Post by ronacc on 2011-06-09
I think you got the syntax wrong shouldn't it be ? 
```
 sudo lightdm stop 
``` or ```
sudo service lightdm stop
```

---

### Post by cariboo on 2011-06-09
> **ronacc said:**
> I think you got the syntax wrong shouldn't it be ? 
```
 sudo lightdm stop 
``` or ```
sudo service lightdm stop
```

On my one system with lightdm, that doesn't work, I've been using Ctrl-Alt-F! to get to a console, and Ctrl-Alt-Del to reboot.

---

### Post by ronacc on 2011-06-09
I keep a couple of icons on my desktop , one being a terminal so I can sudo reboot , of course dropping to console is an option also .

---

### Post by seeker5528 on 2011-06-09
> **ronacc said:**
> I think you got the syntax wrong

I think in the past you would have had to type the full ```
sudo service lightdm stop
sudo service lightdm start
```

But nowadays all you should have to do is ```
sudo stop lightdm
sudo start lightdm
``` assuming the upstart initialization is done correctly when it is started so it's actually recognized as a running service when you try to stop it. I did try it both ways. Works with GDM, KDM, and LXDM.

Later, Seeker

---

### Post by 3vi1 on 2011-06-09
> **ronacc said:**
> I keep a couple of icons on my desktop , one being a terminal so I can sudo reboot , of course dropping to console is an option also .

Set yakuake to autostart on boot.  You'll thank me for the suggestion later.  :)

Not only is it a great terminal app, but I've found that I can hang the desktop at times and the key to drop down the yakuake console almost always still works.

---

### Post by 3vi1 on 2011-06-09
> **TerminX said:**
> and it doesn't seem to automatically restart itself when you Alt+SysRq+k.

Yeah - I noticed that too.  :(

---

### Post by ronacc on 2011-06-09
> **3vi1 said:**
> Set yakuake to autostart on boot.  You'll thank me for the suggestion later.  :)

Not only is it a great terminal app, but I've found that I can hang the desktop at times and the key to drop down the yakuake console almost always still works.

I often do have yakuake running ( when I remember to install it ) thanks for the reminder :D

---

### Post by inportb on 2011-06-10
Hm... is LightDM still the default? I've been updating daily, but KDM is still my default (and only) display manager.

---

### Post by 23dornot23d on 2011-06-10
Is lightdm ok now on Dual monitors .... and will it let me log out .....

as I will test it  again if needed ..... ( I might as well anyway )

Still sits between the two monitors .... but I like the way it sets it out for the 6 users ....

still not able to log out or shutdown ..... but that was also the same using kdm too ....

actually doing (ctrl + alt + del) is giving me the logout screen now which is ok again ......

spoke too soon .....

re-booted ..... ( and the large text worked the high contrast worked ...... for the menu )
but I could not get into any of my sessions ..... purple screen nothing else .... 

ctrl + alt + del had no effect this time .... and fan spun up - nothing happening on the display.
had to kill it to get out    alt + k + sysreq

Tried 3 times to get back in and no good ..... Nvidia graphics on this and dual monitor .... 
Acer Aspire Laptop 7730

_________________________________________

Swapped back to GDM and everything is fine again ......

---

### Post by Starks on 2011-06-11
LightDM + GNOME-Shell = Login twice

Once for LightDM. Once for GDM.

---

### Post by 23dornot23d on 2011-06-11
Seems to be  the case at the moment ..... will keep checking it out though as it develops.

---

### Post by Framli on 2011-06-11
Annoying bugs I have with LightDM:
- I can't launch scripts that are in my ~/bin folder
- my locale isn't recognized, inducing a lot of other bugs

These will be obviously fixed once Lightdm is more integrated with the session, but I wonder how it will work with an encrypted home folder.

---

### Post by seeker5528 on 2011-06-11
> **inportb said:**
> Hm... is LightDM still the default? I've been updating daily, but KDM is still my default (and only) display manager.

The ubuntu-desktop and xubuntu-desktop metapackages depend on lightdm, so if you don't have one of those install lightdm won't get pulled in.

Based on what is typical in these situations, the expectation is that lightdm is what gets used in a new install, but when lightdm is pulled in as part of an upgrade, whatever is currently being used at the time continues to get used.

If you install it from the command line with the command ```
apt-get install -plow lightdm
```

If you set things up so recommends do not get treated as dependencies you will also have to install one of the greeters lightdm-greeter-example-qt, lightdm-greeter-example-gtk, lightdm-greeter-example-vala-gtk, or lightdm-greeter-example-python-gtk. 

Even if recommends are being treated as dependencies I suspect you may have to specify a greeter since it looks like lightdm recommends lightdm-greeter, which is not an actual package but something provided by the lightdm-greeter-example-* packages. 

Later, Seeker

---

### Post by jerrylamos on 2011-06-11
10 June daily build Live here.  The lightdm in the daily build is down level (!) so crash report wouldn't even run.  I had to boot in recovery, do 
sudo dhclient  
sudo apt-get install lightdm.

That got going long enough to get synaptic up, then mark all upgrades.  All 116 of them!!

Boy is the daily build way way down level.

Anyway I'm in persistent mode so I can reboot with the upgrades still effective.

This pc has 766 MB which is nearly full, 56 MB free.  For some reason the Swap is nearly empty.  One crash wouldn't report because there wasn't enough free memory.

Jerry

---

### Post by MacUntu on 2011-06-11
My ?ocale s?tting? are fu??ed ?p! :>

---

### Post by Harry33 on 2011-06-11
> **MacUntu said:**
> My ?ocale s?tting? are fu??ed ?p! :>

Is that due to LightDM packages?

---

### Post by Starks on 2011-06-11
I'm getting boot->ldm->gdm


Not normal I guess.

---

### Post by MacUntu on 2011-06-11
> **Harry33 said:**
> Is that due to LightDM packages?

I'm actually not sure what caused it, but my ~/.dmrc contained an invalid *Language *value (en_US instead of en_US.utf8****).

---

### Post by seeker5528 on 2011-06-11
> **Starks said:**
> I'm getting boot->ldm->gdm


Not normal I guess.

I've never had a problem with it in Debian, but in Ubuntu changing display managers seems a bit quirky some times.

If you do dpkg-reconfigure twice, once for the display manager you want to replace and once for the one you want to switch to, that seems to do it usually. So if switching from GDM to LightDM....

```
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure lightdm
```

The second time all you should have to do is hit enter when the selection dialog comes up since it should already be defaulted to the one you previously selected.

Later, Seeker

---

### Post by jerrylamos on 2011-06-14
> **inportb said:**
> Hm... is LightDM still the default? I've been updating daily, but KDM is still my default (and only) display manager.

Updating daily doesn't do it.  There will be additions coming in that aren't caught by update.  Install or Live may show the display manager, I assume you're downloading kubuntu daily build?

Jerry

---

### Post by Quadunit404 on 2011-06-14
afaik LightDM is currently default in vanilla Ubuntu and Xubuntu.

---

