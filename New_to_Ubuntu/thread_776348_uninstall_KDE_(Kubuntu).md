---
title: "uninstall KDE (Kubuntu)"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Mosaab on 2008-04-30
I had ubuntu installed in my system (7.10) then I installed the KDE so it became kubuntu, then I upgraded ubuntu to 8.04,  I now want to uninstall the KDE and all its dependencies & packages ... how can I do that ... ? I want only ubuntu and the packages that came with it.

thanks

---

### Post by dangerpl on 2008-04-30
Synaptics?

---

### Post by smoker on 2008-04-30
> sudo aptitude remove kubuntu-desktop

also, have a look here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Mosaab on 2008-04-30
That made some uninstall process, but all the KDE packages is still there and KDE session is still there when I restart!

---

### Post by smoker on 2008-04-30
do you have kde applictions installed, they may need certain packages to operate?

---

### Post by Mosaab on 2008-04-30
ok, at least I want all the packages that came with KDE to be uninstalled !
because that command you gave me, didnt actually do anything! every thing is still there. the KDE & the konquerer for example ... and alot of packages that their names start with kde.

---

### Post by smoker on 2008-04-30
hi, it was years ago since i tried that, and can't remember any problems, were you logged out of a kde session when you tried the command, ie, gnome, or terminal session? if not, perhaps try that.

best of luck


Have a look at this thread: [http://ubuntuforums.org/archive/index.php/t-503151.html](http://ubuntuforums.org/archive/index.php/t-503151.html)

i haven't used the   'sudo apt-get autoremove  --purge kde-desktop'  command mentioned in the thread, so am not comfortable recommending it. perhaps read the full thread and decide for yourself,

---

### Post by Mosaab on 2008-04-30
actually I was logged in Gnome when I did that, but thank you anyway , I will take a look at the link and come back to you.

---

### Post by Mosaab on 2008-04-30
I found a huge command in the site you gave me ([http://ubuntuforums.org/archive/index.php/t-503151.html](http://ubuntuforums.org/archive/index.php/t-503151.html)) under remove kubuntu section, and I pasted it in the terminal. it seems that it removes all the kde packages one by one, and it worked fine ..  
Thank you very much :)

---

### Post by smoker on 2008-04-30
glad to help:-)

---

