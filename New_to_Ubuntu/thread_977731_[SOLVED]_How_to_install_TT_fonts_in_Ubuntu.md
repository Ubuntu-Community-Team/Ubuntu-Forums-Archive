---
title: "[SOLVED] How to install TT fonts in Ubuntu?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by sillyboy on 2008-11-10
Is there a simple way to install some TT fonts from my Windows (XP) machine
to my Ubuntu machine? :confused: I'm not advanced enough yet for all those command lines, unless it is simple steps using the command line.](*,)

Thanks  :cool:

---

### Post by philinux on 2008-11-10
Install msttcorefonts from synaptic will get you a lot. Or

sudo apt-get install msttcorefonts

---

### Post by redseventyseven on 2008-11-10
If you still have the *.ttf files from your Windows machine, you can copy them into your fonts folder. The folder is located in your "home" directory and is called ".fonts", however it's hidden (all files and folders which begin with "." are hidden by default).

To reveal hidden files and folders, press Ctrl+H in Nautilus (the file explorer).

PS - I am assuming that you have the right licenses to copy your fonts from your Windows machine to another just like that - wouldn't want to be encouraging you to be breaking copyright laws, now, would I? ;)

---

### Post by Kellemora on 2008-11-11
Hi Silly

Just copy and paste them.

If you don't want to have duplicate files for each user of those fonts, put them where Ubuntu puts them
/usr/share/fonts/truetype
This is NOT a hidden file by the way!

Here is another trick!
Some WinDOZE boxes, if you go to the font's folder, you will find you don't have a COPY button to use to copy the font's.

Drop back to Drive C and create a new folder, name it something like FontsBackupFolder

Go back to the windows directory, scroll down to the fonts folder but Don't open it.  Right click on the fonts folder and you should get the COPY folder button.
Select that.
Then go back to your new empty folder and hit Paste.

Unfortunately, doing it this way you will end up with a folder named fonts inside of the fonts backup folder.
You can open the fonts folder HERE and select all, then hit copy.
back up one folder and paste them into the folder you made.
After they are pasted there, you can delete the folder named fonts that appeared inside that folder.

In any case, you can then copy and paste one or all the fonts to your Ubuntu font's file.  But there is a method to that to.

I assume you have a shared folder on your Winders machine.
Copy your fonts folder to the shared folder ON the Windows Machine, NOT to the Shared Folder on the Ubuntu machine.  It might mess up permissions.
Now, go to your Ubuntu machine and fetch your fonts folder from the Shared folder on the Windows machine.
Then Paste it to your desktop or somewhere handy.
Select All the font's and hit copy again.  This insures you have the fonts from the desktop and NOT from the windows machine.

Now you can paste them into the /usr/share/fonts/truetype folder and no permissions will have been altered.

TTUL
Gary

---

### Post by sneeks on 2008-11-11
there is a video tutorial on this,on youtube and blip.tv.
look for sneekylinux.
p.s. blip is better quality.

---

