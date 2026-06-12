---
title: "Problem displaying certain GUI applications in unity"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by jhn134910 on 2013-07-19
Hello there,
I'm using version 12.04 with unity desktop. Old version, but I'm stuck on it for various reasons.
Vast majority of GUI applications launch correctly, a new application icon appears, and the windows are displayed.
However, I've installed successfully two applications, kdiff3 and more recently visualvm from ubuntu archives. I start them okay from the command line (e.g. './kdiff3 &' or './jvisualvm') in the appropriate directories. Using 'ps' I see that they have processes running. I see their icons appearing on the left hand side of the screen, however no GUI window. When I click on icon (left click / double-click), right click say kdiff3 nothing appears to happen. Visualvm for example, is meant to show a license agreement screen when first started and this is also indicated in the icon, but I cannot access it.
I tried a couple of things, but as I'm a beginner I'm not sure what to do. I tried:

1) Alt-tab through the processes, to see if I can select them. In the case of kdiff3 I can even see its mini-windows here when application is in focus, but cannot enlarge them. For visualvm, when application is in focus I can see no mini-windows.
2) Using the Super Fn key I tried stepping through the numbered icons after I dragged and dropped the application into the dash. Again nothing.

I'm trying to avoid a re-install, as it took me the bones of a day to get my environment just the way I want it.
As this is my first post, I'd just like to thank the community for an excellent working environment. Any guidance much appreciated.
//John.

---

### Post by mc4man on 2013-07-19
As far as visualvm - 
browse in nautilus to /usr/share/applications & scroll down to bottom, you'll see a VisualVm  icon. Drag & drop it on to the unity launcher, it should work fine to start, minimize to or close visualvm. *see screen, shows location & icon in launcher after draggin & dropping.

For kdiif3 same deal, go to /usr/share/applications/kde4 & DnD the KDIFF3 icon on to launcher - screen 2

---

### Post by jhn134910 on 2013-07-20
Thanks mc4man for the response.
After carrying out the instructions you kindly sent on, the kdiff3 and visualvm icons are now locked into unity launcher. However, I still cannot view the windows. On the left hand side of a running kdiff3 or visualvm I can see the symbol '>', which is not the usual solid arrow-head for the other working applications. For example for visualvm, when I right-click the icon I see, visualvm, Unlock from launch and quit (if it is running).

Then I took a screen shot (attached), and got a strange result. The windows were in the screen shot, but not on my screen. Is there something up with my usage of the workspace switcher. My intention is to view all applications in the same workspace.

---

### Post by jhn134910 on 2013-07-20
Changed my display settings and I can view all applications :D
My screen resolution was too high.

---

