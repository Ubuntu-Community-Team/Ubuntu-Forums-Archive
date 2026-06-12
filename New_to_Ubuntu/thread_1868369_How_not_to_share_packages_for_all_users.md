---
title: "How not to share packages for all users?"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by longcheeze on 2011-10-24
If I want to use opera for one user but block other users from using it , how can I do it?
For that matter, will I be able to install packages for only one user and not others?

---

### Post by ajgreeny on 2011-10-24
Just thinking on my feet here!

Maybe possible if you install the usual way, I think, by tweaking the permissions of the excutable file of opera, and perhaps also the group membership of the various users, but it may be easier if you move the executable for opera into a folder named /bin in the home of the user you wish to be able to use opera.  That will mean that only that user will be able to use it.

Depending on the linux skills of these users, however, it would not be too difficult for them to overcome this inability to open opera, particularly with a live CD or using recovery mode, but if they are casual computer users this may not be a problem to you.

---

### Post by Toz on 2011-10-24
Another option is to download the tar version of the file (From: [http://www.opera.com/browser/download/]("http://www.opera.com/browser/download/"), choose "Other (TAR)"), uncompress it somewhere in your home directory, and run it from there.

---

### Post by longcheeze on 2011-10-25
Does this mean that each time I installed a new package, it is for system wide?

---

### Post by critin on 2011-10-25
Long ago windows allowed a user to sign in to his own account with his own choice of browser, etc.  I wonder if you could do the same with Ubuntu users?  I tried it on windows (long ago) and yes indeed, the screen didn't hold the same info as the other screen.  It was like its own os.

Each member had to have their own username/password and could not see another's screen or files.  And they had to remember to log out.

---

### Post by Toz on 2011-10-25
> **longcheeze said:**
> Does this mean that each time I installed a new package, it is for system wide?

Yes, if you've installed it using the normal methods - via the Software Centre, Synaptic, or apt-get.

---

### Post by stinkeye on 2011-10-26
> **longcheeze said:**
> If I want to use opera for one user but block other users from using it , how can I do it?
For that matter, will I be able to install packages for only one user and not others?

Why do you want to block other users?
If another user runs opera it uses completely different settings from their
**~/.opera** folder.
History, bookmarks, passwords,personalization etc etc aren't shared between user accounts.
Firefox will remain as their default browser unless they change it.

---

### Post by longcheeze on 2011-11-01
What other methods other than these normal ones?

> **Toz said:**
> Yes, if you've installed it using the normal methods - via the Software Centre, Synaptic, or apt-get.

---

### Post by mcduck on 2011-11-01
Downloading source code or a precompiled binary file, archives with installation scripts, and pretty much every possible installation method other than the standard .deb packages installed through dpkg or apt.

Of course as those are not standard methods, there is no standard where and how the program gets installed. Perhaps it goes to system directories, perhaps you can choose to install it where you want, the options depend on the program in question and how it was packaged.

Precompiled programs are the easiest way if you for some reason or other want a program to only be available to your own user, as they can usually be just extracted where you want them and executed from there.

However, like already mentioned in this thread, worrying about who gets access to a program is rarely important, while the programs are available to all users, the user data of course isn't shared between users.

---

