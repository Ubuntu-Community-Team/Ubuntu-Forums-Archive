---
title: "C++ creating window help"
date: 2009-08-27
forum: Programming Talk
---

### Post by #Peter on 2009-08-27
Hello!
Me and my two friends are starting a programming-project, and we would like some help. Our task is to create a linuxclient for a program made for handling *school tests*, the client shall make it *impossible for the students to cheat* (open other windows to google the answer).
We have programmed before, mostly in java, but I think C++ is better at this? Anyway, we havn't handled graphical windows before. I have searched the internet in about how you do, and from my understanding you can use linux own API and input all variables and try to create some function to lock in all input into the program..
[U]
Now my questions:[/U]
Is this possible?

Is there any way to handle windows so that you don't have to write 200 lines to create a window? (Like a package or something, I thought I saw something like that but I didn't really get it)

---

### Post by hessiess on 2009-08-27
Short of removing every application form the computer besides the test app (ie chrooting), I dont beleve it is possible to make it absolutely imposable to prevent someone finding a way to break out of an application. You could possibly full screen the app and not put in an event handler to exit it, but there may still be a way around it.

There are multiple ways of creating GUI's on linux, i.e. GTK, QT and WXWigits.

---

### Post by WitchCraft on 2009-08-27
> **hessiess said:**
> Short of removing every application form the computer besides the test app (ie chrooting), I dont beleve it is possible to make it absolutely imposable to prevent someone finding a way to break out of an application. You could possibly full screen the app and not put in an event handler to exit it, but there may still be a way around it.

There are multiple ways of creating GUI's on linux, i.e. GTK, QT and WXWigits.

wxWidgets: [http://www.wxwidgets.org](http://www.wxwidgets.org)


If you need an application in a browser window, then I think you should use GTK (GTK webkit), because the wxWebKit is a 250 MB overkill.


You might have to access the Xlib directly to block application switching. wxWidgets allows for mixing widgets and native APIs.

One thing you could do is create a full-screen application and don't offer any other way out of it other than to quit the program.

When I was at secondary school, the teacher used such a program on windows to prevent the pupils from browsing in the web while he explained excel. 

Then you just have to figure out a way to catch the close event and not close the application on this event, until the server allows closing it.

---

### Post by #Peter on 2009-08-29
Thank you for your answers, I will definately try out GTK and your ideas... Much appreciated :).

---

### Post by Frak on 2009-08-29
The best way would to route all connections through the instructors terminal and block access to all sites as long as the terminal stays on-line. This way you don't need to worry about accessing something such as Xlib to deny app-switching.

Another feature would be to exclude the quit handler (as explained above) and require the instructor or another administrator to verify the operation before firing the event.

---

### Post by soltanis on 2009-08-29
I suggest that you use a different window manager: specifically, use a manager such as fluxbox, or DWM. In fluxbox, you can modify the configuration file to make other programs inaccessible; in DWM, you can change the key combinations at compile time to nothing. Using automated start-up scripts, then, you can run a window manager and then run another program on top of it.

In DWM, if you were to disable the key combinations for opening a terminal and changing the windows, and disabled the combination for running dmenu, this would render the windows unchangeable (and the user could not open any other programs). This is because DWM is a tiling window manager (i.e. no "x" buttons) with no mouse interface (i.e. disable the keystroke combinations and the GUI is at your whim).

Then, use a basic bash script to run the testing program. So long as that program provides no facilities for say, opening random other programs, and the student has no way of logging in through the virtual terminals, they have essentially no way to run arbitrary programs.

I would know -- when I was a kid, the library computers would only let you open Internet Explorer. What they didn't disable was running "Help" by pressing F1; and Microsoft in its infinite wisdom put a menu option in the Online Help for changing the homepage of IE. Couple this with the fact that a homepage like C:\ earns you a Windows Explorer view of the hard drive and you might as well have not used security at all. Avoid putting those kinds of options in your testing programs.

---

### Post by hessiess on 2009-08-29
You will also need to disable the virtual terminals which can be assessed with ctrl+alt+f1-f7.

---

### Post by soltanis on 2009-08-29
Not true -- if the students cannot log into the terminals, they cannot do any harm with them. Leave the terminals for debugging purposes.

However, DO: disable the ctrl-alt-backspace combination to kill the X server, since a student could do this, then hit ctrl-C quickly to kill the restarting server which would drop them into a terminal.

---

### Post by WitchCraft on 2009-08-30
> **hessiess said:**
> You will also need to disable the virtual terminals which can be accessed with ctrl+alt+f1-f7.

Oh damn, I would have forgotten that.

---

