---
title: "Hagen Printers Management System on Ubuntu"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by kpaulsen2 on 2014-02-24
We run a very  old version Hagen Print Management system at our company.
The server is accessed via a windows client emulator with a target path to the server.
Target in Windows is set by right clicking the program shortcut (has to be an alias or shortcut) and going into Properties/Shortcut where the Target path is located.
Proper path is entered and then the emulator client accesses the server for employee job login via department and assigned employee number.

I have installed wine, checked the box on allow executing the file as program but get an error after it opens up, access denied to COM1.
As the target path is not set to the server it obviously can't make the connection.
Path looks like this on my windows box, C:\hagen\emulator.exe -h10.0.0.1
With the obvious path to the emulator program and then the connection to the Hagen server IP.

Question is how do I change the target path, I don't see the option like I do in windows via properties tab.

Thanks

---

### Post by kpaulsen2 on 2014-02-27
Okay, I am going a different route. Instead of using wine I am using a native linux app called Putty.
Program boots up just fine, I have entered my IP address and port and telnet setup.

I get past my first two steps and then it crashes stating...
 
setup error cannot open terminal library file.

Any idea what that means?

---

