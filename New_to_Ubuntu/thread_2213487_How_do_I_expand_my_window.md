---
title: "How do I expand my window?"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by randy8 on 2014-03-26
Hi as of today 3-26-14, I'm completely new to Ubuntu operating systems.  I installed 13.10 from a CD into my desktop computer which used Windows XP before.  Now that I'm online I'm stuck in a window that covers maybe 50% of my screen and no matter what I try, I can't expand this screen.  There must be some kind of Ubuntu trick that I'm unaware of since all my Windows tricks failed.  I'm also confused as to why when I start my system, my desktop is completely blank and doesn't have one thing on it :(  Please help me

After I wrote this post, I did figure out how to expand the window to cover my full screen.  I wish they would have made it as easy as Windows does.  Now I'm still wondering why I'm greeted by a blank desktop and how I can intall something such as my Google Chrome browser on it.  I'm also wondering if this system has the equivalent of Windows "my computer?"

---

### Post by SuperFreak on 2014-03-26
Ubuntu Software Center will have all sorts of compatible programs you can install, mostly free. Open dash and type Ubuntu Software Center and it should come up.
Seriously this OS is not the same as Windows and you need to be prepared to learn a few new things to use it. You can probably use it in a graphical IE entirely although many people find the CLI (Command LIne Interface) the way to go.

---

### Post by Impavidus on 2014-03-27
Yes, Ubuntu is quite different from Windows. Because of its modular design and because everybody can replace parts of it whenever (s)he doesn't like the default, the system is far more configurable than Windows. Not only can you decide what your desktop looks like, but you can even replace it with a completely different desktop or no desktop at all.

Most of us prefer to start applications from docks, panels, menus, the dash (search function) or the command line, whatever interface we use, but if you wish you can put starters on your desktop too. For this you'll need a .desktop file. You can find .desktop files in the directory /usr/share/applications. Copy one of them to your desktop (drag-and-drop out of your file manager should do the job) and it will work as a launcher for that application. You can also open one of them in a text editor, study how they work, modify them or create your own.

I keep my desktop clean and use it as a weather monitor, displaying live satellite images of my part of the world. And in my user interface I have simple close/maximise/minimise buttons, just like in WinXP. But that is configurable too.

---

### Post by buzzingrobot on 2014-03-27
> **randy8 said:**
> Now that I'm online I'm stuck in a window that covers maybe 50% of my screen and no matter what I try, I can't expand this screen.

Looks like you found the the close/minimize/maximize buttons.  Press and hold the Windows key ("Super" key in Ubuntu parlance) for a second or so and it should generate a popup listing all the commands for manipulating the interface via the keyboard, if you prefer that approach.)

   > I'm also confused as to why when I start my system, my desktop is completely blank and doesn't have one thing on it

The Unity interface used in Ubuntu does not, by default, place icons on the desktop. The vertical row of icons on the left -- the Launcher -- is the intended location of icons for applications that you use regularly. When you launch an application, its icon will appear in the Launcher.  Then, a right click on that icon will display an option to "Lock" the icon into the Launcher. You can remove an icon from the Launcher via a right-click, as well.

When you minimize a window, it "returns" to its icon in the Launcher. If you click the icon of an application that's running *and* minimized to the Launcher, its window reopens. If the window is on another workspace, because you opened or moved it there, the display moves to that workspace.

To find applications so you can launch them, you can click on the icon at the top of the Launcher which will expose a window of icons. There are options on this window, so play around with it to get used to it.

Or, you can tap (not hold) the Super key and begin typing the name of an application.  A window will open displaying icons. When you have typed enough characters to identify that app, its icon will be in the top left corner.  This search mechanism is reasonably clever, in that you do not need to know the exact name of the application you are looking for.  For example, type "updater" should display icons for apps involved with updating your system.  (Easier to just try this than to imagine it.)

> ...how I can intall something such as my Google Chrome browser on it.  I'm also wondering if this system has the equivalent of Windows "my computer?"

For assorted reasons, Chrome is not available *from* Ubuntu.  Point your browser at [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/) and you be able to download and install it for Ubuntu. Chromium, the open source version of Chrome, is available from Software Center.

No specific "My Computer" equivalent exists. The "Files" (aka Nautilus) program is the file manager. There's an icon in the Launcher by default.  "System Settings" allows you to adjust a range of settings to your liking. (Icon in the Launcher and it's available from a dropdown menu generated by clicking on the icon in the far right of the top panel). In System Settings is a "Details" panel that displays some basic info about your system.

My best advice on getting used to Ubuntu is to go slow and, most importantly, understand that it is not designed to mimic Windows. If you insist on trying to make it work like Windows, you will quickly become frustrated. 

The command line:  A typical user can make full use of Ubuntu without resorting to the command line.  You will, however, come across many suggestions, fixes, etc. that use the command line.  This is because, first, it is much easier to include textual commands in a post or a comment than it is to try to write an accurate narrative that guides someone through a series of GUI operations.  Second, command line tools often do offer options and flexibility that their GUI counterparts do not.

(Linux began, and exists, as a open source version of the Unix operating system.  Unix development began more than 30 years ago, as an entirely character-based, command line oriented system because hardware at that time couldn't really support GUI operations. As a result, over the years Unix accumulated an extremely diverse and capable collection of command line tools. Hence, they are available in Linux. And, for that matter, in Apple's OS X, which is also a Unix and has the same command line capabilities underneath the GUI interface.)

---

### Post by randy8 on 2014-03-27
Thanks, right now I do have my window expanded to cover my full screen.   I haven't made any other kind of progress though.  It sure would be  nice if when I started my PC, my desktop wasn't blank.  Oh I do have  some empty folders on it, but that's it.  Now I'm searching for an easy  way to uninstall Ubuntu 13.10 :sad:

---

### Post by SuperFreak on 2014-03-27
I tried Ubuntu versions several times before I actually installed it permanently. Definitely need to learn the ropes before you can get accustomed to it. Desktop icons are not used by a lot of people although I do and they are in fact pretty easy to install. But you are deleting your Ubuntu partition so there is no point in discussing it further

---

### Post by buzzingrobot on 2014-03-27
> **randy8 said:**
> Thanks, right now I do have my window expanded to cover my full screen.   I haven't made any other kind of progress though.  It sure would be  nice if when I started my PC, my desktop wasn't blank.  Oh I do have  some empty folders on it, but that's it.  Now I'm searching for an easy  way to uninstall Ubuntu 13.10 :sad:

If you can't manage without icons on the desktop, there are other interfaces that can be installed and used on Ubuntu besides Unity. You don't need to uninstall it.  Just install a new interface:  KDE, XFCE, Mate are three popular interfaces that all support desktop icons.

Some of us, myself included, do not like desktop icons and remove them first thing on any interface that includes them by default.

Repartitioning will suffice to remove any Linux install.

---

### Post by 3rdalbum on 2014-03-28
I think he means that the only thing he can see on his screen is the desktop background. No Unity launcher, no top panel.

I don't know why you are having this problem, maybe just try reinstalling Ubuntu from a fresh CD in case your first CD was bad. Install it straight over the top of the existing Ubuntu. Or try a different version like 12.04 LTS, or something like Lubuntu.

---

### Post by pyrotheseus on 2014-03-28
Ubuntu is definitely different from windows. When I first replaced it a few days ago after only a couple days of experience using it, I nearly had a panic attack XD. It is definitely worth keeping and learning about though. It's tough, but it feels so epic when you can do a bunch of stuff from the command line, or have all of these amazing graphical effects. Just try and stick with it :)

---

### Post by buzzingrobot on 2014-03-28
> **3rdalbum said:**
> I think he means that the only thing he can see on his screen is the desktop background. No Unity launcher, no top panel.

I

Ah.  Hmmm.  If that's the case, the OP should try resetting Unity.  A Google of "reset Unity 13.10" will turn up lots of advice.  Here's one offering: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/). There are threads about this here in the forums, too.

---

### Post by grahammechanical on 2014-03-28
I would like the original poster to explain this comment:

> [COLOR=#000000]Now I'm still wondering why I'm greeted by a blank desktop[/COLOR]

There have been times when I have been testing versions of Ubuntu under development and I have got to a desktop with just a default background wallpaper or without any wallpaper. It is virtually impossible for an inexperienced user to open any applications. It has to be done through the terminal. If we can open a terminal.

I think that the issues this user is having are related to expecting Ubuntu to be Like XP. As we know application windows do have easily recognisable close/min/max buttons. They are on the left side instead of the right side. And we can also grab window edges and enlarge the window just like in a Microsoft OS. What Ubuntu does not give us is application icons on the desktop or cascading menu options.

We do have something that can help the new user. It is found under the power cog menu. It is called "Ubuntu Help." It is the Ubuntu Desktop User Guide. 

Regards.

---

