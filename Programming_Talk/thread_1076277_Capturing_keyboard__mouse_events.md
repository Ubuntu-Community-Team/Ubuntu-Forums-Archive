---
title: "Capturing keyboard / mouse events"
date: 2009-02-21
forum: Programming Talk
---

### Post by zewelor on 2009-02-21
I'm trying to write program which can do some actions after pressing keys on keybord or mouse buttons. I found that mouse events should be in /dev/input/mouse0 but on intrepid when i do cat on that file i cant see anything. I found that after adding 'Option "AutoAddDevices" "false"' to the xorg.conf i'm able to get mouse events thrue the /dev/input but after that my multimedia keys are not working so its not a very good solution. So i'm wondering how it is possible to capture mouse events without setting AutoAddDevices to false. I would like to do it in c++ or python

Edit: i want capture events when i don't have focused window with my program, some system wide solution

---

### Post by Ferrat on 2009-02-21
> **zewelor said:**
> I'm trying to write program which can do some actions after pressing keys on keybord or mouse buttons. I found that mouse events should be in /dev/input/mouse0 but on intrepid when i do cat on that file i cant see anything. I found that after adding 'Option "AutoAddDevices" "false"' to the xorg.conf i'm able to get mouse events thrue the /dev/input but after that my multimedia keys are not working so its not a very good solution. So i'm wondering how it is possible to capture mouse events without setting AutoAddDevices to false. I would like to do it in c++ or python

Well for keyboard you could just write your own interpreter based on c++ standard iostream (a while loop checking for keypress or something), or you could hook them from the desktop manager. 
There are more solutions I guess for ex. 
[https://www.linuxquestions.org/questions/programming-9/registering-keyboard-events-on-c-not-cin-238471/](https://www.linuxquestions.org/questions/programming-9/registering-keyboard-events-on-c-not-cin-238471/)
deal a bit with this. 
otherwise Google is your friend :)

---

### Post by zewelor on 2009-02-21
> **Ferrat said:**
> Well for keyboard you could just write your own interpreter based on c++ standard iostream (a while loop checking for keypress or something), or you could hook them from the desktop manager. 
There are more solutions I guess for ex. 
[https://www.linuxquestions.org/questions/programming-9/registering-keyboard-events-on-c-not-cin-238471/](https://www.linuxquestions.org/questions/programming-9/registering-keyboard-events-on-c-not-cin-238471/)
deal a bit with this. 
otherwise Google is your friend :)

The for the replay

Normally i know how to get keyboard / mouse events but i need to grab them when i don't have focused window with program, something like keylogger which will get any key press and mouse buttons in every program not only in mine.

---

### Post by days_of_ruin on 2009-02-21
> **zewelor said:**
> The for the replay

Normally i know how to get keyboard / mouse events but i need to grab them when i don't have focused window with program, something like keylogger which will get any key press and mouse buttons in every program not only in mine.

And why would you want a to make keylogger? >.>

---

### Post by zewelor on 2009-02-21
i didn't said that i want to write keylogger im just asking how to do similar funcionality, i need it for another purpose, and what is wrong with writing a keylogger ?

---

### Post by Ferrat on 2009-02-21
> **zewelor said:**
> i didn't said that i want to write keylogger im just asking how to do similar funcionality, i need it for another purpose, and what is wrong with writing a keylogger ?

Absolutely nothing, it's a great protection/backup tool just that people only connect them with stealing passwords ect. but I think you need to look up hooking then, hooking the kernel calls

---

