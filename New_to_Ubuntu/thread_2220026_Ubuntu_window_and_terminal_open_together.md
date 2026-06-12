---
title: "Ubuntu window and terminal open together?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by keiths2 on 2014-04-26
Hi, my first of, I suspect, many queries. First timer in any flavour of Linux, switching from WinXP to Ubuntu 14.04. 
After a big struggle yesterday I managed to install Ubuntu onto an otherwise empty second hard drive, and then spent some time trying to figure out why it didn't work. I was able to get it going by looking around here, but I can't see an already answered question covering this query.
Basically, I want to install Seamonkey, as I've been using it for years in Windows and had it configured as I wanted it. I realise it's not in the Software Centre so there are difficulties. I have already downloaded it and can extract it onto the desktop, but then I come to a stop. There is no 'readme' or 'install' file in the package, so I don't know how to proceed from here.
There are a couple of places on the 'net giving some sort of instructions, but as usual, they assume you know what you're doing - I don't.
They give lines of commands to write in the command line (terminal console?), but here I have another problem. If I open a terminal console, it covers the "whole" screen, so now I can't see the window (correct term?) with the instructions to copy&paste into the terminal command line. Should it be like this? Should I be able to have a screen window open at the same time as the terminal console command line, or am I doing something so staggeringly obviously wrong. I can see no means of reducing the console window size, I have to exit the terminal to get back to the window.
Any help, preferably in words of one syllable or less, would be appreciated. Also any further advice on installing Seamonkey please.
TIA

---

### Post by 3rdalbum on 2014-04-26
> **keiths2 said:**
> Hi, my first of, I suspect, many queries. First timer in any flavour of Linux, switching from WinXP to Ubuntu 14.04. 
After a big struggle yesterday I managed to install Ubuntu onto an otherwise empty second hard drive, and then spent some time trying to figure out why it didn't work. I was able to get it going by looking around here, but I can't see an already answered question covering this query.
Basically, I want to install Seamonkey, as I've been using it for years in Windows and had it configured as I wanted it. I realise it's not in the Software Centre so there are difficulties. I have already downloaded it and can extract it onto the desktop, but then I come to a stop. There is no 'readme' or 'install' file in the package, so I don't know how to proceed from here.
There are a couple of places on the 'net giving some sort of instructions, but as usual, they assume you know what you're doing - I don't.
They give lines of commands to write in the command line (terminal console?), but here I have another problem. If I open a terminal console, it covers the "whole" screen, so now I can't see the window (correct term?) with the instructions to copy&paste into the terminal command line. Should it be like this? Should I be able to have a screen window open at the same time as the terminal console command line, or am I doing something so staggeringly obviously wrong. I can see no means of reducing the console window size, I have to exit the terminal to get back to the window.
Any help, preferably in words of one syllable or less, would be appreciated. Also any further advice on installing Seamonkey please.
TIA

Assuming you downloaded SeaMonkey as a binary and not the source code: You double-click on the 'seamonkey' file in the folder to run the program.

If that doesn't work, drag it to the terminal window.

It sounds to me like you are not opening the terminal correctly. The correct way is to press Control Alt T or do a search in the Dash for Terminal. Don't press Control Alt F1, that one takes up the whole screen.

If you are pressing Control Alt T and the terminal window is maximised, either drag downwards from the menu bar or press the little Unmaximise button at the left of the menu bar.

---

### Post by jdeca57 on 2014-04-26
If the problem of the maximized terminal is solved this [http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/](http://linuxg.net/how-to-install-seamonkey-2-25-on-ubuntu-14-0413-1012-1012-04-linux-mint-161413-and-elementary-os-0-2/) seems a rather copy and paste (easy) way of solving the problem. It is based on sourceforge - [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) - which makes it a reliable source.

---

### Post by keiths2 on 2014-04-27
Wow! That's it, thanks. It's so simple when you're told. :D
You were correct in your assumption that I wasn't opening the terminal correctly, I was using the Ctrl Alt F1. I then couldn't believe it was as simple as clicking on the 'seamonkey' file to actually get it started running. I thought I had to do a complicated install thingy. 
Just one further question at the moment <grin>. 
I've got a copy of the seamonkey icon in the Launcher and it works OK, but I still have the extracted seamonkey folder on my nice clean desktop. Where/how would you suggest I move it to, and will the icon in the dash still launch it OK?

---

### Post by keiths2 on 2014-04-27
Thanks jdeca57. That **"WAS" **going to be the link I would have used, but the answers from 3rdalbum solved my problem before I had to do that. Thanks again anyway for taking the trouble.

---

### Post by 3rdalbum on 2014-04-27
You can move Seamonkey's folder anywhere you want. The "correct" location for it is in /opt but that's just a general guideline, in reality you can put it anywhere.

The Launcher icon you created won't find SeaMonkey if you move it. You can unpin the Launcher icon and then create a new one when you have put SeaMonkey in the place you want it.

---

### Post by keiths2 on 2014-04-28
Many thanks again 3rdalbum, much appreciated.

---

### Post by keiths2 on 2014-04-30
Well, it sounded very simple :( but whatever I do the Seamonkey folder still firmly resides on the Desktop. 
I've tried moving it in the graphics Desktop mode, and yes, I've changed to su to try and drag it into the /opt folder, but it refuses and tells me I don't have the permission to do that.
Similarly I've tried the terminal mode with <  ~sudo mv seamonkey /opt > and as many variations of this as I can think of but it either tells me that seamonkey doesn't exist (it does, I tell you , it does. I can see it living on the desktop and if I go into Files it's listed there in the desktop) or I don't have permission for that.
It's only a little thing, but it's beginning to annoy me now ](*,). I have unpinned the icon from the launcher, so that isn't the reason.
Any ideas please anyone?

---

### Post by Paulgirardin on 2014-04-30
You could try opening Nautilus (file browser) as root and moving the file to where you want it:

Paste in to terminal:

> ~$ gksu nautilus 

It may tell you you need to install gksu and will give you the command to do so.

---

### Post by keiths2 on 2014-05-02
Thanks Paul, but that didn't work. I'll live with it for now, and try later when I've learnt a little more

---

