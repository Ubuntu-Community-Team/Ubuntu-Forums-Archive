---
title: "System Calls in C++ Program"
date: 2011-08-05
forum: Programming Talk
---

### Post by anEarthCitizen on 2011-08-05
Hi, 

I have developed a Qt front-end for a command line program.

It just takes the user's input through the GUI, then executes the corresponding system command in the terminal using system ("") from stdlib.h.

**The problem is:** when I run the application form the terminal it works fine as expected, but when I make a launcher for my application only the GUI shows up but no terminal.

I have made a workaround but it's useless (as well as bad practice), since I preceded the command with ```
"usr/bin/konsole -e"
```. I know this is wrong, but it works.

So, any ideas? Many Thanks.

---

### Post by karlson on 2011-08-05
> **anEarthCitizen said:**
> Hi, 

I have developed a Qt front-end for a command line program.

It just takes the user's input through the GUI, then executes the corresponding system command in the terminal using system ("") from stdlib.h.

**The problem is:** when I run the application form the terminal it works fine as expected, but when I make a launcher for my application only the GUI shows up but no terminal.

I have made a workaround but it's useless (as well as bad practice), since I preceded the command with ```
"usr/bin/konsole -e"
```. I know this is wrong, but it works.

So, any ideas? Many Thanks.

Why would you need a terminal if you are developing a GUI frontend?

---

### Post by anEarthCitizen on 2011-08-05
> Why would you need a terminal if you are developing a GUI frontend?Take WinFF for example, when you encode a video, say from mp4 to avi:

you choose the file you want and the output type and destination through the GUI and WinFF then executes a long ffmpeg command (that may seem impossible for a new user to memorize). This new command is executed in the terminal, and the encoding control (stop/pause) is controlled through the terminal (since ffmpeg is the actual program underneath).

See the attached image.

---

### Post by anEarthCitizen on 2011-08-05
Solved! :D

Silly me, I looked into WinFF's and they are using ```
/usr/bin/x-terminal-emulator
``` with ```
-e
``` argument.

Finally, The application runs perfectly. Thanks for your time.

---

