---
title: "Run program as root"
date: 2008-03-03
forum: Programming Talk
---

### Post by Nunslaughter on 2008-03-03
I wrote a program that for each actions needs root privileges. So, no problem I thought, I just add "gksu" before the command to execute in my .desktop file. It worked, but ofcourse only in gnome, not kde.
To fix that, I just put a little piece of code in my Python program that detects which desktop environment is running and based on that, it puts "gksudo" or "kdesu" everywhere where needed.
In Ubuntu, this isn't a problem because for the same program the pasword is being remembered for some time by default, but in OpenSUSE or in Ubuntu if you changed the timeout, it will ask for your password every action.

I looked an looked for examples and explanations, but didn't find anything. So, should I make 2 .desktop files and only show them in their DE, or should I make 2 .deb packages or is there anyway I can fix this in the code?

---

### Post by bruce89 on 2008-03-03
You ought not to run programs as root. However, an useful thing for the future would be PolicyKit, which would mean only small parts of programs are run as root.

---

### Post by Nunslaughter on 2008-03-03
Well it has to be run as root cause it needs access to the bios through libsmbios.
And as said above, every action that is made needs root privileges.

---

### Post by nanotube on 2008-03-03
> **Nunslaughter said:**
> I wrote a program that for each actions needs root privileges. So, no problem I thought, I just add "gksu" before the command to execute in my .desktop file. It worked, but ofcourse only in gnome, not kde.
To fix that, I just put a little piece of code in my Python program that detects which desktop environment is running and based on that, it puts "gksudo" or "kdesu" everywhere where needed.
In Ubuntu, this isn't a problem because for the same program the pasword is being remembered for some time by default, but in OpenSUSE or in Ubuntu if you changed the timeout, it will ask for your password every action.

I looked an looked for examples and explanations, but didn't find anything. So, should I make 2 .desktop files and only show them in their DE, or should I make 2 .deb packages or is there anyway I can fix this in the code?

why not use plain "sudo" instead of the gui equivalents?

---

### Post by shawnhcorey on 2008-03-03
> **Nunslaughter said:**
> Well it has to be run as root cause it needs access to the bios through libsmbios.
And as said above, every action that is made needs root privileges.

I will assume you know what you're doing but...

[COLOR="Red"]WARNING:[/COLOR] use of this technique can compromise the security of your system.

You can change the effective user of your program so that it thinks it's running as root.  If your program is called 'myprogram', then:

```
sudo chown root myprogram
sudo chgrp root myprogram
sudo chmod a=x,ug=s myprogram
```

Of course, now you can only change it via sudo.

---

### Post by Nunslaughter on 2008-03-04
nanotube : It is not run from terminal, but maybe I'm missing something, but I looked at other programs that needed rootprivileges to run (eg gparted, wireshark, synaptic,...) and they all use this in their *.desktop file:
exec=gksu /usr/bin/prog
and this works, offcourse, but you can't use this in KDE. So I removed "gksu" from that line and  in my Python program, I just added that it checks which desktop environment is used and puts "gksu" or "kdesu" everywhere is needed. But as said, in Ubuntu the password is remembered for some time, but for people who changed the timeout or in OpenSUSE the password is asked every action if I do it this way.

shawnhcorey: If I distribute my program, then everyone has to do this too, right?


I just wonder how other programs that needs to be run as root do this, as well as in Gnome and KDE.

---

### Post by nanotube on 2008-03-04
> **Nunslaughter said:**
> nanotube : It is not run from terminal, but maybe I'm missing something, but I looked at other programs that needed rootprivileges to run (eg gparted, wireshark, synaptic,...) and they all use this in their *.desktop file:
exec=gksu /usr/bin/prog
and this works, offcourse, but you can't use this in KDE. So I removed "gksu" from that line and  in my Python program, I just added that it checks which desktop environment is used and puts "gksu" or "kdesu" everywhere is needed. But as said, in Ubuntu the password is remembered for some time, but for people who changed the timeout or in OpenSUSE the password is asked every action if I do it this way.

shawnhcorey: If I distribute my program, then everyone has to do this too, right?


I just wonder how other programs that needs to be run as root do this, as well as in Gnome and KDE.

well, in that case, why not run your whole program with sudo (or gksu or kdesu)? that way anything that it executes will also have root permissions, and you don't have to worry about putting a "sudo" in front of everything. so, e.g., you say your prog is written in python, so to run it, just run
```
gksu python yourprogram.py
```
(and instruct your users to do the same - using either gksu or kdesu, as appropriate for their system). then your problem is solved?

---

### Post by Nunslaughter on 2008-03-04
Well yeah, they can run it manually, but my .deb package places a menu entry by placing a pre-made .desktop file in /usr/share/applications. Untill now, KDE users have to edit this file and change gksu into kdesu, but this isn't that user-friendly.
Maybe I should make 2 .desktop files like Synaptic does, one that only shows in Gnome and one only in KDE, but I don't know if that's the way to do it properly because users install 2 files and will only use one.

Maybe this all sounds confusing, I too have searched examples but didn't find an answer. I never used Kubuntu, so I'm wondering, what if you install Gparted or Gmount-iso or Wireshark in Kubuntu? They all use gksu...

---

### Post by nanotube on 2008-03-04
> **Nunslaughter said:**
> Well yeah, they can run it manually, but my .deb package places a menu entry by placing a pre-made .desktop file in /usr/share/applications. Untill now, KDE users have to edit this file and change gksu into kdesu, but this isn't that user-friendly.
Maybe I should make 2 .desktop files like Synaptic does, one that only shows in Gnome and one only in KDE, but I don't know if that's the way to do it properly because users install 2 files and will only use one.

Maybe this all sounds confusing, I too have searched examples but didn't find an answer. I never used Kubuntu, so I'm wondering, what if you install Gparted or Gmount-iso or Wireshark in Kubuntu? They all use gksu...

two .desktop files seems like a good solution - while "most" people will never use the second one, some people alternate between DEs, so having the two .desktops would work well, i think.

---

### Post by Nunslaughter on 2008-03-05
Yep, so I did it with the 2 .desktop files and works well...Thanks

---

### Post by imdano on 2008-03-05
Out of curiosity, what method did you use to detect the desktop environment being used?  Just checking for a particular process associated with each environment or something else?

---

### Post by Nunslaughter on 2008-03-05
> **imdano said:**
> Out of curiosity, what method did you use to detect the desktop environment being used?  Just checking for a particular process associated with each environment or something else?

Well, I searched alot for this, and this is what I found:
```
#!/usr/bin/env python

import os

desktop_environment = 'generic'
if os.environ.get('KDE_FULL_SESSION') == 'true':
    desktop_environment = 'kde'
elif os.environ.get('GNOME_DESKTOP_SESSION_ID'):
    desktop_environment = 'gnome'
else:
    try:
        info = commands.getoutput('xprop -root _DT_SAVE_MODE')
        if ' = "xfce4"' in info:
            desktop_environment = 'xfce'
    except (OSError, RuntimeError):
        pass

return desktop_environment
```

---

