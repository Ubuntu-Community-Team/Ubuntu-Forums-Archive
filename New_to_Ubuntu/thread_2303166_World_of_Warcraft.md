---
title: "World of Warcraft"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by johnc32 on 2015-11-16
Ok I am new to Linux... I have WoW on my computer and get it to run fine from the terminal window... However, I would like to create an icon for the .exe file to be on my desktop.... yeah yeah I have wine ect... as it works from a terminal window... Also i have loaded Cinnamon... and when you right click the desktop to create a launcher i map to .exe file and it doesn't work.. it has a red dot to the right of the path as well.. any assistance is appreciated.

---

### Post by Geoffrey_Arndt on 2015-11-16
Try installing "PlayOnLinux" . . . . another front end and modification to running Wine.   It's been a while since I've run it, but I believe I was able to add program shortcuts within the PlayOnLinux run Windows.

---

### Post by mastablasta on 2015-11-17
it seem to be a cinnamon issue. something Mint founder came up with. perhaps you would get better support on Mint forums.

I can say it will work in Kubuntu. you need to run "wine your.exe" file in the launcher.

PlayonLinux will create those for you.

---

### Post by leunam12 on 2015-11-17
Have you tried creating a .desktop file with this command after Exec: ```
wine "c:\ProgramFiles\World of Craft\whatever\wow.exe"
```?
Of course, you need the right path and name for your .exe file.

---

### Post by NathanRodriguez on 2015-11-17
You can also try to create a little wow.sh script with wine "yourgamepath\wow.exe" and see if it helps find what isn't working.

---

### Post by Geoffrey_Arndt on 2015-11-17
Or, if your hardware is decent (dual-proc., 6 Gigs of ram, etc.), you can get a Win7 iso and install it via Virtual Box - - so you're running Win7 as a "guest OS" inside your Ubuntu "host OS".    Unless requiring 3d accel. graphics, this is often better than running Wine.

---

### Post by influencedchaos on 2015-11-18
Guys he isn't asking how to run it through wine or a virtual machine, he already mentioned it plays fine. All he wants is an icon to launch it from the desktop.

You can do this by simply creating a .desktop file with the World of Warcraft launch command inside of it.

The format would look something like this.

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0                                     # version of an app.
Name[en_US]=World of Warcraft                   # name of an app.
GenericName=World of Warcraft                   # longer name of an app.
Exec=wine $programlocationhere                  # command used to launch an app.
Terminal=false                                  # whether an app requires to be run in a terminal.
Icon[en_US]=$iconimagehere                      # location of icon file.
Type=Application                                # type.
Categories=Application;Games;                   # categories in which this app should be listed. 
Comment[en_US]=World of Warcraft Launcher       # comment which appears as a tooltip.


```[FONT=Verdana]

[/FONT]This would then be placed inside of your ~/.local/share/applications folder and be named worldofwarcraft.desktop

Yes this is a bit more than the simple GUI but since you said you were having problems where it was showing a red dot after the file location it might be worth giving it a shot,

Welcome to Linux and I hope you have a great experience. The forums and IRC are the greatest places for help on anything you might find and don't give up. It may seem daunting now but over time you will get use to it, We were all there ourselves once.

---

### Post by mastablasta on 2015-11-19
or just editing the file location to show propper path.

---

