---
title: "Netflix Streaming on Ubuntu"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Krommeweg on 2012-12-08
Hey folks,

I'm new to the forum, and new to Ubuntu, still working out the basics.

One issue i cannot resolve is running the Netflix Desktop.  I followed the directions in this thread: [http://ubuntuforums.org/showthread.php?t=2084592&highlight=Netflix](http://ubuntuforums.org/showthread.php?t=2084592&highlight=Netflix)

The app installs and updates normally but when I try to launch Netflix Desktop, absolutely nothing happens.   I haven't found any fixes for this issue, does anyone have any advice?

Thank you all for your time!

---

### Post by pompel9 on 2012-12-09
Did you use this command:

> sudo ap-get install netflix-desktop:i386I had troubles with that one, so I purged the netflix desktop and used this instead:

> sudo apt-get install netflix-desktop

Just use this to purge:
> sudo apt-get purge netflix-desktop:i386Oh, and when you purge it, make sure you run this afterwards:
> sudo apt-get autoremoveThat will clean all the installed packages that did not get removed by the first command.

---

### Post by kostkon on 2012-12-09
Also, try running it in debug mode. In a terminal give
```
netflix-desktop --showdebug
```
Post any output here if you want.

---

### Post by Krommeweg on 2012-12-15
Thank you both for your help!

I purged the old installation and input > sudo apt-get install netflix-desktop.

Then ran > netflix-desktop --showdebugI got "Wine: cannot find 'C:/Program Files/Mozilla Firefox/firefox.exe' "

And that's it.  Which version of firefox.exe is needed?  Couldn't I just download a Windows version of firefox, and install in Wine, so that firefox.exe would be in the correct directory?

Also, what does the suffix  "i386" indicate?

Thanks again for the help!

---

### Post by sdowney717 on 2012-12-16
Delete the hidden folder-file .netflix-desktop in your home folder.
Then do the reinstall.

---

### Post by pqwoerituytrueiwoq on 2012-12-16
> **Krommeweg said:**
> Also, what does the suffix  "i386" indicate?
that it is a 32bit package and you are using 64bit

---

### Post by Krommeweg on 2012-12-18
Ok.  So I deleted .netflix-desktop in my /home folder.

I then entered: > sudo apt-get purge netflix-desktop

Then:  > sudo apt-get autoremove

Everything seemed normal.

Then: > sudo apt-get install netflix-desktop 			 		

It installed normally and when I ran Netflix Desktop the wine configuration updated like normal.

I ran > netflix-desktop --showdebug

And the result was the same as before.  "Wine: cannot find 'C:/Program Files/Mozilla Firefox/firefox.exe"

I'm officially stumped.

Thanks everyone for their input!

---

