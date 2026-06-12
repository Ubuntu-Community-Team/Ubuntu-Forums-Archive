---
title: "how do i remove Google Chrome browser?"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Old-un on 2012-08-26
Have been trying yet again to remove an unwanted GoogleChrome web browser without any success.

I did try ```

sudo apt-get purge google chrome
                          +
sudo apt-get autoremove google chrome

```But all i get back is:
Unable to locate package google
Unable to locate package chrome

I have even tried using ```

sudo apt-get remove google-chrome-unstable

```Still without any success

---

### Post by gandaran on 2012-08-26
maybe you have the stable version
```
sudo apt-get remove --purge google-chrome-stable
```
or if you use ubuntu software center you could find what really is installed and remove it from there.

---

### Post by sikander3786 on 2012-08-26
Are you sure it is Chrome and not Chromium that you want to remove.

For removing Google Chrome:

```
sudo apt-get remove google-chrome-stable
```

For removing Chromium:

```
sudo apt-get remove chromium-browser
```

Or search the Ubuntu Software Center for your desired software and install/remove it from there.

---

### Post by Carborundum on 2012-08-26
Perhaps you have the stable version installed? Did you also try ```
sudo apt-get remove google-chrome-stable
```

---

### Post by Paqman on 2012-08-26
Since you've got Chrome installed you've got a GUI, so why flail around on the command line? Just open up Software Centre, search for "chrome" and click to uninstall.

If you don't like Software Centre, try [Synaptic]("apt:synaptic"). It's a little quicker and more nuts-and-bolts.

---

### Post by Old-un on 2012-08-26
```

sudo apt-get remove google-chrome-stable

```

Worked a treat thanks all!

---

### Post by gandaran on 2012-08-26
> **Old-un said:**
> ```

sudo apt-get remove google-chrome-stable

```

Worked a treat thanks all!
without the purge command included on the remove command there will still be files remaining in the system, only the purge command completely removes everything.

---

### Post by vasa1 on 2012-08-26
Then there's still ~/.config/google-chrome ;)

---

