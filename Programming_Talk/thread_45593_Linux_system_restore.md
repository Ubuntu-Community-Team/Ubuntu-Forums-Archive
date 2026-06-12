---
title: "Linux system restore"
date: 2005-06-30
forum: Programming Talk
---

### Post by darthsabbath on 2005-06-30
Hey guys,

Hoping this is the right place to post this. LOL

I was thinking of making my first real Python app a Windows system restore like tool.  I know I've had occasions where I've screwed up a config file and been unable to fix the problem.  

So I got to thinking... wouldn't it be useful to have one in Linux?  Basically it can backup and restore your system settings to certain dates, much like the one used in Windows.  It would also help newbies in fixing problems they create, because as we all know, they like to change things they know nothing about (guilty here as well).

I plan on coding it in Python, with the majority of the work done as a backend that could be on the commandline if used on, say, a server, but could also enable GUIs to be built for GNOME, KDE, etc.

It would have the ability to backup a list of directories that could easily be modified, and then restore to a certain date when called upon to do so.  It would probably run as a daemon, perhaps making a restore point every 24 hours.

Also, I'd like the program to only be able to restore certain settings... like individual users, just /etc, and so on.  For example, if run as a regular user, it would only restore that users settings, but root could restore the entire system if need be.

A few questions I have are:
1. Besides /etc, what other directories/files would be good to backup?  I'm sure the bash config files in /home/$USER, but do any come to mind that would be good defaults across all Linux/UNIX machines, as I do want to be able to use this on any OS I run with little difficulty.

2.  What would be the easiest way to be able to store the backup files and still maintain portability?  My guess would be tar.gz.

3. This question may be better suited elsewhere, but supposing I'm able to do this and get it working flawlessly, would I be able to submit it for review to be included in Ubuntu?  

Any thoughts that come to mind on this project or suggestions would be welcome.  On the surface it seems to be a fairly simple first program to do... I guess we'll see once I dive in headfirst. ;-)

Thanks
Phil

---

### Post by Kimm on 2005-07-01
well, I'm gona try to answer your questions.

1. Yes, /etc would be very important to backup, but since on a debian system the installed packages list lies within /etc aswell, this would require that the /usr/bin directory is backed up aswell (we dont want dpkg to think packages that arnt installed are...). Then again perhaps the /etc directory could be backed up automaticly before any new install. (or perhaps just the files in question)

2. tar.gz is good ofcourse, but I'd recommend tar.bz2 (higher compression)

3. No idea... but I supose a review is allways possible...

Now I'm gona go and be negative again... I dont think Python is a very suitable language to use for an app like this. Since the restore points will probably be created as the user works it will take up more then enough of system resources.
I'd suggesting using C for an app like this, to remain portable and get as fast code as possible (I can think of a very simple way of writing a non-automated app in C that does this exactly, an automated app wouldnt be much more difficult to make, that code would only recuire a recompile to go to different platforms)

---

### Post by LordHunter317 on 2005-07-01
[QUOTE=darthsabbath]
A few questions I have are:
1. Besides /etc, what other directories/files would be good to backup?[/quote]Large portions of /var, but it's system dependent.  You need a way for applications to register data to be backed up.  

>  I'm sure the bash config files in /home/$USER,Better grab more than that...

>  but do any come to mind that would be good defaults across all Linux/UNIX machines, as I do want to be able to use this on any OS I run with little difficulty.Better abandon that idea right now.  To be able to do real system restore, you're going to have a hard enough time being cross distro.  You need to be able to remove and install software too, to completely move backwards and forwards.  That means interfacing with the package manager.

> On the surface it seems to be a fairly simple first program to do...You need to stop and think this through alot more.  It's decidely complex.

---

