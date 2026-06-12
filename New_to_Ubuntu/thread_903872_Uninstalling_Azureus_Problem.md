---
title: "Uninstalling Azureus Problem"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by h2c4life on 2008-08-28
I recently installed Azureus using this guide here:
[http://ubuntuforums.org/showthread.php?t=144546&highlight=uninstall&page=18](http://ubuntuforums.org/showthread.php?t=144546&highlight=uninstall&page=18)
I was wondering if someone could guide me through uninstalling this application. 
Thanks

---

### Post by Crafty Kisses on 2008-08-28
Have you tried?
```
sudo apt-get remove azureus
```

---

### Post by h2c4life on 2008-08-28
im trying to completely remove azureus...im not sure if thats right
thanks anways

Edit: I basically removed the folder vuze from /opt
and removed Azureus and Azureus.destop from /usr/share/applications/
I hope that fixed it...can anyone confirm this? 
Thanks

---

### Post by lovinglinux on 2008-08-28
> **h2c4life said:**
> im trying to completely remove azureus...im not sure if thats right
thanks anways

Edit: I basically removed the folder vuze from /opt
and removed Azureus and Azureus.destop from /usr/share/applications/
I hope that fixed it...can anyone confirm this? 
Thanks

I don't think this is the proper way of removing it. Go to System > Administration > Synaptic Package Manager, then inside synaptic use the search feature to look for "azureus".

Once you find the azureus package inside Synaptic, click over it with the right mouse button and select "Mark for Complete Removal". Then in the toolbar click "Apply" button and follow the instructions.

If you are looking for a good and relatively simple torrent application, try Deluge. Deluge is a very complete torrent app, without the useless Vuze features and complicated configurations.You can get it from the Ubuntu Repositories. Symply go to Applications > Add/Remove then select the option "All Open source applications next to "Show:" and type "deluge" in the search box. When showed, select the Deluge box from the application list and hit "Apply Changes" button.

 If you are looking for a Vuze-like applet try Miro.

PS: I loved Azureus for some time while running my Windows box, but every new version they add more and more features that I don't need and make it more and more bloated.

---

