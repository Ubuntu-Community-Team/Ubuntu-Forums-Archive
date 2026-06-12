---
title: "I want a program to run when I start a session PS3Media Server"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by theedudenator on 2013-06-23
According to the instructions I need to do this to run software.


4) Run (note: PMS should NOT be run as root):

    cd pms-<version>
    ./PMS.sh

When I do this the software runs and loads fine.
How can I make this auto run?  Or at least create an icon that I can click to start the program?

---

### Post by Kujua on 2013-06-24
Add the commands you want to run in this file: ~/.profile
Then your program will run automatically when you login.

---

### Post by theedudenator on 2013-06-24
I figured there was a way to add graphically?

I think there was in gnome?

---

### Post by MidnightGrey on 2013-06-24
Are you using Unity? You can create a desktop launcher (another name for desktop shortcut i suppose), 

Simple step-by-step way to create a launcher:
1. Right click on desktop > create new document > empty document
2. copy paste this:
```

[Desktop Entry] 
Name=ProgramName 
Comment=This is my comment 
Exec= <put path of PMS.sh here> 
Icon= <put path of icon here> 
Terminal=false/true 
Type=Application


```

3. Save the file and then rename to PMSlauncher.desktop
4. Right click the file > Properties > Permissions > Allow executing file as program
4b. You can also set the icon in Properties by left-clicking the icon in the Basic tab.

If you want you can drag the new launcher into the Unity dash to pin it there.

---

