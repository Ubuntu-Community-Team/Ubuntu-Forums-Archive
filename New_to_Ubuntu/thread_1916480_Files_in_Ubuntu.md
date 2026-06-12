---
title: "Files in Ubuntu??"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by TAspr on 2012-01-28
How do you get rid of these files in Ubuntu?

---

### Post by MG&amp;TL on 2012-01-28
Does clicking on them and deleting them not work? What are they from?

---

### Post by Double.J on 2012-01-28
Right click and "move to rubbish bin/move to trash"? Are they from a wine program? lot's of windows programs create desktop icons by default, have a look in "/home/user/.wine/drive_c/Program\ Files" and see if there's something you didn't mean to install?

Hope it helps :)

---

### Post by TAspr on 2012-01-28
Yes, they are a Wine program.  So the jist is getting them to the recycle bin?  Does this actually move them off of the desktop?

---

### Post by MG&amp;TL on 2012-01-28
So...deleting them does not work? What's the problem?

---

### Post by TAspr on 2012-01-28
No, I just want to completely remove them.  The reference is still there.

---

### Post by MG&amp;TL on 2012-01-28
Are they the only things on the desktop? If so, open a terminal and run this command:

```
rm -f Desktop/*
```

Although as always, I would recommend caution with rm.

---

### Post by Double.J on 2012-01-28
When you say the reference is still there.. do you mean you want to delete the programs they link to? desktop icons are just links to software... as for getting rid of the links themselves.. MG&TL's got you covered :)

Deleting programs from wine should be done with the uninstaller tool.

upen a terminal and enter
```
 wine uninstaller
``` and select what you would like to remove... if you some reason this doesn't work, the brute force option is to go the wine program files directory and remove the program like any other stubborn directory with 
```
 sudo rm -rf directoryname
``` (be SURE to get the right one :| and NEVER use a wildcard such as * with rm -[COLOR="Red"]r[/COLOR]f - just too much scope for error ;) )

Hope it helps :)

---

### Post by TAspr on 2012-01-28
[FONT=Century Gothic][I]MG&TL's got you covered :smile:

Deleting programs from wine should be done with the uninstaller tool.[/I] [/FONT]

I don't mind to sound so stupid, but where is this file?

---

### Post by Double.J on 2012-01-28
The wine uninstaller program? I don't know where it's stored on the disk, but you can start it either by typing "wine" into the dash search-box and clicking on "uninstall wine software" or by opening up a terminal as above and pasting in "wine uninstaller".

Is this what you meant? :)

---

### Post by grahammechanical on 2012-01-28
I am assuming that you are using 11.10 so open the Dash and type wine. You will see an icon called Uninstall Wine Software. It will produce a window called Add/Remove programs. You should see a list of programs that you installed through wine.

Regards.

---

### Post by TAspr on 2012-01-28
Got it!  Thank you so much for the Wine instruction.

---

