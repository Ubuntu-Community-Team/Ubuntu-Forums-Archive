---
title: "How do I get an icon to display in a Launcher item?"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by bwallum on 2012-04-04
Hi

I have an application (Qcad) showing as an icon in the Launcher. The icon is the generic question mark. I have a suitable .png icon file for Qcad.

How do I get the icon to show in the Launcher? Is there a file that shows the current items in the Launcher and their associated icons?

---

### Post by dolphin194 on 2012-04-04
Create a custom launcher for the application, and drag that launcher into the dock.

---

### Post by Frogs Hair on 2012-04-04
You can also add an icon from the main menu without creating a custom launcher . Open the main , select the category of the application on the left and click on the line where the application is listed . A dialog box will open . Click on the icon picture on the left and navigate to a folder where you have placed an icon you want to use . It may not appear on the launcher until logout and back in. The picture has two I am currently using .

---

### Post by bwallum on 2012-04-06
Thanks guys, got it working nicely. I used the 'Main Menu' method, added an item and it did the job without any hassle. One thing that got me going was finding the 'Main Menu'. For anybody following click on Dash, the top left icon in the launcher, and type in "main".

Many thanks again.

EDIT
gandalf3 very kindly pointed out that Main Menu is not a default file so you may have to install it from the Ubuntu Software Centre.

---

### Post by gandalf3 on 2012-04-06
I had a similar problem, not being able to find the main menu.
(it's not under /dash/'main'..)
I'm running Ubuntu 11.10
all help appreciated..

---

### Post by gandalf3 on 2012-04-06
never mind.. i didn't know you had to download it.. :oops:
i haven't tested it yet, but it seems good so far!
thanks!

---

### Post by bwallum on 2012-04-06
Well done gandalf3, I wasn't aware that it wasn't a default file, thanks for adding that bit of useful info.

---

### Post by gandalf3 on 2012-04-11
hmm.. well it worked for me! 
only one problem.. i changed the icon for the launcher for flightgear (fgrun) and flightgear itself (fgfs) the launcher worked right, but when flightgear (fgfs) appears in the launch-bar thing, it's back to it's old ugly question mark self..
(it looks right in the dash though..)
any idea why this happens?
also, there might be a way to changes the icon with out the main menu if you can find the .exe and go to "properties" there's another icon that you can click on and browse to a new image.
i haven't tried it yet though..

---

### Post by bwallum on 2012-04-12
Open Main Menu, navigate to your application. I guess you will go through Menus:Games to your app shown in the Items: pane. Highlight your app and then click properties.

The Launcher Properties window will open. The icon will be shown in the top left of that window. If you now click on the icon the 'Choose an icon' window will open. You can then choose an icon file.

I know that .png files always work as icons, I'm not sure if any other/which formats work. I guess your selected icon image may not work because it is the wrong format or size.

You can use Gimp to change size and formats to create icons from any graphics image in formats that Gimp can handle, which is a lot.

---

### Post by gandalf3 on 2012-04-16
well, no.. that's working, but what happens is it opens as a "panel" (at least, thats what it says when you hover the cursor over the "?" icon..)
i could change the icon for "panel" in the main menu, but then it would change (i suspect)
for every program that opens as a "panel" (i can't think of any right now, but i know there's others) it's not so bad, the launcher appers with the icon i wanted, but it just opens a lot of "?" icons in the launch bar when running fgfs..
if this is not an easy fix, i will just live with it, but..

---

