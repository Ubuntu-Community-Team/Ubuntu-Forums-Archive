---
title: "[SOLVED] Something Went Really Wrong"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Amanda8404 on 2008-08-02
When I go to Places and try to open my Home folder, it instead opens FSpot and shows me two random pictures. Under bookmarks, I click on the folders and the same thing happens - Fspot opens, but in the cases of folders with just Office documents, it doesn't have any pictures. This happened after I tried to uninstall Evolution. What could have happened?

---

### Post by munkyeetr on 2008-08-02
Just a chance...

1) *Right-click* on a folder and choose **Properties**
2) Click on the **Open With** tab
3) If **F-Spot** is there, remove it; and make sure **Open Folder** option is selected.

Maybe/maybe not?

---

### Post by Amanda8404 on 2008-08-02
Thanks - Right clicking just opens more and more F-Spots instead of opening a menu. Is there a keyboard shortcut? 

A lot of things from the top bar are not working right, besides just my personal folders.  When I try to open About Me in the System menu it says "Failed to execute child process "gnome-about-me" (No such file or directory".Some things work though, like Synaptic and and Network under Administration. Network under Places does not work, however. 

I can get at my folders because I have a shortcut on my desktop to one of them, and I can navigate from that one to all the others with no problems. I'm so relieved about that! I feel like I must have deleted some little file on accident that tells the menu how to find stuff.

---

### Post by northern lights on 2008-08-02
Most likely munkyeetr's tip is exactly what you need to do, just from within nautilus (you're on Ubuntu/gnome, right?).

Press "Alt+F2", type "nautilus" (without the quotation marks) and hit Enter.

---

### Post by Amanda8404 on 2008-08-02
It says Nautilus cannot be found...

---

### Post by perlluver on 2008-08-02
I though that when you un installed evolution it took Ubuntu-desktop with it.  I could be wrong, but I thought I read that somewhere.

---

### Post by t0p on 2008-08-02
> **perlluver said:**
> I though that when you un installed evolution it took Ubuntu-desktop with it.  I could be wrong, but I thought I read that somewhere.

Yes, that does happen.  But ubuntu-desktop is just a meta-package, so if that is uninstalled it shouldn't take any actual packages with it.

At least, that's what happened when I got rid of evolution back when I was running dapper.  I would have thought it's still that way.

---

### Post by OldTimeTech on 2008-08-02
When you delete Evolution, you get a dialog box that should of said something like this program is used by other programs in your Ubuntu desktop.  

Probably at that point you shouldn't of deleted.

Anyway, trying going to snyaptic package manager and searching for ubuntu-desktop, I think you will find it unmarked.  Mark it for installation and apply.

Then when (crossing my fingers) it works, you will again have an Evolution envelope showing.  At that point right click on envelope and it will allow you to remove it from the panel...but you can't delete it.

---

### Post by Amanda8404 on 2008-08-02
All is well again - I went back to synaptic and reinstalled nautilus, etc. . Before I did that, though, I reinstalled Evolution but it didn't fix it alone, as I hoped it would. I guess I misremembered Evolution as something I had added myself. Thanks everyone- phew!

I did that before I read what you said to do, and you were right that Ubuntu-desktop was unchecked, so I fixed that. Thanks again...

---

### Post by steveneddy on 2008-08-02
Can we mark this as solved please?

---

