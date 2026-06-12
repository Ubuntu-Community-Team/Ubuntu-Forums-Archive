---
title: "Where are  program startup files"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by mhmiller on 2011-11-24
I'm using Ubuntu 11.10    I am trying to set several programs including Skype and ClipIt to start at bootup.  While I found the startup files for Firefox in usrs/lib file, there is nothing there for either Skype or ClipIt and so I can't add these programs to start up automatically.    Where are those program startup files?  do they all have the format "program.sh"?  thanks     BTW, the search function won't find these files either.

---

### Post by fleamour on 2011-11-24
You need to search for Startup Applications that used to be under Preferences in classic Gnome.  What desktop environment (DE) are you using?

---

### Post by Gone fishing on 2011-11-24
To get the program to start automatically you don't need to know where the executable is just add the command skype to startup applications and skype will start.

As it happens the Skype executable is in /usr/bin

---

### Post by BC59 on 2011-11-24
Solution:

Go to the upper right corner and push the third selection is Startup Applications.

Now go the the upper left corner the dash, search for the app you want eg Skype and click, drag and drop the icon into the Startup Applications.

That's it.

---

### Post by hakermania on 2011-11-24
After you search the Dash for 'Startup Applications' and open the app, you will be shown this:
[IMG]http://i.imgur.com/DG7IQ.png[/IMG]
You click on the 'add' button, and in the 'Command' field you type in the program's name. Click Add again in the new dialog so as to close and you're done!

---

### Post by mcduck on 2011-11-24
> **mhmiller said:**
> I'm using Ubuntu 11.10    I am trying to set several programs including Skype and ClipIt to start at bootup.  While I found the startup files for Firefox in usrs/lib file, there is nothing there for either Skype or ClipIt and so I can't add these programs to start up automatically.    Where are those program startup files?  do they all have the format "program.sh"?  thanks     BTW, the search function won't find these files either.

The standard location used for executable files of user-level programs is /usr/bin, you should find pretty much every program's executable there.

...and no, they are not all .sh files, some are, some are other types of scripts, and most just nomral binary executables. Keep in mind that Linux doesn't rely on file name extensions to mark executable files, it's simply a question of file actually being something you can execute and of course having the execute permission set.

Anyway, like Gone fishing said, the name of the program should be enough as long as the executable is in location that's included in your path (and /usr/bin of course is in the path by default)

---

### Post by mhmiller on 2011-11-25
Thanks all.  I found it in usr/bin and used that and it works.  I think I had tried to simply put the word skype as the program but it didn't work, though maybe I didn't hit "add" again after doing that.  In any event it seems to have worked.  And am glad to be learning a little more about Linux, though at this point is sort of feels like I'm back in the days of DOS.:D

---

### Post by Jacobonbuntu on 2011-11-25
....to find out what is the right command to put in the startup items, you can also use "alacarte". look for the "properties" of an application entry...

---

