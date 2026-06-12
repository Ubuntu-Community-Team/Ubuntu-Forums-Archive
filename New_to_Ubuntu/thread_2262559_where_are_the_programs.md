---
title: "where are the programs?"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by dwood2 on 2015-01-25
I'd like to know how to find the path for the executable files for applications. Sometimes I have to tell a program where to look for the application to run a file.  The PDF viewer needs to know where Okular is so that I can use Okular instead. Also, It would be nice to setup Okular as the default viewer. How do I setup default programs?

---

### Post by whitesmith on 2015-01-25
First of all, why do you need to know the path to the executable? Most programs put an icon (Winspeak=shortcut -- Linuxspeak=launcher) that executes the program, so knowing the path to the underlying application is superfluous. Of course, you **could** be writing a shell script to manipulate that executable in some way, so here is the answer to your question. Open a Terminal (Winspeak=command line). Then:```
which name_of_program
```Be sure to observe Linux' case rules. Happy searching!

---

### Post by deadflowr on 2015-01-25
most application's executables are in /usr/bin.
(Though not all)

You can usually reset file-types to open with a certain program by changing the xdg-mime setting for the file-type.
But an easier way is to simply right click on the file and in properties it should have a OPen with tab.
You then select the program you want to use, if available, and then mark it set as default.

Of course, I assume you mean for vanilla Ubuntu and not another flavor like KUbuntu or Xubuntu...

---

