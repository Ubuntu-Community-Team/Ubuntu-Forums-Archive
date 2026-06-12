---
title: "Image viewer always in full screen?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by iption on 2008-07-01
Is there an image viewer that can always runs in full screen, and when i hit Esc it closes? Or can I do something like that with Eye of gnome? 
For now I made all my images to be run with "eog -f".

---

### Post by nowshining on 2008-07-01
did u try looking in the prefs of eog?

---

### Post by sayakb on 2008-07-01
Try GPic image viewer. Double click on the image and you get fullscreen view. Get it from getdeb.net

---

### Post by iption on 2008-07-03
> **LinuxIsInnovation said:**
> Try GPic image viewer. Double click on the image and you get fullscreen view. Get it from getdeb.net

No it just opens in a windowed mode, and there is no way to set it up in preferences. Btw, I didn't find it in getdeb.net (I couldn't find it there) but from the ubuntu packages.

CAn i set up this from registry - I mean configuration menu by importing keys or setting up the key?

---

### Post by DrTebi on 2012-12-24
> **iption said:**
> Is there an image viewer that can always runs in full screen, and when i hit Esc it closes? Or can I do something like that with Eye of gnome? 
For now I made all my images to be run with "eog -f".

Yes it's possible.

Follow these steps in Nautilus (your file manager):

- Right-click on an image and choose "Properties".

- Click on the wrench icon. It's on the same line as the "Type" information, all the way on the right.

- In the next window ("Edit Filetype...") you can see a list of applications in "Application Preference Order". "Image Viewer" should be on top of the list (if not, move it up there with the buttons). Double-click "Image Viewer"

- In the next window ("Properties for...") click on the "Application" tab.

- On the "Application" tab, change the "Command" entry from
```
eog %U
```
to
```
eog -f %U
```


That's it, now Image Viewer will always open images in full-screen mode.

Note that in order to get out of a full-screen view, you either hit escape twice, or Ctrl+w once.

If you are using a different file manager, the steps should be pretty similar. I have used Image Viewer like this on Ubuntu 10.04 and now on 12.04.

---

