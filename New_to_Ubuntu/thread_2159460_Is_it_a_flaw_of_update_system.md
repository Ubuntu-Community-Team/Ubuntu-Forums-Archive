---
title: "Is it a flaw of update system?"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by criorad on 2013-07-03
[IMG]http://ww3.sinaimg.cn/bmiddle/7024ffectw1e69tu69qucj20mi0h5q6k.jpg[/IMG]

This system update screen stays for half an afternoon...It seems like a download request was banned.
Now, I have some questions:
    1.Can I kill this process now?
    2.Why it starts a new download again after all packages were unpacked? Could I ignore this?
    3.Is it a flaw of update system?

---

### Post by grahammechanical on 2013-07-03
May I suggest that you note down the words where the Update Manager has stopped - flash plugin installer. Click the cancel button. Restart the Update Manager and look for Flash Plugin installer in the list and uncheck it. Then allow Update Manager to continue. This will allow the installing of the packages that have been downloaded and it will not break your OS.

There is something wrong with the file adobe-flashplugin 11.2.202.291.org.tar.gz. It is stopping the Update manager from working. Actually Update Manager is protecting you.

You may want to remove adobe-flashplugin installer. And try reinstalling it.

Regards.

---

