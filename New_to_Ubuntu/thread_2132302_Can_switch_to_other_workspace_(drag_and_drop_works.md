---
title: "Can switch to other workspace (drag and drop works)"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by lxx33 on 2013-04-04
When i click with the right mouse button on ¨move to another workspace¨ I can´t select workspace 1 (light grey).
If i select another workspace, the windows dissapear, but not appear at the selected workspace.

Any tips?

---

### Post by slickymaster on 2013-04-04
Can you do it using the the shortcut keys (Ctrl+alt+left/right) or using the panel?

---

### Post by r-senior on 2013-04-04
Workspace 1 is probably greyed out because that's your current workspace.

---

### Post by lxx33 on 2013-04-04
workspace 1 is also greyed out if i am on workspace 2. 
Ctrl+alt+left/right works to switch between the workspaced.
But for example, i´m not able to move firefox to workspace 2 by rightclicking on the firefox bar and select workspace2....
I can drag firefox to workspace 2. Its just like workspace 2,3 and 4 are nog named 2,3,4. I also have compiz installed, but dont see strange settings.

So i can switch between workspaced, but cannot move open programs to different workspaced by rightclicking with the mouse. Only by dragging.

---

### Post by stinkeye on 2013-04-04
I don't think that menu for moving to a numbered workspace works with compiz.
Moving left or right should work.

If using the cube you can set shortcuts  
in ccsm > rotate cube
to move with window to a particular cube face.

---

### Post by lxx33 on 2013-04-04
moving to the right also dont work

---

### Post by stinkeye on 2013-04-04
> **lxx33 said:**
> moving to the right also dont work
What Ubuntu release and session  are you using?
Terminal...
```
lsb_release -sr; echo $DESKTOP_SESSION
```

---

### Post by lxx33 on 2013-04-04
asus@asus-K52Je:~$ lsb_release; echo $DESKTOP_SESSION
No LSB modules are available.
ubuntu

I can switch with alt+arrow, but is i rightclick with the move and choose ¨move to workspace right¨ it will not work and the window is gone (for example firefox)

asus@asus-K52Je:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

---

### Post by stinkeye on 2013-04-04
Works here on my Quantal install.
Does it work if you log in to the guest session?

---

### Post by mc4man on 2013-04-04
The right click on window deco > Move to another workspace > pick one should work, does here.
Also the default binding to switch WS with the window in focus is shift+ctrl+alt+arrow
(with wall & 2x2 having 'preview' enabled, (it is by default), makes easier, though you have to pick an available direction, rotate doesn't matter.

Maybe create a new user  to see if it works there.., if so you've got some local issue to your current user account

---

### Post by lxx33 on 2013-04-04
@mc4man
shift+ctrl+alt+arrow works :) tnx.


@stinkeye
guest session works also

---

### Post by stinkeye on 2013-04-04
I don't know why, but I need to use the right mouse in the menu to click on one
of the numbered desktops...
while the guest session works with either left or right. :confused:

Even after resetting compiz to defaults it still only works with right mouse.

---

### Post by lxx33 on 2013-04-04
the strange tink is if i do the right click the windows dissapears and cant find it anyware.
If i go the another workspace (thats empty) and than click on firefox icon for example, that i get that old window that i tried to move. It will not open a complete new window, but move the same window from workspace to workspace (hope you know what i mean)

If i have youtube on firefox on workspace 1, and than go to the empty workspace2 and klik on the firefox icon. Than i get my youtube page, and now workspace 1 dont have the youtube anymore.

---

### Post by stinkeye on 2013-04-04
Besides having to use right click it works as it should here.
You could try resetting compiz to defaults and reloading.
**Be aware you will lose any compiz (ccsm) settings you may have changed.**
```
dconf reset -f /org/compiz/ && setsid unity
```

---

### Post by lxx33 on 2013-04-04
dconf reset -f /org/compiz/ && setsid unity

it dont work. I maby make a new install, and look if it that works. And with every software i install, i check when or if this problem occur.
tnx anywayz :)

---

### Post by stinkeye on 2013-04-04
You could create a new user and see how that works.

---

