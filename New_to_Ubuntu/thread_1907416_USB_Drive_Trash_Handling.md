---
title: "USB Drive Trash Handling"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-11
Is there a simple reference document anywhere which describes completely how Ubuntu handles deleting files on a USB drive?

If not, I wonder - why not?

As far as I can see from many threads & articles & tests:
If I simply "delete" a file from a USB drive, it will disappear from Nautilus & I can think it is gone, but it is still on the USB in a hidden folder called .Trash-1000 or similar.
It appears momentarily in my own Trash folder, but then disappears from there.
So deleting files does not create any free space on the USB.

If I want to really delete it afterwards, it is no good going to the .Trash-1000/files folder & "delete"ing it, as it will reappear there with a suffix.
That also generates a new file in the .Trash-1000/info folder...

I can remove the file from .Trash-1000 using "Shift + Delete" & confirming I want to delete.
Alternatively, I can delete the whole .Trash-1000 folder & all contents, with Shift + Delete.
*[EDIT: I can delete the whole .Trash-1000 folder & all contents JUST with DELETE.]*

If I want to really delete a file from the USB without it ever going via Trash, I can use "Shift + Delete" at that stage & no .Trash-1000 folder is created at all.
Instead of "Shift + Delete", I could modify Nautilus to include a "Delete" option as well as the existing "Move to Trash" option.
There are corresponding CLI commands too.

Is that it, or are there other subtleties I have not discovered?

Again, it would be good if that was easily available.
When I was having Trash problems a while back, Bluexrider kindly pointed me at the excellent How To:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
but I don't think it actually deals with USB drives.

---

### Post by jkurtisr32 on 2012-01-11
> **2CV67 said:**
> Is there a simple reference document anywhere which describes completely how Ubuntu handles deleting files on a USB drive?

If not, I wonder - why not?

As far as I can see from many threads & articles & tests:
If I simply "delete" a file from a USB drive, it will disappear from Nautilus & I can think it is gone, but it is still on the USB in a hidden folder called .Trash-1000 or similar.
It appears momentarily in my own Trash folder, but then disappears from there.
So deleting files does not create any free space on the USB.

If I want to really delete it afterwards, it is no good going to the .Trash-1000/files folder & "delete"ing it, as it will reappear there with a suffix.
That also generates a new file in the .Trash-1000/info folder...

I can remove the file from .Trash-1000 using "Shift + Delete" & confirming I want to delete.
Alternatively, I can delete the whole .Trash-1000 folder & all contents, with Shift + Delete.

If I want to really delete a file from the USB without it ever going via Trash, I can use "Shift + Delete" at that stage & no .Trash-1000 folder is created at all.
Instead of "Shift + Delete", I could modify Nautilus to include a "Delete" option as well as the existing "Move to Trash" option.
There are corresponding CLI commands too.

Is that it, or are there other subtleties I have not discovered?

Again, it would be good if that was easily available.
When I was having Trash problems a while back, Bluexrider kindly pointed me at the excellent How To:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
but I don't think it actually deals with USB drives.

When you do a normal delete of something on the flash drive, it should be moved to the hidden .Trash directory on that same drive. It should also then appear in your trash bin in nautilus.

I think that the trash bin in nautilus is a collection of all the .Trash items across the entire system. Emptying the trash should delete the contents completely for the respective drives.

---

### Post by 2CV67 on 2012-01-11
> **jkurtisr32 said:**
> When you do a normal delete of something on the flash drive, it should be moved to the hidden .Trash directory on that same drive. It should also then appear in your trash bin in nautilus.
That's how I remember it in the past, but not today.
I just tried several times with 2 different USB drives & whatever I delete usually just appears for a couple of seconds in my own Trash then disappears.
But sometimes stays in my Trash & cannot be deleted because "file does not exist" or something (but is gone if I close & reopen Trash).
This was one reason I was trying to find some good description of what exactly is supposed to happen.

> I think that the trash bin in nautilus is a collection of all the .Trash items across the entire system. Emptying the trash should delete the contents completely for the respective drives.

I don't want to empty my whole Trash - I use autotrash to keep things for 30 days & very often need to fish things out...
But again I wanted to know exactly what is supposed to happen.
Does emptying main Trash really empty all other Trashes?
Surely not other users' Trashes?
Nor Root Trash?
Which then?

None of this is actually causing me a problem at the moment - I can "Shift+Delete" things from my USB OK.
But it is confusing & I would like to find an authoritative guide.
To be able to look up next time I need it!

---

### Post by mcduck on 2012-01-11
Are you removing the drive before you empty the trash, or unplugging it without unmounting? Those would explain the error about not being able to delete a file from trash becasue it doesn't exist.

Anyway, emptying the trash should epmty all the trash directories *that user* has access to. As you noticed, the trash directory created on removable devices has a number in it, that is the same as your user ID.

I just tested this, only to be sure, and any files I delete on removable drives appear corrctly in Trash, and are removed by emptying it.

edit: It also seems that if I unmount the drive before emptying the trash the deleted files will disappear from trash, but reappear there once the drive is connected again. (the trash icon in my panel seems to get confused by this, though, showing full trash icon even when the drive isn't connected and opening the trash shows nothing at the moment)

---

### Post by 2CV67 on 2012-01-11
> **mcduck said:**
> Are you removing the drive before you empty the trash, or unplugging it without unmounting? Those would explain the error about not being able to delete a file from trash becasue it doesn't exist.

No. The drive is & stays mounted & I simultaneously watch the USB & my Trash in 2 Nautilus widows.

Just tried again & got the same result - see attached.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/trash.jpg[/IMG]

---

