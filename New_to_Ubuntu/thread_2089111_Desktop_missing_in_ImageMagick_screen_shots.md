---
title: "Desktop missing in ImageMagick screen shots"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by dan mdk on 2012-11-28
Hi all, brand new to Ubuntu here.. 

having trouble getting screenshots to work correctly using ImageMagick. I install through the software center, cd into the directory and issue a screenshot command:

import -window root ss1.jpg

but the shot only shows the launcher and the panel. The desktop and any open windows/apps are missing.

[IMG]http://i.imgur.com/tF15W.jpg[/IMG]

Any tips on how to configure this correctly would be very appreciated.  BTW, it must be through this utility.  Thank you!

---

### Post by Frogs Hair on 2012-11-28
Hello and Welcome

While trying to figure out ImageMagick you could use the screenshot tool installed by default if you need screen shots. 

Shutter is also available in the software center if you don't like the default tool. ImageMagick was installed with the XFCE session but I have not used it before.

---

### Post by dan mdk on 2012-11-28
Thank you for the tip. The reason I am bent on getting ImageMagick to work is I use an RMM tool that calls it for screenshots when they are being attached to a service ticket.

Another interesting thing is that I did not have any problem at all getting it to work in OpenSUSE 12.

---

### Post by Frogs Hair on 2012-11-28
I was able to open screen shots made with the default tool in ImageMagic and then use the menu options .I don't know if this is will help. When I use the grab option I get coding error.

---

### Post by dan mdk on 2012-11-28
I was also getting a coding error until the right dependencies were installed.

Unfortunately the grab option is pretty much it, as it runs in the background when called by this other app.

I really appreciate your help though..

Dan

---

