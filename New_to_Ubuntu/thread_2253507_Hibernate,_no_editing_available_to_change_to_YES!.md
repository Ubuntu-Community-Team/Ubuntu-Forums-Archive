---
title: "Hibernate, no editing available to change to YES!"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by hebdave on 2014-11-20
Hi I read an internet article which shows me how to change my Ubuntu version 14.04 to include hibernate. It then shows up in the shut down menu. However when it comes to making the changes it suggests I cannot edit the terminal it shows. It seems to not let me delete anything and fill it in with =No instead. Is does allow you to type after the line though so it cannot be completely read only as in a writeable document. I'm still learning ubuntu.

Here is what was recommended for 14.04 -

To re-enable hibernate, run command below to edit the configuration file:

sudo nano /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

When the file opens in the terminal window, scroll down to find out the section started as:

&#8220;[Disable hibernate by default in upower]&#8220; and &#8220;[Disable hibernate by default in logind]&#8220;
Change the value of ResultActive to =yes in both.

Thanks all much appreciated.

---

### Post by Impavidus on 2014-11-20
So nano allows you to type but it doesn't allow you to type backspace to remove the character before the cursor? That would be very strange. Some terminals have some strange handling of backspace and delete (for backwards compatibility). Have you tried the delete key?

Or did you try to select the text with the mouse and type something over it? Because that doesn't work in the terminal.

---

### Post by hebdave on 2014-11-20
High thanks. It seemed to allow me to use the arrow keys only to get to the places. Then I found delete worked. ie- on this particular terminal part it will not let me place a cursor with a mouse. 

Once I adjust the terminal file I then cannot work out how to save it so the changes are made though ? I went to file and terminal at the top of my screen and could not see anything I thought resembled that. So how do I save new changes once made to achieve the hibernate ? Thanks very much indeed.

---

### Post by Impavidus on 2014-11-20
The terminal (strictly speaking a terminal emulator) is just a program that offers a text based interface to the program running inside the terminal. It only passes on keyboard input and text output. The program running inside your terminal, which is called nano in this case, is unaware of any mouse interactions or menus available from the terminal emulator itself. The terminal allows you to copy text from the terminal, but the program running inside won't notice this. The terminal allows pasting text into the terminal, but the program running inside won't notice the difference between pasting and typing. And you're not directly using the terminal to change the file, but you're using the terminal as an interface to the nano program, which in turn edits the file. The terminal doesn't even know you're editing a file.

So to come to the point, the command to save the file cannot be given to the terminal emulator. Nano has it's own way of accepting commands, which are listed at the bottom of the screen. To save a file, hit control+o (that's an o as in oscar). To exit nano, hit control+x. The ^ character is short for control+something.

---

### Post by coffeecat on 2014-11-20
> **hebdave said:**
> I'm still learning ubuntu.

nano is a nice little terminal text editor, but it takes a bit of getting used to if you are accustomed to GUI editors. If you would like to use a GUI editor for the task you describe, first of all install the package gksu from the Software Centre, or with this terminal command:

```
sudo apt-get install gksu
```

Now you will be able to invoke the default GUI text editor gedit with root privileges. Substitute "sudo nano" with "gksu gedit", so with the command you mention in your first post, the gedit equivalent would be:

```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

```

Although having said all that, it is worth learning your way around nano. It is there if you need it if the GUI fails and you need to edit configuration files.

---

### Post by hebdave on 2014-11-21
Okay thanks I seem to have saved it via nano with ctrl+o , hitting return and then ctrl+x to exit. Can I do something similar altering the amount of brightness on my screen by changing some code lines. Then also something for CPU usage as I here ubuntu uses more of the CPU on average. I am just in the process of changing these extra settings after starting to get used to Ubuntu. Hope I can follow instructions and your able to help. Much appreciated.

---

### Post by Impavidus on 2014-11-21
Screen brightness keys on the keyboard usually work, but if not, or if you want to change the default brightness, the solution may be hardware dependent. If you're using the CPU a lot, that could mean you're rendering the GUI on CPU instead of GPU. This may be caused by too old hardware, in which case switching to a lighter desktop helps, or hardware for which no good open source drivers are available. That often means very new hardware from not very cooperative manufacturers. There may be a proprietary graphics driver available to help you with that. Check via the additional drivers utility, don't try downloading stuff directly from the manufacturers website.

As this is a complete different issue and I don't know very much about driver problems (nearly everything always worked out of the box for me), you can best start a new thread about this and include a precise description of your hardware there.

---

