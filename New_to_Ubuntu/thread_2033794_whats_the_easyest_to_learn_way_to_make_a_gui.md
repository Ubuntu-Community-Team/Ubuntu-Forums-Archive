---
title: "whats the easyest to learn way to make a gui?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-07-26
I have qtdesigner, But im woundering what the fastest, least requiring to learn, way to make a GUI for stuff on ubuntu. I want to make some simple GUIs for running scripts by just clicking a button.

---

### Post by drpjkurian on 2012-07-27
Paste the command in any of the text editor and convert the file to executable file. then create a launcher for it.

I use to get the command from man pages of the programme.....

This is the easiet way of doing it. Hope iam understandable

---

### Post by greenpeace on 2012-07-27
**Quickly** is a very fast way to start making GUI applications:

[https://wiki.ubuntu.com/Quickly/](https://wiki.ubuntu.com/Quickly/)

---

### Post by albandy on 2012-07-27
For simple scripts you can use zenity. 

For example:
zenity --file-selection --multiple --title "Select the required files"

will show you a file selector, then it will return the selected files to stdout

or you can show a message box, or selection list, .....

[http://library.gnome.org/users/zenity/stable/index.html.en](http://library.gnome.org/users/zenity/stable/index.html.en)

---

### Post by HiImTye on 2012-07-27
if you're just using the GUI to simplify your bash scripts, Zenity is perfect

---

### Post by hakermania on 2012-07-27
I can't think of a simpler way than Qt!
You can open QtCreator (not Designer), create a Qt Gui Application, double click on your form (.ui file) (which will automatically guide you to the 'Design' tab on the left for editing your GUI), add your buttons, right click on them->Go to slot->'clicked' and then (as it is for your very own use) you can use the system() function so as to execute your scripts (add the & at the end of your command so as to just launch your scripts, otherwise your GUI will freeze).

But, I guess, there is a more efficient way to launch your scripts in Ubuntu 12.04 under the Unity Interface. I would suggest making your own .desktop file (which is an application launcher, in fact), add to it, as shortcuts, your scripts you want to launch at right click and lock your launcher at the Unity Sidebar.

Example picture:
[IMG]http://i.imgur.com/QHE3v.png[/IMG]

The above launcher was used using the following .desktop file:
```

[Desktop Entry]
Version=1
Name=MyScripts
Comment=A bunch of personal scripts
Exec=/home/alex/Documents/scripts/main.sh
Icon=/home/alex/Pictures/1.png
Terminal=true
Type=Application
Categories=Utility;Application;

Actions=Backup;MoveFiles;DeleteHistory;

[Desktop Action Backup]
Name=Backup your data
Exec=/home/alex/Documents/scripts/backup.sh
TargetEnvironment=Unity

[Desktop Action MoveFiles]
Name=Move files to external disk
Exec=/home/alex/Documents/scripts/move.sh
TargetEnvironment=Unity

[Desktop Action DeleteHistory]
Name=Delete the History
Exec=/home/alex/Documents/scripts/history.sh
TargetEnvironment=Unity

```

For more information about how to make your launcher please see: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by HermanAB on 2012-07-27
Glade

---

### Post by JKyleOKC on 2012-07-27
Using zenity is the simplest way, if you're simply launching a script. Here's an example from one of my desktop launchers:```
zenity --text-info --title="Current XferLog" --width=1430 --height=580 --filename=/var/log/proftpd/xferlog
```This line just reads the specified file and puts it on the screen in its own window, with a "Close" button. Read "man zenity" to find all of the available options; there are many!

---

### Post by moribashi on 2012-07-27
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)

---

