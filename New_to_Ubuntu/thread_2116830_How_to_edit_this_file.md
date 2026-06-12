---
title: "How to edit this file ?"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Innernet on 2013-02-16
Searching for a 12.04 solution to window border, found that I should change values shown by the center of the attached picture as "1"  "1"  "1" into other values.

----> How do I get into 'edit' mode for that file ?    Yes, am a beguinner.

The path for such file is 
Places > Computer > file system > usr > share > themes > Ambiance > metacity-1 > metacity-theme-1.xml

---

### Post by Bashing-om on 2013-02-16
Innernet; Hi !

Open a terminal, and invoke ubuntu's file editor thus:
```
gksudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
```Always a good idea to make a backup prior to editing any file -never can tell what perchances .
```
sudo cp /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml/usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml-bak 
```(be less typing to cd to that directory -- not have to type that full path) in this instance copy and paste will get it done))

Make your changes, save the file, exit gedit and reboot to see the effects of your edit.[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by gnuman on 2013-02-16
You sound better than most beginners, listing the path correctly and sending a screenshot.  Good job!  

There are several things you can do here.  You could save the page from the browser to the destop so that you're not working on the original.  Otherwise, if you want to use the terminal, open the terminal.  The basic steps would be:

1.  navigate to the file
2.  make a backup (just in case)
3.  use nano or vim to edit the file
4.  save the new updated version

You'll need to use sudo, however, as those files are owned by the root user.  You sound like you'll be learning this quickly, so here's an example of the steps on my machine:

```

cd /usr/share/themes/Ambiance/metacity-1/

sudo cp metacity-theme-1.xml  metacity-theme-backup.xml

sudo nano metacity-theme-1.xml


```

That will open the nano text editor in that file.  You can make the changes you stated and then do CTRL-O to over-write the file and CTRL-x to exit nano.  You can then exit the terminal.

Hope that helps

---

### Post by Innernet on 2013-02-16
:D  Total success ! :D
Thanks Bashing om  =D>

Now the window can be grabbed at its edges with ease for resizing, not fighting with 1 pixel positioning of the cursor !

---

### Post by Bashing-om on 2013-02-17
Innernet; You are most welcome; Glad to be of some small assistance.

All things configurable, ain't ubuntu wonderfull !

---

