---
title: "HOWTO: Fix spanish menus"
date: 2005-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by man.life on 2005-05-11
I've seen that some applications in the menu don't even have a spanish translation, or the translation isn't 100% correct. To fix this, I've written a script, but obviously I don't use the same applications you do. I've only included main applications:

```
#!/bin/sh
#Fix spanish menus

cd /usr/share/applications
echo "Name[es]=Navegador web Firefox" >> mozilla-firefox.desktop
echo "Name[es]=Mensajería instantánea Gaim" >> gaim.desktop
echo "Name[es]=OpenOffice.org Hoja de cálculo" >> ooo645calc.desktop
echo "Name[es]=OpenOffice.org Dibujo" >> ooo645draw.desktop 
echo "Name[es]=OpenOffice.org Presentación" >> ooo645impress.desktop
echo "Name[es]=OpenOffice.org Procesador de textos" >> ooo645writer.desktop
echo "Name[es]=Reproductor de vídeo Totem" >> totem.desktop
echo "Name[es]=Escaneo de imágenes XSane" >> xsane.desktop
```

If you want to include some application more,

```
echo "Name[es]=(Spanish name) >> (app).desktop
```

Remember to run it using sudo.

Once an application is updated, the original name will come back. Running the script again will fix it.

PD: It would be nice to have some more spanish translations by default in Breezy.  :)

---

