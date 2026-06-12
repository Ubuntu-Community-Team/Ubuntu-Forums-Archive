---
title: "How to disable application window to move out of viewable area"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by rajeevankv on 2012-03-21
How to disable application window to move out of viewable area. for example if I drag a calculator windows to extreme left side of the screen, half portion will be on my desktop(viewable area) and other portion will be on off screen area. I want to disable this movement of  windows out of screen area.

---

### Post by Immolatus on 2012-03-21
It can't truely be disabled unless you add a class or module to X to prevent it(assuming you are a programer).
Otherwise the best opting is to turn on "snaping windows" in the desktop effects menu. You can still push tham out of view but they will give resistance.

---

### Post by 3rdalbum on 2012-03-21
So we can be sure, which of the following things are you describing?

a. When you drag a window around on any operating system it's possible to position it so that part of it is off-screen. OR

b. In Ubuntu and Windows 7, if you are dragging a window around and you move your pointer to the very left/right edge of the screen, a semi-transparent box appears on that side of the screen. When you release the mouse button while this box is visible, it resizes the window so that it only takes up the left/right half of the screen.

If it's A, I don't think you can turn it off as it's a feature of all graphical operating systems since Mac System 1.0 or earlier.

If it's B, then you need to install the "compizconfig-settings-manager" package (it's in Software Center), launch it from the Dash, and disable the "Grid" plugin. Don't touch anything else in Compizconfig Settings Manager. The changes should take effect immediately.

---

### Post by airplanesimen on 2012-03-21
I think he means that the window he is dragging to the right edge at Desktop two, is showing up at desktop 1, (that part which is going outside desktop two is appearing at desktop 1 at the left edge)
But maybe i am wrong, but that is how i understood it.

---

### Post by HiImTye on 2012-03-21
> **rajeevankv said:**
> half portion will be on my desktop(viewable area) and other portion will be on off screen area
sounds pretty clear to me

there's no way, that I'm aware of to disable this, you can certainly increase the resistance in CCSM but it will not disable it entirely

---

### Post by airplanesimen on 2012-03-21
> **HiImTye said:**
> sounds pretty clear to me

there's no way, that I'm aware of to disable this, you can certainly increase the resistance in CCSM but it will not disable it entirely There is, but it requires "Compizconfig-settings-manager" or something like that (CCSM). In there you can disable the windows-dragging and the apperance of the desktop from a window with alot of setting, but it is not reccomended, it is in some cases crashing with Unity.

---

### Post by HiImTye on 2012-03-21
yes, you can make stationary windows, but that is more of a bandaid as you will not be able to move the window at all. there is no setting to my knowledge to disable moving windows between workspaces

---

### Post by airplanesimen on 2012-03-21
> **HiImTye said:**
> yes, you can make stationary windows, but that is more of a bandaid as you will not be able to move the window at all. there is no setting to my knowledge to disable moving windows between workspaces
Hmm, you can completely disable the workspace-switcher, but it isnt getting any better if you do, you only loose a very nice feature. But, i mean that i did do somthing like this on my last install of ubuntu. But, i cant say anything more, i dont have a solution to this yet.. i am trying for myself.

---

