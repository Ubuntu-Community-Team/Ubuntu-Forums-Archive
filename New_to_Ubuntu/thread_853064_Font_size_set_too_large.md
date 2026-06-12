---
title: "Font size set too large"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by uchihaitachi on 2008-07-08
I made a mistake of setting my font size to 90000 (I saw a flawed screenshot with that figure, my bad) and now I can only see my wall paper and nothing else. Is there anything I can do at this stage to recover to my previous situation?

If a reformat is inevitable, I would like to retrieve some of my files onto a hdd but I'm getting a permission denied when I try to retrieve those files using the live cd.

---

### Post by ChameleonDave on 2008-07-08
> **uchihaitachi said:**
> I made a mistake of setting my font size to 90000 (I saw a flawed screenshot with that figure, my bad) and now I can only see my wall paper and nothing else. Is there anything I can do at this stage to recover to my previous situation?

If a reformat is inevitable, I would like to retrieve some of my files onto a hdd but I'm getting a permission denied when I try to retrieve those files using the live cd.

Definitely no need to reformat anything for such a tiny problem!  This isn't MS Windows!

I presume you are using GNOME.

First, you need to get to a command line.  The easiest way to do this is to boot up, and then hit Ctrl + Alt + F1 to get to a TTY terminal.

Log in.

Then, enter the following command:

```

mv  .gnome2  .gnome2.backup
mv  .gconf   .gconf.backup 

```

That will reset all your GNOME settings to their default.

---

### Post by ChameleonDave on 2008-07-08
I have pin-pointed the exact files that contain your font configuration for GNOME.

Don't reset all of GNOME to its defaults.  Instead do this:

Enter the following commands:

```

rm ~/.gconf/desktop/gnome/interface/%gconf.xml   # *this is the main one*
rm ~/.gconf/apps/metacity/general/%gconf.xml
rm ~/.gconf/apps/metacity/preferences/%gconf.xml

```

That will remove those files.  GNOME will recreate them as necessary.

If you like, you could edit those files to correct the font size, but it's not really very advantageous.

One problem that I came across was that if I exited the session with Ctrl + Alt + Backspace, GNOME refused to honour the settings in those files, and instead restored some sort of emergency backup, with the incorrect font sizes.  I'm not sure how to work around that.

---

### Post by uchihaitachi on 2008-07-08
I tried your first method and it worked like a charm. Thank you very much!

---

### Post by ChameleonDave on 2008-07-08
> **uchihaitachi said:**
> I tried your first method and it worked like a charm. Thank you very much!

Great!  Perhaps you could use the "Thread Tools" menu to mark this as solved.

---

