---
title: "Running program after compilation"
date: 2009-10-28
forum: Packaging and Compiling Programs
---

### Post by needeffexor on 2009-10-28
I built a Gtkmm project with Anjuta IDE, and am having a little difficulty installing it in Ubuntu.  I am certain that the solution is simple, but I can't seem to figure out what I am doing wrong.  
This is my first project targeted for Ubuntu.  It is a simple utility that won't need a .deb for distribution. After running 'make install' the program is saved in /usr/local/bin.  From the console, I can cd to /usr/local and run ./program, and the program runs fine; however, I cannot get the program to run using alt+F2 or a launcher.

I have tried to make a script that runs the program, and am successful from shell.

Thanks in advance for any assistance you can offer.

---

### Post by dinxter on 2009-10-29
What happens when your run from alt-f2? you could try checking the run in terminal checkbox and setting the terminal to not close after execution (profile-preferences->Title & Command if using gnome-terminal).

---

### Post by bribera on 2009-10-29
It seems unlikely, but could you have removed /usr/local/bin from your $PATH?

---

### Post by needeffexor on 2009-10-29
Thank you dinxter for your reply.  If I keep the terminal up, the program terminates by throwing a Glib::FileError exception.  Apparently, the program cannot load the glade file.  I haven't figured out why yet.  If I run '/usr/local/bin/program' from command-line it works but running '/usr/local/bin/program' from alt+f2 does not. I will keep trying.

Thanks again. 

> **dinxter said:**
> What happens when your run from alt-f2? you could try checking the run in terminal checkbox and setting the terminal to not close after execution (profile-preferences->Title & Command if using gnome-terminal).

---

### Post by Anonymousable on 2009-10-31
It looks like the paths are messed up. You haven't got the right working directory, but your program is looking for the glade file in the working directory (probably your home folder).

This can only be fixed by cd'ing to the correct folder manually before running the program (cd /usr/local/; ./program ) or adding in a line of code that chdir's to the correct folder automatically, as far as I know.

Don't trust me all the way, wait for someone else to reply confirming what I've said first please, as I am NOT entirely sure. Shouldn't do damage trying what I said though ;)

---

### Post by needeffexor on 2009-11-08
This was just a noob error on my part.  I didn't anticipate the problems of relative paths to the resources in the code.

Once I used the full path to the glade file in the source code, everything works great!

Thanks everyone.

---

