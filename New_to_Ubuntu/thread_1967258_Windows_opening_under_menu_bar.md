---
title: "Windows opening under menu bar"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-04-28
I've gone back to gnome desktop and got rid of that dreadful unity.
But one problem, all my windows open at the very top left hand corner of the desktop, right under where the menus are. This is a problem because I can't easily move them and have to close them on the taskbar (a pain).

Is there a way that I can default them to open on another place in the page?

Would it be in gconf-editor somewhere? I've googled it and I can't find a fix.

Anyone....?

---

### Post by Senior_Buckethead on 2012-04-28
anyone?

---

### Post by JeepFreak on 2012-07-02
I had the same problem.  I fixed it with the compizconfig-settins-manager.

Install with:
```
sudo apt-get install compizconfig-settings-manager
```

If it doesn't show up in your main menu (like it doesn't for me), open the run menu and launch with:
```
ccsm
```

Click on "Window Management" on the left.

Enable "Place Windows".

Click on the "Place Windows" button for optional settins.  The "Smart" placement works for me.

HTH,
Billy

---

### Post by DevoLopper on 2012-10-08
Thanks SO much -- solved!

---

