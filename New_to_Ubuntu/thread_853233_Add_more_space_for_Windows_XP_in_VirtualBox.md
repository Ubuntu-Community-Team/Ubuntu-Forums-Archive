---
title: "Add more space for Windows XP in VirtualBox"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-08
Initially I allocated 7GB virtual hard disk for XP in VirtualBox (don't remember Dynamic or Static). I had installed Itunes (with the bunch; Qtimes and Bonjour and Apple Updates) and now I need to install Office to help my wife with her assignment. However, the space is not enough even after I deleted unnecessary Windows components. Can I expand my virtual hard drive to give enough space for Office and how do I  achieve it. Thanks

---

### Post by superprash2003 on 2008-07-08
i dont think you can expand.. not sure though.. you would have to set it up again

---

### Post by sydbat on 2008-07-08
Can your wife use Open Office instead? She can save in the .doc format.

---

### Post by bumanie on 2008-07-08
I don't believe you can expand a static disc, mush like a real computer where you cannot magically add gb's to a hard drive. You may be able to do a slight of hand trick and clone the drive, install it on a dynamically expanding disc in a new virtual machine. You will have to look up the documentation to see how to do this, but that should work as long is it is not placed on the same vm (conflicting UUID's etc)

---

### Post by wariskampar on 2008-07-08
How do I check whether it was dynamic or otherwise. If I re-setup and copy the image, do all the installed programs get deleted also?

Do I need to re-install XP once again

---

### Post by bumanie on 2008-07-08
As far as I know if you clone the VDI it will be exactly the same as the original, but **clone**, not copy. I don't know for sure whether this works or not, but you can try it on a new vm and not get rid of the original vm until you are sure it works. I am at work and can't check my own vm, but under file and virtual discs or something near the top of that menu, you should be able check what all your discs are. Can't remember whether it differentiates between virtual/dynamic or not, but you can look at things without changing settings.

---

### Post by lazyart on 2008-07-08
Heh.. this can be a lot of fun or very frustrating.  Think of it in terms of a physical computer and it makes more sense.

What would you do if your computer's hard drive got full?  You would get a bigger one, then move everything over via Ghost or Clonezilla.  Then change the cabling so that the newer drive is the boot device, then discard the old hd.

Same idea.  Create a second hard drive in the Virtual Box console.
Boot the virtual machine with a ghost or clonezilla disk.  Remember that you can just use the .iso and tell virtual box which .iso file to use.

Once your virtual machine is booted, copy everything from one virtual disk to another.  If you've used ghost it will automatically expand the partition.  I'm not so sure about clonezilla-- you might have to use gparted to expand the virtual partition.  You can get a gparted/clonezilla disk and do it all.

Once everything is copied, tell virtual box to boot from the 2nd hd instead of the first and once you're in windows you'll know it's safe to delete the old virtual hd.

---

### Post by ak47_ on 2011-06-04
For the process involved above this will be very useful:
[http://www.my-guides.net/en/content/view/122/26/](http://www.my-guides.net/en/content/view/122/26/)

I ran into a a similar problem.  After some messing around, the approach I'm taking is to create another hard disk and add that as a Primary Slave.  This was the equivalent of adding another hard drive to my VBox as I couldn't find out how to copy the contents of one hard disc to the next as was suggested in the previous posts.


EDIT: Sorry this had not been implemented yet, and I am still working on it.  Will let you know if I was able to do this successfully or not.  Win XP is failing to recognize the secondary slave drive

---

