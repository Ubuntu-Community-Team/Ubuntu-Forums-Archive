---
title: "make python script run like normal program"
date: 2011-10-06
forum: Packaging and Compiling Programs
---

### Post by proxy.qtz on 2011-10-06
How can I get my python script to show up with other applications in the unity interface? I also want to know how to assign it an icon that will work in the unity sidebar.

---

### Post by Tony Flury on 2011-10-06
is it a program that has a GUI ?
If not you will need to create a launcher that opens a terminal window and run your python script in that.

To run your python script as an executable - do the following 

1) at the top of the script add the line 
```

#! /usr/bin/env python

```
This instructs the kernel that the rest of the script should be run using the python interpreter

2) make sure the script is executable
```

chmod +x <myscript>

```

3) if you want to run your script from anywhere regardless of which directory you are currently in : add the directory to your PATH
```

PATH=$PATH:<my directory with the script>

```

If you want to make that change system wide - i.e. for all users ..

[https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables](https://help.ubuntu.com/community/EnvironmentVariables#System-wide%20environment%20variables)

---

### Post by Pynalysis on 2011-10-06
> **tony flury said:**
> is it a program that has a gui ?
If not you will need to create a launcher that opens a terminal window and run your python script in that.

To run your python script as an executable - do the following 

1) at the top of the script add the line 
```

#! /usr/bin/env python

```
this instructs the kernel that the rest of the script should be run using the python interpreter

2) make sure the script is executable
```

chmod +x <myscript>

```

3) if you want to run your script from anywhere regardless of which directory you are currently in : Add the directory to your path
```

path=$path:<my directory with the script>

```

if you want to make that change system wide - i.e. For all users ..

[https://help.ubuntu.com/community/environmentvariables#system-wide%20environment%20variables](https://help.ubuntu.com/community/environmentvariables#system-wide%20environment%20variables)

+1 :)

---

### Post by MG&amp;TL on 2011-10-07
I think, as well, the OP may mean that he/she wants to be able to install his/her program and have it show up with a logo like the many professional-looking programs around, e.g. firefox, libreoffice.

You will need to make a .desktop file for your program, it isn't too technical. [http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

However, this guide does need to be worked through slowly.

Secondly (and as a sideline) if you're going to that effort, you may want to consider making a debian package as well (double-click program build/install)
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)

This IS quite technical and can be very tricky.


IT does work, though, I've tried it myself. ;)

Have fun, whatever you end up doing. :)

---

### Post by bspymaster on 2011-10-07
> **Tony Flury said:**
> is it a program that has a GUI ?


Hello, I'm on the dev. team for this project with proxy.qtz, and yes, there is a GUI involved. We are using Tkinter, although knowing how to create a terminal-application is something good to know as well. Thank you MG&TL, for the link on .deb packaging. That should be useful as well.

---

