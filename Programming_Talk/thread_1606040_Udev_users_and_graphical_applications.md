---
title: "Udev users and graphical applications"
date: 2010-10-26
forum: Programming Talk
---

### Post by nowardev on 2010-10-26
Hi 
i have made my own udev rules to automount nokia 5800
but ... when i  do ...

 RUN+="/bin/myscript"

it's root that run the script... so $HOME is the root home and so on 

basically i would like syncronize my nokia like normal user ...without typing any password ... 


another issue .. 
udev doesn't run graphical applications like zenity or kdialog ...

so i have find out this 


xhost + 
export DISPLAY=:0 

kdialog --textinputbox "Continue or cancel?" 

but i can't get it working fine.

^^ help :P

---

