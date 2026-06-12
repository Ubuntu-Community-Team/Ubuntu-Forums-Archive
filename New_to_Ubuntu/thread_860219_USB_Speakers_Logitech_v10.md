---
title: "USB Speakers Logitech v10"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by phil81uk on 2008-07-15
Hello,

I purchased a set of USB speakers (Logitech V10 - very popular speakers). The volume control on them seems to work in that it changes the system volume, but sound does not go through them.

---

### Post by Krydahl on 2008-07-15
Are you using Hardy (8.04)?

---

### Post by prophet73 on 2008-07-15
[http://gentoo-wiki.com/HOWTO_Logitech_V10_Notebook_Speakers](http://gentoo-wiki.com/HOWTO_Logitech_V10_Notebook_Speakers)
Not sure if this will help but have a look anyway.

---

### Post by phil81uk on 2008-07-15
Yes, Hardy 8.04.

---

### Post by Krydahl on 2008-07-15
In Gutsy (before the change to pulse audio) I had automatic detection working, but I haven't found a way to sort it yet in Hardy. 

However, if you go System->Preferences->Sound you should see a devices tab with all options set to autodetect.

If you change the options you're interested to the USB speakers things should work (mine are detected as USB audio). Hope this helps.

---

### Post by phil81uk on 2008-07-15
Hey! That worked!

---

