---
title: "Howto: Edit Kubuntu Kmenu &amp; Create Custom Launcher"
date: 2011-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by TurtleKing on 2011-07-17
Well, I figured out how to do it, and wanted to make a tutorial (might be easier than Google-Fu) on adding custom launchers and removing them (tested both). In addition, I wanted to give back to the Linux community for all the support they given me in the past, present and future. So like Black Eye Peas would say, "Let's Get it Started!" (lame quoting skills :lolflag:)

Part I: Edit Kmenu on Kubuntu 11.04 (64 bit)

Step 1: If you have a working keyboard, then your good to go. If you don't get your hands on a working one. You are going to need the Alt key and the F2 key. Of course this can be changed in the keyboard shortcuts.

Step 2: If step 1 checks out fine, proceed to press and hold alt and press F2 on your keyboard.(order does not matter)). After doing so you will see a quick pop-up at the top of your screen like in the screenshot below:
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot2.jpg[/IMG]

If you do not get this pop-up window, then I am afraid your going to have to get additional help (not me). 

Step 3: In this pop-up box; type in kmenuedit, you should get a suggestion below that will allow you to click on it. This is not important since hitting enter will open it anyways.
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot3.jpg[/IMG]

Hopefully you should get a window with the menu options listed like in the following picture:
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot4.jpg[/IMG]

If you don't, get additional help (not me).

Part II: Making shortcuts with Kmenuedit:

Step 1: Click on arrow (>) for the menu section where you want to place your launcher. For practice sake, lets pick system or utilities:
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot6.jpg[/IMG]
Step 2: Once you are in the menu section where you want to place your new launcher, click on new items near the top of the window. You should get a pop-up asking you, for an "item name?" This is pointless really since you can rename it once you fill this out.
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot7.jpg[/IMG]

Step 3: For pratice sake, lets make a kmenu launcher:
for the name; put kmenu, 
leave description blank,
for comment; kmenu editor, 
and for command; kmenuedit.
Make sure there is no space in between kmenu & edit (menu edit = wrong; kmenuedit = good).

Step 4: Once you filled out all the stuff on step 3, go ahead and click on save near the top of the window:
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/snapshot8.jpg[/IMG]

I will not save mine since I already have one created. Once you clicked on save it will display a small loading notification and disappear to indicate it is done.

Step 5: Double check that it is now in the kmenu > [menu section where you placed it] > Kmenu. If it is not there, did you click on save silly? lol

Step 6: Grab a cup of juice, coffee, or whatever you prefer and pat yourself on the back. Good Job! B)

Notes: To give launchers an icon, just click on the empty space box on the top right corner.

Also, if you didn't have trouble following this howto, then try making a launcher for root folder privileges (root dolphin). Unless, you don't ever need this or are afraid to mess with your system files. Hint: command is "kdesu dbus-launch dolphin" without quotes.

Thanks for reading. And don't forget, Linux Rocks!!!!!:guitar:

---

