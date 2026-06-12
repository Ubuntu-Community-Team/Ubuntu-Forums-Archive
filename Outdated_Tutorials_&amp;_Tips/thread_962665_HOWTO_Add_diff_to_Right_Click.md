---
title: "HOWTO: Add diff to Right Click"
date: 2008-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by opscure on 2008-10-29
Today I was getting rather annoyed when I kept have to jump into terminal to check code changes between versions of code.  I was doing a diff, dumping the data to a file (lot of changes, small screen buffer), and then opening the file in a text editor.  While this is all fine and dandy, I wanted something a bit more immediate without having to type so much.

Here's what I did:

First I installed the nautilus-actions package from the repository:

[HTML]sudo apt-get install nautilus-actions[/HTML]

This will allow us to modify the desktop right click menu visually.

After that was installed I made a little script to call diff.  

```
#!/bin/bash
if [ -!e $3 ] 
	then
	if [ -!e $2 ]
		then
		kdialog --error "You need at least two files selected to do a diff"
	else
		diff -EbB $1 $2>/tmp/tempDiff
		gedit /tmp/tempDiff &
	fi
else
	kdialog --error "This script only supports comparison of two files"
fi
```

This makes sure that there are only two files being passed to the diff and outputs a file to the /tmp directory.  Then opens the file in gedit.
yey.


Next, you just have to add this script to the right click menu.

This is pretty easy too.

Just go to System->Preferences->Nautilus Actions Configuration

Click the Add button and you will get a popup

Enter any label, tooltip, and icon that your little heart desires then set the path to your new script (above).  So if you saved your script in ~/ you would type in ~/myDiffScriptName.

in the Parameters field you will need to enter: %M

Don't forget to capitalize this, with a lowercase 'm' the full path of the files selected won't get passed to the script.

You can jump through the tabs at the top as well and change any other options you might or might now want.

Once this is done all you need to do is kill the current Nautilus process and you should be good.

To find nautilus pid use:
```
ps ax|grep nautilus
```
and to kill use:
```
kill -HUP [nautilusPID]
```

Right click and your new item should be on your menu and working.

---

