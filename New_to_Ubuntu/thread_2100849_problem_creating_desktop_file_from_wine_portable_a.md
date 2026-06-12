---
title: "problem creating desktop file from wine portable app"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by Froylan on 2013-01-03
hello, I am fairly new to this, I am creating a wine desktop configuration file from apps(visual novels) and I am stuck with an app with spaces, i already did 2 but with this one i'm struggling, i got one working in my "Videos" folder, the text inside the desktop file is this:
```
[Desktop Entry]
Version=1.01
Name=president
Exec=env WINEPREFIX="/home/froylan/.wine" wine Z:\\\\home\\\\froylan\\\\Videos\\\\President\\\\President\\\\osana.exe
Terminal=false
Icon=/home/froylan/Pictures/21.png
Type=Application
Categories=Games;
StartupWMClass=osana.exe
```this one was working propperly but then when i did this one inside of ~/Videos/SecondReproduction/SecondReproduction/TSR Patch - English v0.99b/[English] The Second Reproduction.exe it didn't work so i changed the path to:
~/Pictures/Webcam/SecondReproduction/SecondReproduction/English/english.exe
 and it didn't work either, what i did was this:

```
[Desktop Entry]
Version=1.01
Name=The_Second_Reproduction
Exec=env WINEPREFIX="/home/froylan/.wine" wine Z:\\\\home\\\\froylan\\\\Pictures\\\\Webcam\\\\SecondReproduction\\\\SecondReproduction\\\\English\\\\english.exe
Terminal=false
Icon=/home/froylan/Pictures/21.png
Type=Application
Categories=Games;
StartupWMClass=english.exe
Name[en_US]=second_reproduction
```but then i get this weird message
[ATTACH]229502[/ATTACH]
and then this:
[ATTACH]229503[/ATTACH]

---

### Post by vasiliscnisrok on 2013-01-03
Please set
 Terminal=true
and give me error messages from Terminal.

---

### Post by Froylan on 2013-01-03
> **vasiliscnisrok said:**
> Please set
 Terminal=true
and give me error messages from Terminal.
it gave me this:
```
 '/home/froylan/Desktop/second reproduction.desktop' 
/home/froylan/Desktop/second reproduction.desktop: line 2: [Desktop: command not found


```and it repeated the steps of the screenshots.
EDIT: I changed to a false version and it gave me error, and i chaged to the english patch version and it ended the same way.

---

### Post by vasiliscnisrok on 2013-01-03
1) rename /home/froylan/Desktop/second reproduction.desktop  to  /home/froylan/Desktop/second_reproduction.desktop

2)  set Exec
```
Exec=env WINEPREFIX="/home/froylan/.wine" wine "Z:\\home\\froylan\\Videos\\President\\President\\osana.exe"
```

---

### Post by Froylan on 2013-01-03
> **vasiliscnisrok said:**
> 1) rename /home/froylan/Desktop/second reproduction.desktop  to  /home/froylan/Desktop/second_reproduction.desktop

2)  set Exec
```
Exec=env WINEPREFIX="/home/froylan/.wine" wine "Z:\\home\\froylan\\Videos\\President\\President\\osana.exe"
```
that will activate osana, not second reproduction :-s
EDIT:it did activate osana, not second reproduction.

---

### Post by RottNKorpse on 2013-01-03
if you navigate to the wine directory and Drag & Drop the .exe file to your desktop holding down Ctrl+Shift it will create a link to that file allowing you to run it from your desktop.

You can also hold down Alt when you drop it to see more options and it may contain a WINE desktop option.

I do not have WINE installed so I can't say exactly what will happen but that Link method may be all you need...unless you are trying to do more than just a desktop launcher.

---

### Post by vasiliscnisrok on 2013-01-04
> **Froylan said:**
> that will activate osana, not second reproduction :-s
EDIT:it did activate osana, not second reproduction.

sorry
```

Exec=env WINEPREFIX="/home/froylan/.wine" wine "Z:\\home\\froylan\\Pictures\\Webcam\\SecondReproduction\\SecondReproduction\\English\\english.exe"

```

quote your path

---

### Post by Froylan on 2013-01-04
meither of them worked, closing thread, i'd rather go and do the manual work ;)

---

