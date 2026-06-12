---
title: "[SOLVED] how to fix chunky looking fonts"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-20
this thread shows how. i didnt know if it would work on Xubuntu 8.04 but it sure does

[http://ubuntuforums.org/showthread.php?t=500856](http://ubuntuforums.org/showthread.php?t=500856)

Try This

Ubuntu Linux has an option for font smoothing that isn’t turned on by default for some strange reason. This makes fonts significantly smoother, enough to be very noticable. To enable this option, you need to edit the .fonts.conf file in your home directory.

To create and open the file, run this command and paste in the xml data below it.

sudo gedit ~/.fonts.conf

Paste in this text:

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

You’ll have to log out and back in to see the difference.


Thanks to RAH66 for posting this in the first place

---

### Post by philinux on 2008-08-20
My display is fine by using LCD smoothing and slight hinting. Not sure what these chunky fonts look like. The default look I thought was more spidery and thin than chunky. :confused:

---

### Post by stinger30au on 2008-08-20
install xubuntu 8.04 and look at defaults, you will know what i mean

---

