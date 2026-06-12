---
title: "change desk top"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by jaxom98 on 2014-03-15
OS Edubuntu 12.04
I followed instructions on how to change my desktop. Having tried it I want to try others, but the instructions don't work now. It brings up a different window. The current desk top is xfce. There is no "system settings" entry in the menu.Can anyone help me unjam things?

---

### Post by bapoumba on 2014-03-15
Which instructions did you follow ? Could you please give a link or detailed instructions ? Thanks.

---

### Post by iLikeIt on 2014-03-15
link of the instructions please ?

---

### Post by evan8 on 2014-03-15
Usually with xfce you just right click and you will see desktop settings

---

### Post by jaxom98 on 2014-03-16
The instructions were verbal.  I wrote down the instructions : right click on desktop . In window select "change desktop" and click,  scroll through options and click on your choice (in this case lxde).  
The trouble is in lxde the right click takes you to a slightly different window that fails to give the option "change desktop" it only give options to adjust lxde. I want to try another desktop , not be confined to lxde.
The OS is edubuntu 12.04.1

---

### Post by bapoumba on 2014-03-16
Do not you have the options to choose from at login ?

---

### Post by Odyssey1942 on 2014-03-16
i think that the "options" that bapoumba refers to can be found by clicking on the little logo just above and to the right of where you enter your password. (Do this before entering pw)

Edit: BTW, are you interested in the desktop similar to the one that was in 10.04 (I think it is called Gnome 2)? If so, I can find and supply the code.

---

### Post by jaxom98 on 2014-03-19
Excuse the delay replying, work went crazy.
Odyssey1942, that is **exactly** the info that I needed.The "footprint" logo meant nothing to me, so I never tried it.  Unstuck and merrily experimenting . Many thanks.
bapoumba, until I read Odyssey1942 I didn't understand what you meant. thank you for your time

---

### Post by Odyssey1942 on 2014-03-19
Try this (has worked for me on 5 different computers) in terminal:

```
sudo apt-get install gnome-session-fallback
```

You will then need to restart. When the login screen comes up, click on the little logo top right above the pw box, choose something like ("use gnome desktop", sorry cannot remember exactly, but you can try all the options to see which works best for you.) Then enter password, etc.

If this does not work, post here. If I do not answer, PM me.

---

### Post by jaxom98 on 2014-03-28
"sudo" instruction did not install, as current Gnome is already installed. 
I have made a note of the sudo instruction for future referance.
As it turns out gnome works best for me.

---

### Post by bapoumba on 2014-03-29
> **jaxom98 said:**
> 
Odyssey1942, that is **exactly** the info that I needed.The "footprint" logo meant nothing to me, so I never tried it.
The "footprint" is a swallow :)

> **jaxom98 said:**
> "sudo" instruction did not install, as current Gnome is already installed. 
I have made a note of the sudo instruction for future referance.
As it turns out gnome works best for me.
Please have a look here : [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware), and here for apt-get : [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Thanks much Odyssey1942 :)

---

