---
title: "How to refresh nautilus"
date: 2008-11-24
forum: Programming Talk
---

### Post by 3togo on 2008-11-24
let say I modify a line inside the file
 ./.nautilus/metafiles/file:%2F%2F%2Fhome%2Fjc%2FDesktop.xml

[PHP]by changing 
 <file name="tvon" timestamp="1227511765" icon_position="220,382" icon_position_timestamp="1227511765" custom_icon="file:///usr/share/pixmaps/gnome-palm.png" icon_scale="1"/>[/PHP]
to 
[PHP] <file name="tvon" timestamp="1227511765" icon_position="220,382" icon_position_timestamp="1227511765" custom_icon="file:///usr/share/pixmaps/gnome-log.png" icon_scale="1"/>[/PHP]

I know I could refresh the icons by 
[PHP]nautilus --restart[/PHP]

but it is really a little bit overkill. I wonder if there are any cleverer way to just refresh the icon concerned?

---

