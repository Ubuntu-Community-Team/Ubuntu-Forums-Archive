---
title: "Launcher Bar"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by Patreick_Lucas on 2015-02-16
Hi

I have a few questions on the launcher bar to the left of the display.

1) Can it be moved to the bottom of the screen?
2) Why do some apps appear on it and some don't?
3) Ir ir possible to manually add programs to it?

Hope someone can enlighten me.

Regards

Patrick

P.S. I installed Skype. I know it is running because I hear the sign-in sound when Ubuntu starts up. The only way I can get to the Skype window is by going through Search. Is there another way such as putting the Skype icon on the launcher bar?

---

### Post by slickymaster on 2015-02-16
> **Patreick_Lucas said:**
> Hi

I have a few questions on the launcher bar to the left of the display.

1) Can it be moved to the bottom of the screen?
Shortly, you can't. You can achieve something close related by installing unity-tweak-tool```
sudo apt-get install unity-tweak-tool
```and then run it and in Launcher choose autohide. With that done  install cairo-dock```
sudo apt-get install cairo-dock
```run it and add the applications in the dock you wanna use.
> **Patreick_Lucas said:**
> 2) Why do some apps appear on it and some don't?
I think it's basically a development design decision.
> **Patreick_Lucas said:**
> 3) Ir ir possible to manually add programs to it?

Hope someone can enlighten me.

Regards

Patrick

P.S. I installed Skype. I know it is running because I hear the sign-in sound when Ubuntu starts up. The only way I can get to the Skype window is by going through Search. Is there another way such as putting the Skype icon on the launcher bar?
See this: [How can I edit/create new launcher items in Unity by hand?]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand")

---

### Post by haplorrhine on 2015-02-16
Drag-and-drop from the dash-home interface (the uppermost icon).
right click + "Unlock from Launcher"

You can also return to the gnome desktop, with drop-down menu at the top, if you prefer.

---

### Post by craig10x on 2015-02-16
Adding programs to the launcher is easy...just search for the program using the dash and open it, once it is opened (at which point it appears in the launcher) just right click it's icon on the launcher dock and select "lock to launcher" and it will stay on....to remove an app on the launcher, right click and select "unlock from launcher"....

---

### Post by grahammechanical on 2015-02-16
> [COLOR=#000000]1) Can it be moved to the bottom of the screen?[/COLOR]

No. Unity 7 is not designed to do that. In fact it has never been possible to do that. And it would cause all sorts of problems when Unity 8 is converged into Ubuntu during the next 12 to 18 months. The Ubuntu phone has a launcher on the left that is activated by swiping from the left screen edge and the other three screen edges of a Ubuntu phone also have swipe activation. The intention is to converge the Ubuntu phone code into the Ubuntu desktop code. So, the four screen edges are now protected space in Ubuntu.

Regards.

---

### Post by newb85 on 2015-02-16
> **slickymaster said:**
> Shortly, you can't. You can achieve something close related by installing unity-tweak-tool```
sudo apt-get install unity-tweak-tool
```and then run it and in Launcher choose autohide. With that done  install cairo-dock```
sudo apt-get install cairo-dock
```run it and add the applications in the dock you wanna use.

I think it's basically a development design decision.

See this: [How can I edit/create new launcher items in Unity by hand?]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand")

It's been a couple years since I played with Cairo-Dock, but as I recall, last time I installed it, it set itself up as its own DE, so when logging in, I clicked the Ubuntu logo by my name and selected Cairo-Dock, resulting in a session that had Cairo-Dock *instead* of Unity.  (No auto-hiding of the Launcher required.)  Of course, Unity also includes the top bar, so that goes away, too.  I recall Cairo-Dock having a few extra bars in the top corners to essentially fill its shoes.

---

### Post by craig10x on 2015-02-16
Right, when you install Cairo Dock, a session was created so that you had the option of logging into it on the log in screen by clicking the "cogwheel" next to where you type the password in...
And when you went into that, you still had the top panel bar but no unity launcher or dash...and cairo dock on bottom, which can be auto-hidden of course...

---

### Post by newb85 on 2015-02-17
I decided to give the current version of Cairo-Dock a test drive on VirtualBox.  It was as I remembered it, although I was pleasantly surprised to find they've added nice search functionality to the application menu.

---

### Post by craig10x on 2015-02-17
@newb85: Very Nice Added Feature (the menu did not originally have that "search function"...I think you have the option of having the full top panel or the abbreviated top panel yours has...isn't that right?

Also: I recall that once you initially log into the "cairo dock session" it automatically defaults to it each time you sign in on the log in screen (until you manually change it again...say, back to unity session for example)...
So, if one wants a dock on the bottom, cairo dock session is an easy alternative...

---

### Post by newb85 on 2015-02-17
> **craig10x said:**
> @newb85: Very Nice Added Feature (the menu did not originally have that "search function"...I think you have the option of having the full top panel or the abbreviated top panel yours has...isn't that right?

Don't know about the full top panel.  The top panel is actually a dock in "Panel" view, which means no zoom on mouse-over, and separators are shown as spaces between groups of icons.  I don't know of a way to eliminate that empty space while in Panel view.

> **craig10x said:**
> Also: I recall that once you initially log into the "cairo dock session" it automatically defaults to it each time you sign in on the log in screen (until you manually change it again...say, back to unity session for example)...
So, if one wants a dock on the bottom, cairo dock session is an easy alternative...

I think that's actuall a function of the display manager.  In the cases of GDM and LightDM, that's true.

---

### Post by Patreick_Lucas on 2015-02-18
Thanks guys

---

