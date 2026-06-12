---
title: "Nautilus not working anymore"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Troca on 2008-06-10
I dont know what i done more then applying the automatic updates today. well i installed wine aswell but now nautilus dosent work anymore 

when i type sudo nautilus i get 

seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

and it dosent start 

and dvd burning also screwed up i use to have cool icon that showed my progress in avant but when i tryed to drag stuff to a blank dvd and click burn it didnt work so i started brasero made it my default burning program restarted the comp now i can burn but the icon is messed up just a white square that dosent show the progress.

any help would be gr8 thank

---

### Post by gr4nf on 2008-06-10
try re-installing nautilus:
```

sudo apt-get remove nautilus
sudo apt-get install nautilus

```

---

### Post by Troca on 2008-06-10
still get the same error :(

---

### Post by gr4nf on 2008-06-10
what happens when you simply open a folder form the desktop? does it not allow you to do so?

also, you could try the same reinstall process for your dvd burner too.

---

### Post by Troca on 2008-06-10
i spoke to soon i restarted now after the reinstall and its working thank you very very mutch :) 

dont know the name of the "default" dvd burner program you know the one that u just dubbel click the empty dvd drag and drop files to it (it dosent actualy start a program so to say)

and right now i dont have the Burn it button there anymore eather any idea how to get that back ?

---

### Post by Troca on 2008-06-10
bah and it stoped working again same error.... i hate trubel shooting linux sens i dont know what could be the problem :(

---

### Post by darbid on 2008-06-11
Hello, I am having exactly the same problem

[http://ubuntuforums.org/showthread.php?t=819480]("http://ubuntuforums.org/showthread.php?t=819480")

---

### Post by pigphish on 2008-06-11
turned out to be my fault. I uninstalled evolution. 

Installing ubuntu-desktop package fixed the issue for me. 

sudo apt-get remove ubuntu-desktop 
sudo apt-get install ubuntu-desktop 

(I only needed to do the install as i already uninstalled it)

also ran:

sudo apt-get update
sudo apt-get upgrade

hope this helps.

---

### Post by peterthewolf on 2008-06-12
I too had this segmentation problem. Was not prepared to waste time hunting such a basic fault. So stopped using nautilus and used thunar instead. Install thunar via synaptic the sudo thunar.

---

