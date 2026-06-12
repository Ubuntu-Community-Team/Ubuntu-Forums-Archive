---
title: "Ubuntu - Can't quite make it my main OS yet"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Orographic on 2008-11-30
Hi all,

I love Ubuntu but its still just a bit fiddly for me to make it my main OS. For the last week I have tried to make it my main OS as the sole install on my main drive and have nearly gotten there. I even manually partitioned with the Hardy CD so I could still use Acronis to backup with that inode issue in Intrepid.

I even bought a new DVD burner as my previous one had issues with Ubuntu. Gimp 2.6 is my friend, Ufraw too and Opera is great to view my router settings that can't be viewed in FF. In fact, I love most things about Ubuntu but Intrepid especially, has been a bit buggy for me.

Today I did some 'My Documents' backups and twice to different external drives my Intrepid system wouldn't shut down after moving stuff to trash can and then deleting it. The caps lock and the 'downward pointing arrow' button next to it were flashing and my system wouldn't shut down at all - it just froze. It hasn't done this in XP and for such a simple exercise like using trashcan and then shutting down, I expect more. 

I did check the intregrity of my install CD and also my ram = all good there.

Still I love Ubuntu and the philosophy behind it and will be still fiddling with it more for sure but its just not quite there for me and my needs...yet. 

I so wish it was...

---

### Post by pp. on 2008-11-30
> **Orographic said:**
> The caps lock and the 'downward pointing arrow' button next to it were flashing and my system wouldn't shut down at all - it just froze.

It's not quite clear to me what you mean by "caps lock" and "downward pointing arrow". Are these lights on your keyboard?

If so, your problem might be related to the BIOS or your hardware.

---

### Post by flanagan on 2008-11-30
Have you seen the thread at [http://ubuntuforums.org/showthread.php?t=965935](http://ubuntuforums.org/showthread.php?t=965935) ?

I would suggest following the advice of [unutbu]("http://ubuntuforums.org/member.php?u=518895"), especially this:

[http://ubuntuforums.org/showpost.php?p=6098072&postcount=6](http://ubuntuforums.org/showpost.php?p=6098072&postcount=6)

---

### Post by lametike on 2008-11-30
the caplock is the "A" on the keyboard and num lock is the "1" on the keyboard,similarly,the downward pointing arrow is the scroll lock!

---

### Post by 3rdalbum on 2008-11-30
The flashing lights indicate a "kernel panic" - that's where the kernel itself crashes.

Shutting down, changing to virtual terminals, and logging out are times when it's not unheard of to get kernel panics. Basically, changing graphics modes can expose bugs in the Nvidia or ATI proprietary driver that will bring your system crashing to a halt. It probably has little or nothing to do with the files you were copying.

See if the problem occurs with proprietary graphics drivers DISABLED, and if it doesn't, then you might want to consider ditching them perminantly or updating to a later version of the drivers.

---

### Post by Orographic on 2008-11-30
Thanks guys. Re kernel panic, I don't have any proprietry drivers installed. This problem has only happened when I have my external usb hard drives connected but as suggested, this may not be related. It only happens when they are connected and I've emptied the trash though and not other times. 

So, do I have to insert that linked command into terminal each time I shut down? That's a bit complicated if my wife for example is using the computer. 

Yeah, sorry for the ambiguity.  Scroll lock and caps lock just flash on shutdown and the system just hangs and I have to do a manual reset.

I will look into it more as time permits.

---

### Post by flanagan on 2008-11-30
> **Orographic said:**
> So, do I have to insert that linked command into terminal each time I shut down? That's a bit complicated if my wife for example is using the computer.

The *ln* command, assuming it works for you, is once and done.

---

### Post by PierreDeKat on 2008-11-30
> **Orographic said:**
> Today I did some 'My Documents' backups and twice to different external drives my Intrepid system wouldn't shut down after moving stuff to trash can and then deleting it.
Ubuntu has a rather troublesome way of handling "trash" with regard to external drives. 

When you are supposedly "moving something to trash", you are in fact moving it into a hidden folder on the same drive called ".Trash-1000".

Theoretically, if you empty your trash can before you unmount this drive, the files do actually get deleted.

Or if you unmount the drive the official way, you will be asked if you would like to empty the trash can first -- probably "yes".

But if you yank a USB drive out before you officially unmount it, you may start to have some real problems. 

The files won't be deleted, and if you're lucky, they will show up in your trash bin the next time you plug in that same drive.

But if you're not so lucky, you might wind having to reformat the drive after Ubuntu decides that the file system has gotten corrupted.

Windows will tolerate a corrupt file system to some extent, but Ubuntu goes into panic over it.

Anywho, keep working with Ubuntu. Hopefully, as time goes along, you will become a little more comfortable with it, and it may yet replace Windows for you.

Cheers.

---

### Post by Orographic on 2008-11-30
Yes, I noticed Ubuntu had a confusing way of dealing with trashed files on usb sticks or usb hardrives - they end up on the  external drive after being trashed. I would never just pull a usb key or hard drive out without unmounting it. The deleted files went to trash then I removed them from trash then I either unmounted and shutdown or just shutdown and both methods froze the system. It only happens when doing the above process but is a real annoyance. 

I'm concerned my two external drives may now be corrupted even though I have been very careful. 

I have a lot of images and backed up files on them and may now have to temporarily move these files and reformat...

---

### Post by Orographic on 2008-12-02
Well, I couldn't resist re-imaging my drive with Intrepid and having a look at this issue again. Strangely, I can't replicate the problem as now when I try to move files from my external drive into Garbage Bin it wont give me that option but only says something like, 'Cannot move files to Garbage Bin, Do you want to permanently delete them?' 

I've also found out via Google that you can add the 'Delete' option quite easily in Nautilus by heading to Edit>Preferences>Behaviour and selecting the delete option there. Then you have the option of Delete or Move to Garbage.

NB: I may have accidentally deleted the temporary trash files on my external drive myself - there was a recycle file there. Could this have caused my initial problems?

---

