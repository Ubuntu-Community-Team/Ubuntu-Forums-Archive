---
title: "Tip: add an &quot;Open current page in Firefox&quot; to Opera's main toolbar"
date: 2007-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by erfahren on 2007-12-15
An "open current page in Firefox" button can be added to Opera's toolbar. This comes in handy if viewing a webpage/site that doesn't support Opera. - There's more information about this at [aimwell.org - Opera Buttons](http://www.aimwell.org/Help/Buttons/buttons.html#Understanding). (The instructions there are mainly for Windows but much is still applicable.) 

All that's needed is a text editor and, if desired, a resized Firefox icon (about a 16x16 PNG) and a custom skin (see below).

To do this, first enable Opera's "Main" toolbar (if this hasn't been done) - Tools > Appearance > Toolbars - then go to Opera's Tools > Preferences > Advanced Tab > Toolbars and under "Toolbar setup" highlight *Opera Standard* and click the "Duplicate" button. It should then show up as *"Copy of Opera Standard"* - highlight it to put it in use and click "OK".

Close Opera and browse to ~/.opera/toolbar (hidden folder in your home directory - press Ctrl+H to view). There should be a "standard_toolbar(2).ini" file in there. Open it in the text editer (gedit) - (the file should be long) - and click gedit's "Find" button and search for the section "[Browser Toolbar.content]". Mine looks like:
```

[Browser Toolbar.content]
Button0, 21204=Open document
Button1, 21205=Save document
Button2, 21206=Print document
Button3, 21208=Find
Button4, 21212=Go to homepage
Button5, 69682="Set alignment, "hotlist", 6, , "Panels" | Set alignment, "hotlist", , , "Panels""
Platform Windows-Unix-QNX, Button6, 21215=Tile vertically
Platform Windows-Unix-QNX, Button7, 21216=Cascade
**Button8, "Firefox"="Execute program, "firefox", "%u", "Firefox", "Firefox""**
Platform Win2000-Unix-Mac, Feature Voice, QuickButton15, 67676=Start listening | Stop listening,,,67677 | Stop speaking,,,67678

```
Just add that line associating an appropriate button number to the execution command for Firefox.
in the above example it's:
```

Button8, "Firefox"="Execute program, "firefox", "%u", "Firefox", "Firefox""

```

An icon can be added to a custom skin for it as well. About a 16x16 .png works (24x24 is a little too big). (To find skins go to Tools > Appearance > Skin tab and click "Find more skins". The skins are installed to ~/.opera/skin)  

Go to the skin's archive in ~/.opera/skin and double-click it to open it in the Archive Manager. Add the icon into either the existing "icons" or "buttons" folder in the skin's archive. Then extract the skin's "skin.ini" file and open it in a text editor (gedit). Search for the "[Images]" section. Under it add "Firefox = *relative-path-to-icon*" 
- example: Firefox = icons/firefox16.png
Add the "skin.ini" file back into the archive.

When Opera is relaunched the Firefox button with its icon should be in the toolbar.

**To undo this** just revert to Opera's Standard Toolbar (and delete the duplicate you made) under "Toolbar setup" in the Tools > Preferences > Advanced Tab > Toolbars 
- no real need to undo the changes to the skin archive or the skin.ini - it can just be deleted and downloaded again if need be.

This has been used with various releases of Opera 8 and Opera 9 (and should work on future versions of Opera) on Ubuntu 6.06 32-bit, Ubuntu Feisty 64-bit, and the 32-bit versions of Feisty and Gutsy. 

**troubleshooting:**
[LIST]
The button doesn't appear -check that the correct toolbar is being used under "Toolbar setup" in the Tools > Preferences > Advanced Tab > Toolbars 
[/LIST]
[LIST]
The button is there but no icon - is the path to the icon in the skin.ini correct? Also - If an archive is completely unzipped it needs to be re-zipped with the skin.ini file in the root of the archive. -(I don't know a better way to explain that!) 
[/LIST]

Use this tip at your own risk. I won't be providing any support. (I don't anticipate anyone having problems, it's pretty straightforward. Opera is specifically designed to enable these types of modifications.)

---

