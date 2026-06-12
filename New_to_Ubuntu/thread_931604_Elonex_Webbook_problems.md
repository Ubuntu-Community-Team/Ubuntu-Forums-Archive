---
title: "Elonex Webbook problems"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Iaintoo on 2008-09-27
Hi all,
having major problems withan Elonex Webbook running Ubuntu.

Attempting to play games I just get a screen with lines on it, the Games appear to load as the music is playing and the screen is the colour of the intro screen, just full of fuzzy lines

I was prompted to load updates, which I did, now, whenever I try and access anything through the address bar or Search, I get a large box headed:
 Assertion Failed!
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://www.yahoo.co.uk/](http://www.yahoo.co.uk/))
7:getEngineByAlias([http://www.yahoo.co.uk/](http://www.yahoo.co.uk/))
8:getShortcutOrURI([http://www.yahoo.co.uk/](http://www.yahoo.co.uk/),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])

Any ideas, on either??
thanks

Iain


SOLVED


Right, if anyone else has screen corruption problems, go to :
[http://www.webbookblog.com/?cat=24](http://www.webbookblog.com/?cat=24) and install the via drivers for compiz, solves the problem completely. (even if you don't install compiz.)

---

### Post by Iaintoo on 2008-09-28
OK, solved the firefox problem. Had to reboot several times and reinstall the latest version.
Still have the corrupted screen issue when playing games or the educational package, anyone any ideas on those? Everything appears to load but the screen is just a mess of horizontal lines.

thanks

iain

---

### Post by tonybaqain on 2008-09-28
[I]before reading this, please note that at the last of this post, there might be a loss of your data.
[/I]
if this is a happens-many-time problem, you can do the following:
first close all instances of firefox, if you're not sure firefox totally exited: then do the following using the terminal :
```
sudo killall firefox
```

and then type the following :
```
mv ~/.mozilla/firefox ~/.mozilla/firefox-old
```

then run firefox again.
a new profile will be created for you, but please be aware of the following loss: 

[LIST]
[*] All saved sessions and passwords.
[*] History, bookmarks and favourites.
[*] Some plugins that rely on the personal directory.
[*] Might be more, if your using special plugins, or i forgot something.
[/LIST]

be aware, and have fun :)

---

### Post by Iaintoo on 2008-09-28
Thanks Tony, I eventually solved the firefox problem by doing just that. 
It's the corrupted screen issue that remains. Found on the webbookblog I can get the educational package to open from the terminal window. Apparently *"there is an XV issue with Gcompris, the educational package, which causes it to launch to a corrupted screen"*, Not sure how I'd get a game to open from the terminal to see if that works, just going to try pot luck.

iain

---

