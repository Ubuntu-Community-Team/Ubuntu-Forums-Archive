---
title: "What to do if linux based game freezes? 0_o"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Kronie on 2008-06-11
basically title sais it all.. in windows it was as simple as pressing alt+tab or ctrl+alt+del, and then finishing the process. in ubuntu(linux) on the other hand, its as far as my experience goes-impossible. or say i want to switch to another program(firefox for example), but i dont want to quit the game.. what do i need to press? alt tab doesnt work. ubuntu just cant seem to notice that i am pressing it. all it does is switching menus in game. when i am working in ubuntu(firefox, music player,[and even]wine etc) alt tabbing does what its meant to do, switching tasks.. so, what button combination do i need to press to switch to other task while i am i linux based game?

---

### Post by sdennie on 2008-06-11
Often times if a fullscreen game hangs and you can't get out of it, you can hit Ctrl-Alt-F1, login and forcefully kill the game (kill -9) and then hit Ctrl-Alt-F7.  As for why you can't Alt-Tab when the game is running, I'm not sure.  Maybe the game is intercepting those keys and not letting them get through to the window manager.

---

### Post by Hobo Joe on 2008-06-11
A workaround I've found for this is to set the game to windowed mode, and when it launches, set it to fullscreen with the window manager hotkey.

This will free up your keys for other things like alt-tab or media control etc.


By default the 'set fullscreen' hotkey isn't mapped. To change it, go to System > Preferences > Keyboard Shortcuts.

---

### Post by Kronie on 2008-06-12
@hobo joe
ok, that sounds like a way out.. and i just found a use for scroll lock button :P the only problem is, how do u start the game in windowed mode? 0_o Is that something u need to change in in-game options or some magick u apply on the launcher?

---

### Post by Paqman on 2008-06-12
Alt-tab works just like it does in Windows. Alternatively you can switch to another workspace (often Ctrl-Alt-arrow key)

From there you can go to System Monitor and end the process. Alternatively, hit Alt-F2, type in 
```

xkill

```
and click on the unresponsive window.

---

### Post by Trail on 2008-06-12
You can press Alt+SysRq+F to kill the process with the highest memory consumption. Probably that game.

---

### Post by dje on 2008-06-12
You can use Ctrl + Alt + Backspace to restart X

---

### Post by billgoldberg on 2008-06-12
You can do multiple things,

I switch to another workspace using the expo plugin activated by moving my mouse to the right corner.

The use the terminal to kill the app.

Or you could just try "alt+f4" and a dialog box should come up asking you if you want to force quite the app.

---

### Post by Kronie on 2008-06-14
nope, none of those work.. its like.. a game is some kind of layer over the desktop that is tightly sealed over it.. i cant make ubuntu see any commands while i am in game. except for wine games.. they work alright. even if i make the edge shortcuts, it simply wont see it. i tried every possible button combination that could kill/minimize the game, but none of them work.. its like the game is my OS 0_o
i tried this one:
Alt+SysRq+F
all it did is it took the screenshot of the active window.
i tried restarting X(ctrl+alt+bkspace (all at the same time -_-), all it did was the charachter in game fired(ctrl) and alt fired(alt)
alt f4.. no results either
ctrl+alt+left/right.. doesnt work. so does ctrl+alt+f1(for the terminal)

---

### Post by ramjet_1953 on 2008-06-14
If none of the previously suggested methods work, the only way to get back control is the famous [COLOR="Red"]R[/COLOR]aising [COLOR="Red"]S[/COLOR]kinny [COLOR="Red"]E[/COLOR]lephants [COLOR="Red"]I[/COLOR]s [COLOR="Red"]U[/COLOR]tterly [COLOR="Red"]B[/COLOR]oring key sequence.

i.e.

[SIZE="4"]Alt+SysReq+r

Alt+SysReq+s

Alt+SysReq+e

Alt+SysReq+i

Alt+SysReq+u

Alt+SysReq+b[/SIZE]

This manually takes control of things and safely shuts the system down.

Regards,
Roger :cool:

---

