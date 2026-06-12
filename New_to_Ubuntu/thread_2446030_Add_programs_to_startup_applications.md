---
title: "Add programs to startup applications"
date: 2020-06-23
forum: New to Ubuntu
---

### Post by regularpersontrying on 2020-06-23
Hello - 

How do I find the command to add a program to startup apps?

I searched here. I searched google. Lots of different responses but none of them show me how to locate the program and tell it to start up. 

In the startup application prompt...shouldn't I just be able to select from the installed apps?

In looking at a list of all the installed apps...shouldn't I just be able to select "Launch at Login" or something similar?

Is there a tool I can install that will make this easy? I don't want to go searching for commands every time I need to do something simple like tell a program to start with Ubuntu.

Edit - I have now read about 30 articles and not a single one just tells me how. I looked in the Ubuntu help...no help. "Run the command" - how do I find the command? 

Does anyone know of a tool I can install that will just let me select a program and tell it to start on boot?

---

### Post by Holger_Gehrke on 2020-06-23
Most - if not all - programs to set programs to run after login ask for a command because in a lot of cases the program you want to start is not graphical but a small command line tool that makes some settings (example: since an update a while ago my touchpad can't be set to "tap to click" - the option is just not there in the settings app; no problem, just run 'xinput set-prop "ETPS/2 Elantech Touchpad" "libinput Tapping Enabled" 1' after login and everything is good).

Finding out the command to run a specific program depends a bit on which variant -- or 'flavour' as they are often called -- of Ubuntu you're running. In XUbuntu I can just right-click on an item in the whisker-menu, select 'edit starter' from the context-menu and get a form which has the command and lots of other thing. In other flavours it might be different. On the command line / in the terminal you can either use the 'apropos' command to find commands which mention a term in the first part of their manual page (example: 'apropos writer' will among others give me 'lowriter' as the command for the word processing component of LibreOffice) or you can search through the .desktop files in /usr/share/applications for the name of the program with 'grep "Put the name of the program as it's displayed in whatever starter you use here" /usr/share/applications/*.desktop' and then look at the content of the files grep found (.desktop files are just text, you can open them with an editor or use 'less' on the command line) and check the line beginning with 'Exec' for the command.

Holger

---

### Post by regularpersontrying on 2020-06-24
Thank you for your reply. 

I am just using the Ubuntu version downloaded from the Ubuntu website - [https://ubuntu.com/download/desktop/thank-you?version=20.04](https://ubuntu.com/download/desktop/thank-you?version=20.04)

Is there a better more full-featured version?

It seems in this version I can't just right click to get info. I also just discovered I cannot drag & drop files to move them around...all of this seems like it should be very, very basic functions. 

This OS is beautiful and has some cool features...but I worry that I am going to run into this kind of basic thing not working on a regular basis.

---

### Post by ajgreeny on 2020-06-24
You have, I believe, come across a few of the minor (or major, depending on your point of view) annoyances of the gnome desktop which is now the default of Ubuntu.

I do not use Ubuntu partly for that very reason, and moved to Xubuntu which has a more standard type desktop design when gnome-2 ended and gnome-3 became the default, and in my opinion Xubuntu allows the user to continue using those "basic functions" that you have found missing in gnome.

You could try installing the ***xubuntu-desktop*** package to your current Ubuntu install and then choose Xubuntu at login, though this will then leave you with duplicate file manager, text editor, terminal and several other utilities, which may be annoying and could possibly conflict with each other, though probably not seriously so.
Alternatively you could reinstall using the Xubuntu.iso archive file from [https://xubuntu.org/download](https://xubuntu.org/download) but as both systems are gtk based I would suggest you try adding the ***xubuntu-desktop*** package first to see how you manage with that arrangement, and reinstall the whole system if you find the two systems too difficult when on the same OS.

For a more immediate answer to your query it would help us if you tell us what application or utility you want to add to the startup-applications as we may be able to give you a more direct answer.

---

### Post by ActionParsnip on 2020-06-24
If you put a ".desktop" file for the application in ~/.config/autostart it will run at login

---

### Post by Dennis N on 2020-06-24
If you open "Startup Applications", you can add a program there. That's what it's for. See screenshot.
The command is the only place that might confuse a user. Usually the command is the same as the package name or you can use the browse button to get a complete path to the executable. Most common program executables are in /usr/bin. Once you locate it there, click 'open' and it will fill in the command box. In the screenshot, I added 'Audacious' to my startup applications.

---

### Post by ActionParsnip on 2020-06-24
> **Dennis N said:**
> If you open "Startup Applications", you can add a program there. That's what it's for. See screenshot.
The command is the only place that might confuse a user. Usually the command is the same as the package name or you can use the browse button to get a complete path to the executable. Most common program executables are in /usr/bin. Once you locate it there, click 'open' and it will fill in the command box. In the screenshot, I added 'Audacious' to my startup applications.

That's what my method does, just more manual :KS

---

### Post by pantazi on 2020-06-24
If, for example you wanted Audacity to be added to startup, open terminal and type 'which audacity' (without the speech marks) and it will show the command needed.

---

### Post by propolis2 on 2020-06-28
I've just started with ubuntu 20.04 and it's my first real look at linux
I like it.
Using duckduckgo I searched "set vino to startup automatically"
I got this immediately:
[https://askubuntu.com/questions/1062727/how-to-get-vino-vnc-server-to-start-on-startup-in-ubuntu-18-04-1](https://askubuntu.com/questions/1062727/how-to-get-vino-vnc-server-to-start-on-startup-in-ubuntu-18-04-1)
basically it says:
 "After startup, click the square array of dots in the lower left of the screen.

  Type 'startup applications' (no quotes) into the search box that appears at the top of the screen. Clock on the resulting icon.

  Click Add at the right of the box, Type 'start vino' in the Name box, and paste /usr/lib/vino/vino-server into the command box.

  Click Add at the bottom of the box.

  Close the app.

  You're done."

It worked first try for me.

---

