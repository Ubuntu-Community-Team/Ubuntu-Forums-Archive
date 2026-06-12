---
title: "Restoring Ubuntu"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by twotwohappy on 2013-11-13
Ok, so I tried to install the splashtop deb package through the terminal and got errors, so then I tried to use the package manager to do it and still got some kind of error. 
Well I google'd the error and the command 'sudo apt-get install -f' was a step called for the resolve the broken package I guess.  Well -f didn't 'fix' anything, it removed 
everything!  I saw it saying removing but I was hoping that it was just going to remove/re-install.  

Anyway, now I don't even have a toolbar when I login to my computer : (.  How should I go about fixing this?

---

### Post by BBQdave on 2013-11-13
Probably the most straight forward way to recovery, would be to pull your data with a Live ISO - unless, hopefully, you already had your data backed up :)

And then fresh install of your system.

However you chose to proceed, I would back up your data.

---

### Post by twotwohappy on 2013-11-13
I'm going to back up the data when I get home and try a sudo apt-get install --reinstall ubuntu-desktop.  If that doesn't work I'll just do a fresh install and setup my partitions and raid again I guess : (.  I do remember separating the system and data into two separate partitions.  Hopefully I can just reinstall Ubuntu and it not affect the storage.

---

### Post by Habitual on 2013-11-13
> **twotwohappy said:**
> I'm going to back up the data when I get home...
Backups are always a good idea.
I'm just not convinced re-installing is necessary.


> **twotwohappy said:**
> I don't even have a toolbar when I login to my computer
 Suggestion:
Create a new user on the system and login as that user graphically and see if you have a toolbar?

Let us know...

---

### Post by jdeca57 on 2013-11-13
> **Habitual said:**
> Backups are always a good idea.
I'm just not convinced re-installing is necessary.

 Suggestion:
Create a new user on the system and login as that user graphically and see if you have a toolbar?

Let us know...
For a user with some knowledge of linux and Ubuntu I'd agree. 

But a reinstallation is quick and you start with a clean slate. Programs tend to work as they should. 

I know, learning is part of the fun. But only at your own pace.

And so, I'm not so convinced that re-installing is not the most satisfying solution for this person.

---

### Post by twotwohappy on 2013-11-13
I'm a programmer but I rarely deal with Ubuntu on this level.  I'm sure I could Google, "How to reinstall Gnome/unity" and "How to install terminal application ubuntu" so on and so forth.  I will keep you guys posted on progress and when I get the issue(s) resolved.

---

### Post by Habitual on 2013-11-13
it just seems "over-the-top" if it's just something as simple as a broken something under ~/.gconf or ~/.config

I merely wish to show the user that there's more to "fixing" a system than re-installing.

---

### Post by Habitual on 2013-11-13
> **twotwohappy said:**
> I don't even have a toolbar when I login to my computer...OK. What DO you have? A blank Desktop?
are you able to login graphically using the "greeter" (is it called that now?)

Creating a  new user  will tell us if it's the System or Your Profile that needs "fixing".
If you are inclined to re-install, that's entirely your choice, but it seems like a lot of work.

Personally, I prefer to *know* what's broken and where before I start slicing and dicing an install.

Peace.

---

### Post by twotwohappy on 2013-11-13
That's what I'm going to do first.  Yeah I get to the GUI log in screen and after logging in, I still have the desktop background and all, but the side toolbar (with app short cuts) and the top thin bar (with the internet, time and cog-wheel) aren't there any more.  What are the commands (via terminal) to create a new user?  I'll have to use ctrl + alt + F2 as well, ctrl + alt + t isn't working anymore.

---

### Post by twotwohappy on 2013-11-13
So does 'sudo apt-get install -f' only remove/fix packages installed under that user?  I would think it uninstalled all those packages across the board.  Which makes me think gnome/unity or whatever it is is foo-bar'd.  After running that command, I came back to the computer and noticed that the Netflix application I installed was gone (off the tool bar), FireFox, the terminal wouldn't work anymore and when I tried to play a movie/song it said there was no application installed to play the file(s).  I'm thinking I may have seriously messed some stuff up. 

It wasn't until I rebooted (hoping the packages would be reinstalled/fixed at that point) that I noticed there were no toolbars, only a BLANK desktop.

But I'll try the user thing first and then go from there I suppose.

---

### Post by Habitual on 2013-11-13
> **twotwohappy said:**
> So does 'sudo apt-get install -f' only remove/fix packages installed under that user?   No, it's system-wide.

> **twotwohappy said:**
> I would think it uninstalled all those packages across the board.  Which makes me think gnome/unity or whatever it is is foo-bar'd.  After running that command, I came back to the computer and noticed that the Netflix application I installed was gone (off the tool bar), FireFox, the terminal wouldn't work anymore and when I tried to play a movie/song it said there was no application installed to play the file(s).  I'm thinking I may have seriously messed some stuff up. 

It wasn't until I rebooted (hoping the packages would be reinstalled/fixed at that point) that I noticed there were no toolbars, only a BLANK desktop.

But I'll try the user thing first and then go from there I suppose.
Good idea.

```
apt-get install --reinstall ubuntu-desktop
``` just may very well resolve this issue for you.
All my analysis could be wrong. 

What I don't know could fill a warehouse.
What I do know could fill an outhouse.

but won't you be pleased-as-punch if a new user has an entire desktop?

bookmark [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by twotwohappy on 2013-11-14
Ok, so I did the apt-get install --reinstall ubuntu-desktop.  Everything seems to be working fine now.  Firefox is bundled with the full ubuntu-desktop...  package?  I just reinstalled NetFlix and set up the desktop share and downloaded android vncviewer from the market place and everything is like it should be!

Thanks for all the suggestions and advice!

Justin

---

### Post by Habitual on 2013-11-14
Glad to hear that!

---

