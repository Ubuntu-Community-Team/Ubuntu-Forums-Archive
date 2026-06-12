---
title: "Ubuntu the Worst OS I Hath Ever Used In My Life"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by john_smith15 on 2014-06-28
Went to try out linux-Ubuntu for the first time as I'm not a geek programmer so Ubuntu should be more friendly from a former windows user; it's not...

I wanted to install Windows 7 theme into Ubuntu so I could work my way round and adapt gradually.  

Not much to ask from an OS to change a few appearances/themes etc.

So I paste this string of nonsense into the Ubuntu Console

sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install win-themes

and

sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update
sudo apt-get install win-icons

and 

sudo add-apt-repository ppa:freyja-dev/unity-tweak-tool-daily
sudo apt-get update
sudo apt-get install unity-tweak-tool

and

sudo add-apt-repository "deb [http://repo.mate-desktop.org/archive/1.8/ubuntu](http://repo.mate-desktop.org/archive/1.8/ubuntu) $(lsb_release -cs) main"

and

wget -q [http://mirror1.mate-desktop.org/debian/mate-archive-keyring.gpg](http://mirror1.mate-desktop.org/debian/mate-archive-keyring.gpg) -O- | sudo apt-key add -

and

sudo apt-get update
sudo apt-get install mate-core mate-desktop-environment mate-notification-daemon

and

I then select the Unity tool from the lol dash to select the themes that I want.

and what do I get for my efforts?

Absolutely nothing...

The icons change to windows lookalike yes that's great however... the - [] X controls are on the left hand side of the window, the menu/taskbar is locked to the ceiling, there is no programs list; instead I hath to go through the lol dash and select apps and scroll all the way down to run a program I want.

In addition you cannot move icons around and drag them to the desktop, you hath to go to great lengths to do the most simplistic of things.

To troll it all off the system reverts back to its default theme when I restart Ubuntu.

At this point in time I just want to crawl under a rock and just die this system hath ruined my life and my afternoon I was just getting into it.

The only reason I got into Ubuntu is because of Bitcoin security, however I think I'll abandon this little venture and just use the OS for offline wOllets as it's supposedly more secure than windows.

---

### Post by tgalati4 on 2014-06-28
Linux is an acquired taste.  It's better to learn it with the default themes and setup, since it is not Windows and does not behave like Windows.  Pasting commands that you don't understand is not recommended.  If you stick with it, in ten years or so, you may come to appreciate Linux.

---

### Post by kurt18947 on 2014-06-28
I want Windows 8 to look and work EXACTLY like Ubuntu.  How do you think I'll get along with that?  You might try installing Ubuntu or one of the 'flavors' unmodified and see if that works for you.  
Linux is NOT windows[URL="http://linux.oneandoneis2.org/LNW.htm"]
http://linux.oneandoneis2.org/LNW.htm[/URL]

---

### Post by robbie 348 on 2014-06-28
To the op. Did you not try it live first to see if you liked it before installing it and "ruining your life"?

---

### Post by buzzingrobot on 2014-06-28
Mate is an entire GUI -- desktop environment -- that *replaces* Unity.  It is not a theme.

To use Mate, log off.  Then, when you log in again, click the small icon to the right of your user name.  It's usually round and white.  A dropdown menu will allow you to select Mate.  That choice will remain in effect until you log out and in again and choose another interface.

Be aware that Mate is not officially supported in Ubuntu 14.04 and that the repository you drew from is also considered unofficial by the Mate developers due to unresolved issues with a few packages. (The Menu Editor and the User and Groups applets do not work.) That said, in my use here it's been fine.

Mate's initial appearance on Unity doesn't show it at it's best. Use the menus on the top panel and make your way to "Appearance".  Select "Fonts" and enable "slight" under hinting, and antialiasing to RGB.  "Appearance" is also where you enable different themes, etc. Explore the "Customize" tab on the Theme panel.

PPA's are unoffical and unsupported by Canonical.  Many of them work just fine, but you assume the risk when you install from these third-party sources.

Unity-Tweak-Tool is available in the Ubuntu repos.  No need to use a PPA.

You should not expect a theme -- a collection of colors and decorations -- to add fundamentally new code like a program menu, etc.  Unity and a Win7 lookalike theme seem like a pretty awkward mix to me.

---

### Post by Elfy on 2014-06-28
Thanks for joining the forum to tell us all about that - but as it's not a support request you'll not be requiring any help.

Closed.

---

