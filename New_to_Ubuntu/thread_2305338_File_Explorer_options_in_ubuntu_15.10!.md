---
title: "File Explorer options in ubuntu 15.10!"
date: 2015-12-04
forum: New to Ubuntu
---

### Post by thexnightmare on 2015-12-04
Dear,
I am new to ubuntu and using now version 15.10.
I saw an image for ubuntu user where it shows the file manager in ubuntu pretty cool with 2 features:
1- Icons showing the file types.
2- There is a terminal on bottom of the file explorer.
How to get these options?
Thanks
[ATTACH=CONFIG]265951[/ATTACH]

---

### Post by grahammechanical on 2015-12-05
Is that an image of a utility called "File Explorer" or are you still using a Microsoft Windows name for what we call a file manager? Ubuntu uses the Gnome Files utility as a file a manager, which is also known as Nautilus. What you may be seeing is a KDE file manager called Dolphin

It does have that terminal feature that you mention

[https://docs.kde.org/stable5/en/applications/dolphin/panels.html](https://docs.kde.org/stable5/en/applications/dolphin/panels.html)

It is in the Ubuntu Software Centre and it can be installed but how well it integrates with the Ubuntu theming I cannot say and it most likely will bring in a lot of KDE libraries which it depends on. If you web search for "kde dolphin" you will see links to lots of images of Dolphin. some of which are similar to the one you show.

Regards.

---

### Post by thexnightmare on 2015-12-05
Amazing response, thanks, ive  checked dolphin and seems that is what I am looking for, I ve downloaded it, and seems it is but I am facing 2 problems:
1- The icons are not like that in the orihginal picture.
2- The terminal is a blank white, not showing the terminal.
[ATTACH=CONFIG]265961[/ATTACH]

---

### Post by buzzingrobot on 2015-12-05
The terminal used in KDE is called "Konsole". You might check if that was installed as one of the Dolphin dependencies. (Should be found in the Dash if it was installed.) It has a "Settings" (or is it "Profile?)  menu entry that enables changing background color, etc.  Now, if the terminal embedded in Dolphin is Konsole, those settings *might* carry over.

A right-click on the embedded terminal display might display something useful.

Also, Files/Nautilus has an "Open In Terminal" right-click option. This opens a new terminal, on the desktop, in the directory currently open in Nautilus.  If the option doesn't appear, install the "nautilus-open-terminal" package and then restart Nautilus to activate it, either by logging out and in or with "nautilus --quit" in a terminal.

---

### Post by thexnightmare on 2015-12-05
Thnks man,
1- I know about Opn in terminal, ut I liked more the dolphin way, how can i isntallit with all it's dependencies?
2- Whataboutthe good icons which shows the file types?

---

### Post by buzzingrobot on 2015-12-05
Packages have dependencies -- other packages that also must be installed -- and "recommended" packages, which are packages that are not required but are often used in conjunction with the package being installed.  You can avoid installing recommended packages by using the "--no-install-recommands" option for apt-get. E.g., "sudo apt-get install --no-install-recommends SomeAmazingPackage".

Dolphin is a core component of KDE, intended to be used in KDE, not Gnome or Unity, and it has, of course, a considerable number of dependencies on other KDE packages. (You can see them listed here: [http://packages.ubuntu.com/wily/dolphin](http://packages.ubuntu.com/wily/dolphin). Clicking on each dependency will display *its* dependencies, and then you can keep burrowing down that dependency chain.)

If you like Dolphin's approach, you might also like KDE.  Burn a copy of the Kubuntu install image, run it in live ("Try") mode and see what you think. (KDE can be installed on a Unity system, but I very much recommend doing a clean install of Kubuntu.  KDE is a very large and complex piece of work.)

Not quite sure what you mean about the icons.  The text displayed by a file manager is a function of that file manager, not the icons in use.

---

### Post by thexnightmare on 2015-12-05
Thanks

---

### Post by thexnightmare on 2015-12-05
Dear,
When I am trying to isntall dolphin, sudo apt-get install dolphin, this error appear (Unable to locate package), anything wrong?

---

### Post by buzzingrobot on 2015-12-05
As grahammechanical mentioned, Dolphin is in the Universe repository, which should be enabled.  You can check to make sure it is via "Software Sources" in the Software Center, or launch the "Software and Updates" tool and check that it is enabled there.

Be aware that it's likely Nautilus will continue to be the default file manager after Dolphin is installed. That is, when Unity needs to launch a file manager, it will launch Nautilus.  I don't know how to set Dolphin as the default file manager. The Cinnamon file manager, Nemo, is used by some as a replacement for Nautilus, so Google might turn up some guidance there that could be applied to your scenario.

---

### Post by thexnightmare on 2015-12-05
I donno, just restarted the pc and it worked, thanks

---

