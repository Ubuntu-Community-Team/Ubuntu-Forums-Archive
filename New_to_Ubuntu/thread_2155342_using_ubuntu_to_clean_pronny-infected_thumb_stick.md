---
title: "using ubuntu to clean pronny-infected thumb stick"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by kobudo on 2013-06-18
Hey all, dumb question for those who know stuff:

I have a thumb drive that picked up an Autorun.AC worm (win32/pronny) from another person's PC, and my question is this: if I stick the removable media into my Ubuntu desktop and delete the autorun.inf and the bait .exe files associated with the worm, will my thumb drive be safe for windows computers again? Are there any other areas to check (master boot record [?], etc) with a worm like this?

---

### Post by MidnightGrey on 2013-06-18
Run a virus scan over your USB just to be safe.

If your thumb drive isnt too big, copy your files to a temp folder, format the USB, and then replace your files / virus scan the new USB.

---

### Post by HermanAB on 2013-06-18
Howdy,

Just delete the file.  Linux is basically honest.  It shows you everything that is in the file system and it allows you to manage anything that is in the file system. So, delete it.  If it then shows you nothing, then there really is nothing.

I know that is rather hard to fathom for a long term abused Windows user, but it really is that simple.

---

### Post by user_of_gnomes on 2013-06-18
You can run clamav on the usb key after deleting the files. or beforehand.

---

### Post by newb85 on 2013-06-18
Ubuntu does have hidden files (the filenames start with a "."), but it's different from Windows.  They're only hidden for convenience, and can easily be viewed by hitting Ctrl+H in Nautilus (the default file browser in Ubuntu).  I don't think you can have that kind of hidden files on a flash drive from Windows, though.

---

### Post by kobudo on 2013-06-18
Thanks, all! Solved!

Oh, and if any other new people come across this thread with a similar issue, the terminal command to scan the drive is:
> clamscan -r /media/your_thumb_drives_name

---

### Post by user_of_gnomes on 2013-06-18
don't forget sudo clamfresh as well to update the database.

---

### Post by Grenage on 2013-06-18
If you don't have access to clam (or simply don't trust it), you can simply wipe the drive and the boot record.

---

### Post by sudodus on 2013-06-18
> **Grenage said:**
> If you don't have access to clam (or simply don't trust it), you can simply wipe the drive and the boot record.
+1

You can use a shell-scipt to help wiping the intended target USB pendrive and nothing else. See [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

