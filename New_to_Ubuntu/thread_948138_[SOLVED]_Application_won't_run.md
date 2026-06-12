---
title: "[SOLVED] Application won't run"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-14
I downloaded FrostWire, and I'm pretty sure I installed it correctly, but when I click on it under applications, it simply doesn't run. It's there, but it won't run.

Can anyone tell me how to fix this?

---

### Post by Mister.Vash on 2008-10-14
open up gnome-terminal and run it from there.  You can possible see an exit code or error running it that way. 

If you are not sure where it is installed, your can right click on your Application Menu, select Edit Menus.  Then find the application, right click, then choose properties.  The dialog will show you the path to the program and any options being passed to it.  Just run that in gnome-terminal and see what happens, you might get an error that you can fix yourself, or you may need to post the error.

---

### Post by Haruki-kun on 2008-10-14
Alright, the error is as shows:

/usr/bin/frostwir

Starting FrostWire...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

What does this mean?

---

### Post by trikster_x on 2008-10-14
I had the exact same problem when I first installed frostwire.  The problem for me was that two versions of java were installed on my OS.  Open system--administration--synaptic package manager and do a search for java.  You'll come up with a big list, but concentrate on packages that start with java.  Now look at packages named sun-java.  If there are packages selected from both java programs, you have to pick just one to use.  Personally I use sun-java.

---

### Post by trikster_x on 2008-10-14
Okay, with your new post I think you might need to install the newest versions of java.  Or just uninstall your current java program via synaptic and install sun-java through synaptic.

---

### Post by Haruki-kun on 2008-10-14
But how does one do that?

---

### Post by trikster_x on 2008-10-15
Go to your system menu, then to administration, then to synaptic package manager.  Click the status button and select installed.  Now you have a list of all the installed packages on your computer.  Scroll down to find java.  if you have anything other than java commons installed, mark them for removal.  Now go back to all and search for sun java.  You will need to mark sun-java6-bin and sun-java6-jre for installation as well as any accompanying packages.  Now check open-jdk.  Check this for install as well.  Click on the apply button, and it should automatically download the packages.  Now hopefully frostwire will start.

Edit:  OK, just checked the package for FrostWire. All you really need to do is open synaptic package manager and install the sun-java6 packages I mentioned before.  According to the package information, FrostWire will not work without it.

---

### Post by SunnyRabbiera on 2008-10-15
yeh removing the openjdk packages will probably help you out.

---

### Post by Haruki-kun on 2008-10-15
Alright, I tried it out and it got the application running.

Sadly, it opens up a blank window. Am I missing something?

---

### Post by trikster_x on 2008-10-15
Does the FrostWire splash screen appear when you start it at all?

If not, then try removing Frostwire through synaptic, then open a terminal and type this command:

sudo apt-get install frostwire

This will reinstall through the repositories.  You can just copy/paste into the terminal window.

---

### Post by forger on 2008-10-15
Choose the correct java:
```

sudo apt-get install sun-java6-jre
sudo update-alternatives --config java

```

---

### Post by Haruki-kun on 2008-10-15
It worked! Thanks a lot, guys! :)

---

