---
title: "How to create a script to creat a desktop launcher?"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-16
I downloaded Scrivener (a wordprocessing/organizational tool for writers) in a beta version. I'd like to set up a desktop launcher, so I didn't have to run it from the command line. 

The text below (found on a website about installing Scrivener on Linux) says this is what I need as a 'script' to create a laucher: 

[B][Desktop Entry]                                                                                                            
 Name=Scrivener
GenericName=Scrivener Editor
Exec=/usr/local/LiteratureAndLatte/bin/Scrivener %f
Terminal=false
Type=Application
StartupNotify=true
Icon=/usr/local/LiteratureAndLatte/Scrivener_Logo.png
Categories=Office;WordProcessor;[/B]

But that doesn't look executable to me (this is where I point out I have NOT yet written a script; trying to learn how). There's no "#!/bin/bash" or anything that signifies which shell is supposed to run it. 

Is that right? If so, what would I need to do to make the script executable (again, my goal is to create a desktop launcher/sidebar laucher for Scrivener; I have the icon for it).

---

### Post by deadflowr on 2013-06-16
If the exec command you give works, then all that's left should be to give the file a .desktop extension and throw it into either /usr/share/applications folder (which needs root).
Or throw it in the /home/username/.local/share/applications folder (which doesn't need root).

Added: Once the file is a .desktop file and placed in either applications folder it will show up in the dash under the assumed name and icon.
From there you can either launch it or drag it to the launcher side panel.
If you decide to launch from the dash, the app will drop an icon(or at least should) in the launcher bar, where you can just right-click on it and select lock to launcher.

---

### Post by MidnightGrey on 2013-06-16
> **jps2012 said:**
> 
But that doesn't look executable to me (this is where I point out I have NOT yet written a script; trying to learn how). There's no "#!/bin/bash" or anything that signifies which shell is supposed to run it. 


So you dont get confused in the future, desktop launchers are not scripts but rather a type of file .desktop, hence the absence of #!/bin/bash headers.

---

### Post by Dennis N on 2013-06-16
You want a launcher showing on the Desktop. Make a text file containing just your bold text, and save it in your Desktop folder as **<program-name>.desktop** . Make it executable. Double click to launch.

No script needed.

---

### Post by monkeybrain2012 on 2013-06-17
Put the .desktop file in /usr/share/applications or /home/username/.local/share/applications and it will show up in the dash.  There is no need to litter your desktop with icons like in Windows.

so, suppose your .desktop file is on the desktop right now, do either

```
sudo mv Desktop/xxxx.desktop /usr/share/applications

```

or 

```
mv Desktop/xxxx.desktop  .local/share/applications
```

---

### Post by jps2012 on 2013-06-17
Monkeybrain, deadflowr and everybody: Many thanks for the quick and thorough answers. It looks pretty straightforward. 

Do you guys know if the same text (saved in the same way as listed below) would work on a Mac (using the command line)?

---

### Post by jps2012 on 2013-06-17
> **Dennis N said:**
> You want a launcher showing on the Desktop. Make a text file containing just your bold text, and save it in your Desktop folder as **<program-name>.desktop** . Make it executable. Double click to launch.

No script needed.

Dennis, I believe I followed the above instructions, but when I double click, _I get the following error message:_ "Details: Failed to execute child process "/usr/local/LiteratureAndLatte/bin/Scrivener" (No such file or directory)" 

I named the file "scrivener.desktop" and saved it in my desktop folder. Does anyone see something I did wrong?

I wanted to copy the text from it, so I removed the checkmark from "make executable." Now when I double click on it, I get the following: "The application launcher "scrivener.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." At that point, I'm only offered a "cancel" icon.

---

### Post by Dennis N on 2013-06-17
> I wanted to copy the text from it, so I removed the checkmark from "make executable." Now when I double click on it, I get the following: "The application launcher "scrivener.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." At that point, I'm only offered a "cancel" icon. 

In recent releases, you get that warning unless you mark it executable. Then you won't see it. 

> when I double click, I get the following error message: "Details: Failed to execute child process "/usr/local/LiteratureAndLatte/bin/Scrivener" (No such file or directory)" 

I would suspect something wrong with the path since it gives "no such file or directory". Check that everything is correct - the actual path to the program executable, spelling of directory names and file name (everything is case-sensitive).

A check that it's right: Does the program start from the terminal with this path?

---

### Post by jps2012 on 2013-06-17
> **monkeybrain2012 said:**
> Put the .desktop file in /usr/share/applications or /home/username/.local/share/applications and it will show up in the dash.  There is no need to litter your desktop with icons like in Windows.

so, suppose your .desktop file is on the desktop right now, do either

```
sudo mv Desktop/xxxx.desktop /usr/share/applications

```

or 

```
mv Desktop/xxxx.desktop  .local/share/applications
```

Dennis and Monkeybrain: What I failed to do was follow your (Monkeybrain) instructions per the above. I moved the file, and the icon for my program now shows up in dash and in the launcher. My apologies. Everything looks good now. Thank you very much. 

One further note (and a question, if you don't mind): I was trying to get around the problem of launching Scrivener from Terminal. I was using "nohup" in bash, but when I quit Terminal, Scrivener still quit. I thought maybe "nohup" behaved differently in bash than in zsh, so I installed zsh, and ran nohup there ... with the same result. I've also tried "nohup -h scrivener" but get a notice that I'm using an inappropriate argument. 

I've read nohup is a way to disown a process ... but am I using it incorrectly? (I've also used "open & disown" but that also doesn't dissociate the two processes.)

---

### Post by kurt18947 on 2013-06-17
Here's an alternative GUI method that I've been using for set-in-their-ways users.  Computers are supposed to have launchers on the desktop -- by cracky!:D   This works with gnome-shell and perhaps Unity though I don't recall having  tried this in Unity.

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

A "Create Launcher" window opens which is pretty self explanatory.

---

### Post by jps2012 on 2013-06-17
Thanks, Kurt. I will check out the desktop creator. It took a long time to figure it out via the command line, but I learned a lot today (thanks to a lot of help).

---

### Post by stinkeye on 2013-06-17
Also have a look at
[**_[COLOR="#B22222"]Ezame: A New Menu Editor For Unity[/COLOR]_**]("http://www.webupd8.org/2013/06/ezame-new-menu-editor-for-unity.html")

---

### Post by jps2012 on 2013-06-18
Thanks, Stinkeye. I just looked at their website. I'm vacillating on downloading it, because I'm tempted to use a GUI to manage files, but that undermines the need to learn the command line (which I'm both scared of, and enjoying). And thanks for listing "how to mark threads solved." I'd forgotten how to do that.

---

