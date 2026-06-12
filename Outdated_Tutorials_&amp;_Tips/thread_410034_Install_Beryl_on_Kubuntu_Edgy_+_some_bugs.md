---
title: "Install Beryl on Kubuntu Edgy + some bugs"
date: 2007-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by vivia on 2007-04-15
Hey,

I would like to describe here my complete experience with Beryl - from preparing, installing it, and fixing a few bugs. I am using Kubuntu Edgy on an i386 machine. There are many HOWTO's out there which describe the installing process, so I will just tell you which ones I used and then focus on the problems I had and how to solve them.

I started by following this HOWTO: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

However, I used Treviño's repository: [http://ubuntuforums.org/showthread.php?t=279456](http://ubuntuforums.org/showthread.php?t=279456) which contains the latest SVN version of Beryl, untested and unsupported. It always contains the latest changes and bugfixes, but it might still be very buggy. If you don't feel like experimenting and would like to go for something stable and older, use the repositories from the first HOWTO.

I ran into the following bugs:

1) The infamous NVIDIA black-window bug.

It was annoying, because after running 4 xterm sessions and one aMSN (plus all background toys), I couldn't open a full-screen Firefox.

WARNING: Some people state that the NVIDIA driver revision 9755 solves the bug for them. Well, not for me. Apart from this, there is no .deb for 9755 so you have to run their compiler. I'd say that it's not worth the effort.

SOLUTION: As stated in the first HOWTO, I had to select Copy rendering. It is a bit slower indeed, but it's usable not annoyingly slow.

UNDO: If you don't like Copy rendering, you can select Automatic again, and good luck with the bug! (Useful with those who have a lot of video memory and don't open many windows)

2) Desktop switching in KDE.

The "desktop preview and pager" applet was acting up when I started beryl.

PREVIOUS WORKAROUND: I started a gnome-panel under KDE (lol), made it transparent, and moved my taskbar and desktop preview there. It seemed to work OK with earlier Beryl versions, but then it was acting up too, so with some more searching I found the real solution.

SOLUTION: Install this: [http://www.kde-look.org/content/show.php/kicker-compiz?content=46021](http://www.kde-look.org/content/show.php/kicker-compiz?content=46021). It works fine under both Beryl and KWin. Really great. The .deb works fine.

WARNING: You can never get it to work properly until you reduce "Number of virtual desktops" to 1 and increase the "Horizontal virtual size"

UNDO: Install the previous "desktop preview and pager" and remove the .deb

3) KDE Autostart

I can't find a proper way to make Beryl start normally with KDE. Everything I tried makes Beryl start before KDE finishes loading, or something like this, which makes Beryl crash. The best-case scenario is that only the window decorator crashes, so you can right click the Beryl icon and reload the window decorator. The worst-case scenario is one where all windows are frozen, no window decorator, no keyboard input (apart from Control+Alt+Space) and no way to access the Beryl icon, because the kicker applet is showing A LOT of desktops.

I really messed it up when I selected "Save session" having started Beryl. Then I couldn't even start a normal KDE session, Beryl would try to load but fail and freeze. I had to open xterm quickly, before it crashed, and type :
```
killall -9 beryl
```
then tidy up my messy desktop and save session again.

If you have added something to your ~/.Kde/Autostart, you need to remove all relevant entries from ~/.kde/Autostart AND save your KDE session with no Beryl running.

WORKAROUND: Log in under a normal KDE session, and start beryl-manager by hand.

SOLUTION: None known yet.

4) Screen stays blank after a suspend / hibernate

I only get the mouse pointer in a nice blank screen. Nothing works, not even Ctrl+Alt+Backspace, I have to reboot by hand.

WORKAROUND: Select KWin from the Beryl applet, suspend, then when it comes back, select Beryl again. ( You can also edit your suspend and resume scripts as described here: [http://ubuntuforums.org/showthread.php?t=247187](http://ubuntuforums.org/showthread.php?t=247187) but I haven't tested this )

SOLUTION: None known yet.

5) Windows sometimes stay white or black

SOLUTION: Minimize the window and maximize it again, or find another way to redraw it.

6) I don't want webcam windows to be transparent

I am using aMSN as an instant messenger, which opens separate windows for webcam. Of course, these windows rarely have focus. I have set trailfocus to make all inactive windows 70% opaque. As you can imagine, all webcam windows are always 70% opaque - which looks AWFUL. I gave "Window-specific settings" a go, but I bumped into a problem: The only relevant window property was the window class, but it looked like : Webcam_343596245 , the digits being completely random. On KDE it accepted regexps so Webcam_[0-9]+ worked perfect.

I suggested them to add to the Window-specific settings plugin a way to handle regexps, describing my problem. To my surprise, current Beryl SVN states that you can add a regexp! However, when I gave it a go, it didn't seem to work. Oh well, it's SVN so I suppose the feature isn't finished yet.

WORKAROUND: Being too impatient and a developer of aMSN, I changed the window class to AmsnWebcam and committed the change to SVN. If your problem is with this particular application, you can fetch its SVN version as described here: [http://amsn-project.net/wiki/SVN](http://amsn-project.net/wiki/SVN) Then you can add a window-specific setting for the window class AmsnWebcam !

UNDO: Remove the window-specific setting, remove /usr/share/amsn as well as the aMSN SVN sources directory and install your previous aMSN version.

WARNING: The window property detector of Window-specific settings is buggy. When I press Grab, it detects the old window class, which is some other property of the window. However, if I manually enter AmsnWebcam (a value different from the one it detects, but which I know to be correct) it works fine :)

SOLUTION: Wait for the Beryl team to implement regexps :)

---

