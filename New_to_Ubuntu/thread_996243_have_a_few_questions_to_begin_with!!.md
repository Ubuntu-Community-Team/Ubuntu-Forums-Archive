---
title: "have a few questions to begin with!!"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by roaddummy on 2008-11-28
OK, I just recently installed Ubuntu on my computer.  So far I am loving it.  I think it is a great alternative to Vista.  I already used GIMP before I got Ubuntu.  Now, I need to know a couple of things.  I have a graphic tablet and it won't work right now with Linux.  Is there any type of software that I can get to allow that to work??  Is there something that will allow you to use windows only type devices with Linux??  I really need my tablet!!!  

Second, I had GIMP already installed into Ubuntu.  I want to add my brushes and fonts and stuff like that back to it.  When I do a cut and paste into the folder where I want them, it won't let me.  It tells me something like I don't have permission to do so or soemthing like that.  If there is anyone who can help me with that, I would greatly appreciate it!!  I need my fonts and brushes back!!!

Melanie

---

### Post by LowSky on 2008-11-28
these instruction will help install your extra fonts,

to install MS core Fonts  go to add/remove

look for ubuntu-restricted-extras, and install that, it give you, mp3 support, java, flash and a few other things too

welcome to the linux world

---

### Post by roaddummy on 2008-11-28
OK, I think I did that last night for something.  I think it was for the music formats.  So, can I install fonts now????  Also, do you know if I install the fonts to Ubuntu, will GIMP pick them up?  Will this work for the brushes also??  Thanks for the help so far.  Keep in mind I am not computer literate!!!

---

### Post by kk0sse54 on 2008-11-28
I can't help with your first problem since I've never used a tablet pc but with your second problem you are having permission problems because that folder is owned by root. You have two options
[B]
GUI way[/B]:
-press alt+f2 and type gksudo nautilus and enter your password to start nautilus with root permissions. Then just do what you did before and copy and paste the necessary files into the correct folder

**CLI way**:
-use the command "cp"
for example to copy and paste a file into another folder open up a terminal and type (the use of sudo is necessary to give you the permission to copy and paste into a root folder) ```
sudo cp /<path to file> /<path to destination and name of newly pasted file>
```
-also try "man cp" in the terminal to find more information about the cp command

---

### Post by roaddummy on 2008-11-28
The first option sounds easier!  I am still at a basic level on computers.  Many people think I am really good with them, but I guess I have them fooled.  I will see if I can put them there when I get home.  I did the permissions thing last night so I hope I can get it to work!  Thans for the help!

Melanie

---

### Post by stoogiebuncho on 2008-11-28
You can install ms core fonts from add/remove as was mentioned before, but if you want to install other types of fonts, you'll have to do it a different way.

1) Open up your home folder  (it will be /home/*yourusername*)
2) Press Ctrl + H to show hidden files (hidden files and folders in Ubuntu start with a "."
3) Look for a folder named ".fonts".  If you don't have one, create it.
4) Put the .ttf files (or other font files) in that folder.

I can't remember if you have to log out and log back in, or if they are installed immediately, but they will be available to all programs, including GIMP.

---

### Post by halitech on 2008-11-28
If you do the same first 2 steps as above, you will see a folder called .gimp-2.x. in there  you will find brushes/gradients/scripts/etc where you can place them without needing to be root. added benefit of this is when you back up your /home folder, it will grab those files as well.

---

