---
title: "Is it possible to make the TeamviewerQS script run from a desktop icon?"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by twalp on 2014-06-10
TeamviewerQS, after extracting, is apparently designed to run from a script. Here are its contents.

```
#!/bin/bash

# If you see this message, you probably attempted to start TeamViewer.
# Please open a terminal (Konsole, gnome-terminal, xterm),
# navigate to this folder (type 'cd /path/to/teamviewer' [Enter])
# then execute TeamViewer (type './teamviewer' [Enter])


TV_SCRIPT_DIR="$(dirname "$(readlink -e "$0")")"
source "$TV_SCRIPT_DIR/tvw_main"

Main "$@"
```

I followed the instructions in the comments like a good keyboard monkey and Teamviewer's GUI appeared, it fetched and displayed a new ID and Password - in other words, it worked. The following text appeared in LXTerminal's window.

```
Init...
Checking setup...
Launching TeamViewer ...
Starting network process (no daemon)
Network process started (3228)
Launching TeamViewer GUI ...

```
However, I'm going to turn this system over to someone who may not be able to follow instructions for running a script, so **can anyone here can tell me how to run a script from a Desktop icon** -- if that's even possible?? (note that TeamviewerQS requires no installation and is not the same as the full Teamviewer)

---

### Post by twalp on 2014-06-12
Does the absence of a reply, despite 147 views, indicate that there is no way to run the script from a desktop icon, or are viewer merely marveling at a stupid question?

---

### Post by coffeecat on 2014-06-12
There may have been 147 views, but only 8 forum members including yourself have viewed the thread. The other 139 views would be accounted for by multiple viewings from one person or, numerically more important, viewings from people not logged in or search engine spiders and the like. The ratio of people viewing the forum not logged in to logged in members is always very high - just a moment ago it was "167 members and 33438 guests". We do get an extraordinarily large number of "guests" viewing the forum. Let's hope they get something for their effort even if they give nothing back.

I'm sorry no one has been able to answer your question yet. Bump your thread occasionally, but not more than once every 24 hours, and hopefully someone will soon get to you.

---

### Post by twalp on 2014-06-14
[COLOR=#222222][FONT=Verdana]Thank you for replying to explain. Every addition to my understanding of this forum [/FONT][/COLOR]*and *[COLOR=#222222][FONT=Verdana]Linux is helpful.[/FONT][/COLOR]

---

### Post by sudodus on 2014-06-14
Maybe these links will help you make a desktop file running your script.

[https://wiki.archlinux.org/index.php/Desktop_Entries](https://wiki.archlinux.org/index.php/Desktop_Entries)

[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

Enter the ***full path*** to the script file in the **[FONT=courier new]Exec[/FONT]** line

You may need a terminal to run the script, so I think you should use [FONT=courier new]**Terminal=true**[/FONT]

---

### Post by twalp on 2014-06-14
> **sudodus said:**
> Maybe these links will help you make a desktop file running your script.

[https://wiki.archlinux.org/index.php/Desktop_Entries](https://wiki.archlinux.org/index.php/Desktop_Entries)

[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

Enter the ***full path*** to the script file in the **[FONT=courier new]Exec[/FONT]** line

You may need a terminal to run the script, so I think you should use [FONT=courier new]**Terminal=true**[/FONT]

Thank you for replying, sudodus.  The archlinux info was a awfully far over the head of this "**Absolute Beginner**", and I've ventured into deep weeds in "Anatomy of a Desktop File". I hope you or someone here can guide me out.  

The "Anatomy" article provides an example of a .desktop file.

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=$HOME/MyApp
Name=My Application
Icon=$HOME/Icons/MyIcon.png

Save your entry (as filename.desktop), then put a copy in $HOME/.local/applications and (if you want) another in $HOME/Desktop.
```

Using PCManFM to determine the path to the TeamviewerQS script, I come up with:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=True
Exec=home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
Name=TeamviewerQS
```


**Questions**

The example refers to $HOME so I don't know if I should replace "home" with "$HOME" in the "Exec=" statement. I tried it both ways but neither ultimately worked.

I'm already so deep in the weeds I hope I can omit the icon file for now.

The article says to save the above text as TeamviewerQS.desktop to $HOME/.local/applications, which a little research suggests that this might mean the "home/jack" folder ("jack" being the user name) but there's no "applications" folder there.  Additional research suggests that in Ubuntu one should substitute the word "bin" for "applications", so I created a "bin" folder, saved the file there, and tried running it from there but of course it didn't work.  At this point I really feel way out in the deepest weeds.


Halp! :confused:

---

### Post by sudodus on 2014-06-14
> **twalp said:**
> Thank you for replying, sudodus.  The archlinux info was a awfully far over the head of this "**Absolute Beginner**", and I've ventured into deep weeds in "Anatomy of a Desktop File". I hope you or someone here can guide me out.  

The "Anatomy" article provides an example of a .desktop file.

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=$HOME/MyApp
Name=My Application
Icon=$HOME/Icons/MyIcon.png

Save your entry (as filename.desktop), then put a copy in $HOME/.local/applications and (if you want) another in $HOME/Desktop.
```

Using PCManFM to determine the path to the TeamviewerQS script, I come up with:

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=True
Exec=home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
Name=TeamviewerQS
```


**Questions**

The example refers to $HOME so I don't know if I should replace "home" with "$HOME" in the "Exec=" statement. I tried it both ways but neither ultimately worked.

I'm already so deep in the weeds I hope I can omit the icon file for now.

The article says to save the above text as TeamviewerQS.desktop to $HOME/.local/applications, which a little research suggests that this might mean the "home/jack" folder ("jack" being the user name) but there's no "applications" folder there.  Additional research suggests that in Ubuntu one should substitute the word "bin" for "applications", so I created a "bin" folder, saved the file there, and tried running it from there but of course it didn't work.  At this point I really feel way out in the deepest weeds.


Halp! :confused:

There should be a slash in the beginning (before home) to make it a 'total' or 'absolute' path.

```
Exec=/home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
```

Check if there is a file [FONT=courier new]**/home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer**[/FONT] with the command (ell ess space minus ell)

```
ls -l /home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
```

---

### Post by twalp on 2014-06-15
> **sudodus said:**
> There should be a slash in the beginning (before home) to make it a 'total' or 'absolute' path.

```
Exec=/home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
```

Check if there is a file [FONT=courier new]**/home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer**[/FONT] with the command (ell ess space minus ell)

```
ls -l /home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
```

Thank you for your continued help and patience, sudodus.

I inserted the slash at the beginning of the path and the List Directory command (LS) found the teamviewer file successfully, but when I double-click on TeamviewerQS.desktop an error message appears:
```
Invalid desktop entry file: '/home/jack/bin/teamviewerqs.desktop'
```

Might it be relevant that if I go to the target folder where the teamviewer shell script resides (the *Exec=* path) I can double-click on "teamviewer", left-click on the Execute button that appears (choices: Execute, Execute in Terminal, Open and Cancel), and TeamviewerQS will run successfully?  Note that "Execute in Terminal" just opens a terminal window; it doesn't run TeamviewerQS like the Execute button does. Yet setting Terminal=true or false in the .desktop file doesn't resolve the problem of it being declared an invalid desktop file.

That suggests to this Absolute Beginner that I need something on the user's Desktop that will simulate what the aforementioned Execute button does.  Is that the purpose of the .desktop file described in "[Anatomy of a Desktop File]("http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/")"? If so, there must be an error in the teamviewerqs.desktop. 

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=True
Exec=/home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
Name=TeamviewerQS

```
I'm also curious why the .desktop file needs to be a newly created /home/jack/bin folder instead of just in /home/jack/Desktop?

---

### Post by sudodus on 2014-06-15
The desktop file should be located in the desktop directory

**/home/jack/Desktop**

not in the bin directory.

---

### Post by twalp on 2014-06-15
> **sudodus said:**
> The desktop file should be located in the desktop directory

**/home/jack/Desktop**

not in the bin directory.

I copied the teamviewerqs.desktop file to /home/jack/Desktop, double-clicked on it, and got the same "invalid desktop entry file" error.

---

### Post by sudodus on 2014-06-15
Maybe try this

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=xterm -e /home/jack/Downloads/teamviewer9qs/tv_bin/script/teamviewer
Name=TeamviewerQS

```

or make a script file

/home/jack/Downloads/teamviewer9qs/tv_bin/script/**tmv.bash**

containing

```

#!/bin/bash

cd /home/jack/Downloads/teamviewer9qs/tv_bin/script/
teamviewer

```

and call it from the desktop file

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=bash /home/jack/Downloads/teamviewer9qs/tv_bin/script/tmv.bash
Name=TeamviewerQS

```

---

### Post by rupprath-fred on 2014-08-28
With ubuntu 14.04 it is simple: In Nautilus in Settings/Einstellungen under behavior/Verhalten At: Jedes mal nachfragen/for executable textfiles/ausführbare Textdateien activate "ask each time". Klicking on the teamviewer qs script will open a window -select Ausführen/execute and QS starts with its GUI. (excuse my german/english mix - so hopefully it works in both languages) This was standard in 12.04LTS. A shortcut/Verknüpfung might bei placed to the desktop.

---

