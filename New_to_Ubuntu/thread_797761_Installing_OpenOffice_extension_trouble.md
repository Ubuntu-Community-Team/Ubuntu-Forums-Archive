---
title: "Installing OpenOffice extension trouble"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by mmelville3 on 2008-05-17
I want to install OpenOffice.org Writer extension LanguageTool on my Ubuntu laptop. I have installed it without trouble on my Windows Vista desktop using OpenOffice Writer > Tools > Extension Manager.

Now I want it installed on my Ubuntu laptop. Installation on the laptop appears to go well. Extension Manager says enabled. I restart OpenOffice Writer and I expect to see the new menu items, but none are there.  I've tried installing with Extension Manager, command line, installed in MyExtension, OpenOffice Extensions, unchecking and re-checking Java jre options in OpenOffice, rebooting.

OpenOffice is either:
Not looking in the right place to load the extension on launch
Loading the extension but not the GUI menu items

---

### Post by bclintbe on 2008-05-18
I found this helped with other OOo extensions. The current Ubuntu (8.04) ships with a stripped down install of OOo. First, remove the extension your talking about in the extensions manager. Shut down OOo. Then, to get the full install just go to synaptic and install the package called openoffice.org (it will say in the description that it is a meta package). Ignore all the other packages that show up when you search. When you install it, you'll see it's adding a bunch of other files to the OpenOffice install. Restart and reinstall the extension and see if it works.

---

### Post by SunnyRabbiera on 2008-05-18
also you hmay have to play with java too, I use the launguagetool plugin and I had to install the normal java as opposed to the one installed by default.

---

### Post by bclintbe on 2008-05-19
Just curious... what is the "normal" java you're referring to? Is it the one installed when you install all the ubuntu restricted extras? Something else? Just curious, since I once had java issue, and if you can tell me what I should be installing to clear that up in the future, it would be great.

---

