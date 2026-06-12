---
title: "Program Launching"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by gordon99 on 2014-07-04
I am trying to create a  launch shortcut, on the Ubuntu 14.04 desktop,for a bridge scoring program.
I started by typing in Terminal "sudo apt-get install --no-install-recommends gnome-panel". I then typed "gnome-desktop-item-edit ~/Desktop/ --create-new".
This brought up a window asking for the program name and command.
I am able to launch the program in Terminal by typing "cd kbs && cd club && perl ../kbs.pl". However, this command will not work when I put it in the window where the command is required. When I click on the desktop icon an error message appears.
Could someone please suggest the command syntax I should be using to create a shortcut to the program?

---

### Post by whitesmith on 2014-07-04
You'll find what you need at [http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04](http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04). Cheers!

---

### Post by gordon99 on 2014-07-04
I have no trouble getting, what seems to be referred to as, the GUI app. It is the command line requirement within the GUI app which is giving me grief.

---

### Post by gordon99 on 2014-07-06
Still having no luck. As I said in my first note, the terminal command " cd kbs && cd club && perl ../kbs.pl" launches the program ok. But that command will not work, it seems, when I transfer it to desktop program launchers. The kbs folder is in my home directory. Might 'perl' be the problem?

---

### Post by mooreted on 2014-07-06
Create a bash script to perform the commands and use the desktop file launcher to point to that script"

#! /bin/bash
" cd kbs && cd club && perl ../kbs.pl"

You could create that in Gedit and save it as something like "kbs.sh". Then open a terminal and make the script executable:

chmod +x kbs.sh

---

### Post by gordon99 on 2014-07-07
mooreted et al, I wish I new what the problem is but I have tried every alternative that has been suggested without success. There must be a way to transfer a command that works in terminal into a desktop shortcut that a beginner can follow without screwing up.

---

### Post by JeQhdMD on 2014-07-07
Ok  - here are a couple "assumptions",

>  you're not running Unity desktop on standard Ubuntu, as it's drop-dead easy to create a shortcut (aka launcher icon) in Unity that will start any gui application,
>  it's also easy to create a panel launcher in standard Gnome 2x or Mate (don't know about Gnome 3x) that will also do the same thing,

If you like, you can go to your file manager, and right-click on the saved script, and make it executable via the properties dialog . . .

---

### Post by deadflowr on 2014-07-07
Is changing the directory twice necessary?
Have you tried running it fullpath.
perl /home/me/kbs/club/kbs.pl
(me being, you/your username.)

You might also think about posting the .desktop file's output for further analysis.

---

