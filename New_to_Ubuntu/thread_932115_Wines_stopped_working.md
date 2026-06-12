---
title: "Wines stopped working"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by heiowge on 2008-09-28
I use Ubuntu Hardy, and have used wine with Utorrent for months now. Yesterday it failed to respond.

It won't let me load utorrent from the Applications menu, nautilus or command line.

It won't let me configure wine either.

I have uninstalled and reinstalled both with latest versions.

I have switched to KDE to try to get them to work - no joy!

Any ideas?

---

### Post by Jim! on 2008-09-28
Damn that sucks dude, I had that problem once but I can't recall how I fixed it. Try running these commands:

sudo apt-get autoremove

sudo apt-get autoclean

Those commands basically just clear out unneeded 'junk' packages. It could fix the problem.

PS: Does anyone remember how to insert something as 'code' on the forum. I can't remember:D

---

### Post by heiowge on 2008-09-28
Sorry.  No difference

---

### Post by Jim! on 2008-09-28
Hmmm... Are you currently running Ubuntu under KDE or GNOME? Also, do you have any idea why it might have stopped working? What was the last thing you did on your PC before (or when) Wine stopped working?

---

### Post by jualin on 2008-09-28
Go to your home partition and press CTRL+H so the hidden files can be seen. Then delete the folder named ".wine". Try running Wine now. You will have to install Utorrent again after this. Hope this helps!

---

### Post by Jim! on 2008-09-28
You could remove Wine completely:

```
rm -rf ~/.wine
```
Don't worry I'm not trying to make you corrupt your harddrive or anything, I know some people get kind of iffy when "rm -rf" is at the beginning of a command but it will only get rid of Wine and anything to do with Wine installed on you computer, really!

After you do that you will need to reinstall wine and any programs you had installed under wine - but it's a fix none the less.

---

### Post by heiowge on 2008-09-28
removed completely.  Reinstalled wine 1.0  Reinstalled utorrent

wine doesn't respond.  neither does utorrent.:(

Oh, and I'm back in Gnome btw.

---

### Post by heiowge on 2008-09-28
Last thing done with PC - firefox to web browse.  Thats it.  I used utorrent.  Web browsed and went back to it.

Oh and I used amarok once.

---

### Post by heiowge on 2008-10-01
Its still broken.

---

### Post by Orange_and_Green on 2008-10-01
Hello heiowge,

maybe if you were to run wine from the command prompt, we could have a look at the error messages.

Try opening up a terminal and write:
```
env WINEPREFIX="/home/USERNAME/.wine" wine "**C:\Program Files\Utorrent\Utorrent.exe**"
```

NOTE: Please subsitute "USERNAME" with your username (so that /home/USERNAME points to your home directory) and also make any changes necessary so that the part I wrote in bold points to the correct utorrent executable, _case-sensitive_.

Please post the output you get.
Good luck :KS

P.S. @Jim!: To highlight code, just write [C0DE] before it, and [/C0DE] after it. Note that it's a letter O in CODE, not a zero (I put a zero so it doesn't get formatted).

---

### Post by heiowge on 2008-10-02
root@******-desktop:/home/******# env WINEPREFIX="/home/******/.wine" wine "C:\Progrm Files\Utorrent\Utorrent.exe"
wine: '/home/******' is not owned by you, refusing to create a configuration directory there
root@******-desktop:/home/******# 

Obviously I removed the username!

---

### Post by heiowge on 2008-10-21
Problem solved - Uninstalled Wine, virtualised XP in Virtualbox.  uTorrent works just fine from in there.

---

