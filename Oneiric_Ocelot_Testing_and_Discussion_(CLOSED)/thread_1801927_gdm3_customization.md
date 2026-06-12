---
title: "gdm3 customization"
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bedbug on 2011-07-11
Suppose you are using gdm instead of default lightdm ...

To Change Background Edit picture-uri in
/usr/share/glib-2.0/schemas/10_gsettings-desktop-schemas.gschema.override

To Change theme, font etc, Edit
/usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override

finally
sudo dpkg-reconfigure  libglib2.0-0:i386
sudo restart gdm


Note:Mine look like this:

cat /usr/share/glib-2.0/schemas/10_gsettings-desktop-schemas.gschema.override

[org.gnome.desktop.background]
show-desktop-icons=true
picture-uri='file:///usr/share/themes/Adwaita/backgrounds/stripes.jpg'


cat /usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override

[org.gnome.Empathy.conversation]
theme="adium"
adium-path="/usr/share/adium/message-styles/ubuntu.AdiumMessageStyle"

[org.gnome.desktop.interface]
gtk-theme="Adwaita"
icon-theme="Faenza-Dark"
cursor-theme="Adwaita"
font-name="Ubuntu 10"

---

