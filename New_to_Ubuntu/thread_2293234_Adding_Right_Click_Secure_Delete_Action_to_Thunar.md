---
title: "Adding Right Click Secure Delete Action to Thunar"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by Naja_Linux on 2015-09-03
Hello all, new to Ubuntu (Studio 14.04 with upgrades on PC), returning to Linux after a decade.
I was very  impressed with the ease of installation and all the software that installs easily and works so well.

One thing I value is securely erasing files from the filesystem.  I've set up an action in Thunar (file manager) that runs this command:

/usr/bin/shred -u -z %f

It's set up to delete, remove and overwrite finally  with zeros one file that is selected in the manager at a time.

I would like to, instead, write a script that does the work, but that displays (a dialog? a terminal?) something that shows which file(s)
are selected and asks if I am sure, then allows to choose cancel or engages the action (as above).  I know there are graphical toolkits
that should make the graphical display trivial to accomplish (I've never worked with these, but see references frequently.)  Could this
all be best accomplished with a bash script?  I have some (rusty old) knowledge working with bash, but not sure how to pull in a 
dialog. Am I reinventing wheels here or is this a worthy pursuit?  

Thanks for help, 

NL

---

### Post by HermanAB on 2015-09-03
Shred doesn't really work on a modern file system, due to journaling and also doesn't work on a modern solid state disk drive, due to block remapping.  Rather encrypt the whole disk with LUKS, or use ext4 per file encryption, in which case, you can just do simple deletes.

---

### Post by Naja_Linux on 2015-09-16
Thanks for this info: it takes less effort to delete files rather than shred them, even with a shortcut.
Even with a journalling file-system (ext-4) on an SSD, would it still be more secure to over-write with 0's?

Thanks

---

### Post by HermanAB on 2015-09-16
On an SSD, overwriting deleted files doesn't help and zeroes would be the wrong value to use anyway, since the erased state is all ones.  A SSD is managed by a little processor (just like a HDD is managed by a drive controller), and the user doesn't have direct access to the media.  The controller can remap blocks for wear leveling, so when you overwrite a file, there is no guarantee that you are in fact overwrite a previously used block, unless you first format the whole thing.

The only proper security is to encrypt the whole SSD.  Then one day, when you want to irretrievably delete it, hit yourself upside the head with a brick to forget the password...

---

