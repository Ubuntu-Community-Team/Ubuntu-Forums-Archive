---
title: "Missing &lt;alsa/asoundlib.h&gt; library"
date: 2010-10-22
forum: Programming Talk
---

### Post by alejandro910 on 2010-10-22
[FONT=Arial]Hi,
I want to compile and execute the code of this link: [http://www.linuxjournal.com/article/6735?page=0,1](http://www.linuxjournal.com/article/6735?page=0,1) to record sound in real time from a jack,but the library 
[/FONT][FONT=Arial]<alsa/asoundlib.h> is missing and i can't find it.It says that i can add the option -lasound on the
linker command and i did it but it doesn't work.
I would appreciate it a lot if you could help me.
Thanks[/FONT]

---

### Post by Zugzwang on 2010-10-22
Dear OP (original poster),

You have ran into the problem that some files are missing on your system. This can be seen more or less directly from the error message. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.

---

### Post by Asoka2 on 2012-09-09
Thank you for the post Zugzwang; it fixed my problem, and is a good thing to know for future ones.

---

