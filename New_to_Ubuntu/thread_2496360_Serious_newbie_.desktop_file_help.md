---
title: "Serious newbie .desktop file help"
date: 2024-03-25
forum: New to Ubuntu
---

### Post by humpjock on 2024-03-25
Greetings all,
Serious newbie here. I've successfully installed Ubuntu 22.04 and am slowly learning it.
I'm having an issue trying to create a desktop shortcut or even a icon on the application bar for an program I've installed (X-Plane 12) which runs fine from it's exe file. I've been reading the forums for a couple of days now to no avail. I'm sure due to my lacking knowledge.
I've built several .desktop files but keep getting the following error:

"This .desktop file has errors or points to a program without permissions. It cannot be executed"
"Edit the file to set the correct executable program"

Here is the file:
[Desktop Entry]
Version=1.0
Name[en_US]=X-Plane 12
GenericName[en_US]=X-Plane 12
Comment[en_US]=Flight Simulator
Exec=/home/Robert/X-Plane 12/X-Plane-x86_64
Path=/home/Robert/X-Plane 12
icon=/home/robert/X-Plane 12/Aircraft/King Air C90B EVO G1000 V1.0.4/C90B_icon11_thumb.png
Terminal=false
Type=Application
Categories=Application
Hidden=false


The installer placed the program under the /home/Robert/X-Plane 12 folder. I'm the single user that was setup initially. Haven't seen my user name anywhere in the usr folder or the home.

Any help or reading locations would be greatly appreciated. Thanks in advance,

---

### Post by monkeybrain20122 on 2024-03-25
First check that your path is correct, i.e the executable is indeed /home/Robert/X-Plane 12/X-Plane-x86_64, as this looks like a folder rather than an executable file (sorry I can't download 25G to find out)

If you are sure that it is correct, check it t (/home/Robert/X-Plane 12/X-Plane-x86_64) has  permission to execute. Check by running in terminal

```
/home/Robert/X-Plane 12/X-Plane-x86_64
```

or go to the folder and right click it.

If you get an error saying the program is not executable, either in the terminal

```
chmod +x /home/Robert/X-Plane 12/X-Plane-x86_64
```

or go to the folder, right click it, from properties, check the box allow to execute. They do the same thing. (+x means adding the execution bit, chmod means change mod)

The Path = line is not necessary. The .desktop file should be in ~/.local/share/applications and be executable (either chmod +x or right click -> properties -> allow to execute)

---

### Post by yancek on 2024-03-25
> I've installed (X-Plane 12) which runs fine from it's exe file 

That doesn't seem right, a file with an .exe extension is windows only.  Did you download the right program, the Linux version?
Check owner and permissions with ls -l on the directory and file in question.  Is the name of the file actually /home/Robert/X-Plane 12/X-Plane-x86_64.  The directory "/X-Plane 12/" has a space in it.  You could try putting double quotes around the Exec line in your Desktop file:  Exec="/home/Robert/X-Plane 12/X-Plane-x86_64"  Verify that the file has execute permissions with the ls -l command.

---

### Post by humpjock on 2024-03-26
Thanks for all for the responses. I was out of pocket for a bit but will recheck and try the ideas you provided. I'm trying to learn this in baby steps so I'll understand it. 
 Will report back when I do. Thanks again!

---

### Post by humpjock on 2024-03-26
Greetings,
Unfortunately, none of the suggestions above worked. I get a No such file or directory response from the "ls" commands. A a loss. The permissions on the file say:
Owner Me, Access Read and write, Group Robert, Access Read Only, Others Read Only, Allow executing file as program is checked. Thanks again

---

### Post by Holger_Gehrke on 2024-03-26
The path to the file contains a space-character.
From the [Specification for a desktop file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s07.html"):
> If an argument contains a reserved       character the argument must be quoted. ... Reserved characters are space (" "), tab, newline, double       quote, single quote ("'"), backslash character ("\"),        greater-than sign (">"), less-than sign ("<"),       tilde ("~"), vertical bar ("|"), ampersand ("&"), semicolon (";"),       dollar sign ("$"), asterisk ("*"), question mark ("?"), hash mark ("#"),       parenthesis ("(") and (")") and backtick character ("`").

So try
```

Exec="/home/Robert/X-Plane 12/X-Plane-x86_64"

```
I believe similar rules apply to the "Path" and "Icon" fields, so I think those might need quotes, too.

Holger

---

### Post by yancek on 2024-03-26
You neglected to post the actual command you ran with the results so it is difficult to suggest a correction.  
I asked you in my previous post about the .exe file you mention.  The software you are using has a Linux version which I would not expect to use an .exe file.  Do you actually have one?  When you are running command in a terminal you should not have speaces in filenames and if you do, you need quotes around the command.  Did you do that?  I agree that it is likely that will be the same with a desktop file.  The fact that you get a no such file error indicates that you are running a command with a file name that has a space in it so it would find the file named:  /home/Robert/X-Plane and stop because there is a space there and the rest of the path is not seen.  If you copied/pasted the command I suggested and the path you gave is correct it would have worked so you have some other problem.

You would need to change the Exec. Path and Icon lines in your desktop file also for it to work.  Are you aware that the developers of Gnome and Nautilus do not like desktop files and therefore it is more difficult to get them to work on Ubuntu.  If you do an online search for creating desktop files with Ubuntu you will get many sites discussing it.

---

### Post by humpjock on 2024-03-26
Hi yancek,
 I sincerely apologize. The file I've been working with is in the first post. I thought I had answered the Linus install and "exe" above but can't find it.
I read numerous posts and watched videos (two days worth) on how to make a .desktop file and was aware that Ubuntu doesn't like them but I also saw posts from some that said they had made it work. I always try and learn myself first and usually ask for help when I'm at wits end. 
 It's obvious to me that I've missed something so I'm going to start over and look for a better alternative to launch a program. The Linux install program from X-Plane.org did not place a icon in the app area. The exe to me just means a file that launches a program be it Linux,MAC or Windows. 
 I will spend more time in the "books" and again sincerely apologize for my lack of explaining.  I had taken screen shots of all the info you mentioned but the firewall didn't like them. I won't post anymore until I actually have something but again the help so far is appreciated. I learned a lot.

---

### Post by yancek on 2024-03-28
>  The Linux install program from X-Plane.org did not place a icon in the app area. 

My understanding is that generally only happens when you install from repositories for Ubuntu rather than 3rd party sources.  I have desktop files which start googleearth, Zoneminder and mount an additional partition with another OS so it can be done.  In your desktop file, you will need to put double quotes (single may work) around the Exec, Path and icon entries.  Did that not work when you tried it?  The executable file to start your program must be executable and I would expect it to be.  Also make the .desktop file should be executable.  

I'm using 20.04 so I don't know this will work on 22.04 but would expect it to. Once you have created the .desktop file (I would create it by opening the file manager and going to the Desktop directory.  Not sure that this matters but I had problems initiall)  and right click the icon and select properties and in this window, click the Open With tab and have Default Application show Run Software and click Set as Default tab in lower right. Close window. Right click desktop icon again and you should see an option to Allow Launching, click that.

Before beginning or if you have problems, you may need to install:  sudo apt install gnome-shell-extension-desktop-icons

---

