---
title: "applying an icon theme doesn't change the directory nor the mounted partition icons?!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-05-21
i've tried a lot of icon themes on ubuntu, some do change my default icon for folders and most of them doesn't, even though they have icons for directories, like the icon theme: dropline nuovo..
so whenever i change my icon theme, the folder icon sticks to the old GNOME square-greenish icon..
is this a bug of some sort? how do i fix it?

---

### Post by crossedout on 2008-05-22
I've noticed some themes are packaged with icons in a different directory than where they are called from.  Check that your directory and folder icons are located in the 'Places' directory within your chosen icon theme.

To access the folder, navigate to your Home folder, ctrl-h to show hidden folders, navigate to .icons and down into your icon theme folders.
Good Luck.

-Xout

---

### Post by mcduck on 2008-05-22
Just try if logging out and back again would load the theme correctly, or try restarting the file manager (alt-f2 and run "killall nautilus"). As long as the icon theme you are trying to use is complete it should work after this..

---

### Post by paranoid_humanoid on 2008-05-22
the themes are in /usr/share/icons/
the one i'm talking about for example is Nuouvo, it's in the repositories, you can get it by "sudo apt-get install gnome-icon-theme-nuovo"..
the index.theme says:

> [Icon Theme]
Name=Dropline Nuovo
Comment=Yet another SVG iconset
Inherits=gnome
Directories=scalable/apps,scalable/filesystems,scalable/mimetypes,scalable/mimetypes/audio,scalable/mimetypes/images,scalable/mimetypes/misc,scalable/mimetypes/office,scalable/mimetypes/packages,scalable/mimetypes/special,scalable/mimetypes/text,scalable/mimetypes/video,scalable/devices,scalable/emblems,scalable/stock,24x24/stock/evolution,24x24/stock
Example=gnome-theme-preview.svg

[scalable/apps]
MinSize=1
Size=128
MaxSize=256
Context=Applications
Type=scalable

[scalable/devices]
MinSize=1
Size=128
MaxSize=256
Context=Devices
Type=scalable

[scalable/emblems]
MinSize=1
Size=128
MaxSize=256
Context=Emblems
Type=Scalable

[scalable/filesystems]
MinSize=1
Size=128
MaxSize=128
Context=FileSystems
Type=scalable

[scalable/mimetypes]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/audio]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/images]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/misc]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/office]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/packages]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/special]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/text]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/mimetypes/video]
MinSize=1
Size=128
MaxSize=128
Context=MimeTypes
Type=scalable

[scalable/stock]
MinSize=1
Size=24
MaxSize=128
Context=Stock
Type=scalable

[24x24/stock/evolution]
Size=24
Context=Stock
Type=Fixed

[24x24/stock]
Size=24
Context=Stock
Type=Fixed

and all those dirs exist, so what's wrong here? could somebody please download the package and try it out?!
i tried restarting the pc and it didn't work btw..

---

### Post by paranoid_humanoid on 2008-05-22
apparantly the icon naming scheme changed in hardy, here's the bug report: 
[https://bugs.launchpad.net/ubuntu/+source/nuovo/+bug/224527](https://bugs.launchpad.net/ubuntu/+source/nuovo/+bug/224527)

---

