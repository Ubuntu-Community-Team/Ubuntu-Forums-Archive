---
title: "[SOLVED] shutting down Ubuntu from Terminal without Root prvileges"
date: 2007-09-30
forum: Programming Talk
---

### Post by Balazs_noob on 2007-09-30
Hi guys 
i am searching for a way to shuttdown Ubuntu with a Terminal command without root priviliges and without editing any text files because i am writeing a Java shuttdown app that i want to work on Ubuntu too , i already found the XP solution.

sorry for my english 

Thx guys...

---

### Post by mssever on 2007-09-30
That isn't possible unless you tweak the Linux system. One way to do that would be to make /sbin/shutdown setuid. You'd have to do this as root, and there would be a number of security issues you'd need to be aware of.

---

### Post by Balazs_noob on 2007-09-30
yeah i found the same :(

because the pourpose of the app would have
been to shuttdown the computer when the user 
can not be there.....

looks like my app will only work on XP :S

Thanks any way :)


U.I. i just wonder what command does the system give
when it shuttsdown when i Press the red button because
then it dosn't ask for a password :P

---

### Post by slavik on 2007-09-30
there is no command, the kernel/acpi detects the power button press (acpi kernel module is running in kernel space, ie: has root access).

---

### Post by Acglaphotis on 2007-09-30
> **slavik said:**
> there is no command, the kernel/acpi detects the power button press (acpi kernel module is running in kernel space, ie: has root access).

He means the red button on the top-left corner.

The gui is running as root. If you do startx as a normal user, you wont be able to shutdown via the GUI.

---

### Post by mssever on 2007-09-30
> **Balazs_noob said:**
> because the pourpose of the app would have
been to shuttdown the computer when the user 
can not be there.....

looks like my app will only work on XP :S
Another option would be to separate the part of your program that does the actual shutdown into a separate program, VERY CAREFULLY audit it for security, then run just that program setuid root. The key would be to have the absolute minimum possible in the setuid program, as long as it had the necessary logic to ensure that it was only invoked in an approved manner.

---

### Post by slavik on 2007-09-30
actually, you could have a daemon running as root (started on bootup) and then have a userspace app communicate via a named pipe :) no setuid needed. :)

---

### Post by Balazs_noob on 2007-09-30
Thanks guys for your input :)

i find slavik's solution easier to do , but again the problem is that for this to work you have to  download the deamon seperatly and add it as a Startup program.

So my main goal is that the only dependecy for the program is the java JRE...

is there any way to ask for the password when the app starts and make the app enter it when nedded?? ( i know i know security hole :) ) 

thanks again guys for everything :popcorn:

---

### Post by ssam on 2007-09-30
if i understand right
gdm runs as root.
all of gnome is running as normal user.
gnome can tell gdm to shut down the computer.

there ought to be a way that any user program can talk to gdm, or at least tell gnome to tell gdm to shutdown.

---

### Post by jpkotta on 2007-09-30
[http://fvwmwiki.bu-web.de/Tips/DisplayManagerCommands](http://fvwmwiki.bu-web.de/Tips/DisplayManagerCommands)

Look at the lines that start with "+ I Exec", they give commands to display managers (gdm or kdm) that will do what you want.

---

### Post by mssever on 2007-09-30
> **Balazs_noob said:**
> i find slavik's solution easier to do , but again the problem is that for this to work you have to  download the deamon seperatly and add it as a Startup program.Just make your installer install an init script to start the daemon (or use Ubuntu's new Upstart init system). No dependency needed.
> is there any way to ask for the password when the app starts and make the app enter it when nedded?? ( i know i know security hole :) )
Run your app as root. (Start up using either gksudo if it's a GUI or sudo if it's CLI.)

---

### Post by Balazs_noob on 2007-10-01
Thanks guys i think with all this info i can accomplish my task :)
 of course after my university exams :(

thanks again :)

u.i : i mark the thread as solved

---

### Post by BUGabundo on 2007-10-02
> **mssever said:**
> Run your app as root. (Start up using either gksudo if it's a GUI or sudo if it's CLI.)

thats the worse solution. thats the main prob of all windows apps. they like to run as root, when they shouldnt need it

---

