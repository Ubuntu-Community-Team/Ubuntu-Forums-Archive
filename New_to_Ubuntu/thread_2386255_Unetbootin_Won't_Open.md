---
title: "Unetbootin Won't Open"
date: 2018-03-02
forum: New to Ubuntu
---

### Post by jeche on 2018-03-02
I've just installed ubuntu 17.10 and I'm having problems with Unetbootin. I installed the program in the software center, when I clicked launch I received a popup message saying "failed to run /usr/bin/unetbootin rootcheck=no unable to copy the users Xauthorization file". After doing a little research I attempted a solution by opening the terminal and entering "touch .Xauthority". Now when I try to open Unetbootin I'm asked for my password but after I enter it nothing happens. I'm at a loss for what to do any help would be much appreciated.

---

### Post by ajgreeny on 2018-03-03
This may be as a result of a feature (not a bug according to the devs) of wayland which has taken over the graphics in 17.10 from xorg, and does not allow GUI apps to run as root.

There are two possible options to overcome this.
[LIST=1]
[*]At the login screen choose xorg instead of wayland ( can't remember if wayland is even mentioned, but xorg certainly is).
[*]If you login to the wayland session run command ```
xhost si:localuser:root
``` and after that using root GUI applications should work for that session.
[/LIST]
See [https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w) for a lot more info on this.
The next Ubuntu version, 18.04-LTS will not be using wayland as default as it has been agreed that it is not yet ready for general use, particularly in a LTS version of Ubuntu.

---

