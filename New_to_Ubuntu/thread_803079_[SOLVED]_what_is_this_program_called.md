---
title: "[SOLVED] what is this program called?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-22
Afternoon everyone,

I have a menu entry in system>preferences that reads 'GL Desktop' I believe that I inadvertently installed this program when installing Compiz Fusion and its associated config manager. 

I have some weird happenings on the login where after inputting the user and pwd the screen goes black with the old X11 cross on it, and it takes maybe a minute to load the desktop. Also I am getting windows graying out, which did not happen before. 

I think that the two 3D programs are not happy together and as I want to use the compiz config manager, I want to remove GL Desktop, the only thing is, it is not listed under GL Desktop or 3d Desktop, or 3ddesktop (which names I came up with after googling it)

I have studied my installed list but cannot spot its description

can someone help?

---

### Post by iaculallad on 2008-05-22
> **tropdoug said:**
> Afternoon everyone,

I have a menu entry in system>preferences that reads 'GL Desktop' I believe that I inadvertently installed this program when installing Compiz Fusion and its associated config manager. 

I have some weird happenings on the login where after inputting the user and pwd the screen goes black with the old X11 cross on it, and it takes maybe a minute to load the desktop. Also I am getting windows graying out, which did not happen before. 

I think that the two 3D programs are not happy together and as I want to use the compiz config manager, I want to remove GL Desktop, the only thing is, it is not listed under GL Desktop or 3d Desktop, or 3ddesktop (which names I came up with after googling it)

I have studied my installed list but cannot spot its description

can someone help?

Try uninstalling 'GL Desktop' first and observe if everything goes back to normal.

---

### Post by tropdoug on 2008-05-22
Thats my aim, only I don't know what it is called to be able to uninstall it. It does not appear in synaptic under any of the three names in my first post.  :-)

---

### Post by sam_delta on 2008-05-22
according to [http://linuxventanitas.wordpress.com/2007/07/14/gl-desktop-una-alternativa-a-%E2%80%9Cefectos-de-escritorio%E2%80%9D-linux-mintubuntu/](http://linuxventanitas.wordpress.com/2007/07/14/gl-desktop-una-alternativa-a-%E2%80%9Cefectos-de-escritorio%E2%80%9D-linux-mintubuntu/)
GL desktop  is installed by typing "sudo apt-get install gnome-compiz-manager", so i guess thats the package your looking for

sam

---

### Post by tropdoug on 2008-05-22
WOW fantastic, how did you find that  info?

Yup that was the one, thank you very much :-)

---

### Post by sam_delta on 2008-05-22
> **tropdoug said:**
> WOW fantastic, how did you find that  info?

i googled it, and got some spanish articles/threads, and since i understand spanish, i was able to read and get the package name :p

sam

---

### Post by iaculallad on 2008-05-22
Or you could try this to reset the settings:

Go to your terminal by pressing CTRL + ALT + F1, login to your account and issue this command: **rm -rf .gnome .gnome2 .gconf .gconfd .metacity** to reset the settings. Afterwards press CTRL + ALT + F7 to get back to your GUI.

---

### Post by sam_delta on 2008-05-22
no problem, glad i were able to help
enjoy ubuntu :)

btw, now that you deleted gl desktop, did you got your problem fixed?

sam

---

### Post by tropdoug on 2008-05-22
Sorry just had to slip out for a while, 

Yes sam, it appears to have fixed it. 

again thanks a lot :guitar:

---

