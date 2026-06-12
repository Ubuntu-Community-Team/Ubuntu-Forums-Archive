---
title: "How to install the Firefox3 +- tar.gz from the main firefox site (manual install)"
date: 2008-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by nowshining on 2008-07-11
**(Ubuntu/Kubuntu Hardy 8.04 + Gutsy 7.10)+-**

**IMPORTANT 1 and 2:** Remove the FF3 from synaptic, etc.. if you have it installed & more importantly to **NOT** get things in a bind, remove Firefox2 as quickly as you can.

Note: Doing this manually requires installing it one by one to each account incl. root if you think root should have one.

If u'd rather have the non-ubuntu patched version and want to install the one from mozilla, ur in luck, why? well the one from mozilla requires no compiling.

1.) untar

2.) move the firefox folder to your home or wherever you want it,

3.) edit your menus as usual and in the command box find the **firefox** - **NOT Firefox-bin** - file and select it, Example:

/home/USERNAME/firefox/firefox

**TIP: To run it from the terminal add sh or ./ in front of firefox, example: sh firefox & ./firefox, but make sure u cd into the folder first if not, then use the full path.**

4.) For the icons - click on the icon picture, go back into the firefox folder but this time find the **icons** folder and select a firefox icon from there. **For Ubuntu users** when u select the folder **NOTHING** will show, click open, and now you should see the icons, select one and click ok.

Bonus: Adding a Profile Manager shortcut without ever having to divulge into the terminal.

Q: WHAT IS THE PROFILE MANAGER?
A: Profile manager allows one to create additional profiles than the default one, this is useful incase you want to browse the web without any add-ons & without disabling the ones you already have, etc.. + if the (your) default firefox profile messes up on you, ie: crashes, etc.. you'll have a chance to create a new profile and continue using firefox without messing with your old one and to hopefully get your ol' one fixed or removed **(BACK UP FIRST)** and restart over with a clean slate.

1.) Do the above for making a firefox menu shortcut, etc.. but in the command after you select the firefox file, add a -profilemanager next to it, example:

/home/USERNAME/firefox/firefox -profilemanager

BONUS2: If your Cautious and want to protect this firefox folder, do the following in the terminal:

**sudo chown -R username:username /home/USERNAME/firefox/** but make sure firefox is closed first & of course you will have to do the above for each firefox you manually installed to each account.

[color=#339999]CONGRATULATIONS:[/color] There your done, it's all over. :) & Now to ReStart/Start firefox just click the shortcut you made in the menus & it should detect your .mozilla folder and all the add-ons, etc.. that you have if you had FF2. :)

---

