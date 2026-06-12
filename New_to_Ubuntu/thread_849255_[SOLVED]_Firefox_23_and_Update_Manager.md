---
title: "[SOLVED] Firefox 2/3 and Update Manager"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by TreverT on 2008-07-04
I hope someone can help with a strange problem I'm having with Ubuntu 7.1 (I'm still unnerved at upgrading to 8.04 due to the various problems I keep reading about, especially NTFS read/write problems, as half my computer relies on Windows NTFS drives).  

When Firefox 3 was released, I DLed it from the Firefox site and installed per their instructions.  I love FF3.  All went perfectly fine until now.  Suddenly my Update Manager is popping up wanting to update my Firefox from version 2.0.0.14 to version 2.0.0.15.  :confused:  I DON'T want it overwriting my Firefox with an older version.  But the Update Manager notices won't go away, even when I uncheck them.  Any advice on how to clear this off the Update Manager?

Thanks for any help you can provide!

---

### Post by DJ_Peng on 2008-07-04
The Update Manager is only trying to update the Firefox that was installed from Ubuntu's repositories. It actually doesn't even know about the Firefox 3 you installed manually. Although if you put it anywhere other than your /home directory (since I don't know what instructions you followed) I'd take the precaution of taking the update and using your downloaded version to replace it. Personally when I install Firefox with tarballs from Mozilla I install them in my /home folder so I don't have to worry about it getting overwritten when Ubuntu finally realizes there's an update.

---

### Post by TreverT on 2008-07-04
> **DJ_Peng said:**
> The Update Manager is only trying to update the Firefox that was installed from Ubuntu's repositories. It actually doesn't even know about the Firefox 3 you installed manually. Although if you put it anywhere other than your /home directory (since I don't know what instructions you followed) I'd take the precaution of taking the update and using your downloaded version to replace it. Personally when I install Firefox with tarballs from Mozilla I install them in my /home folder so I don't have to worry about it getting overwritten when Ubuntu finally realizes there's an update.

Thanks very much!  I copied my Firefox directory from /usr/lib to my home folder as a backup, then let Update Manager run its thing, and then copied my backup back over the version in /usr/lib (also keeping a copy in my /home too, just in case).  FF3 is still there and works fine, and the Update alert has finally gone away.

---

