---
title: "GNOME - Register Application with MIME Type"
date: 2008-03-16
forum: Programming Talk
---

### Post by Cheiron on 2008-03-16
I'm trying to create a .deb package for a programme I'm developing called OpenFracas, and I would like to be able to have it create a new MIME type upon installation, and then to register that application with GNOME so that nautilus automatically opens files of that type with this application.

I've been reading through the GNOME docs that I found here:
[http://www.gnome.org/~shaunm/admin-guide/mimetypes-9.html]("http://www.gnome.org/~shaunm/admin-guide/mimetypes-9.html")
and I've been able to create the new MIME type, by placing this file in /usr/share/mime/packages/openfracas.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
   <mime-type type="text/fracas-map">
     <comment>Fracas2 map</comment>
     <glob pattern="*.map"/>
   </mime-type>
</mime-info>

```

And .mime and .keys files in  /usr/share/mime-info/
.mime:
```
text/fracas-map
	ext: map

```
.keys:
```
text/fracas-map:
	description=fracas map
	default_action_type=application
	short_list_application_ids_for_novice_user_level=openfracas
	category=Documents/Data
```


Nautilus now shows the correct MIME Type for these files, but I cannot get it to open files of this type with the desired application. I have also created a .desktop file in /usr/share/applications and a .applications file in /usr/share/application-registry/

.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=OpenFracas
Comment=A strategy game of tactical combat and world conquest
Exec=openfracas %f
Icon=/usr/share/games/openfracas/Misc/icon.png
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;ArcadeGame;
StartupNotify=true
MimeType=text/fracas-map;
X-Ubuntu-Gettext-Domain=gnome-games

```

.applications
```
openfracas
	command=openfracas
	name=OpenFracas
	can_open_multiple_files=false
	expects_uris=false
	requires_terminal=false
	mime_types=text/fracas-map
```

But nautilus still says "No application is known for this kind of file."

Am I missing a step somewhere, or have I gotten something wrong in my configuration files? I'd appreciate any help anyone can offer.

Thanks.

---

### Post by mssever on 2008-03-16
I don't know about your actual problem, but I think that the extension .map is likely to collide with other filetypes with the same extension. It's too generic.

I'm pretty sure that Nautilus determines mimetype by examining magic numbers, not extensions. My evidence is that a .php file beginning with [FONT=Courier New]<?php[/FONT] is identified as a PHP file, but one beginning with HTML code is identified as HTML, despite the extension.

So it might pay to examine how to add your data to the mime magic file. If the file command gives proper info, my guess is that Nautilus will start to behave with your other settings.

---

### Post by Cheiron on 2008-03-16
Thanks for the tip. I actually just solved the problem, I wasn't calling `update-desktop-database` as root, so it wasn't regenerating the mimeinfo.cache file in /usr/share/applications

---

