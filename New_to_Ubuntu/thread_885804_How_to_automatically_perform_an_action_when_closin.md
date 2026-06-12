---
title: "How to automatically perform an action when closing a program?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by kramer65 on 2008-08-10
Hello,


In order to install photshop cs2 I followed [this how to]("http://youralternative.blogspot.com/2007/06/photoshop-cs2-on-linux-in-3-easy-steps.html"). I can start it but the second time I start it I get an error saying: "Unable to continue because of a hardware or system error. Sorry, but this error is unrecoverable".

Then I found [this threat]("http://ubuntuforums.org/showthread.php?t=642331") which advises to delete a psp file where all the settings are stored. That works, but only for once. When photshop starts again it recreates the file and I have to delete it again when I want to use photoshop again.

So is there a way to delete this file automatically when I close down photoshop? Or do you know any other solution to this problem?

---

### Post by SunnyRabbiera on 2008-08-10
well because its a wine app I am unsure there is a viable option for you.
If this is a adobe issue there is not a lot you can do.
I know its possible to make linux apps do stuff like this, but not wine apps.

---

### Post by bpowell2005 on 2008-08-10
> **kramer65 said:**
> Hello,


In order to install photshop cs2 I followed [this how to]("http://youralternative.blogspot.com/2007/06/photoshop-cs2-on-linux-in-3-easy-steps.html"). I can start it but the second time I start it I get an error saying: "Unable to continue because of a hardware or system error. Sorry, but this error is unrecoverable".

Then I found [this threat]("http://ubuntuforums.org/showthread.php?t=642331") which advises to delete a psp file where all the settings are stored. That works, but only for once. When photshop starts again it recreates the file and I have to delete it again when I want to use photoshop again.

So is there a way to delete this file automatically when I close down photoshop? Or do you know any other solution to this problem?

How about you make a bash script that first deletes the file, and then uses Wine to launch Photoshop? The end result is the same, the file is missing before Photoshop launches. This Bash script would of course be what you use to launch Photoshop in the future.

---

### Post by kramer65 on 2008-08-10
Well, a bash script would be a perfect solution then. If you could only help me started? I have no clue how I would be able to set that up..?

---

### Post by okey666 on 2008-08-10
I will write you one, if you tell me the addresses of where photoshop is within wine, and the file to be deleted.

---

### Post by bpowell2005 on 2008-08-10
Well, I'm a little new to this... but here's my attempt!

You'll want to make a new text file called whatever..."photoshop_launcher"

Then enter the following:

```
#!/bin/sh
# This file will delete photoshop configuration file xxx.psp
# Which is required prior to photoshop starting

rm ~/.wine/drive_c/ <rest of path to the file to be deleted/xxx.psp (replace xxx.psp with actual file name)

# Now we launch photoshop with wine
wine ~/.wine/drive_c/ <rest of path to photoshop executable>
```

Once that's done, save the file, and then make it executable..in terminal do:

sudo chmod +x photoshop_launcher

Then just type sh photoshop_launcher and you should be in good shape!

---

### Post by kramer65 on 2008-08-10
That would be great!

The file that needs to be deleted is as follows:
/home/ricam/.wine/drive_c/windows/profiles/ricam/Applicatie Data/Adobe/Photoshop/9.0/Adobe Photoshop CS2 Settings/Adobe Photoshop CS2 Prefs.psp

And the command to start [hotoshop is this:
wine "/home/ricam/.wine/drive_c/Programma Bestanden/PortaShopCS2/PhotoshopPortable.exe"

I hope you can do something with that..?

---

### Post by okey666 on 2008-08-10
In fact if I am not wrong it would be as simple as:
```
rm /home/<username>/.wine/<path to file>
wine /home/username/.wine/<path to cs3>
```

Plop that in a .sh file, add permissions and execute with a double click.

---

### Post by okey666 on 2008-08-10
I can't test it(cause I don't have PS), but the file is attached.

edit:
to add permissions, simply right click on it. Then the tab "permissions" then tick "execute as program"

---

### Post by okey666 on 2008-08-10
A version below adds a few echos and changes cs3 to cs2.

---

### Post by kramer65 on 2008-08-10
That worked almost smoothless. I just had to add two double quotes around the first file path as well because there were spaces in the name. The second file you uploaded however, doesn't start it up properly and gives some kind of weird error while the first one works perfectly.. I don't have a clue why..

So I can now make a starter that points to this bash file?

---

### Post by okey666 on 2008-08-10
Yep... put the file somewhere thats not going to be moved. Then right click on your menus and click "edit menus". Navigate to where you want the launcher. Then click "new item". Enter name/comment then click browse beside command and go to where ever you put the file. Job done!

I don't know why the second file breaks. What command do you use to run the file?

---

### Post by kramer65 on 2008-08-10
Perfect! That works like a charm now. You guys have been a great help!

I have only one last tiny little insignificant thing left. I want to put an icon next to it in the menu, but when I want to select the png which I want to put for it, it doesn't "see" it like it does when you make a normal starter. Is there a reason for that? Maybe because the png which I want to use doesn't have the exact dimension that it may need to have. But I just made a normal starter on the desktop and there it does recognise it..

---

### Post by bpowell2005 on 2008-08-10
> **kramer65 said:**
> Perfect! That works like a charm now. You guys have been a great help!

I have only one last tiny little insignificant thing left. I want to put an icon next to it in the menu, but when I want to select the png which I want to put for it, it doesn't "see" it like it does when you make a normal starter. Is there a reason for that? Maybe because the png which I want to use doesn't have the exact dimension that it may need to have. But I just made a normal starter on the desktop and there it does recognise it..

You should be able to add the icon of your choosing in the same "edit menus" section. On Ubuntu, I go to System, Preferences, Main Menu, and then I find my application, right-click it, properties, and click on the Icon and you'll be able to change it.

---

### Post by okey666 on 2008-08-10
The only reason I can think of is that png is not supported. Most of the images seem to be .svg. You can make that format with inkscape (I think) or you could convert the image you have (using GIMP) to another format and try that. I cannot use png either.

---

### Post by kramer65 on 2008-08-10
I converted the image to gif and jpg but none of them works. I wanted to make it an .svg like you suggested, but GIMP doesn't seem to support the creation of an .svg image...

---

### Post by okey666 on 2008-08-11
Inkscape (add/remove programs and search it) can produce svg (scalable vector graphics). I don't think you could convert an existing image though...

---

