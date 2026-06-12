---
title: "Launcher in Menu Will NOT go away"
date: 2017-03-17
forum: New to Ubuntu
---

### Post by poisonfor3 on 2017-03-17
PLEASE HELP

This is a little thing to most people but it is bugging me to no end.

Background to problem:

I just switched to Xubuntu and took 3 days but got all my theme, programs and settings just the way I like them. Last thing I am doing is to setup the Menu the way I like it. 

Been using alacarte to sort it out because the default one will not let me do some stuff. I going along, learning a lot and having a lot of fall backs, so be it. Then, the Menu got a "Launcher" somehow "stuck" in my menu. 

I do not like the new look of whisker and hate Unity so i use a basic Application Menu. (PLEASE do not get me wrong I am glad the other menus are out there for the people who like them, I am not trying to put them down. Just not my cup of tea.) I have both the "whisker menu" and the "basic Application Menu" right now and am going to delete the "whisker menu" after it is all setup. 

Problem:

The menu(s) keep moving stuff on me and adding stuff ... kinda buggy. BUT I keep plugging away at it then the evil Launcher from hell showed up in my Menu. not in the whisker menu just the one I want to use the application menu. I think it is one I made myself but ended up not using because I have the Launcher for that program in the Panel now. BUT I can not get rid of it from the menu.

The bug is, It is not even showing up in alacarte or the stock menu editor ... at all. You can't delete what you can not see. I tried removing alacarte. Nope. I tried deleting the program the Launcher was pointing at (Konqueror) that got rid of the other Launchers for the program but not the one that is stuck there. It did however remove the "Konqueror Icon" that was attached to the Launcher. And when I re-loaded Konqueror it found the Launcher and re-applied the Konqueror Icon back to it. It is a wrking Launcher and works just fine BUT I just can not get rid of it.

A google search and a search of this site just keeps showing how to ad or remove Launchers without this "bug". I just could not find anything on this problem at all.

Anyone know how to delete that silly thing?

---

### Post by ajgreeny on 2017-03-17
Have a look in **~/.local/share/applications** to see if there is a konqueror.desktop file which will then make a launcher automatically appear in both the main and whisker menus.

I am not sure why you can not stop it showing using alacarte, but if you either delete the .desktop file, or just move it somewhere else in case you want it later, that might remove the menu item.

---

### Post by poisonfor3 on 2017-03-17
With your help I had it fixed faster than it took to make this post. First I went to where you pointed "**~/.local/share/applications" ****and clicked on the jumpers there**&#8203; and found one that seemed like it was going to the same place. (Nothing named what you said it was kde4... something) Next i deleted konqueror in case I deleted the wrong thing it would (I hope) remake the stuff when I re-installed it. Then I went back to where you pointed "**~/.local/share/applications  **and removed the jumper and POOOOOF ALL GONE! I kid you not I did a little dance :)

THANK YOU. 

Here is a nice pic. Is it so nice and clean. No need for all them fancy stuff. Just a simple little menu to get me where I need to go. :P

---

### Post by ajgreeny on 2017-03-18
Not sure what you mean by "jumper" but I am glad you got it fixed, and thanks for marking as SOLVED.

---

### Post by poisonfor3 on 2017-03-18
My bad. Not sure what it is called but the   kde4 ____ .desktop file.  They seem to me a key part of the menu layout. I have spent all day today researching the whole menu topic to learn how to backup my menu. I started a post on it here:

[https://ubuntuforums.org/showthread.php?t=2355897](https://ubuntuforums.org/showthread.php?t=2355897)

 but not getting any help on it but that does not go no here. I will do a follow up post on that thread soon.

---

