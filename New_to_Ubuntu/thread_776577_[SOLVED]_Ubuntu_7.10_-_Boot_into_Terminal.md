---
title: "[SOLVED] Ubuntu 7.10 - Boot into Terminal?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-04-30
I have installed Ubuntu 7.10 on my computer and dual-booted with XP. Now, when I go to boot into Ubuntu, my monitor will turn off or go to stand-by. I than hit Ctrl + Alt + F1 and I am at the login screen.. only it is the terminal. How do I boot to the Desktop instead of the terminal?

Also, if needs be, would it be easier to just install Ubuntu or Kubuntu KDE with Wubi? If so, how would I go at wiping away Ubuntu from my system without killing XP? Thanks for the help.

---

### Post by garyedwardjohnston on 2008-04-30
Use windows to format the Ubuntu partition, then extend your windows partition, then install Ubuntu via Wubi

---

### Post by jimv on 2008-04-30
What kind of video card are you using?


And try this and see if it gives you any errors

Press control+alt+f1 to get to the command line
Log in
Type:

sudo killall gdm
sudo killall x-session-manager
sudo killall Xorg

THEN type:

startx

That will attempt to start the GUI, and should give an error if it fails.

---

