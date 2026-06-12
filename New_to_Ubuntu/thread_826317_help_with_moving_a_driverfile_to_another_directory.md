---
title: "help with moving a driver/file to another directory"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by ontherooftop on 2008-06-11
Ok I am a noob and I need to move a file thats called rtl8187.ko,
the file is in lib/modules/2.6.24-18-generic/kernal/drivers/net/wireless/
rtl8187.ko.    and I want rtl8187.ko  in the path lib/modules/2.6.24-18
generic/kernal/net/ieee80211.  How can I install that driver or file
into that path I am such a noob right now I need a good explanation
or commands in terminal to do this function thanks.

---

### Post by cdtech on 2008-06-11
sudo mv /filetomove /directory/filename

You can just use the directory name on the destination and not the file name to leave it the same name or rename it with another filename on the destination.

hope this helps.......

P.S.
You could leave it where it is and just link to it with a symbolic link.

---

