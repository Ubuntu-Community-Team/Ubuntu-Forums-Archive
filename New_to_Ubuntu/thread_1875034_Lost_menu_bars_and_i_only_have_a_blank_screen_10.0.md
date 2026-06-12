---
title: "Lost menu bars and i only have a blank screen 10.04"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Peterfc on 2011-11-04
Hi All

I am in Portugal and my son has a problem in the UK we are in touch via my Skype and he on Skype on Iphone. 

He has lost his screen, the only things he has are picture on his screen. I asked him to try F11 and nothing happened. He moved something to his Trash and when asked he said yes. what i think is he may of dragged his desktop to the trash. 

Thanks for taking the time to read this post

---

### Post by bokgeneraal on 2011-11-04
It seems to me that Desktop is just a folder. If that's the case maybe one can just open a terminal and create one using : " mkdir Desktop " .
If the panel is just deleted then one can create a new one by right clicking the mouse and selecting new panel.

---

### Post by Peterfc on 2011-11-04
Hi Bokgeneraal

Thanks for your reply.

The problem is that there is nothing to open to allow access to the Terminal. The desktop only has a couple of folders with docs in them the rest of the screen is just Ubuntu Purple.

---

### Post by bokgeneraal on 2011-11-07
Have you tried using the virtual consoles i.e alt+ctrl-f3 to f5 . They are always there. To get back to desktop press alt-f7.

---

### Post by blade4 on 2011-11-07
The terminal can be opened with the shortcut : ctrl+alt+t . It should work if nautilus is still functioning .

 Also , you mentioned that there are folders on the desktop. Can they be accessed ? If so then why not access the trash bin from the tree in the folder window after accessing a folder . Your son can then check if the desktop folder has indeed been deleted . If so , one can always restore the folder like in windows .      

If this is not the case , then one might consider reinstalling gnome panel :     

sudo apt-get install --reinstall gnome-panel 

Not sure if reinstalling will work though .    
Hope this helps     
Cheers :)

---

