---
title: "Is it possible to switch window controls(close,minimize,mx)to the left (Gnome Shell)?"
date: 2017-01-03
forum: New to Ubuntu
---

### Post by lemler32 on 2017-01-03
Hello all
to start off im new to ubuntu and linux in general.I'm coming from apple products so it would feel a little more like home in a way. I am running GNOME Shell 3.20.4 (ubuntu 16.04) any help would be greatly appreciated THANK YOU :]

---

### Post by oldrocker99 on 2017-01-03
Welcome to the forums! Your post doesn't mention a question. This is a good place to start: [https://help.ubuntu.com/](https://help.ubuntu.com/).

Help with GNOME:[https://help.gnome.org/users/gnome-help/3.22/](https://help.gnome.org/users/gnome-help/3.22/).

---

### Post by vasa1 on 2017-01-03
OP left the question in the title! so it's one of those "how can I move the min, max, and close buttons from where they are to where I want them" questions.

---

### Post by Geoffrey_Arndt on 2017-01-03
The standard Ubuntu desktop already has the window controls on the left.   Only mentioning it in case someone else installed or setup your desktop (Ubuntu-Gnome).

---

### Post by deadflowr on 2017-01-03
To the question, yes you can.
Two ways
Simple graphical way
Or 
Little harder.

the graphical way involves installing an application called dconf-editor.
It should be available in the software store/center/whatever it's-called-for-the -version-of-ubuntu-you-have.

In this application you need to go to org >> gnome >> desktop >> wm >> preferences and you'll see an option for button-layout.
Double click on that and set it to 
```
close,minimize,maximize:
```
(Might need to do so manually)
and the buttons should show on the left.

The little harder method is actually simple, but requires you to use the terminal.
Open a terminal and run
```
gsettings get org.gnome.desktop.wm.preferences button-layout

```
This will give you the current settings.
And to change run
```
gsettings set org.gnome.desktop.wm.preferences button-layout close,minimize,maximize:

```
To note, the layout is determined by where the : symbol is, if at the front, the button will be at the right, if at the end, the buttons will be at the left.

Hope it helps, or makes sense
good luck

---

### Post by lemler32 on 2017-01-04
ooh wow [[COLOR=#C61919]deadflowr[/COLOR]]("https://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000]  it worked perfectly! actually kinda surprised on how easy it was xD thank you so much![/COLOR]

---

