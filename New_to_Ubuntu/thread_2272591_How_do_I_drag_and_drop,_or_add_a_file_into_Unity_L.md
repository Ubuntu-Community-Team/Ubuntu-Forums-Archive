---
title: "How do I drag and drop, or add a file into Unity Launcher? This is ridiculous."
date: 2015-04-07
forum: New to Ubuntu
---

### Post by Clifurd on 2015-04-07
This should take 2 seconds to do.   I'm not installing anything else WHATSOEVER.  I just want to add a .jar file to the Unity Launcher.

If it isn't possible to just simply add any file that I want, into the unity launcher bar, then please let me know now so I can move onto something else.

---

### Post by mc4man on 2015-04-07
I'd start moving then.

---

### Post by QIII on 2015-04-07
A jar file runs in the context of the Java Virtual Machine.

Strictly speaking, .jar != application.

Raw Java code is "compiled" into byte-code -- somewhere between source code and an actual program --  which comprises the .jar.  The .jar can't do anything until it is consumed by a JVM, JIT compiled and executed.  The byte-code is platform agnositic.  A JVM running on Windows can run it, as can a JMV running on Linux. That's what makes Java portable.

To run from the command line, you must execute the following command

```
 java -jar </path/to/jar>
```

You may also associate .jar file with Java to launch them with a double click in your file manager - but that involves making sure you EXPORT your JAVA_HOME or JRE_HOME among several other steps, such as setting permissions and making them executable as a program.

When you install a Java application via a package, the developer will likely have included a launcher you can drag on to the Unity launcher bar.

If you have created your own, you will need to create a custom launcher and use the command above in the "Command" box on the GUI launcher creator.

I do believe there are some distros that launch by double click by default in the file manager.  I don't think Ubuntu does.  But it's been a while since I stopped agreeing to do any Java development.

---

### Post by buzzingrobot on 2015-04-08
I don't use Java, so this could easily be nonsense, but... 

The icons that appear in the Dash and the Launcher are determined by .'desktop' files that point to the icon, point to the executable, etc.  Perhaps you could dig into how to make a new .desktop' file and create one for a jar file, with the path to the executable being as QIII illustrated.

---

### Post by CantankRus on 2015-04-08
....in addition to the above posts here is a .desktop file I use to launch a java application.
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
[COLOR="#EE82EE"]**Name=**[/COLOR]FFgenie
[COLOR="#FF8C00"]**Comment=**[/COLOR]afl football statistics stats analysis
[COLOR="#40E0D0"]**Exec=**[/COLOR]/usr/bin/java -jar '[COLOR="#808080"]/home/glen/football/FFGenie2015/dist/FFGenie.jar[/COLOR]'
[COLOR="#800080"]**Icon=**[/COLOR]/home/glen/Pictures/icons/Genie2.png
Categories=Utility;
```
[COLOR="#EE82EE"]**Name=**[/COLOR]choose a name
[COLOR="#FF8C00"]**Comment=**[/COLOR]whatever you put here is searchable in the dash
[COLOR="#40E0D0"]**Exec=**[/COLOR]test your command in terminal
[COLOR="#800080"]**Icon=**[/COLOR]Full path to an image ...download a png image on google images (transparent backgrounds look best)

Create your .desktop file via terminal ...
```
gedit ~/.local/share/applications/[COLOR="#FF0000"]<your-app-name>[/COLOR].desktop
```
Copy and paste in the contents of my .desktop and edit for your application. Save.

Search in dash for launcher
or
navigate to **~/.local/share/applications** and drag-n-drop your .desktop file to the launcher.

---

### Post by haplorrhine on 2015-04-08
Is using the launcher really that important?

You could make a symbolic link (shortcut) on the desktop.
ln -s <file>  <shortcut>

If you want to have a keyboard shortcut
System Settings > Keyboard > Shortcuts > Custom Shortcuts

---

### Post by GrouchyGaijin on 2015-04-11
> **haplorrhine said:**
> Is using the launcher really that important?

You could make a symbolic link (shortcut) on the desktop.
ln -s <file>  <shortcut>

Yeah that is what I did for Minecraft.

---

### Post by haplorrhine on 2015-04-11
> **GrouchyGaijin said:**
> Yeah that is what I did for Minecraft.

Are we playing troll the troll? :P

---

### Post by GrouchyGaijin on 2015-04-11
> **haplorrhine said:**
> Are we playing troll the troll? :P

Actually no - that really is what I did with Minecraft.:p[ATTACH=CONFIG]261228[/ATTACH]

---

### Post by Keith_Helms on 2015-04-11
Being able to more easily create launchers for executable jar files or to invoke applications with a specific file as input is one of the reasons I prefer XFCE and Xubuntu to Unity.   I just prefer to be able to click on a desktop icon or a taskbar quick launcher and not have to click on an icon in a sidebar THEN find the app I want in a second popup window.  To me Linux is about the flexibility to do things the way I want and not about somebody's idea of "desktop purity".  If I wanted a "my way or the highway" operating system, I would have stayed on Windows.

---

### Post by coffeecat on 2015-04-11
Since the OP has not logged in since posting, and since this has now morphed into a discussion thread in an area intended for technical support, I'll close this now.

@Clifurd, you've been given advice for creating a jar file launcher. If you do decide to return and need further help you can start a new thread, but next time please avoid the belligerent tone.

---

