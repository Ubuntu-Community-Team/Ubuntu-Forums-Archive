---
title: "Lost my GNOME Panel."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by markekeller on 2008-09-23
I installed Awesome (a window manager) the other day.  To be able to select it from the list in GDM, I followed the instructions at the bottom of [this page]("http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-Ubuntu-git"), creating .xinitrc and .Xsession files.  Then I read the [Awesome tutorial]("http://ubuntuforums.org/showthread.php?t=675292") on these forums, and decided to try it that way instead, creating an awesome.desktop file in /usr/share/xsessions, and deleting the files I'd created before.

And when I logged into GNOME next, I saw that the panel was missing.  I don't see how the above could have caused it, but that was the only config-file type stuff I'd done recently.  The keyboard shortcuts, Alt-F1 and Alt-F2, didn't work anymore either, even though Ctrl-Alt-Delete did.  Starting gnome-panel from a terminal gave the message that the panel was already running.  And reinstalling gnome-panel didn't do any good, either.

What should I do?  I'd really like to get my GNOME system fully operational again.  Thanks for any help/suggestions you can give me!

---

### Post by phidia on 2008-09-23
When you say you deleted the files you created were these files in your user's home directory? Is it possible you deleted the wrong file?

One way to troubleshoot this is to create a test user > sudo adduser test and if the gnome panel works properly in that test user just copy over the neccessary dot files to your regular user.

---

### Post by markekeller on 2008-09-23
Yes, those files were in my home directory.  And I don't *think* I deleted the wrong file. . . .

Anyway, I created a new user like you suggested, and the panel works fine in it!  But even though I copied over ***_all_*** the dot files and folders from the test user to myself, the panel still doesn't show.

---

### Post by jemate18 on 2008-09-23
open a terminal and type

```
gnome-panel
```

here is what the man-pages tell about gnome-panel> gnome-panel(1)                                                  gnome-panel(1)

NAME
       gnome-panel - display the GNOME panel

SYNOPSIS
       gnome-panel

DESCRIPTION
       The GNOME panel displays an area on your screen, which acts as a repos&#8208;
       itory for the main menu, application launchers, and applets.

OPTIONS
       The GNOME panel obeys all normal GNOME and GTK+ command  line  options,
       and has no application specific options.

SEE ALSO
       gnome-options(7), gtk-options(7).


---

### Post by jemate18 on 2008-09-23
you can try pressing

ALT+F2

and type

gnome-panel

---

### Post by markekeller on 2008-09-23
Actually, I can't.  :(  Alt-F2 seems to be tied to the panel somehow - it has no effect.  Luckily, I can right-click on the desktop background and select "Open Terminal," though, so I was able to try it, and got the same message as the first time:

```
 ________________________________________
( Your analyst has you mixed up with     )
( another patient. Don't believe a thing )
( he tells you.                          )
 ----------------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
mark@kellerboys:~$ gnome-panel
A panel is already running.
mark@kellerboys:~$ 

```
But I guess we now know it's not that it's not autostarting the panel, but rather that there's something wrong with the panel itself.

---

### Post by jemate18 on 2008-09-23
> **markekeller said:**
> Actually, I can't.  :(  Alt-F2 seems to be tied to the panel somehow - it has no effect.  Luckily, I can right-click on the desktop background and select "Open Terminal," though, so I was able to try it, and got the same message as the first time:

```
 ________________________________________
( Your analyst has you mixed up with     )
( another patient. Don't believe a thing )
( he tells you.                          )
 ----------------------------------------
  o
   o   \_\_    _/_/
    o      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
mark@kellerboys:~$ gnome-panel
A panel is already running.
mark@kellerboys:~$ 

```
But I guess we now know it's not that it's not autostarting the panel, but rather that there's something wrong with the panel itself.

What do you mean by that COW thing? I was just trying to help..........

---

### Post by markekeller on 2008-09-23
Sorry. :D

I've got my terminal set up so that it runs [FONT="Monospace"]**fortune**[/FONT] (complete with an ASCII animal and voice bubble) every time I open a new shell.  The message is randomly chosen by the computer.  No offense, I hope?

---

### Post by jemate18 on 2008-09-23
> **markekeller said:**
> Sorry. :D

I've got my terminal set up so that it runs [FONT="Monospace"]**fortune**[/FONT] (complete with an ASCII animal and voice bubble) every time I open a new shell.  The message is randomly chosen by the computer.  No offense, I hope?

Then you should have edited it before posting, your [COLOR="DarkRed"]fortune[/COLOR] might next time display an offensive message, and those trying to help might be offended......

Anyway.. back to THE ORIGINAL problem, since gnome-panel returns a message that a panel is working, it means that you might have deleted something....

---

### Post by markekeller on 2008-09-24
I don't have the offensive fortune package installed; but yeah, you're probably right.  Sorry about that.

And yes, the evidence does seem to point in the direction of some component of gnome-panel being damaged or missing.  I reinstalled gnome-panel yesterday, though, with no effect: do reinstallations rewrite configuration files, too?

I think I'll have a look on Google to see if anyone's ever had this problem before.  In the meantime, if any of you think of something, let me know!

---

### Post by markekeller on 2008-09-24
It seems a lot of people have had this problem - Google even suggests "gnome panel missing" in a search.  It looked like some folks found killing gnome-panel and then restarting it helped, so I booted my computer into Linux to try it.  On a whim, I changed the "Session" mode to Gnome (even though I thought it was the default) and logged in.  It said that Gnome was not my default, but instead I had apparently somehow set "Run Xsession script" to default instead.  I told it I wanted Gnome to be the default, and proceeded - and my panel was there again!

In fact, all this while, I'd been logging in under "Run Xsession script" rather than "Gnome", which is why the panel wasn't coming up.  Now I feel like an idiot. :D

But there's still a few things that remain unanswered.  I have no Xsession script in my home directory - I had deleted it.  So why did running the Xsession script give me Gnome without the panel?  And, I'm rather curious to know, does *everybody* have "Run Xsession script" as an option when logging in?

---

### Post by carwee on 2009-07-12
I just upgraded from Hardy to Intrepid, and as an absolute Linux newb, I was freaking out because my panels were gone.  I must have punched in so much stuff into the terminal that I have no idea what it does, and luckily I didn't screw anything vital up (so far as I can tell lol!)  Reading this thread, I restarted, and checked the options you suggested.  I ALSO didn't have GNOME as default.  I guess that's a result of the upgrade?  At any rate, thanks for posting this!  I have panels again! YAY!

---

