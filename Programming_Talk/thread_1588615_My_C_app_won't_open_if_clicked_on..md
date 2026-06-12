---
title: "My C app won't open if clicked on."
date: 2010-10-05
forum: Programming Talk
---

### Post by RicDev on 2010-10-05
Hi all.

So I am learning to code in Ubuntu coming from WinXP and Win7 and
I have to say it is great. I recently downloaded C::B my prefered IDE
for coding and made a new project in C and it was just a simple helloworld.

The program compiled and linked fine, everything went smooth letting
me know that I did not mess something up while setting the IDE up.

So my problem is this, I can run the just built program by pressing the run
or debug button in C::B and a terminal will open and output "Hello World"
But I can't go to my project directory and just double click on it.

More notes:

if I open up terminal and cd to my programs directory and ./run it
it will open in terminal but it won't run alone.

I added a getchar(); to the code to keep it from closing but it still does not work.

So again it runs great from terminal and C::B but alone it won't open and no kind of error code.

Please Help :(

---

### Post by Barrucadu on 2010-10-05
Is it executable?

---

### Post by matthew.ball on 2010-10-05
I'm under the impression that under an X11 session STDOUT redirects elsewhere (where as, run through a terminal STDOUT sends the output to the terminal display).

Since you are trying to run it through the GUI the output is just going to the same place that the X11 output is directed to (possibly /dev/null? I'm not sure).

However, I could be totally wrong. :p

---

### Post by spjackson on 2010-10-05
With the normal setup of nautilus, it does not open a terminal to run an application when you click on it. This applies to any terminal-based application; it's not specific to yours.

I don't know whether there is a way to configure nautilus to do that. However, you can achieve something similar as follows.

Create and edit a file (e.g. run-in-terminal) in ~/.gnome2/nautilus-scripts/ . Insert the following code.
```

#!/bin/bash

gnome-terminal --execute bash -c "$1 ; read"

```then
```

chmod +x ~/.gnome2/nautilus-scripts/run-in-terminal

```Now, in nautilus you can right-click on your program and select scripts->run-in-terminal.

---

### Post by Barrucadu on 2010-10-05
Ahhh, of course. If you check your Xorg log, you should see the output of your program.

---

