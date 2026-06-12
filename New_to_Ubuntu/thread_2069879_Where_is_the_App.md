---
title: "Where is the App?"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by garymansperger on 2012-10-11
I have installed an application. Software Center tells me it is installed and will let me reinstall it. However I can not find it to run the app.
Where is it? I have looked at all the obvious places not on the launch bar, not in the software center under installed apps).
Thanks,
Gary

---

### Post by whatthefunk on 2012-10-11
What app is it?  Try running it from command line.

---

### Post by deadflowr on 2012-10-11
There are two kinds of applications used in Ubuntu, graphical, and command line.
To find the graphical apps, either click on the icon at the very top of the launcher(the panel with icons on the left side of the screen), or press the windows(super key on your keyboard. This icon is the dash, which is the pseudo menu program for Ubuntu. Once the dash is open either type the name of the app, or at the bottom of the dash screen, you'll see several icons, like a house and document, and so forth. Those switch between different types of application and files and folder in your system. Find the application click it and go through the look for installed(programs are listed alphabetically.
Unfortunately, command line apps are not list in the dash. So to find them, you'll need to open a terminal, press ctrl+T to open a terminal, then type the name of the program.

---

### Post by garymansperger on 2012-10-11
I think the problem is that the app is actually a service (in windows anyway). It should have started when loaded. To access the service I go to localhoast (I use the IP) with a given port address. As this does not work, I think the service is not started.
Possibly I should have asked, how do I see what services are running or how do I start one?
 
I did do as you sugessted and could not find it. The app is called "AirControl" from ubnt.com and is a monitor for a network of wireless radios. I had it running last week with no problems, but do to another problem had to reinstall UBUNTU and now have this problem.

---

### Post by Frogs Hair on 2012-10-11
Are you using 12.04 ? I am on 12.10 and it is not in the software center. I located the web site and it is supposed to have a GUI and I see they have a .deb package also . Is that what you installed ?  [http://forum.ubnt.com/showpost.php?p=177840&postcount=1](http://forum.ubnt.com/showpost.php?p=177840&postcount=1)

---

### Post by grahammechanical on 2012-10-11
You can use System Monitor. It has a processes tab. And then there is the command

```
top
```

Type that in a terminal and it will show the processes that are running.

Regards.

---

