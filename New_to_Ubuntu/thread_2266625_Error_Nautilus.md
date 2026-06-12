---
title: "Error Nautilus"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by paco9 on 2015-02-24
Hello and sorry for not knowing how to express myself in English. I had to translate my comment about not knowing English. That said passage discuss my problem.

I am new to Linux, never before had used and in doing so I realize it's a great OS've tried a few distros and I liked most and best for me fits, is Ubuntu Studio. But I have encountered some problems that I am slowly solving, all but one.
This distro is not installed by default brings "Nautilus" and I realized that to handle certain files, you need to have it installed, so I installed it. But to use it always gives me an error that I could know how to fix it, is a bit long message and is as follows:
  
 
 (nautilus:2679): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
 Initializing nautilus-open-terminal extension
 Intializing nautilus-pastebin extension...
 sys:1: Warning: Source ID 280 was not found when attempting to remove it
 sys:1: Warning: Source ID 281 was not found when attempting to remove it
  sys:1: Warning: Source ID 282 was not found when attempting to remove it
  
 
  I have no idea how to fix this or that out, so if anyone has this problem and knows how to fix it, I would be very grateful if you help me fix it.
Thank you very much and sorry for the bad english.

Regards
Eduardo F.
  
 
 Buenos días y perdón por no saber expresarme en inglés. He tenido que traducir mi comentario por no saber inglés. Dicho esto paso a comentar mi problema.
 
 
 Soy un nuevo usuario de Linux, nunca antes lo había usado y al hacerlo me doy cuenta de que es un  gran S. O. He probado  unas cuantas distros y el que me ha gustado más y se adapta mejor a mis necesidades, es Ubuntu Studio. Pero me he encontrado con algunos problemas que poco a poco voy solucionando, todos menos uno.
 Esta distro no trae instalado por defecto “Nautilus” y me he dado cuenta de que para manejar ciertos ficheros, es necesario tenerlo instalado, así que lo instalé. Pero al usarlo siempre me da un error que no he podido saber como solucionarlo, es un mensaje un poco largo y es el siguiente:
 
 
 (nautilus:2679): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
 Initializing nautilus-open-terminal extension
 Intializing nautilus-pastebin extension...
 sys:1: Warning: Source ID 280 was not found when attempting to remove it
 sys:1: Warning: Source ID 281 was not found when attempting to remove it
 sys:1: Warning: Source ID 282 was not found when attempting to remove it
 
 
 No tengo ni idea de como solucionar este problema ni porque sale, así que si alguien tiene dicho problema y sabe como arreglarlo, le estaría muy agradecido si me ayudara a solucionarlo.
 Muchas gracias y perdón por el mal inglés.
 
 
 Saludos
 F. Eduardo

---

### Post by ajgreeny on 2015-02-24
If I remember correctly Ubuntu-Studio uses the XFCE desktop so nautilus may cause some problems if started with the normal command of **nautilus**, as that will start it with the default configuration to manage the desktop of your system and will do strange things such as removing your wallpaper, and I suspect that may be the cause of your problem here.

You need to use the command ```
nautilus --no-desktop
``` to use it as just a file manager and leave your session and desktop unchanged, so to be able to use the nautilus menu item edit its launcher desktop file with ```
sudo nano /usr/share/applications/nautilus.desktop
``` and change the line 
```
Exec=nautilus --new-window %U
```to ```
Exec=nautilus --no-desktop %U
```
Hopefully that will help you.

---

