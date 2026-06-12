---
title: "Replace Your Show Desktop Button"
date: 2005-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2005-07-31
For all you "modders" out there, I found a great way to replace your GNOME Show Desktop button. This is more than just merely replacing the image -- you can eliminate the button altogether and replace it with a launcher that doesn't have any button-like border around it, then place that on the panel. This might not sound so spectacular, but there's another reason too why this is so special. In this forum, I mention how to create a wide GNOME main menu, wider than one that GNOME normally provides:

[Wide GNOME Main Menu](http://www.ubuntuforums.org/showthread.php?t=51640)

In this link, you can see that I have an Ubuntu icon that pops up the real GNOME Main Menu, and then beside it, which almost looks attached, is the "ubuntu" label that does nothing.

Therefore, you can replace the static functionality of the "ubuntu" label part of the "main menu" that you create with the ability to minimize all windows and show the desktop.

Here's how:

1. Temporarily enable your universe setting in /etc/apt/sources.list, then do apt-get update.

2. Type the following command to install xmacro, which is necessary for this. xmacro is a set of 4 small, simplistic C++ programs put up on SourceForge.net that let you record and playback XWindows keystrokes, mouse clicks, moves, and drags. They appear to be poorly documented at this time, so I help you wade through this here.

```

apt-get install xmacro

```

3. Comment back out your universe setting in /etc/apt/sources.list, followed by an apt-get update, so that you make certain you are more in-line with the way the makers of Ubuntu would rather you have your settings as to lower risk of potential harm.

4. Create a text file "showdesk.macro" with GNOME Text Editor that looks like this:

```

KeyStrPress Control_L
KeyStrPress Alt_L
KeyStrPress d
KeyStrRelease d
KeyStrRelease Alt_L
KeyStrRelease Control_L

```

5. Open GIMP and create a transparent PNG file that's like 48x48 pixels, like this:

a. Open Gimp.
b. File, New.
c. Type in 48x48 on Width x Height.
d. Click Advanced Options.
e. Change Fill With to Transparency.
f. Click OK.
g. File, Save As, clear.png, Save.
h. Exit out of Gimp.

6. Create a new Bash script file "showdesk.sh" with GNOME Text Editor that looks like this:

```

#!/bin/bash
cat showdesk.macro | xmacroplay ":0.0"

```

7. Create a new custom launcher on your desktop and set it to this command:

```

/bin/bash ~/showdesk.sh

```

...and for the icon, set it to clear.png.
...and for the label, set it to "Show Desktop".

8. Drag the custom launcher right where you want it on your GNOME panel. In my case, I drag it over the top of the "ubuntu" label, right in the middle.

9. Remove the custom launcher from your desktop since you have it on the GNOME panel.

And that's it! Now when you click the launcher, it runs this macro script, minimizing all windows. In my case, when I click the word "ubuntu", I see my desktop with all windows minimized.

Some further explanation...

Q. What else can you do with xmacro in this case?
A. Anything accessible from GNOME keyboard shortcuts can now be mapped to a launcher with xmacro. You can also use it for programmer testing, or use it to record and playback keystrokes and mouse events. In some cases you might even find that you can make a fancier "pager" tool, or augment the existing one you have on the GNOME panel.

Q. How do I use xmacro to record and playback keystrokes and mouse events?
A. The short answer is that you use 

```

xmacrorec2 > mymacro.macro

```

at a command prompt, press the Scroll Lock key, do your little keystroke thing that you want to record, then press the Scroll Lock key again to stop the recording.

Now that you have your macro, edit it and remove anything referring to mouse movements unless you need to use that too. 

To play your new macro back, this is not so apparent. You have to cat this file through a pipe to xmacroplay ":0.0" like:

```

cat mymacro.macro | xmacroplay ":0.0"

```

Note that if you have more than one display, then in some cases you might want to change ":0.0" to either ":1.0" or ":0.1", etc., until this works.

---

### Post by kikushima on 2007-03-17
Sorry to ask Im a total newbie... where exactly should I save the text file and the bash file?

Thanks a lot, I've been looking for this for days.

---

### Post by SuperMike on 2007-03-19
Oh, I simply created a "bash" folder in my home directory, but you can do other things as you wish. I put the files there.

---

### Post by mike_m on 2007-09-09
I've been trying to make a launcher for this command:
cat macro | xmacroplay :0
but can't get it to run from the launcher (works in term & run app.)
I tried your way above too. any ideas?

PS. the file just types my web address with a 3 sec delay so I can focus my target like gedit

---

### Post by humhum on 2008-03-24
Hi, it's an old thread, but I just had a little fight getting the button work...  so to get the macro functioning from the panel you need (or I needed) to add the full path to the xxx.macro file in the script file... so I had to do it like this::

```
#! /bin/bash
cat /home/ukkonen/bash/showdesk.macro | xmacroplay ":0.0"
```

It works from the terminal, because you are in the same directory where your xxxx.macro file is... I guess... :)

---

### Post by toxin on 2008-03-25
I'd suggest using xte from the xautomation package instead of xmacros.
You could simply create a launcher for the following command:
```
xte "keydown Control_L" "keydown Alt_L" "key d" "keyup Control_L" "keyup Alt_L"
```

---

### Post by deathsshadow77 on 2008-06-25
great guide!
I was able to create a button that will tile my windows in compiz
thank you

---

