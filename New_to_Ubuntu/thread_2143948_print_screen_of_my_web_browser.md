---
title: "print screen of my web browser?"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by linuxdad1976 on 2013-05-10
I am not quite new to Linux as a whole but every time I try to switch a laundry list of problems keeps me using windows. Right now I cannot ,for the life of me, figure out why when I have my webbrowser open I press Alt+print screen it takes a picture of my desktop instead of my window. Using ubuntu 13.04. Any ideas?

---

### Post by stinkeye on 2013-05-10
Check the setting in ccsm.
May have to install....
```
sudo apt-get install compizconfig-settings-manager
```

May want to try **shutter** as your screenshot tool.
Has a handy quicklist and editing tool for simple annotating.

Shutter allows you to automatically name and save a file.
Hover the Filename box for naming options.

---

### Post by alhefner on 2013-05-10
If you just want to print the webpage you are viewing in Firefox use "File" > "Print". The "alt"+"prntscrn" function will take a screenshot of your entire screen and that is exactly how it is supposed to function.

---

### Post by tgalati4 on 2013-05-11
PrtSc (Printscreen) will print just the current window.  Alt-Printscreen will print the entire desktop.

---

### Post by stinkeye on 2013-05-11
> **alhefner said:**
> If you just want to print the webpage you are viewing in Firefox use "File" > "Print". The "alt"+"prntscrn" function will take a screenshot of your entire screen and that is exactly how it is supposed to function.
> **tgalati4 said:**
> PrtSc (Printscreen) will print just the current window.  Alt-Printscreen will print the entire desktop.
Not according to my default settings.

---

### Post by zombifier25 on 2013-05-11
> **stinkeye said:**
> Not according to my default settings.

Seconded. Alt+PrtScr will take a screenshot of the current window, while just PrtScr will take a screenshot of the entire screen.

---

### Post by tgalati4 on 2013-05-11
I stand corrected.  Alt-PrtSc will capture the entire desktop.  PrtSc will capture the current window.

---

### Post by zemega on 2013-05-11
You guys stand corrected on your system, wont argue about that. So post opener, you can try between prntsc and alt+prntsc. If you still have trouble, take a look at the dconf editor.

---

### Post by pfeiffep on 2013-05-11
I believe 13.04 comes with a gui screen print utility - at least mine has "Screenshot" found in accessories.

---

### Post by deadflowr on 2013-05-11
> **pfeiffep said:**
> I believe 13.04 comes with a gui screen print utility - at least mine has "Screenshot" found in accessories.

Yep, sure does.

You can even launch it from the terminal
```
gnome-screenshot
```

If the default bindings aren't working, you could try to make a custom one, or two, or three.:P

Go to system settings > keyboard > shortcuts
Then click on the plus sign and make a new one
For a window screenshot enter
```
gnome-screenshot -w
```
Name it and click ok.
Then go to custom short tab and click on the keyboard short on the right, and make a shortcut.
If you choose to make one with the currently used binding, then it will ask you if want to reassign.
Do so at your own will.

---

### Post by VirginiaDrifter on 2013-05-11
> **pfeiffep said:**
> I believe 13.04 comes with a gui screen print utility - at least mine has "Screenshot" found in accessories.

You beat me to it.  :)

---

