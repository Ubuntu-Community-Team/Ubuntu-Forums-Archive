---
title: "QuickLook support with Budgie"
date: 2019-12-15
forum: New to Ubuntu
---

### Post by akidd on 2019-12-15
I want to add a "Quick Look" feature like OSX.   Hit the spacebar when a file is highlighted in the file manager and view is invoked.  Any suggestions?

I've found, but not tried, [Sushi]("https://github.com/GNOME/sushi").  It sounds just like the ticket but it is built for Nautilus and I can't find it in the official Ubuntu software repositories.  I believe Ubuntu Budgie is using Nautilus and am pretty sure this won't work?

Thanks.

---

### Post by Frogs Hair on 2019-12-17
Budgie now uses the Nemo file manager as default. I think Budgie 18.04 still has nautilus and I used Sushi with Gnome and it was activated via a keybinding. Sushi is in the repository and can be installed with the following command, but I have never tried it in Budgie with nautilus. ```
sudo apt install gnome-sushi
```

> To activate the preview, left-click the file and hit space.The preview can be closed by hitting space again, or escape.

---

