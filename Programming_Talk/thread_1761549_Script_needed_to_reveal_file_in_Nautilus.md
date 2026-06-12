---
title: "Script needed to reveal file in Nautilus"
date: 2011-05-18
forum: Programming Talk
---

### Post by rg4w on 2011-05-18
I'm writing an app in which I'd like to provide a button the user can click and it'll open the folder containing the file and select it.

I have AppleScript code to do this on OS X and VBScript for Windows, but now I need to implement this on Linux and I'm coming up empty in Google.

Thanks in advance for any insights you can share.

---

### Post by slavik on 2011-05-18
well, if you have the full path of the file, finding the dir is easy:
```
dirname ${FILE}
```

as for selecting it ... you may need read nautilus docs and ask for help in the gnome irc chatroom.

---

