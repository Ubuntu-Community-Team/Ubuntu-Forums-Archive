---
title: "[SOLVED] Digikam not picking up camera when plugged in"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Indy452 on 2008-06-01
I have Xubuntu 8.04 and would like to use Digikam program for photo management but when I plug in my Canon powershot A630 camera, Digikam is not recognizing it, or anything for that matter. What can I do to get this working?

Thanks alot.

---

### Post by phidia on 2008-06-01
After you plug the camera into the usb port and turn it on; open a terminal and type dmesg & press the <enter> key.
You should see some output related to your device there. You can search that or post it here.
Sorry I didn't immediately see that you're using xfce-actually it still should auto mount a usb device but if it doesn't you may need to create a mount point using the info from the dmesg output.

---

### Post by Indy452 on 2008-06-01
I performed this but I really don't know what to be looking at.

I can post the results but it would be long list. Would you like to see it?

---

### Post by phidia on 2008-06-01
> **Indy452 said:**
> I performed this but I really don't know what to be looking at.

I can post the results but it would be long list. Would you like to see it?

Your camera should show towards the bottom of that output, and go ahead post the results of > dmesg | tail that should be a shorter list. With your camera still plugged in you can type > sudo fdisk -l Note: l = a lowercase L
that should also show your camera memory card.

---

### Post by wolfen69 on 2008-06-01
if you decide to give up on digikam, try gthumb. in gthumb, go to file>import photos.

---

### Post by Indy452 on 2008-06-01
> **wolfen69 said:**
> if you decide to give up on digikam, try gthumb. in gthumb, go to file>import photos.

O.K, I decided to add gthumb and it works!! Yeah!

Sorry digikam, It just wasn't working out between us:( I had better things to do besides configure you:confused:

All kidding aside gthumb just worked and digikam didn't, and I'm not big into configuring and tinkering too much. I just need a basic OS that just works and Ubuntu/variants just work and if they don't something else will. Gotta love that!

Thanks for the suggestions folks!!

Neal

---

### Post by Chriis on 2008-06-05
sorry

---

