---
title: "Changing Ubuntu Menu Icon w/ Configuration Editor?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-28
I've been trying to change the Ubuntu menu icon on the left side of the GNOME menu to use a custom icon, but it doesn't seem to want to cooperate with the Configuration Editor. Is there anything special I need to do?

---

### Post by pofigster on 2008-09-28
I was trying to figure this out for a while too - I wrote a post about it [here]("http://amymark.ewingsonline.com/?p=67") on my blog. 

[http://amymark.ewingsonline.com/?p=67](http://amymark.ewingsonline.com/?p=67)

Hope it helps!

Also, just to make it clear, it was faster for me to give you this link than to find the thread about it here.  It should also be easier this way.

---

### Post by drs305 on 2008-09-28
The icon used (in Hardy):
/usr/share/icons/Human/24x24/places/start-here.png

Run these commands, replacing the appropriate section with your icon.
```
sudo cp /usr/share/icons/Human/24x24/places/start-here.png /usr/share/icons/Human/24x24/places/start-here.png.original
sudo cp ***/pathtoyouricon/iconname*** /usr/share/icons/Human/24x24/places/start-here.png
sudo /etc/init.d/dbus restart
```

If it doesn't look right after you have inserted your own icon, scale it to 24x24.

Note: Some posters have indicated they needed to run this command as well. In  my case it wasn't necessary:
```
sudo gtk-update-icon-cache /usr/share/icons/Human
```

---

