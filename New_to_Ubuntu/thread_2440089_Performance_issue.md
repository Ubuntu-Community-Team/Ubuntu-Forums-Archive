---
title: "Performance issue"
date: 2020-04-05
forum: New to Ubuntu
---

### Post by nikolajov on 2020-04-05
I`m new to the linux world. So i had an old laptop Dell Latitude D630 with 4GB ram 2.60GHZ dual core cpu, ssd and intel graphics. So it was running windows 7 smooth and fast but thought that with linux will be even fast but there seems to be lagging like launching apps takes more time than in the windows 7. So is there something that I`m missing or doing it wrong. 

Thanks

---

### Post by CelticWarrior on 2020-04-05
When that laptop was new the Ubuntu you could have installed back then would have been slightly snappier than Windows. But the current Ubuntu is only comparable to Windows 10. How Windows 10 performs in that same machine should be the benchmark, not Windows 7.

For better results use some Ubuntu flavor lighter on resources. Current Xubuntu should run better than the original Windows 7 in your laptop; standard Ubuntu is geared to the current crop of hardware.

---

### Post by Artim on 2020-04-06
+1 for Xubuntu!

---

### Post by nikolajov on 2020-04-06
okay thanks for the reply i`ll boot and install the Xubuntu

---

### Post by TheFu on 2020-04-06
> **nikolajov said:**
> okay thanks for the reply i`ll boot and install the Xubuntu

No need to reinstall the complete OS just to change the GUi.  The GUi is just another program.

```
sudo apt search xubuntu
```

says the package you want is:
xubuntu-desktop

So install that using whatever package manager you want.

A few others to consider are lubuntu-desktop, ubuntu-mate-desktop Those are all lighter than Gnome3, the default, heavy, Ubuntu DE.

To prevent setting conflicts, while you search for a new favorite DE, it is best to use a new user-account for each different DE tried.  When you are done, just delete them (users and packages). That will clean up the disk storage used.

Having many DEs on a single system isn't an issue.  The problem is with customizations that are placed into each user's HOME, especially if the different DEs are using the same toolkit like GTK2 or GTK3.

To change the DE used, before logging in, there's a "gear" icon. Click that, pick the DE/WM you want, then use the new userid.  Simple.  There are lots of times where having a multi-user OS is really helpful.

---

### Post by mörgæs on 2020-04-07
Though TheFu's approach is possible I don't think there is a reason to keep an Ubuntu environment for hardware like this. It's not likely that you are going to get any joy from it.

Just do a clean install of a light Buntu, erasing everything in the process.

---

### Post by TheFu on 2020-04-07
installing alternative DEs was just step 1.  

Removing the Gnome3 DE would have come or after the shopping around was done, then wiping and doing a fresh, single, install to get the full DE experience from boot to shutdown.

But there are always 50-500 different ways to resolve any issue.

---

