---
title: "Image viewer with non-max slideshow?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by christophergraz on 2008-10-13
Can anyone recommend an Ubuntu image viewer that can display a slideshow *without* maximizing and taking over the whole screen?  And can be launched from a GUI file manager such as Nautilus or Konquerer?

The popular/default image viewers I've tried seem to force slideshows to consume the whole screen while running.  

Gnome- or KDE-specific suggestions are both welcome.  (Free Windows programs that run reliably under Wine are fine too.)

Thanks in advance for your advice!

---

### Post by unutbu on 2008-10-14
```
sudo apt-get install gqview
gqview /path/to/images
```


Once you configure your desktop manager to open images using gqview, you should be able to simply double-click on an image to start gqview.

Press 's' to start the slideshow.
If you don't want to have to press 's', you can also make a launcher with this command:```

cd /path/to/images && gqview -s
```
Then you can simply double-click on the launcher and the slideshow will begin.

The first time you run gqview it might open with a maximized window. If you resize the window it will remember that window size from then on.

The first time you run gqview you might have to 
press Ctrl-h to hide the file list.

Go to Edit>Preferences to configure the slideshow.
Click the Image tab to select "Fit image to window". 
This will ensure that the window does not change shape as the image changes. Also "Allow enlargement of image to zoom to fit".

---

