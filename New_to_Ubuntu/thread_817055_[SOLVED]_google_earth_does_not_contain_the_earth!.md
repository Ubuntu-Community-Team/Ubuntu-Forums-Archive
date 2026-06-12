---
title: "[SOLVED] google earth does not contain the earth?!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-03
its just a load of stars and no earth
I followed these instructions:
[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu)
and it worked a treat the first time but now no earth and the side bar stuff has disappeared
any ideas?
help appreciated as usual

---

### Post by _sphinx_ on 2008-06-03
Try writing:
> sudo googleearth
on the terminal, see if it works
Or after that you can also try writing just:
> googleearth
on the terminal

---

### Post by golgo13 on 2008-06-03
that was easy
cheers mate

---

### Post by wahoobob on 2008-06-20
In your HOME directory, there is a ".googleearth" directory (the "." makes it hidden, but it should be there). Try deleting this directory (it contains all your Google Earth preferences, so be careful - maybe make a backup). In a terminal, you would type:

Quote:
sudo rm -rf ~/.googleearth  

***_Running Google Earth or any app as Root is not a good idea_***.  I think the when you run the ".bin" installer, there is a checkbox at the very end of the install process that says something like "Start Google Earth." If this is checked, it starts the application as the "root" user (since you have to use "sudo" to install the app) and creates the ".googleearth" directory with root privileges. When you run the app. without these privileges, all sorts of problems seem to occur. They should probably make the checkbox default to unchecked.

---

### Post by Ashejoe on 2008-06-21
I don't know what I'm doing wrong ?

I too followed the directions on that webpage for installing Google Earth and kept getting this error message:

chmod +xGoogleEarthLinux.bin
chmod: missing operand after `+xGoogleEarthLinux.bin'
Try `chmod --help' for more information.

I was using the Shell Konsole

---

### Post by AndThenWhat on 2008-06-21
> **Ashejoe said:**
> I don't know what I'm doing wrong ?

I too followed the directions on that webpage for installing Google Earth and kept getting this error message:

chmod +xGoogleEarthLinux.bin
chmod: missing operand after `+xGoogleEarthLinux.bin'
Try `chmod --help' for more information.

I was using the Shell Konsole

I believe there is a space between the +x and GoogleEarthLinux.bin. If that is what you put in the terminal then it definitely will cause problems.

---

