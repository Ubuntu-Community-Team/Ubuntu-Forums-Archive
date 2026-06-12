---
title: "keyboard layout"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by ellii on 2012-03-03
hi , I've installed KDE on my Ubuntu and i also had gnome 3.2 on that user !
so i had some problem and then I've totally removed Kde , when i log in to Ubunto(+gnome 3.2 ) I have problem with Persian layout .I've checked layout and saw that both English and Persian is already installed and then i use too choose Persian from tray but every time i choose that it changes to English immediatly and when i click on "show keyboard layout " it gives me this error :
execution of "gkbd-keyboard-layout" failed . command not found 
I've tried to install that but another error :
E: Unable to locate package gkbd-keyboard-display
I've relodaed synaptic package manager and also use command ```
"sudo apt-get update " 
``` but still i encounter above error when i wanna download that .
now I have no Persian layout or I have but i can't use that !
what should i do ?

---

### Post by ellii on 2012-03-03
Oh,I've solved my problem by this way :
first :
sudo apt-get install gkbd-capplet
and then i removed Persian layout and installed it again !
both of my problems has been solved

---

