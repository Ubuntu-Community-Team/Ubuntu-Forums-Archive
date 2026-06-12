---
title: "File copy permission denied"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Nikhilc on 2011-12-17
I was trying to copy libflashplayer.so to firefox-6.0/plugins. I got the error as permission denied. How can i copy the file o this folder

---

### Post by yetiman64 on 2011-12-17
Ensure you use "sudo" before the command as you are trying to copy to a part of the filesystem owned by root.

I suspect the folder you are trying to copy to is /usr/lib/firefox-6.0/plugins (the path is not fully listed in your post), correct me if I'm wrong on that please.

So the command would be (in such a case)

```
sudo cp libflashplayer.so /usr/lib/firefox-6.0/plugins/
``` this command is also assuming you have libflashplayer.so currently in your home directory. Good luck.

Edit: BTW welcome to the forums :-)

---

### Post by lovinglinux on 2011-12-17
Welcome to the forums.

If you are experiencing problems with flash or want to use the latest beta, then try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) for Firefox. I recommend getting [version 2.2.2](http://www.webgapps.org/add-ons/flash-aid/download-firefox) from my web site. This version hasn't been approved by Mozilla yet, but it fixes some issues that affect the latest Ubuntu.

Flash-Aid will take care of copying the plugin to the proper folders, removing conflicting plugins and optimizing flash performance.

---

