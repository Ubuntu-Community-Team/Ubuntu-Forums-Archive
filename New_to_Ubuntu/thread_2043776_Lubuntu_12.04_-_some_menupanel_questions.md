---
title: "Lubuntu 12.04 - some menu/panel questions"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by lamarkia on 2012-08-17
Hello, bit of a noob here but trying to learn more. I can do the basics like installing and adding ppas but use the GUI option if possible before using command line. Lubuntu is less familiar to me, hence asking questions here.
Installed Lubuntu 12.04 as an upgrade from Ubuntu 10.04, after trying Ubuntu 12.04 and wanting something more lightweight and customizable. Overall, I like it - got all the apps I need and my computer is running quietly for a change. There are just a few minor things which I'd like to tweak:

1. Main Menu (the app from Lubuntu software centre) doesn't work. I can open it and uncheck items I don't want but they still appear in the menu.

I found a workaround but would prefer to use the app:
-Open usr/share/applications
-Tools>Open as root
-Copy unwanted item to new folder named 'Deleted menu items'
-Delete unwanted item from usr/share/applications
-They can be restored by copying back from 'Deleted menu items'

2. How do I add a launcher (single icon to link to my home folders, not an application) to the panel? It's not an option in Add/Remove Panel Items. The closest I got was 'Directory Menu' which can be edited to go to home/lamarkia/documents but not on one click, it opens a drop-down menu.

3. How do I remove the menu option 'Open in Terminal' and just have drop down items open on one click? If that's not possible, could I make a keyboard shortcut to open e.g My photos

Thank you for reading. I hope I will be able to contribute answers as well as ask questions to the forum. Some [[COLOR="Blue"]_Linux user tips_[/COLOR]]("http://delicious.com/lamarkia/linux") I have bookmarked.

---

### Post by nyamina on 2012-08-17
> **lamarkia said:**
> Hello
Hi :)

I think the Main Menu program is a bit funny with Lubuntu. I don't think it's really designed for it. This program, however, is designed for LXDE and worked fine with me when I used Lubuntu. [http://forums.linuxmint.com/viewtopic.php?f=175&t=83926](http://forums.linuxmint.com/viewtopic.php?f=175&t=83926) I know, I know, it's command line stuff, but you can just copy and paste it in to the terminal (you can copy and paste commands into the terminal with ctrl+shift+v) and it should work fine.

I'm not quite sure what you're asking with the second one, but if you just want a launcher to open your home folder on the panel, just add the file manager as an application launcher.

With the third one, I'm not quite sure what you're asking! As far as I know, open in termal is just a little shortcut, all it does is, say if you're in your "photos" folder, basically just does "cd photos."

---

### Post by lamarkia on 2012-08-17
Thanks, nyamina. That answers question 1. Will try that now :) Also, thanks for CTRL+SHFT+V. I couldn't work out why terminal didn't accept CTRL+V.

2. In this example, I edited the path to home/lamarkia/photos. I would like to open 'photos' (to look at them) as the default. I don't need the option for terminal here. I'm not averse to using terminal, and can see the advantages for such tasks as renaming batches of files, but 99% of the time I open 'photos' I want to see the pictures.

[img]http://i.imgur.com/tOx0F.png[/img]

3. In this example I would like to click menu folder, then music folder (again to open in gui as default), and not be given a third step.

[img]http://i.imgur.com/cuXEN.png[/img]

---

### Post by lamarkia on 2012-08-17
Ok, tried the [[COLOR="blue"]_Mint forum instructions_[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=175&t=83926"). Menu editor appeared on my drop down menu. Clicked on it, box with "Please enter password to run lxmed in fully operational mode" , entered my password, box disappeared, menu editor didn't open. Uninstalled via Software Centre.

Tried [_[COLOR="Blue"]these instructions[/COLOR]_]("http://lxlinux.com/#8") (having previously DLd and extracted lxmed, to my Download folder, from sourceforge) which seems to be a longer way to do the same thing and obviously, produced the same result.

 cd Downloads/lxmed
    sudo apt-get install build-essential
    sudo mkdir -v /opt/lxmed  *[COLOR="DarkRed"](*MY NOTE this wasn't necessary as that file already exists)[/COLOR]*
    sudo cp -v content/lxmed /usr/bin
    sudo chmod -v +x /usr/bin/lxmed
    sudo cp -v content/LXMenuEditor.jar /opt/lxmed 
    sudo cp -v content/uninstall.sh /opt/lxmed 
    sudo chmod -v +x /opt/lxmed/uninstall.sh
    sudo cp -v content/lxmed.png /opt/lxmed 
    sudo cp -v content/lxmed.desktop /usr/share/applications

I'll go with the workaround for now. Will update the thread if I find another solution.

EDIT: [_[COLOR="Blue"]The next chapter[/COLOR]_]("http://lxlinux.com/#9") seems to be what I'm looking for but I don't fully understand the instructions (how to save in what format)

---

### Post by nyamina on 2012-08-19
> **lamarkia said:**
> Thanks, nyamina.

That's alright, I wish I could have got it sorted for you! So are you saying that when you click on the icon you get an option to either open in terminal or open in folder? I never got that when I was using LXDE. That could actually be a bug.

As for wondering whether you can have a link directly there, to "music" or "photos" I don't think so; I mean, you could possibly do it, with a lot of effort - like making a link, then creating a .desktop file, and putting it in the right place, or something, but I wouldn't like to say, it's not my specialty. The new Lubuntu comes with the Audacious music player, you could put an icon to that on the panel (or whatever music player you use) and use that to access your music?

I couldn't help but notice you have GIMP in your launcher. If you can run GIMP, you could probably run Gnome-Classic (no effects), or another environment (like XFCE, which is also light) which will likely be a lot more featureful. I've heard it said that LXDE is unfinished. Then again, there's not all that much that you can't do in LXDE, apart  from editing the menu. It's just the menu editing and startup programs,  stuff like that, real customising which is just a nightmare in LXDE. You could try their forum for advice too, it seems pretty good. You could go around editing .desktop files directly, which I only know how to do from having to install Zotero. It's not too hard, it just involves editing text files, so if you have to do more than a few it could be a pain.
*Edit:* I just saw your link to the work-around, which is about the same kind of thing =)
*Edit again!:* Actually, I think you need Java for the lxmed. Maybe that was the problem?

---

