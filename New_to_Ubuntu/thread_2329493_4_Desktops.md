---
title: "4 Desktops"
date: 2016-07-02
forum: New to Ubuntu
---

### Post by Vincent_Massi on 2016-07-02
I have the program for using 4 desktops installed. I can easily switch desktops, but they are all identical. The web tells me to drop and drag from one to another (when I have all four open) but nothing will move. How do I get them to work as separate desktops?

---

### Post by howefield on 2016-07-02
What "web" tells you to drag and drop - share the link so others can get an idea of what it is that you are trying to accomplish. Are you trying to move applications from one workspace to another or something else altogether ?

---

### Post by Vincent_Massi on 2016-07-02
I'm trying to move my games to one desktop, and my writing applications to another.

---

### Post by deadflowr on 2016-07-02
You can try the keybindings to move open windows from desktop to desktop with shift+ctrl+alt+arrow key.

---

### Post by Vincent_Massi on 2016-07-02
Thanks, Deadflowr. But while that allows me to switch desktops, it does not allow me to drag files from one desktop to another.

---

### Post by CantankRus on 2016-07-03
Using compizconfig-settings-manager you should be able to set up "edge flip move" in the Desktop Wall plugin.
[ATTACH=CONFIG]269911[/ATTACH]
Doesn't appear to be working here though.
You should still be able to use ctrl+alt+shift+arrowkeys to move to adjacent workspaces with focused window.

What I do here is install compiz-plugins which includes the cube plugin because I like the rotation effect when changing workspaces.
In ccsm you disable **Desktop Wall** and then enable **Desktop Cube** and **Rotate Cube**.
[ATTACH=CONFIG]269914[/ATTACH]
 
In **Rotate Cube** you can enable "edge flip move" and/or use keyboard shortcuts.
[ATTACH=CONFIG]269912[/ATTACH]

What I prefer to do is set up gestures in easystroke to move to next/previous workspace because it can be annoying 
when the workspace flips unintentionally when moving a window.
Perform the gesture on a window to focus and move.
(Tip: If using easystroke, change the gesture button to 3 rather than middle mouse)
[ATTACH=CONFIG]269913[/ATTACH] [ATTACH=CONFIG]269915[/ATTACH]

---

### Post by howefield on 2016-07-03
Not sure if it will help but using the "Spread" feature will show you the available desktops from which you can drag and drop the windows as you wish. To activate the spread use the Super + S keys.

Alternatively right click the window title bar of an application to be moved and select "Move to Another Desktop" or one of the other menu options.

---

### Post by Vincent_Massi on 2016-07-03
I figured it out.

You can open one desktop to the internet and another desktop to Libre Office, and switch back and forth. You can have a third desktop set to play music CDs's at the same time.. But you cannot drop and drag icons from one desktop to another.

---

### Post by peter d on 2016-07-03
It is simple to drag windows from one desktop to another. Press <Super> + <S> to reveal the desktops and drag whatever you wish wherever you wish.

---

### Post by deadflowr on 2016-07-03
> But you cannot drop and drag icons from one desktop to another.
That is something different entirely.
Icons should be the exact same on all desktops, at all times.
So don't know why they would be different from one to another.

> You can have a third desktop set to play music CDs's at the same time
You don't even need any windows open to play music. Only when you initially start playing any music.
But once you start your playlist, you can close the music player window and it'll keep running in the background.
Then just use the indicator sound application in the top right area of the panel to do some basic controls.

---

### Post by Vincent_Massi on 2016-07-03
You are correct, Deadflowr. All four desktops are identical. Using the desktops is easier that minimizing programs on the same desktop, so that's why I use them.

However, you cannot drop and drag icons from one desktop to another.

---

### Post by Geoffrey_Arndt on 2016-07-03
Because they are all actually just one desktop in the first place.   When you open different apps in desktop 1, and then other apps in desktop 2, you can click on either desktop to just work with those apps (without all the window-clutter).   You can't drag an app to another virtual desktop*  cause it's "already there" . . . just hidden from view on that alternate desktop.   That's why they are called "virtual" desktops (or more accurately, virtual workspaces . . . they "simulate" different desktops).    Now, for actual different desktops, another type of technology is needed altogether - -  virtual machines or docker containers **.

EDIT . . decomposition of points below:

* . . (without removing it from its original window - so drag is just another method of "move")

** . . (or as buzz relates below, KDE has the "activities" function . . although I personally haven't used it when I was running only KDE,  so, can't be 100% sure how it operates)

Bottom line. virtual workspaces, the way Ubuntu has it set up with the Quad Screen default, works great for segregating apps by type of use case (file mgmt, photo mgmt, number crunching, programming, etc.)

---

### Post by buzzingrobot on 2016-07-04
Display the "spread" of all virtual desktops, either by a keystroke or by clicking the icon in the Launcher (enable it in System Settings) and move app windows around.  You can also usually right-click on an app windows header and expose an option to move the window to another workspace.

If the OP wants to maintain *different desktops* in each virtual workspace, KDE's Activities feature is the only thing I'm aware of that will do something like that.

---

