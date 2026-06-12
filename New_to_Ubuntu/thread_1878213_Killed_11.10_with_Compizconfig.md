---
title: "Killed 11.10 with Compizconfig"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Azrael84 on 2011-11-09
Hi,

I didn't see the warning for this program for ubuntu 11.10 and blindly installed compizconfig-settings manager  (CCSM) on my machine. I opened it up and changed some setting to try and customise window behaviour, then all hell broke loose. After a restart I have no unity sidebar, I have no internet connection, the top bar has gone and been replaced with some drop downs (File...), it's a total mess.

I can still log in to a semi normal desktop by selecting unity 2D upon sign in, although still no internet....so I tried to uninstall CCSM thinking that may fix things (this was before reading another possible fix that needed CCSM so I could select unity plugin and resolve some issues; now I can't do that as I can't get CCSM back because no internet). I've also tried moving .gconf/.gnome/.gnome2 to a temp folder named /bak in my home directoy as I read that worked on another site, but these folders just reappear in my home directory upon logging back in and nothing changes....

Has anyone got any idea how I can fix things and go back to my original desktop? I really don't want to have to reinstall...what a nightmere..

---

### Post by sikander3786 on 2011-11-09
Please take a look at this troubleshooting guide and let us know how that goes:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by mhjones on 2011-11-09
I have had the same issue.  I tried several "fixes" I found around the net, but still at a loss.

I finally went to Gnome 3, and I have decided to stay there.  So much for Unity.

---

### Post by Azrael84 on 2011-11-09
Think I may struggle with some of that guide due to lack of internet...so can't do apt-get's etc ,will have a go though...

How do I go back to gnome if I can't fix things? and why is this affecting the internet?

---

### Post by vallvi on 2011-11-09
I had something similar, and this solved my problem:
[http://ubuntuforums.org/showthread.php?p=11391671#post11391671](http://ubuntuforums.org/showthread.php?p=11391671#post11391671)

Tried signing in as 'guest'? that gave me back my internet

---

### Post by philinux on 2011-11-09
> **Azrael84 said:**
> Hi,

I didn't see the warning for this program for ubuntu 11.10 and blindly installed compizconfig-settings manager  (CCSM) on my machine. I opened it up and changed some setting to try and customise window behaviour, then all hell broke loose. After a restart I have no unity sidebar, I have no internet connection, the top bar has gone and been replaced with some drop downs (File...), it's a total mess.

I can still log in to a semi normal desktop by selecting unity 2D upon sign in, although still no internet....so I tried to uninstall CCSM thinking that may fix things (this was before reading another possible fix that needed CCSM so I could select unity plugin and resolve some issues; now I can't do that as I can't get CCSM back because no internet). I've also tried moving .gconf/.gnome/.gnome2 to a temp folder named /bak in my home directoy as I read that worked on another site, but these folders just reappear in my home directory upon logging back in and nothing changes....

Has anyone got any idea how I can fix things and go back to my original desktop? I really don't want to have to reinstall...what a nightmere..
 [http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

Reset unity

---

### Post by ahmed.cnbd on 2011-11-09
Gnome is more stable than unity 
unity is just beautiful but not stable at all

---

### Post by alphacrucis2 on 2011-11-09
> **Azrael84 said:**
> Hi,

I didn't see the warning for this program for ubuntu 11.10 and blindly installed compizconfig-settings manager  (CCSM) on my machine. I opened it up and changed some setting to try and customise window behaviour, then all hell broke loose. After a restart I have no unity sidebar, I have no internet connection, the top bar has gone and been replaced with some drop downs (File...), it's a total mess.

I can still log in to a semi normal desktop by selecting unity 2D upon sign in, although still no internet....so I tried to uninstall CCSM thinking that may fix things (this was before reading another possible fix that needed CCSM so I could select unity plugin and resolve some issues; now I can't do that as I can't get CCSM back because no internet). I've also tried moving .gconf/.gnome/.gnome2 to a temp folder named /bak in my home directoy as I read that worked on another site, but these folders just reappear in my home directory upon logging back in and nothing changes....

Has anyone got any idea how I can fix things and go back to my original desktop? I really don't want to have to reinstall...what a nightmere..

Try 

<cntrl -alt f1>

login and then

```
unity --reset
sudo shutdown -r now

```

---

### Post by Azrael84 on 2011-11-09
Thanks for the replies, I followed the guide posted here: [http://ubuntuforums.org/showthread.php?t=1863905](http://ubuntuforums.org/showthread.php?t=1863905) post #2, and have back it seems most features of my system, the sidebar, top panel, tray in right hand corner etc...However I still have no wireless internet! I found I can get online with a wire but for some reason not wirless, I've no idea how messing with compiz has affected that, could anybody help?

EDIT: oops, the wireless thing was just me being an idiot: I had accidently pressed the wireless on off switch with flicking between tty's attempting various fixes (the hardware wireless on/off switch doubles with my f2 key), sorry.

Looks like I'm back to normal, phew. Thanks for all the great help.

One last question since CCSM is screwy for 11.10 is there some other way to tweak settings that wont destroy my desktop? cheers

---

### Post by anewguy on 2011-11-09
Let's face it - the real reason for Unity is so that eventually Ubuntu can be installed on phones and tablets and the interface will already be there and will be the same between your PC, phone or tablet.  If I wanted a common interface between my phone, tablet and PC I would ask for it - I don't.  Unity to me serves no real purpose unless you have a touch screen.

That's just my opinion.

Messing with desktop effects and Unity results in a real mess for me as well.  If you decide you want to enable the desktop cube - there goes Unity, and your desktop will probably be an insane mess - mine was.  I gave up on special effects for now.

Dave ;)

---

### Post by Favux on 2011-11-09
The OP ran into this bug:  [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861643](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861643)  Easy fix a few posts up.  Bug found and apparently fixed and coming in an update soon, with luck.  As you can see the Profile object's label gets corrupted.

---

### Post by anewguy on 2011-11-14
Mine will let me set things - like enable the cube - but then watch as you can't do anything with the desktop.  The top bar only shows a file/edit/etc., menu for the current window, nothing else, and no unity menu.  The only thing I've been able to do is go in a terminal and force a restart, go to recovery mode and then do a unity --reset.  I know enabling the cube removes something like the large desktop or some such thing such that the plugin for Unity won't run.

Been around this many times.  Since to me at least it's just eye candy I just gave up on using the cube, etc., with Unity.


Dave ;)

---

### Post by anewguy on 2011-11-21
Anyone who feels like I do regarding Unity and being prepped for other devices, see the Windows 8 developer release (pre-beta).  They even tell you there that the new interface is best with a touch screen.  Guess where they are also going with their OS.

Dave ;)

---

### Post by lolpenguin on 2011-11-22
> Let's face it - the real reason for Unity is so that eventually Ubuntu can be installed on phones and tablets and the interface will already be there and will be the same between your PC, phone or tablet. If I wanted a common interface between my phone, tablet and PC I would ask for it - I don't. Unity to me serves no real purpose unless you have a touch screen.

That's just my opinion.

Messing with desktop effects and Unity results in a real mess for me as well. If you decide you want to enable the desktop cube - there goes Unity, and your desktop will probably be an insane mess - mine was. I gave up on special effects for now.

Dave :)
> Anyone who feels like I do regarding Unity and being prepped for other devices, see the Windows 8 developer release (pre-beta). They even tell you there that the new interface is best with a touch screen. Guess where they are also going with their OS.

Dave :)
Unfortunately to all desktop power users, the future of desktop computing is clear.
It will not survive.
With netbooks, tablets, smartphones, and now Ultrabooks(TM), most people have shifted from the traditional desktop to the portable computers.
Ubuntu had a netbook remix from way back, netbook edition in maverick, and now the UI has been integrated into the desktop edition. GNOME had to take this approach too, with GNOME Shell.
MacOS was usuable on smaller screens since MacOS X, and there's iOS for tablets and smartphones.
Windows has just shown off it's Metro UI in the Windows Developer Preview, and it too is optimised for smaller screens and touchscreens.
Gone are the days of GNOME Panel. Soon, the whole idea of desktop computing will be gone too, with high-powered notebooks and Ultrabooks being able to run high-performance games and edit videos, the Internet will be accessed from tablets and netbooks, and the smartphone will fill all the gaps and run games and browse the web.
[U][B]If you killed the Unity interface, GNOME 3 is an alternative. But to restore Unity run this:
[/B][/U]```
unity --reset
```[B][U]
Do NOT sudo this command or you will reset the root user's Unity not yours.[/B][/U]

---

### Post by anewguy on 2011-11-25
While I own a nice laptop and an Android tablet, I still prefer my desktop for a lot of things.  However, if someone was to make me a decent offer on my desktop I could go without it ;)

I really don't like Unity myself - just personal opinion only.  I don't want it on my laptop at all, for example.  However, trying to get Gnome 3 working in 11.10 has been, well, an "uncomfortable" frustrating experience that has also gotten me nowhere.  

I come from way back, and when we had proprietery OS's we still didn't make "jumps" like this without some easing into it.   Just to me, this jump to Unity was a little ill-timed.

Dave ;)

---

### Post by sophia911 on 2011-11-25
Did you solve it ? 
I have a friends met it before and it is ok now . 
I can contact him .

---

### Post by lolpenguin on 2011-11-25
> **anewguy said:**
> While I own a nice laptop and an Android tablet, I still prefer my desktop for a lot of things.  However, if someone was to make me a decent offer on my desktop I could go without it ;)

I really don't like Unity myself - just personal opinion only.  I don't want it on my laptop at all, for example.  However, trying to get Gnome 3 working in 11.10 has been, well, an "uncomfortable" frustrating experience that has also gotten me nowhere.  

I come from way back, and when we had proprietery OS's we still didn't make "jumps" like this without some easing into it.   Just to me, this jump to Unity was a little ill-timed.

Dave ;)
Hehe, we all feel this way at first, but eventually we have to change, and as support for outdated proprietary software is dropped, and official support for OS software is dropped. But funnily enough, KDE4 came to this issue some time ago, and has come through quite well, emerging as the top alternative to GNOME!
As for the "jumping" the Natty release of Unity *was* ill-timed, but if you used the Netbook edition/remixes before you would know the Unity pretty well, and for desktop users, the Oneiric release of Unity is much more polished and beautiful (but compiz is not quite stable _enough_)
This thread should be marked as solved now, and as with all threads regarding a broken Unity interface, unity --reset is the universal solution.

---

### Post by JRV on 2011-11-25
> **Azrael84 said:**
> 
One last question since CCSM is screwy for 11.10 is there some other way to tweak settings that wont destroy my desktop? cheers

You can tweak Unity.  In CCSM you can use the Ubuntu Unity Plugin to change some settings.  You can uncheck "Grid" under Window Management to stop a window from automaximizing when dragged to the top of the screen.  At the very bottom there is an option to enable Unity MT Grap Handles. It is good idea to stay out of almost everything else.

You can install a pre-release version of ubuntu-tweak. This is a work in progress, some things don't work.  It is in active development and getting better all the time.  It installs with the command:
```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

Gnome-tweak-tool works to change themes, and probably some other things I have not tried yet. Install it with the command:
```

sudo apt-get install gnome-tweak-tool 

```

---

### Post by anewguy on 2011-11-27
> **lolpenguin said:**
> Hehe, we all feel this way at first, but eventually we have to change, and as support for outdated proprietary software is dropped, and official support for OS software is dropped. But funnily enough, KDE4 came to this issue some time ago, and has come through quite well, emerging as the top alternative to GNOME!
As for the "jumping" the Natty release of Unity *was* ill-timed, but if you used the Netbook edition/remixes before you would know the Unity pretty well, and for desktop users, the Oneiric release of Unity is much more polished and beautiful (but compiz is not quite stable _enough_)
This thread should be marked as solved now, and as with all threads regarding a broken Unity interface, unity --reset is the universal solution.

I've come "all the way up" on Ubuntu for a long time, including having the netbook remix on a netbook I used to have and replacing remix with what in those days would have been the default download for Ubuntu like you would use on any other machine.  It's not a matter of "hehe we all feel this way at first....".  I'm not against change - I am, however, against being fed something like Unity when it obviously is an attempt to use a common (hence "Unity") interface when that interface is not conducive on a desktop or laptop unless you have a touch screen.  The developer preview release of Windows 8 also has a front-end which they even say works best with a touch screen.

And no, unity --reset is NOT the universal solution.  Might solve problems for you - but definitely not for me.  Been there done that a long way back in this process.

---

### Post by anewguy on 2011-12-09
Just another example of what I've been saying about Unity - this time it's Windows 8 taking the hit.  For those who don't know, Windows 8 has a front-end that is meant for touch screen devices.

[http://news.cnet.com/8301-10805_3-57337636-75/will-windows-8-be-irrelevant-to-regular-pc-users/]("http://news.cnet.com/8301-10805_3-57337636-75/will-windows-8-be-irrelevant-to-regular-pc-users/")

To me, the same comments about the portable versus desktop uses of such an interface apply across the board on OS's.

---

