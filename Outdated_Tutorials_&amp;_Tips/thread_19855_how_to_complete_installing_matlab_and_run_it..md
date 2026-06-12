---
title: "how to complete installing matlab and run it."
date: 2005-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by lorap on 2005-03-14
when you begin installing matlab and get some errors saying "access denied" don't pay attention,just go ahead.
after you've matlab installed you probably go to the .../.../matlab7/bin/nlx86
directory and try to run executable called MATLAB.don't do it!
you should firstly go,right after installation,to the directory .../.../matlab7
and run a script "install_matlab".after you run it you would be able to run matlab this way:go to the .../.../matlab7/bin/scripts/matlab(it's a script you'd run)
and run it!
have a nice day friends!
pavel

---

### Post by Behel on 2005-05-20
Just for completeness to our friend Pavel (thank you for the great tips by the way!)

During my installation of Matlab coming with 3 CDs on Ubuntu Hoary (not Warty as this thread is in), I had two difficulties. 

First was simply to run the the *install* script on the first CD. I couldn't run the script with a simple *sudo*... I don't know why... So I unlocked the Root account:

1. *sudo passwd root* then enter your user password and then a root password (that you need to remember!).
2. Then switch to root via *su* and enter your root password.
3. Finally I run the install script on the 1st CD: *sh /cdrom/install* &*

My second difficulty came when I had to change CDs during the installation. I didn't manage to eject the CD either from the terminal or the GUI so I used the brute force that everybody knows. But when I put the second CD, I had problems for unmounting the first one and mounting the second one. So I copied all the files of the CDs to my desktop and when asked by the Matlab installer to change, I indicated not the cdrom but the created folders.

This way I manage to install successfully Matlab on Ubuntu and it runs quite smoothly on my old laptop! And I can also say cheerfully, bye bye Windows!

---

### Post by Dolboeb on 2005-06-24
Thanks a lot guys! That really helped me; I spent a lot of time trying to figure out first why Matlab didn't work at all, and then why it couldn't find a single library... Now it works, at least partially.

However, when I try to open any new window, for example, File->Preferences, or File->New->M-file, it gives the following:

java.lang.InternalError: Current locale is not supported
	at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
	at sun.awt.motif.MWindowPeer.init(Unknown Source)
	at sun.awt.motif.MFramePeer.<init>(Unknown Source)
	at sun.awt.motif.MToolkit.createFrame(Unknown Source)
	at java.awt.Frame.addNotify(Unknown Source)
	at com.mathworks.mwswing.MJFrame.addNotify(MJFrame.java:861)
	.....

I tried a workaround [1-184MH](http://www.mathworks.com/support/solutions/data/1-184MH.html?solution=1-184MH) but it didn't help. Any ideas what may be wrong?...

---

### Post by Dolboeb on 2005-06-24
I've solved the problem with the help of Matlab techsupport. They suggested I change LANG variable from whatever I had (en_SG.UTF- 8) to en. Now all GUI in Matlab works fine.

---

### Post by Girondin on 2006-08-01
Hi I have the same problem with java stuff and matlab...
How did you fix it?
I work presently with Edgy Eft and Matlab does not want to work sincy my upgrade...

```
Exception in thread "AWT-EventQueue-0" java.lang.InternalError: Current locale is not supported
	at sun.awt.motif.MWindowPeer.pSetTitle(Native Method)
	at sun.awt.motif.MWindowPeer.init(Unknown Source)
	at sun.awt.motif.MFramePeer.<init>(Unknown Source)
	at sun.awt.motif.MToolkit.createFrame(Unknown Source)
	at java.awt.Frame.addNotify(Unknown Source)
	at com.mathworks.mwswing.MJFrame.addNotify(MJFrame.java:861)
	at com.mathworks.mwswing.desk.DTFrame.addNotify(DTFrame.java:145)
	at com.mathworks.hg.peer.FigureFrameProxy$FigureFrame.addNotify(FigureFrameProxy.java:72)
	at java.awt.Window.show(Unknown Source)
	at com.mathworks.mwswing.MJFrame.show(MJFrame.java:713)
	at java.awt.Component.show(Unknown Source)
	at java.awt.Component.setVisible(Unknown Source)
	at com.mathworks.mwswing.MJFrame.setVisible(MJFrame.java:740)
	at com.mathworks.mwswing.desk.DTSingleClientFrame.setVisible(DTSingleClientFrame.java:304)
	at com.mathworks.hg.peer.FigureFrameProxy$FigureFrame.setVisible(FigureFrameProxy.java:52)
	at com.mathworks.hg.peer.FigureFrameProxy.setVisible(FigureFrameProxy.java:152)
	at com.mathworks.hg.peer.FigurePeer.nonDockedShow(FigurePeer.java:2522)
	at com.mathworks.hg.peer.FigurePeer.show(FigurePeer.java:2539)
	at com.mathworks.hg.peer.FigurePeer.doSetFigureVisible(FigurePeer.java:3373)
	at com.mathworks.hg.peer.FigurePeer$26.run(FigurePeer.java:2581)
	at com.mathworks.hg.util.HGPeerQueue$HGPeerRunnablesRunner.runit(HGPeerQueue.java:244)
	at com.mathworks.hg.util.HGPeerQueue$HGPeerRunnablesRunner.runThese(HGPeerQueue.java:277)
	at com.mathworks.hg.util.HGPeerQueue$HGPeerRunnablesRunner.run(HGPeerQueue.java:318)
	at java.awt.event.InvocationEvent.dispatch(Unknown Source)
	at java.awt.EventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.run(Unknown Source)

```

I cannot find the solution to fix it... Please help me... #-o

---

### Post by Theja on 2006-08-19
Yo dude the answer to your prob and my prb is just losted above. Sorry for the PM I sent you.
Just do this:
$locale
and if its not en_US.utf8 then change it like this:

export LANG=en_US.UTF-8

Add this line to .bashrc too....and enjoy Matlab..:)


Theja

---

### Post by andiii on 2006-08-24
I got Matlab installed and running. However, it requires a Terminal to start.

If I create a launcher with the command Matlab in the Gnome-menu I just see the splash-screen and then nothing.. If I tick "run in terminal" it works fine, but I don't want a terminal window that is just there for matlab.

Is it because of Java?

---

### Post by lastlandstalker on 2006-08-25
try matlab -desktop.
Have fun, Andrew

---

### Post by sbrinkmann on 2006-11-14
Have Matlab a special Linux Version?

I have the 3 Matlabs CD's but i can't find a linux installer....

---

### Post by Tanazzo on 2007-03-24
I have a problem with Matlab 7 on Ubuntu Edgy Eft 6.10...I have installed it correctly without problems!
But the GUI doesn't work at all (It loads only the spash screen and an empty window)...and I've installed Java on my system...
While, if I type ```
matlab -nojwm
``` on terminal, it works finely on the command-line...
Could you help me,please?
So I cannot use Simulink...

---

### Post by lazcisco on 2007-09-15
I extracted an iso into my "me" folder (where I keep general documents) , but when I go into the folder and ./install, it always tells me my Permission is Denied. I did the su command and typed my password, but it still tells me that, what am I doing wrong?

---

### Post by JibberFisch on 2007-09-16
So I have a peculiar problem.  I got Matlab totally installed (student version), and it runs from the command line (which is a bit inconvenient, but to be played with later).  When it runs, I get two lines of errors (below), then it runs as normal, with splash screen, then the command window, etc.  The main window doesn't show menus, but they do exist when you can guess where to click on them.  When I open Editor, the screen is completely blank, but like the main window, the menus are still openable.

/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:241: Priority specification is unsupported, ignoring


If you have any ideas on how to fix this, I haven't been able to find anything online to help me with it.

Running it on a Gateway CX2610 tablet, if it's any help.
Thanks,
Will

---

### Post by J77 on 2007-09-17
The instructions in the installation manual, which is on the matlab DVD, work fine if you follow them step-by-step.

No "tricks or hacks" are needed.

---

### Post by mottalli on 2007-09-17
In order to have a MATLAB icon on your applications menu, you must create the file **/usr/share/applications/matlab.desktop** with the following contents (change the path if needed):

```

[Desktop Entry]
Name=Matlab
Comment=Matlab
Exec=/usr/local/bin/matlab -desktop
Icon=/opt/matlab7/X11/icons/matlab48c_icon.xpm
Terminal=false
MultipleArgs=false
Type=Application
Categories=Application;Development;
StartupNotify=true

```

---

### Post by frenchcr on 2007-09-17
> **J77 said:**
> The instructions in the installation manual, which is on the matlab DVD, work fine if you follow them step-by-step.

No "tricks or hacks" are needed.


rubbish! i have followed them i am still unable to install it.

./install ...access denied  .....same problem as **lazcisco** post above!

---

### Post by J77 on 2007-09-18
> **sbrinkmann said:**
> Have Matlab a special Linux Version?

I have the 3 Matlabs CD's but i can't find a linux installer....Yes -- one DVD has the windows stuff, the other the mac and linux stuff.

---

### Post by J77 on 2007-09-18
> **frenchcr said:**
> rubbish! i have followed them i am still unable to install it.

./install ...access denied  .....same problem as **lazcisco** post above!Did you mount the disc as a DVD, not a CD -- I had to create a separate mount point a DVD, over my default CD ones.

sudo mkdir /media/dvd
sudo mount -t iso9660 /dev/dvd /media/dvd
/media/dvd/install &

...then do all the license and link stuff like it says in the pdf manual.

And, it's hardly rubbish as I updated my version with no worries just the other day :D

---

### Post by HgBoy on 2007-09-20
I have matlab installed, but I don't have any idea how to start the program... Preferably with a gui, but terminal will work too for now. is there just a command to type into the terminal?

---

### Post by spectatorion on 2007-10-07
JibberFisch: I also have the peculiar problem that Matlab runs fine, although I cannot see the menus or toolbars.  The editor window comes up blank, too.  I was using the desktop effects.  When I turned off the effects, the windows came up fine.  It is not a great solution, since I really like the wobbly windows and spinning cube transition, but it works for now.

Have you made any progress toward getting Matlab to work fully with the desktop effects enabled?

---

### Post by spectatorion on 2007-10-07
quick update:  if i turn off desktop effects, then open matlab, then turn back on the desktop effects, i can still see all the matlab buttons and menus.  any new windows i open, however (like an m-file editor or an help window) come up blank.

if i turn of desktop effects, then open matlab and an m-file editor, then turn desktop effects back on, the window is not blank and all the buttons are visible.  this messes up my virtual desktops, however, due to a bug in compiz (or ubuntu's implementation, anyway).

hardly ideal, but workable.

---

### Post by MaximusTG on 2007-10-07
If you follow my instructions in post #3 in this thread:

[http://ubuntuforums.org/showthread.php?t=467133](http://ubuntuforums.org/showthread.php?t=467133)

You'll have GUI even with desktop effects on. 

On Gutsy (and maybe Feisty with latest Compiz Fusion?) there's an option in compizconfigsettingsmanager in workarounds called "java window fix" Don't have matlab installed on Gutsy yet, so don't know if that works. But I suspect it will :)

---

### Post by spectatorion on 2007-10-08
maximus, thanks for the great tip!  i'm getting a couple font warnings in the terminal, but everything seems to be working just fine.  fantastic.  so glad i don't have to boot into windows anymore for serious matlab work.

now if i could only get a nice R Gui to work...

---

### Post by tikey on 2007-10-27
thanks for the hint maximus.

I had the problem that when I started Matlab after upgrading to Gutsy the splash screen would show up but nothing else happened. I thought it's a java problem and tried everything I could think of to fix my java. After I read your post I just installed compiz-kde, started it and...
...Matlab just works!

---

### Post by phen on 2007-11-28
hello all,

did anybody here try to work with simulink on the newer ubuntu versions?

When I try to launch simulink, matlab crashes and complains about missing libXft.so.1

after google, i tried to link libXft.so.1 to libXft.so.2, as supposed to work for intel fortran compiler. but it doesnt help with matlab, except that the error message is now:
```

??? Can't load '/usr/local/matlab7/bin/glnx86/libmwsimulink.so': /usr/local/matlab7/bin/glnx86/libqt-mt.so.3: undefined symbol: XftFreeTypeOpen
```

I remember that with feisty the linking-trick worked.

I am trying to install Matlab R14

please help if you can, it will soon be very important to have matlab running :-(

thanks!

---

### Post by phen on 2007-11-28
ok solved it.

find the howto here:
[ [Howto] make Simulink 6 run (Matlab Version 7.0.0.19901 (R14)) ]("http://ubuntuforums.org/showthread.php?p=3855871#post3855871")

---

### Post by archon123 on 2008-09-28
I installed matlab and ran the post installation and everything appeared to be fine.

But when I try to run matlab from the command line I get this message:

"No MATLAB executable for this machine architechture

usr/lib/matlab7/glnx86/matlab does not exist"

I'm not sure why this is occurring or how to fix it. Does anyone know how to fix this? 

Thanks

---

