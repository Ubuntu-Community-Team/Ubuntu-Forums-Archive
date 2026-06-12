---
title: "[SOLVED] how to uninstall mac4lin 1.0rc package?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by syms on 2008-09-16
ive installed package, how can i completely uninstall it? because now my close window button is on left but not in right

---

### Post by Nepherte on 2008-09-16
How did you install it in the first place? If you used a .deb package, you should be able to remove it in synaptic.

---

### Post by howefield on 2008-09-16
You could go to system > preferences > appearance and change the theme back to what you want ?

---

### Post by bgblanch on 2008-09-16
I have the same problem.  I've gone into System -> Preferences -> Appearance and changed the theme back to Human and clicked on Customize and the Window Border tab to make sure it looks right with no luck.  This is annoying.  Anyone able to help?


Fixed: Paste this in a terminal (not sudo or as root)
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:close,minimize,maximize"

---

### Post by syms on 2008-09-17
> **bgblanch said:**
> I have the same problem.  I've gone into System -> Preferences -> Appearance and changed the theme back to Human and clicked on Customize and the Window Border tab to make sure it looks right with no luck.  This is annoying.  Anyone able to help?


Fixed: Paste this in a terminal (not sudo or as root)
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:close,minimize,maximize"

thanks  but now the close button is left i wanna change back to everythink
edit: i fixed this

---

### Post by NullHead on 2008-09-18
This is what fixed it for me: ```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

I installed mac4lin with their install script, avoid it if possible!, and then I realized I liked the default ubuntu theme allot better ... so now I changed it all back to find out that my buttons were on the wrong side. 

Thanks, bgblanch, for bringing to my attention that it's a gconf setting. 

:popcorn:

---

### Post by PhaeZee5 on 2008-10-05
Excellent!
I got the icons to the right of the window, and NullHead's simple code fixed it!

---

### Post by actionscripted on 2008-10-25
Here's an uninstall script that will completely remove and repair all files and settings created or modified by running the Mac4Lin installer -- returning your system to exactly how it was before you installed Mac4Lin assuming you had a normal Ubuntu setup, of course.

Just download it and run it like you did the original Mac4Lin installation script.

---

### Post by rawfool on 2008-12-11
I downloaded that file but I am not able to run that file :confused:

---

### Post by bwang on 2008-12-11
Open a Terminal and cd to the directory where the script is.
Then run
```

chmod +x Mac4Lin_Uninstall_v1.0.sh
./Mac4Lin_Uninstall_v1.0.sh

```

---

### Post by nateryanphoto on 2009-03-13
Thanks BWANG 

I had the same issue! Totally fixed.

---

### Post by ehderube on 2009-04-03
Thanks, same problem but the copy and paste into terminal solved it!

---

### Post by HenkH on 2009-05-19
Thanks,

Also the same problem, script works fine.

---

### Post by mutarasector on 2009-07-06
> **NullHead said:**
> This is what fixed it for me: ```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

I installed mac4lin with their install script, avoid it if possible!, and then I realized I liked the default ubuntu theme allot better ... so now I changed it all back to find out that my buttons were on the wrong side. 

Thanks, bgblanch, for bringing to my attention that it's a gconf setting. 

:popcorn:

Yes, thanks!   I've been batting my head around for 3 days trying to fix the same problem after uninstalling mac4lin.  Now my titlebar buttons are the way they're SUPPOSED to be, not Steve Jobs *** backwards layout...

---

### Post by bapoumba on 2009-09-08
Closing this older thread that keeps getting revived. (moved recent post to its own thread).

---

