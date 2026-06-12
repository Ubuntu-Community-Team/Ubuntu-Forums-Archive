---
title: "[SOLVED] Cannot burn iso image to DVD..."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-10-29
OK. I've just finished downloading 8.10 rc and want to burn it. But I can't.
Is it because I'm using a DVD?

---

### Post by eternalnewbee on 2008-10-29
This is how it looks like:

---

### Post by philinux on 2008-10-29
I'm glad it failed as it would not boot and it would have wasted a dvd LOL.

You need to burn the iso file to the disk as an image not a data disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I use k3b for my burning. And remember to burn it no faster than 4x. 

Good luck.

---

### Post by bullfrog5 on 2008-10-29
what iso burner are you using?

---

### Post by NewJack on 2008-10-29
I agree with philinux.  Use K3b to burn the .iso, great program.

---

### Post by eternalnewbee on 2008-10-29
> what iso burner are you using?
Brasero

---

### Post by eternalnewbee on 2008-10-29
Sorry for the bad attachment. This is the final version:

---

### Post by eternalnewbee on 2008-10-29
> I use k3b for my burning. And remember to burn it no faster than 4x. 
I'll have to install it first.

---

### Post by Duck2006 on 2008-10-29
> **philinux said:**
> I'm glad it failed as it would not boot and it would have wasted a dvd LOL.

You need to burn the iso file to the disk as an image not a data disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I use k3b for my burning. And remember to burn it no faster than 4x. 

Good luck.

+2 on k3b

---

### Post by NewJack on 2008-10-29
I don't use Brasero, but where it states "Image Type" the drop down box says "Let Brasero Decide".  What other options are listed there?

---

### Post by eternalnewbee on 2008-10-29
I like to communicate visually:

---

### Post by eternalnewbee on 2008-10-29
> I don't use Brasero, but where it states "Image Type" the drop down box says "Let Brasero Decide". What other options are listed there?
There is no other option.

---

### Post by NewJack on 2008-10-29
Yep, that is K3b alright.

---

### Post by NewJack on 2008-10-29
Any luck with K3b?

---

### Post by eternalnewbee on 2008-10-29
It's taking a long time...

---

### Post by philinux on 2008-10-29
It does. Make a coffee.

---

### Post by eternalnewbee on 2008-10-29
Patience is a virtue..

---

### Post by eternalnewbee on 2008-10-29
> It does. Make a coffee.
Thanks:)
It's ELEPHANT time here :lolflag:

---

### Post by eternalnewbee on 2008-10-29
I don't think I can use it on my Gnome...

---

### Post by forger on 2008-10-29
I use brasero to burn cd images on DVD and DVD-RW media, never had a problem :)

---

### Post by philinux on 2008-10-29
> **eternalnewbee said:**
> I don't think I can use it on my Gnome...

I'm using gnome and got k3b and kopete installed both kde apps. No worries there at all.

---

### Post by forger on 2008-10-29
As said from others, your RIGHT-CLICK ON THE .ISO file and open with brasero

---

### Post by NewJack on 2008-10-29
> **philinux said:**
> I'm using gnome and got k3b and kopete installed both kde apps. No worries there at all.

'Nuff said!

---

### Post by eternalnewbee on 2008-10-29
> I use brasero to burn cd images on DVD and DVD-RW media, never had a problem 
Neither had I, but hold on. I closed Add/Remove and tried again and... it's downloading! OK. About 4 minutes left. See you on the other side.

---

### Post by eternalnewbee on 2008-10-29
> As said from others, your RIGHT-CLICK ON THE .ISO file and open with brasero
Didn't think of that. Went to Brasero instead and that's where I got stuck.
But I'm ready to go now:guitar:

---

### Post by eternalnewbee on 2008-10-29
> 'Nuff said!
Gee thanks.

---

### Post by por100pre1 on 2008-10-29
Try using k3b and a **CD**...

---

### Post by NewJack on 2008-10-29
> **eternalnewbee said:**
> Gee thanks.

I wasn't being sarcastic, I was just agreeing with philinux on the fact that some KDE programs work well in GNOME.

---

### Post by Taboo Mirage on 2008-10-29
So much complication using GUI apps. =P
```
growisofs -dvd-compat -Z /dev/cdrom=/path/to/image.iso
```

You win.

---

### Post by eternalnewbee on 2008-10-29
> Try using k3b and a CD...
Didn't have one..
Anyways, burnt the dvd successfully with Brasero and installed Intrepid alright.
> I wasn't being sarcastic, I was just agreeing with philinux on the fact that some KDE programs work well in GNOME.
No hard feelings here.

> Code:

growisofs -dvd-compat -Z /dev/cdrom=/path/to/image.iso

You win.
Sorry I couldn't try that one as I was already installing.
____________________________________________________________________________

OK, guys. Sorry for my late reply. It was very late.
So, I've got the system running, but I've run into a problem with activating the Nvidia driver. I think I should just close and try again, but I'm confused as to the 3 choices it gives. Take a look.
Any thoughts?

---

### Post by forger on 2008-10-30
try installing it using a terminal command:
e.g. if your version is 177:
```
sudo apt-get install nvidia-glx-177
```

---

### Post by eternalnewbee on 2008-10-30
Thanks for your advice forger. I just closed the Application and opened it again and it started downloading right away, but your method
```
sudo apt-get install nvidia-glx-177
```
will most probably come in handy for others with the same problem, who stumble upon this Thread.
So this Thread is solved. Thanks again.

---

### Post by philinux on 2008-10-30
OT whats the theme you're using.

---

### Post by eternalnewbee on 2008-10-30
> OT whats the theme you're using.
It's called New Wave, and if I recall correctly, you can find it in Gnomelook.

---

### Post by philinux on 2008-10-30
Cheers I was using dark looks and tried out ubuntu studio theme. I'm giving this one a look right now.

---

### Post by eternalnewbee on 2008-10-30
You're welcome.

---

