---
title: "Compiz and Googleearth (or java app)"
date: 2009-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by shane2peru on 2009-05-12
Ok, I have found googleearth and compiz to not get along very well.  So I made a simple little script to fix this.

[COLOR="Red"]As always if smoke starts coming out of your monitor and your computer blows up, I assume no responsibility, continue at your own risk.  [SIZE="1"]This has been your disclaimer warning, procceding with the following steps binds you to this agreement.  You read the fine print?  lol.[/SIZE][/COLOR]

I will give the GUI instructions anyone who wants to probably would know how to do this with cli:

Open nautilus to your home direcotry and create a folder called ```
bin
```
now **Applications -> Accessories -> Text Editor**

Paste this into it:
```

#!/bin/bash
metacity --replace &
googleearth
compiz --replace &
done
exit

```
save this in the new bin folder you created in your /home/username directory.
Let me explain what it is:
metacity --replace this will change your compiz setting to metacity then it will run googleearth, after you close googleearth, it will replace metacity with compiz.  Got it, good.

Now go ahead and close the text editor.  With Nautilus navigate to the new folder bin, right click on the file gearth that you named it, go down to **Properties** go to Permissions and click on the box at the bottom that says Execute until there is a check mark in the box.  

**Last Step**

Now right click on the menu and select edit menu go down to internet, and double click on googleearth.  replace the command box that says this:
```

googleearth %f

```
with this:
```

gearth %f

```

If you don't like the screen flickering with the googleearth setup that we just made, then just reverse the last step that I posted, and delete the gearth file we made in the bin folder, if your bin folder is empty, then just go ahead and delete the bin folder.  Couldn't be simpler.  If you don't have or use compiz then obviously this script is not going to work for you.  Hope this helps!

Shane

PS You can modify this however you want to run any java apps you want.  I found that java apps don't respond well to compiz for whatever reason.  Any questions just ask I will see what I can do to help out!

---

### Post by jpeddicord on 2009-05-13
Approved. Thank you for your tutorial contribution. :)

---

### Post by shane2peru on 2009-05-13
> **jacobmp92 said:**
> Approved. Thank you for your tutorial contribution. :)

Glad to be a part of the Ubuntu community, and able to contribute back. 

Shane

---

### Post by binbash on 2009-05-14
[http://www.ubuntu-inside.me/2009/05/howto-automatically-disable-compiz-when.html](http://www.ubuntu-inside.me/2009/05/howto-automatically-disable-compiz-when.html)

---

### Post by shane2peru on 2009-05-14
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/05/howto-automatically-disable-compiz-when.html](http://www.ubuntu-inside.me/2009/05/howto-automatically-disable-compiz-when.html)

Hmmm, I guess I missed that before. :)  Thanks for sharing.

Shane

---

