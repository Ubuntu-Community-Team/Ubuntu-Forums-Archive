---
title: "How to create launcher items from scratch"
date: 2011-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Jacobonbuntu on 2011-06-11
I am hesitating to propose this tutorial, as I am probably one of the most inexperienced users of this forum. However, the numerous remarks on the (supposed) limited functionality of the Unity launcher give me the impression that many of the newest Ubuntu users (like me) are not aware of how easy it is to extend and modify the functionality of the Unity launcher.
                                    I hope it is of any help to complete newbees, but feel free to remove this post if it is not useful :)

                                  This example shows how a new launcher is created from scratch, to quickly access some office-tools: calculator, special characters and tomboy notes (in this case). Of course you can fill-in any application, location, file or tool you want.


                                  **Good to know before you start:**
The functionality of launcher buttons is defined by .desktop files. These files are stored in /usr/share/applications, or in your home-folder, in ~/.local/share/applications. (~ is the path to your personal folder; in my case: /home/jacob). If the file exists in both locations, the one in your personal folder &#8220;overrules&#8221; the one in /usr/share/applications.[INDENT]1. Create a new file with gedit, and     save it as &#8220;tools.desktop&#8221; in ~/.local/share/applications [this     is a hidden directory by default, make it visible by pressing     command+h]. You can give it any name, as long as it ends with     .desktop.

2. Paste this text into the file:>                                   [Desktop Entry]  
 Version=1.0  
 Type=Application  
 Terminal=false  
 Exec=  
 Name=tools
 Icon= /home/jacob/Thema/icon/officetools.png
 [/INDENT]***Notes:**


[LIST]
[*]The last line obviously defines the icon you want to show up in the launcher, pick an appropriate icon to your preference.
[*]The &#8220;Exec&#8221; -entry can be left empty for now, it defines what happens if the icon is left-clicked.
[*]On fresh installed systems, the directory ~/.local/share/applications may not exist yet, so you will have to make it then...
[/LIST]
[INDENT]3. Now we'll define the entries that will appear when we right-click the icon in the launcher. Add this after the last line:

>                                   X-Ayatana-Desktop-Shortcuts=**calculator;special characters;tomboy notes**;
                                  -to define the entries,
 and after that:


>                                   [calculator Shortcut Group] 
 Name=calculator 
 Exec=gcalctool 
  
[special characters Shortcut Group] 
 Name=special characters 
 Exec=gucharmap 
  
[tomboy notes Shortcut Group] 
 Name=tomboy notes 
 Exec=tomboy &#8211;search
                                  - to make the entries show up, when the icon is right-clicked.
 
[/INDENT]***Note **
you can find the appropriate Execute-command as follows: open the /usr/share/applications -directory and find the icon of the program of your choice, right click on it and in the &#8220;properties&#8221; you will find the command to open the application. 

                                 Save and close the tools.desktop file, navigate to the containing directory (hidden by default, press command-h to show all folders) and drag it onto the launcher. Done!
it should look something like this, when you right-click on it:
[http://dl.dropbox.com/u/1155139/Schermafdruk-1.png](http://dl.dropbox.com/u/1155139/Schermafdruk-1.png)


                                  ***Tips**
 
[LIST=1]
[*]if you have a lot of entries, you     can add dividers, by making an empty entry ( *                                X-Ayatana-Desktop-Shortcuts* -definition + *Shortcut Group*), with     &#8220;------------------------------&#8221; as &#8220;Name&#8221; (in the Shortcut-Group), and leave the     &#8220;Exec&#8221; entry empty.
[*]To easily edit the file, add an     &#8220;edit&#8221; -entry, so you won't have to open the terminal to edit.
[/LIST]
 
 The complete contents of the file would look like this:
> [Desktop Entry] 
 Version=1.0 
 Type=Application 
 Terminal=false 
 Exec= 
 Name=Office tools 
 Icon= /home/jacob/Thema/icon/officetools.png

 X-Ayatana-Desktop-Shortcuts=calculator;special characters;tomboy notes;divider;edit; 
 
[calculator Shortcut Group] 
 Name=calculator 
 Exec=gcalctool 

[special characters Shortcut Group] 
 Name=special characters 
 Exec=gucharmap 
  
[tomboy notes Shortcut Group] 
 Name=tomboy notes 
 Exec=tomboy &#8211;search 
  
 [divider Shortcut Group] 
 Name=----------------------------- 
 Exec= 
  
[edit Shortcut Group] 
 Name=edit 
 Exec=gedit /home/jacob/.local/share/applications/tools.desktopthe result would be like this:
[http://dl.dropbox.com/u/1155139/Schermafdruk-2.png](http://dl.dropbox.com/u/1155139/Schermafdruk-2.png)


**examples of Execute -entries:**

to go to a directory:
Exec=nautilus /*path-to-directory*
to go to a website:
Exec=firefox -new-window [http://ubuntuforums.org/](http://ubuntuforums.org/)
to open a specific file:
Exec=*command-to-open-application* /*path-to-file/name-of-the-file*

I hope it is of any help to anyone!

---

