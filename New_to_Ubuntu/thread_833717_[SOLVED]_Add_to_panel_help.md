---
title: "[SOLVED] Add to panel help"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Sim777 on 2008-06-18
I'm trying to create a launch button for Firefox3.  
But running into a problem. I have FF2 installed and when I type 'firefox' in terminal, it opens up FF2. 

FF3 is extracted into a folder and requires "./firefox" command to run it within /home/sim777/firefox folder 

unfortunately, no combination of commands run FF3.

My goal is to push a button that will open FF3.  

Thanks.

---

### Post by Duck2006 on 2008-06-18
Go to Applications and find where ff3 is (i think it's under Internet) right click on the icon and click on add to panel.

---

### Post by Sim777 on 2008-06-18
> **Duck2006 said:**
> Go to Applications and find where ff3 is (i think it's under Internet) right click on the icon and click on add to panel.

FF3 is not installed. It is just extracted from tar.

---

### Post by pawnrocket on 2008-06-18
Is it a .deb or source?

---

### Post by cmay on 2008-06-18
hi there.
you can use the add to panel .
its on the panel it selve .
there your can add a new shortcut to an existing program of your own choice
from add from menu .

i guess it should work that way.

---

### Post by Duck2006 on 2008-06-18
If you havn't installed it yet get the *.deb download from the ff site, and right click on it and install, then you can add it to the panel.

---

### Post by pawnrocket on 2008-06-18
yeah what duck said... :idea:

---

### Post by Sim777 on 2008-06-18
> **pawnrocket said:**
> Is it a .deb or source?


neither. It's a folder.     home/username/firefox/

---

### Post by pawnrocket on 2008-06-18
what is inside the folder? 

Stuff like "MAKE" and a bunch of text files? 

If the .deb isn't there go back and download the ubuntu binary.deb 

if there isn't one and you downloaded the sources then you will have to follow the instructions to install. 

I will go look on their site and see what is there.

---

### Post by Happy_Man on 2008-06-18
Cool, here's what you do. Instead of doing just ```
firefox
```, enter ```
/home/sim777/firefox/firefox
```. Then it should work just fine.

---

### Post by Sim777 on 2008-06-18
> **Happy_Man said:**
> Cool, here's what you do. Instead of doing just ```
firefox
```, enter ```
/home/sim777/firefox/firefox
```. Then it should work just fine.

Thanks. exactly what I was looking for. 

I was making things a bit too complicated....

---

