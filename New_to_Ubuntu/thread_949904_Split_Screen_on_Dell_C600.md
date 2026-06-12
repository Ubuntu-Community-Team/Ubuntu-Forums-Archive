---
title: "Split Screen on Dell C600"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by letzgo on 2008-10-16
I ran Ubuntu 8.04 from the install CD and have a split screen problem.  There seems to be three parts to the screen and I can hardly make out the desktop.  I then installed it under XP with the same result.  I have followed the suggestions about modifying the xorg.conf. However whenever I try to locate the file I use the whereis command on the command line and it says it is in /usr/lib/xorg.  I have used sudo gedit /etc/x11/ xorg.conf and it says cannot not display.  I have tried to look in the usr/lib/xorg directory but run into the same problem ... cannot display.  It must be that the standard place for the xorg.conf is in the etc/X11/ directory but is it in a different place if loaded under XP?  This isn't easy for a newbie.  Any suggestions.

thanks

---

### Post by Arl on 2008-10-16
letzgo,

Check this thread out for editing xorg.conf file ->[Here]("http://ubuntuforums.org/showthread.php?t=885015&highlight=dual+screen").

> However whenever I try to locate the file I use the whereis command on the command line and it says it is in /usr/lib/xorg.

It is in the etc/X11 folder, but you can't really edit it except for how is described in the above link -as far as I know but I'm pretty green, too. Hope this helps with some of the problem.

---

