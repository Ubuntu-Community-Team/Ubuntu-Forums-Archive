---
title: "unity gone after adjusting compiz"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Trisket on 2011-10-16
So I wanted my wobbly windows back and after downloading compiz advanced settings manager I started to work on doing so and the following happened: 
After accidentally clicking the enable cube selection, compiz prompted me that unity would be turned off, so i clicked cancel and right then my system froze. So after about 10 minutes I rebooted and the unity bar is gone and I can't get to anything. Getting to the terminal through the keyboard I tried to restart compiz via (compiz -- replace) and the terminal reads (compiz (core) - couldn't load plugin 'replace') and (compiz - (core) - fatal: couldn't open display)
Any help would be greatly appreciated.

---

### Post by Meelad on 2011-10-16
Try searching the forum, this issue has been discussed many many times in the last 48 hours..

Trying running

```
unity --reset
unity --replace
```

in the terminal. You can use the guest account to log in to run it..

---

### Post by WB0HYQ on 2011-10-16
I did exactly as Trisket did.  Somehow, in the middle of Compiz the computer froze.  When it came back, all I had was a desktop picture.

I rebooted (by going to a TTY and entering the shutdown command), and now I have a thin, grey line across the top with 'File Edit View Go Bookmarks Help".  That's it.

I started a terminal and issued the first command Meelad gave - the screen danced downwards with the results of various commands, then hesitated.  There has been no disk activity except a very occasional blip for the last ten minutes.  If I try to close the terminal (I have no prompt), I gat a warning that a process is still running.

I still have no prompt after 15 minutes.  Will I have to completely re-install everything (including about 20 apps installed over the last two days), or is there a way to recover my desktop?

Bill

---

### Post by LinuxFan999 on 2011-10-16
> **WB0HYQ said:**
> I did exactly as Trisket did.  Somehow, in the middle of Compiz the computer froze.  When it came back, all I had was a desktop picture.

I rebooted (by going to a TTY and entering the shutdown command), and now I have a thin, grey line across the top with 'File Edit View Go Bookmarks Help".  That's it.

I started a terminal and issued the first command Meelad gave - the screen danced downwards with the results of various commands, then hesitated.  There has been no disk activity except a very occasional blip for the last ten minutes.  If I try to close the terminal (I have no prompt), I gat a warning that a process is still running.

I still have no prompt after 15 minutes.  Will I have to completely re-install everything (including about 20 apps installed over the last two days), or is there a way to recover my desktop?

Bill
You can go to the terminal and remove Unity, Compiz, and Gnome. You can then install any desktop environment you want, like KDE, or XFCE, but I reccomend that you install a desktop environment before you remove Unity. Otherwise, your only other option is to reinstall Ubuntu.

---

### Post by David006 on 2011-10-16
check out:
[http://ubuntuforums.org/showpost.php?p=11319786&postcount=15](http://ubuntuforums.org/showpost.php?p=11319786&postcount=15)

The last 8 lines (or so) may resolve this issue for you ..

---

### Post by garvinrick4 on 2011-10-16
If worse comes to worse, Go to your trusty Live Cd (install Cd using Try Ubuntu) and install
ccsm while in Unity and then open it and see what is checked off and set yours back to
same in your install. I believe I had to do this in 11.04 Alpha when first used Unity and started playing with ccsm settings.  Not the prettiest fix but better than idea of reinstall.
Last resort anyway. There are usually the unity --reset and such given before my post that can most of times fix.

---

### Post by Lisiano on 2011-10-16
Login into Unity 2D, open a terminal, type ```
unity --reset
```
Now logout of Unity 2D and log back into Unity 3D, this should solve it.

---

### Post by WB0HYQ on 2011-10-16
> **LinuxFan999 said:**
> You can go to the terminal and remove Unity, Compiz, and Gnome. You can then install any desktop environment you want, like KDE, or XFCE, but I reccomend that you install a desktop environment before you remove Unity. Otherwise, your only other option is to reinstall Ubuntu.

Okay.  How do I 'remove' and 'install' from a command line?

I am no stranger to command lines (or computers, for that matter) but since the GUI disappeared, I'm left dealing with a command line.  I would rather keep Unity, but this time I'll stay the heck away from compiz as I don't think it's ready for prime time.

Bill

---

### Post by Lisiano on 2011-10-16
```
sudo apt-get install ubuntu-desktop
```
Replace ubuntu-desktop with the desktop you wish to have
ubuntu-desktop -> Ubuntu (Gnome/Unity)
kubuntu-desktop -> Kubuntu (KDE)
xubuntu-desktop -> Xubuntu (XFCE)
lubuntu-desktop -> Lubuntu (LXDE)

EDIT: The syntax for installing and removing anything from the terminal is
```
sudo apt-get <mode> <app>
```
Where mode is one of the following
install
remove
purge (Same as remove but also remove configuration files)
There are more but those are the primary ones.
Replace <app> with a actual application name, for example Skype
```
sudp apt-get install skype
```

---

### Post by wildmanne39 on 2011-10-16
Hi, this is how I did it when I installed 11.10 and it happened to me.

ctrl+alt+t
then
```
software-center
```
Then type in compiz when it finds compiz install compiz settings manager then open it with ccsm in the terminal then look for unity plugin and see if it is checked if it is uncheck it and recheck it and that should fix the problem.
Thank you

---

### Post by WB0HYQ on 2011-10-16
That did it!  :D  Wildmanne39, your post was right on the money.  I have now saved that procedure off in a text file for future use.  I now have my desktop back fully.  I will not mess with Compiz until I learn a whole lot more about it.

The Unity plugin was UNchecked and, when I checked it and closed the window, the prompt came back in the terminal window AND my desktop returned - completely intact.

@Lisiano: Your post has also been recorded in my text file.  Many years ago, I had to maintain a HPUX machine.  The commands are starting to come back to me now (me looks in my garage for any leftover manuals).  Thanks for that.

When I started with computers (in 1963) things were a whole lot simpler.  I have bookmarked this forum because I'm betting I'll get hung up again. :mrgreen:

I write this from FF in my restored desktop.

Bill

---

### Post by wildmanne39 on 2011-10-16
Hi, I am glad to help! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by WB0HYQ on 2011-10-16
Not sure I'm the one to mark the whole thread.  I kind of "piled on" after the whistle.  Trisket started it, so he should actually be the one to check it off.  Normally, I don't tag onto a thread unless my problem is EXACTLY the same.  Trisket's description fitted mine to a tee, so I responded.

If everyone is satisfied that the problem was taken care of, then I'd be happy to tick it off.

Bill

---

### Post by wildmanne39 on 2011-10-16
Hi, I have been helping a lot of people and did not notice that you did not start the thread, only he can mark it solved.

---

