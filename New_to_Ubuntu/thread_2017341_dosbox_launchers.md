---
title: "dosbox launchers"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by paul1945 on 2012-07-05
Is there any way to make different dosbox launchers in Ubuntu that will run different Dos programs from dedicated ".conf" files? In Windows the line C:\Program Files\DOSBox\DOSBox.exe -noconsole -conf "c:\Program Files\dosbox\wordfuge.conf" directs dosbox to use a modified ".conf" file called "wordfuge.conf"  that launches a Dos program called "wordfuge.exe", rather than the default "DOSBox 0.73.conf".
I have tried for hours, but have had no luck with anything resembling the Windows link in an Ubuntu launcher; I can only do one of two things through a Ubuntu launcher, either open dosbox as a C: prompt and start the program of choice manually, or launch one single program through a modified "DOSBox 0.73.conf" file.

---

### Post by mastablasta on 2012-07-05
have you tried DBGL : [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
 
you might need Sun Java .: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)  to run it
 
in the past you had to use it but i am not sure if it is sitll necessary with 12.04. good luck.

---

### Post by Marric on 2012-08-12
The following works fine for me on Ubuntu 12.04 Gnome 3.

Create a .desktop file (using Terminal)
```
sudo gedit /usr/share/applications/tetris.desktop
```Paste the following code and change it to your needs
```
[Desktop Entry]
Type=Application
Terminal=false
Icon=/path/to/tetris.ico
Name=Tetris
Exec=dosbox /home/user/dosprogs/Tetris/TETRIS.EXE -noautoexec -conf /home/user/dosprogs/wherever/dosbox.conf -exit -fullscreen
```DOSBox options:

file
Open a file or mount a directory 
Make  sure to write the complete path of the file (.com .exe .bat), do   not  use the tilde (~) and remember that Linux is case-sensitive.

-noautoexec
Skips the [autoexec] section of the loaded configuration file. eg to mount a certain directory.

-conf 
Allows you to enter the path to the configuration file of your choice. 
When you start a game for the first time, dosbox will automatically create a dosbox.conf file in the game's directory.

-exit
Will close dosbox when you quit the game.

-fullscreen 
I had trouble to start games in fullscreen mode when this option was not placed at the very end of the command line.


For more information
```
info dosbox
```[http://www.dosbox.com/DOSBoxManual.html](http://www.dosbox.com/DOSBoxManual.html)

GNOME Desktop File Tutorial [http://developer.gnome.org/integration-guide/stable/desktop-files.html.en](http://developer.gnome.org/integration-guide/stable/desktop-files.html.en)
Desktop Entry Specification [http://standards.freedesktop.org/desktop-entry-spec/latest/index.html](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)

---

