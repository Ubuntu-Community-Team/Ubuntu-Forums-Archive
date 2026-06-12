---
title: "What are Ubuntu items&quot;?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-11-08
In Windows, I go to the C: drive, open Windows File Manager, and display all the folders on the C: drive. Then I click on Edit > Select All. Finally, I right-click on the selected list, and click on Properties. What results is a total of all the FILES and FOLDERS on my computer in all the Windows folders. For Windows, this is usually about 55,000 files and 5,000 folders, or close to that.

In Ubuntu, I open Nautilus as root and then display all the folders in the / folder. Then I click on Edit > Select All. Finally, I right-click on the selected list, and click on Properties. What results is a total of all the ITEMS on my computer in all the Ubuntu folders. For Ubuntu, this is usually about 475,000 items. 

When Ubuntu reports that there are 475.000 items in Ubuntu on my computer, exactly what are these "items"?  What does the items total consist of?

JBA2337

---

### Post by scragar on 2008-11-08
Because ubuntu is linux, and lists devices as places on the file system(check /dev), and uses real libraries, instead of windows broken idea of dll's(which don't work nearly as well).

Oh, and a directory is a few items in of itself, first there's the link to it in it's parent, then there's it's own to itself(.) and it's own link back to it's parent(..), where windows will only list a single item, for linux that's 3...

Oh, and I forgot links to things.

---

### Post by ggaaron on 2008-11-08
Yeah, many things in Unix like systems are shown as files - for example whole /dev and /proc directories are fake. This are not files written on disc. 475.000 seems quite much but it can be, GNU+Linux has many more features pre-installed not to mention a manual and probably an info page for most programs.

---

### Post by JBA2337 on 2008-11-08
I forgot to mention, I am now using the new Ubuntu 8.10 "Intrepid Ibex". Maybe it show more "items" than the previous Ubuntu 8.04.

I am still not too clear on what an "item" is. From the previous answers I understand that an item can be almost anything in Ubuntu/Linux. That would include file folders (directories), actual files, links to files, links to folders, links to devices, or links to anything else.

I guess that explains why Ubuntu has so many more items than Windows.

Thanks for your answer.

JBA2337 :D :D

---

### Post by ggaaron on 2008-11-08
Item is just a word used in nautilus, I'd assume that it means file=) And as really many things are represented in Unix-like systems as files there is a lot of them.

---

### Post by Kellemora on 2008-11-08
Hi JBA

I think someone already said this, but to be a little more clear.

You have a FOLDER named /dev (that's item 1)
Inside this folder are lots of files and a few folders, (over 3000 of them, but for clarity.
You have a Folder named /disk (usually contains 4 folders (that's item 2)
You have a Folder named /by-label (that's item 3)
Up to this point WinDOZE has not counted anything.
But you open this Folder named /by-label and you will find a document for each major partition.  In my folder there are three documents (items 4, 5 and 6 in Linux)  Items 1, 2 & 3 in WinDoze.

Had I got to the file named /media for this example, you will find a Folder for each device, like your CD or DVD, Floppy Drives, etc.
Each Folder is an Item that represents the device.  So these are counted to, along with the drivers, mtab file, etc.

Windows only counts files and then they don't count all files, I don't think hidden files are counted unless you unhide those folders.

That's why they use the word ITEMS instead of files!

Hope that helps!

TTUL
Gary

---

