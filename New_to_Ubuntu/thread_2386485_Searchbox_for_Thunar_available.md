---
title: "Searchbox for Thunar available?"
date: 2018-03-06
forum: New to Ubuntu
---

### Post by xipho2 on 2018-03-06
The Explorer in Win displays a search box on the right. I would like to have somethinglike that in Thunar, is that possible? I know Catfish via right clickmenue, but I do not want to start for every search a tool. Or should I remove Thunar and try another file manager, which one? I simply want to reduce clicks as far as possible. Keyboard shortcuts are welcome. 
Thanks for your suggestions!

---

### Post by kerry_s on 2018-03-06
searching for what, you should not need to leave the home folder.

in thunar, in any folder you can just start typing it will start highlighting the match
example:
open thunar-> press p & enter, etc...

---

### Post by xipho2 on 2018-03-08
I plug in a flash drive, Thunar opens it. There are a bunch of files and folders, one folder contains a pdf called "Xubuntu Shortcuts". Where would you type "Xubuntu", thus finding that pdf without further ado?

---

### Post by kerry_s on 2018-03-08
> **xipho2 said:**
> I plug in a flash drive, Thunar opens it. There are a bunch of files and folders, one folder contains a pdf called "Xubuntu Shortcuts". Where would you type "Xubuntu", thus finding that pdf without further ado?

just open that folder & start typing

---

### Post by vanadium on 2018-03-09
To open that folder, you first need to navigate to it. That is typing, typing and typing. The OP just wants to launch the file. He knows the name. Why should the system force him to navigate through all the folders to reach that file? That was appropriate in 1990, with Windows 3 and less powerfull computers. It is not anymore appropriate in the current time. Unfortunately, in some areas, linux sticks to the past.

nautilus in gnome does such searching. Typing a file name will pop up all matching files in the current and lower level directories.

There are some work-arounds:
- You could install a suitable launcher. Albert perfectly fits your user case. You call it with a hotkey, type part of the file name and the file will pop up, ready to be launched with <enter>. Albert is very light-weight and wants to be "desktop-agnostic". Other launchers work less well with file search.
- I am currently using rofi menu launcher with a custom script. This works extremely well. You type substrings of the entire path name - in any order -, and the displayed files narrow down to your criterium in the glimpse of an eye.

---

### Post by kerry_s on 2018-03-09
there's already a app for searching. he wants to search in the file manager.

i just looked in thunar, pressing ctrl+s brings up the search. you can also create a custom action if you wanted to.

---

### Post by xipho2 on 2018-03-10
@kerry: The method you are suggesting works within the drive, not in folders. 
@vanadium: I could not find Albert neither in "Software" nor in "Synaptic". What is the difference between Albert and Catfish? Anyway, using A. or C. does mean a few clicks more, using an additional software? rofi seems to be a terminal application, that requires some learning, just watched a YT vid....

---

### Post by vanadium on 2018-03-10
Albert is a highly efficient and lightweight application and file laucher (and can do other things if you enable the plugins). It is not in the repository, but it is quite easily installed using a repo from opensuse: [https://albertlauncher.github.io/docs/installing/](https://albertlauncher.github.io/docs/installing/) That page describes how to add the key. On the linked page, you find easy instructions on either adding the repo, or just installing a deb build.

If you like it and want to have it autostart, you will have to do this according to the procedure of your desktop environment. In xfce, you probably can, like under gnome, just copy the /usr/share/applications/albert.desktop file to your ~/.config/autostart folder, although xfce has an extensive gui for that (gnome not, anymore ;-)

Albert is just way more efficient with the keyboard than catfish. 1st you do not need to press enter to start the search, 2 You just press enter to launch the item, or use arrow down to move to another displayed item before pressing enter - in catfish you need to <tab>, which brings you to the settings cog first (do I need that after a seach?) then another tab to bring you to the list where you can press enter to launch the item.

Rofi indeed would require some scripting before it acts as a file search utility. However, out of the box, it can act as a program launcher, a run dialog, a keyboard based window switcher and a tool to quickly connect to ssh.

Indeed, I do not have thunar myself, but when I see the arch wiki and other blog, it does not appear to have file search capability build in.

---

### Post by xipho2 on 2018-03-11
At first I tried to install it via "Clone" and the terminal, but I could not remember how to do this. So I downloaded ZIP, "Extract"... then? The down mentioned code is not what Github tells. Generally, also for the next time, when downloading from Git: What is the common installation procedure and what ensures safety and security of such a download? Is Albert updated via "Software Updater"?


 I searched the internet (how to install Albert), here one result: 

[COLOR=#C20CB9]**sudo**[/COLOR] add-apt-repository ppa:nilarimogard[COLOR=#000000]**/**[/COLOR]webupd8
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get update**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] albert
(Just searched, how to format the code in the forum, did not find it)

---

### Post by vanadium on 2018-03-11
I wollowed the instructions for "Debian 9, Ubuntu 16.04+, Fedora 25+ and openSuse - OBS (Official)", then added the repo as indicated here [https://software.opensuse.org/download.html?project=home:manuelschneid3r&package=albert](https://software.opensuse.org/download.html?project=home:manuelschneid3r&package=albert) with the instructions for Ubuntu, and it immediately worked.

---

### Post by jasonbrown1965 on 2019-02-09
[SIZE=4][FONT=arial narrow]For those still searching, the following worked for me (on Zorin OS):

Commands below from (with how-to pictures):
[/FONT][/SIZE]https://iwf1.com/how-to-make-xfces-file-manager-thunar-more-usable[SIZE=4][FONT=arial narrow]

[/FONT][/SIZE][h=2][SIZE=4][FONT=arial narrow]Adding search to Thunar[/FONT][/SIZE][/h]> [h=4][SIZE=4][FONT=arial narrow]Requirements:[/FONT][/SIZE][/h]
[LIST]
[*][SIZE=4][FONT=arial narrow]Catfish &#8211; a GUI search tool[/FONT][/SIZE]
[*][SIZE=4][FONT=arial narrow]mlocate &#8211; a CLI search tool[/FONT][/SIZE]
[/LIST]
[SIZE=4][FONT=arial narrow]
To add a search functionality to Thunar simply open it up and click on Edit from the top menubar, then select Configure custom actions&#8230; > click the Add new custom actionbutton and in the dialog that opens fill in the following details:[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]
Name: Search[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]Description: Search for files and folders[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]Command: catfish &#8211;path=%f[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]Icon: choose whatever you like or leave empty[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]
Now click on the Appearance Conditions tab and fill the following:[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]
File Pattern: *[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]Appears if selection contains: Directories[/FONT][/SIZE]
[SIZE=4][FONT=arial narrow]That&#8217;s it, click OK button.


[/FONT][/SIZE]


[FONT=&quot]Not sure if file types (image, audio, video, others) have to be clicked as well to search more than directories?

. . .
[/FONT]

---

### Post by oldos2er on 2019-02-10
Back to sleep.

---

