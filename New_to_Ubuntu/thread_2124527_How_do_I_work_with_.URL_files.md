---
title: "How do I work with .URL files?"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by johnu1960 on 2013-03-11
I am a recent convert from the Windows 7 system.  I am used to being able to click on a .URL file and it would load up into my FireFox application.  I tried to associate these URL file types with Firefox now 
in Ubuntu and when I click on a file, the application just keeps opening tabs one after another.  Is there a way I can simply get these files to work with firefox?  Also I couldn't get Chrome to work with them either.  Thanks.

---

### Post by |{urse on 2013-03-11
[http://ubuntugenius.wordpress.com/2009/12/09/how-to-open-url-internet-explorer-shortcuts-in-ubuntu-using-firefox/](http://ubuntugenius.wordpress.com/2009/12/09/how-to-open-url-internet-explorer-shortcuts-in-ubuntu-using-firefox/) <-- This is likely what you're looking for.

---

### Post by Frogs Hair on 2013-03-11
Hi, johnu1960

If I understand correctly open with another application in the right click context menu may help when you select the file/document . I don't know if you are referring to .html files or some thing else.

---

### Post by |{urse on 2013-03-11
Doing some more reading on this and it looks like the fix listed above stopped working around Lucid. I'll keep an eye out, sad that Microsoft felt the need to create this .url format, god forbid something standard was kept standard.

---

### Post by 3rdalbum on 2013-03-11
Isn't it just a couple of binary characters and then a URL? What's stopping you from opening the files in a text editor and just copying and pasting the URL into Firefox? Or creating a simple launcher using "xdg-open <url>"?

---

### Post by The Cog on 2013-03-11
Try creating a script like this (a text file containing two lines):
```
#!/bin/sh
firefox $(grep -m1 'URL=.*' $1 | cut -d= -f2-)

```
then make it executable (right click it end edit the properties)
and then right-click a .url file and edit its properties so that it is always opened by the script you just made.

---

### Post by johnu1960 on 2013-03-13
Thanks to everyone for your replies.  I have been busy at work this week so I am just getting to this now.

Cog,  I created the text file you suggested and saved it in my home folder.   The file is called **URLopen** and it has a type of** shell script  (application/x-shellscript)**.  The permissions were set to allow  executing file as program.  But when I right click on a .url file, it  does not list the newly created script, URLopen, as one of the options.  How do I get the script to show up in Opens With?

---

