---
title: "Using a .desktop file to add an item to the &quot;open with other app&quot; button"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by mcjohnalds45 on 2012-08-13
So I could easily open files with a program called sublime text I made a file called sublimetext.desktop in ~/home/john/.local/share/applications that looks like this

```

[Desktop Entry]
Version=2.0
Name=Sublime Text
Exec="~/home/john/Sublime Text/sublime_text" %f
Terminal=false
Type=Application
GenericName=Code editor
GenericName[en]=Code editor
Name[en_AU]=Sublime Text

```

"Sublime Text" appears as an option the the open with other application menu but when selecting it I receive an error complaining that it cannot find "~/home/john/Sublime"

I don't know why surrounding the path in double quotes doesn't work, I tried looking at [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html) but I still couldn't figure it out, if you help, I'll give you cookies.

---

### Post by JKyleOKC on 2012-08-13
Try changing one line in the file from ```
Exec="~/home/john/Sublime Text/sublime_text" %f
```to```
Exec="~/home/john/Sublime[COLOR="Red"]\[/COLOR] Text/sublime_text" %f
```The error message is the giveaway that the "exec" function is interpreting that space as a delimiter rather than as part of the path. With the added escape, you may not need the double quotes either...

---

### Post by Marric on 2012-08-13
Maybe also leave out the Tilde (~) or the path is interpreted as /home/john/home/john/Sublime\ Text/

Use this
```
Exec=/home/john/Sublime[COLOR=Red]\[/COLOR] Text/sublime_text %f 
```

---

### Post by mcjohnalds45 on 2012-08-13
> **JKyleOKC said:**
> Exec="~/home/john/Sublime\ Text/sublime_text" %f
I get the error message "Text ended before matching quote was found for ". (The text was '"~/home/john/Sublime\')"

> **Marric said:**
> Exec=/home/john/Sublime\ Text/sublime_text %f

I get the error message "Text ended just after a '\' character. (The text was '/home/john/Sublime\')." I also tried what you said in quotes and got "Text ended before matching quote was found for ". (The text was '"/home/john/Sublime\')"

---

### Post by Marric on 2012-08-14
Did you try those```
Exec=~/Sublime\ Text/sublime_text %f
Exec=~/"Sublime Text"/sublime_text %f
```If it does not work you can try this workaround:

Create a script in Terminal
```
sudo gedit ~/Desktop/sublimetext.sh
```Paste the following
```
#!/bin/bash

~/Sublime\ Text/sublime_text %f
```Save and Close

Then  give the script the appropriate permissions so that it can be executed (Terminal)
```
chmod a+x ~/Desktop/sublimetext.sh
```In the Desktop Entry you use
```
Exec=bash /home/john/Desktop/sublimetext.sh
```


After all renaming the folder might be  an option (when installing Sublime Text).

---

### Post by mc4man on 2012-08-14
Use 
```
Exec="/home/john/Sublime Text/sublime_text" %f
```

Or you could just go & rename the Sublime Text folder to remove the space

---

### Post by mcjohnalds45 on 2012-08-14
I wanted a solution I could apply to future situations like this, but renaming the folder seems to be the easiest way, thanks for the suggestions though. (But Marric's solution is still pretty clever)

---

