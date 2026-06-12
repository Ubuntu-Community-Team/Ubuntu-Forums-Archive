---
title: "[SOLVED] Finding Installed Programs"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by NJ0E on 2008-08-11
Hekllo all,

My problem -- I have Hardy Heron installed and running.  Have installd some programs/packages thru Synaptics.  I marked them for install and applied.  Where did they go?  I would like to use them but I looked in my Applications tab no no avail.  I also checked System -> Preferences and Administration.  No programs there either.  Where od I look for these programs.

Or,  how can I set up a launcher for them?  

Thanks,

Joe

---

### Post by Ryadt on 2008-08-11
You can launch them in the terminal or do ALT+F2.

---

### Post by bobnutfield on 2008-08-11
Try typing the name of the program in a terminal.  If it launches the program, you can create a menu entry for it or a launcher from your panel.  Installed programs are usually installed to /bin, /usr/bin or /sbin.  But locate your program by typing in a terminal either:

> whereis <nameofprogram>

or:

> which <nameofprogram

If it is installed into a directory in your path (it usually is), it will tell you where it is.

---

### Post by unutbu on 2008-08-11
The command
```

dpkg --listfiles PACKAGE
```

will list all the files installed by the package named PACKAGE.
Usually, the executable will be installed in a directory called bin, so if you run
```

dpkg --listfiles PACKAGE | grep bin
```

it will usually print the path to the executable. Once you know the path to the executable, you should be able to set up a menu item or a launcher for it:

To make a menu item:

[list]
[*]Click System>Preferences>Main Menu.
[*]Click the Menu in the left panel to select the appropriate submen you desire.
[*]Then click +New Item. 
[*]A dialog box will appear asking for Name, Command and Comment. 
You can set the name to anything you like
Set the Command to the path to the executable. 
Comment can be left blank, or be anything you like.
[/list]

To make a launcher:

[list]
[*]Right click on the background root window of your screen (anywhere there is no application window).  
[*]Select "Create launcher...". The same dialog box will pop up. Enter the info in the same way as above.
[/list]

If the above commands do not reveal the executables, post the name of the package(s) and we'll puzzle it out from there.

---

### Post by lapubell on 2008-08-11
sometimes the name of the executable file isn't always clear.  Whenever I can't find a program, I go back to Synaptic after I install it, right click on the program and click Properties.  Then I go to the installed files and it will list out all the files it installed.

The one that launches the program is (usually) /usr/bin/NAME_OF_PROGRAM

---

### Post by Flyingjester on 2008-08-11
> **lapubell said:**
> sometimes the name of the executable file isn't always clear.  Whenever I can't find a program, I go back to Synaptic after I install it, right click on the program and click Properties.  Then I go to the installed files and it will list out all the files it installed.

The one that launches the program is (usually) /usr/bin/NAME_OF_PROGRAM

+1 probably one of the easiest ways to find the command.

---

### Post by NJ0E on 2008-08-11
Thanks to every one that gave advise...  found one of the programs that I was looking for.  Will be getting a book soon, just trying to unlearn windows and learn unix/ubuntu!!

Again
Thanks

Joe

---

