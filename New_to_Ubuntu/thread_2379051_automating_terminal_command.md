---
title: "automating terminal command"
date: 2017-11-30
forum: New to Ubuntu
---

### Post by steven91222 on 2017-11-30
Hi,

I always have to run this command to open sublime text, how can I save the terminal command so I can just double click the script to run?


steven@E6440:~$ cd Downloads
steven@E6440:~/Downloads$ cd sublime_text_3
steven@E6440:~/Downloads/sublime_text_3$ ./sublime_text

---

### Post by ajgreeny on 2017-11-30
I assume you open that file in gedit or whichever text editor you normally use,

If so you need to create a script with content 
```
#!/bin/bash
gedit ~/Downloads/sublime_text_3/sublime_text
``` and then make it executable.
Depending on you DE and your settings re scripts, double clicking on that script will either execute it or ask you what you want to do.

---

### Post by Holger_Gehrke on 2017-11-30
@ajgreeny 
Thank you, I needed the laugh (To explain that: "Sublime Text" **is** an Editor ...)

@steven91222
What you probably want is a desktop shortcut or a menu item, right ? Those are created in most DEs using files with the extension ".desktop" that are placed in specific locations in the file system. Those locations are /usr/share/applications for programs available to all users of the system or ~/.local/share/applications. Depending on the DE you use, you might have a program to create new .desktop files as part of your system, like alacarte or menulibre. If you don't, simply copy one of the .desktop files and name it 'sublime text.desktop' then edit it with your text editor of choice. Change the lines beginning with "Name", "Exec", "Path" and if you have one you want to use "Icon". If you want "Sublime Text" on the desktop, copy the file to you desktop directory and make the file executable.

Holger

---

### Post by ajgreeny on 2017-11-30
Well I never!  

I have never heard of it as a text-editor, and from the way the question was asked, I assumed that it was a subfolder in Downloads in which the OP had a file called sublime_text.  

Well I suppose I was correct about the first part of that; sublime_text_3 is a subfolder of Downloads but it contains the executable file for the editor, not a text file by that name.

---

### Post by again? on 2017-11-30
Why not install from the [**sublime repo**]("https://www.sublimetext.com/docs/3/linux_repositories.html#apt") where you will have an application launcher.
Is the same version as the manual download.

If you don't want to install from the repo, you can make your own application launcher
based on what the repo version installs..
In a terminal run...
```
gedit ~/.local/share/applications/sublime_text.desktop
```
Copy and paste in the following...
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Sublime Text
GenericName=Text Editor
Comment=Sophisticated text editor for code, markup and prose
Exec=[COLOR="#FF0000"]/home/steven/Downloads/sublime_text_3/sublime_text[/COLOR] %F
Terminal=false
MimeType=text/plain;
Icon=[COLOR="#FF0000"]/home/steven/Downloads/sublime_text_3/Icon/32x32/sublime-text.png[/COLOR]
Categories=TextEditor;Development;
StartupNotify=true
Actions=Window;Document;

[Desktop Action Window]
Name=New Window
Exec=[COLOR="#FF0000"]/home/steven/Downloads/sublime_text_3/sublime_text[/COLOR] -n

[Desktop Action Document]
Name=New File
Exec=[COLOR="#FF0000"]/home/[steven/Downloads/sublime_text_3/sublime_text[/COLOR] --command new_file
```
If the [COLOR="#FF0000"]paths[/COLOR] are incorrect change them.
Save and close.
Should now have a "Sublime Text" entry in your Applications menu.

---

### Post by again? on 2017-11-30
> **ajgreeny said:**
> Well I never!  

I have never heard of it as a text-editor, and from the way the question was asked, I assumed that it was a subfolder in Downloads in which the OP had a file called sublime_text.  

Well I suppose I was correct about the first part of that; sublime_text_3 is a subfolder of Downloads but it contains the executable file for the editor, not a text file by that name.
Easy mistake. Original post contained subliminal messages. :shock::razz:

---

### Post by ajgreeny on 2017-11-30
> **guber2 said:**
> Easy mistake. Original post contained subliminal messages. :shock::razz:

Ouch !!!

What a dreadful, or maybe that's very clever, pun.
):P

---

### Post by cariboo on 2017-12-01
+1 for installing Sublime Text from the ppa.

---

