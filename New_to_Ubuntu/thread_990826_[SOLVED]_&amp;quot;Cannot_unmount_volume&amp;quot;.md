---
title: "[SOLVED] &amp;quot;Cannot unmount volume&amp;quot; (whats going on)"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-23
just recently I am having this problem. I will out in a dvd and not open any software but immediately after when i try to eject i get this

"Cannot unmount volume"
"An application is preventing the volume 'name_of_movie' from being unmounted."

I know I can run int terminal
```
umount -l /media/cdrom
eject
```

This does work however if i do that then the next time I insert a DVD it will not automount. Furthermore I don't want to have to do this every time I want to simply Eject a DVD

I don't know what to do any more.
Any help would be so great.
Thanks

---

### Post by chuckyp on 2008-11-23
Try right clicking on the volume on the desktop and select unmount. Then you should be able to eject with out a problem. The other option is just to use the eject command which should take care of the unmount for you.  You shouldn't have to specify unmount -l /dev/cdrom

---

### Post by nakama85 on 2008-11-23
> **chuckyp said:**
> Try right clicking on the volume on the desktop and select unmount. Then you should be able to eject with out a problem. The other option is just to use the eject command which should take care of the unmount for you.  You shouldn't have to specify unmount -l /dev/cdrom

When I try this I get the same message

---

### Post by nhasian on 2008-11-23
what application were you using with the dvd drive?  mplayer?  vlc?  you may need to kill that program before you can unmount the drive.

---

### Post by nakama85 on 2008-11-23
> **nhasian said:**
> what application were you using with the dvd drive?  mplayer?  vlc?  you may need to kill that program before you can unmount the drive.

Vlc.... how to i kill the program?

---

### Post by chuckyp on 2008-11-23
Close vlc by clicking the X in the upper right of the window. If it is closed and you are still encountering the error. Open a terminal and type:
```

$ps aux | grep vlc

```

This will show any processes that are still running with the name vlc. Also you can try:
```

$killall vlc

```

---

### Post by Michael.Godawski on 2008-11-23
If you are the visual type go to System > Administration > System Monitor > Processes and then right click on a process and select kill process.

In terminal use

```
killall processname
```

this will show you the processes running
```
ps -e
```

---

### Post by nakama85 on 2008-11-23
> **Michael.Godawski said:**
> If you are the visual type go to System > Administration > System Monitor > Processes and then right click on a process and select kill process.

In terminal use

```
killall processname
```

this will show you the processes running
```
ps -e
```

thanks that worked.... One question. I noticed the vlc process starts every time I put in a dvd. is there any way to prevent this from happening so I don't have to do this every time?

---

### Post by Michael.Godawski on 2008-11-23
Wild guess.
Perhaps you can check if vlc is set as the preferred application in the well... preferred applications menu in system > preferences.

---

### Post by nakama85 on 2008-11-23
> **Michael.Godawski said:**
> Wild guess.
Perhaps you can check if vlc is set as the preferred application in the well... preferred applications menu in system > preferences.

ok so i tried that and it did not work.
I even completely removed vlc and low and behold...no more problems.
But I really like vlc so i did a reinstall and the problem is back.

Does anyone know how to solve this?

---

### Post by nakama85 on 2008-11-23
bump

---

### Post by Michael.Godawski on 2008-11-23
OK this is not a clean solution. Just a try.

When you open up vlc and go to tools > preferences > (show settings > all) Input/codecs > default devices. There should be your dvdrom. What happens if you delete the path ( of course safe it somewhere before deleting it) to your dvdrom? Can you watch dvds?

Have you tried another application? Perhaps it will work with another?

---

### Post by diablo75 on 2008-11-23
I'm interested in a solution about this too... just did some looking around for an answer to thread but couldn't find anything in the System menu that allowed me to change the default app that opens up when you insert a DVD.  On my laptop, DVD's autoplay with Mplayer (I didn't choose this default, that's just the way it decided to do things).  If I had the option, I'd rather it auto-launch vlc... unlike the OP.  But we're looking for the same setting, I think.

---

### Post by nhasian on 2008-11-24
If you open Nautilus (gnome's file browser) and go to Edit -> Preferences then the last tab is Media. In there you can instruct Gnome as to which program to use for CDs or none.

---

