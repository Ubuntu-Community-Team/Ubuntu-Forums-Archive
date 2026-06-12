---
title: "Right-click to create a new document"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by Kenkoy on 2014-06-19
Apparently I'm a new user again with a very basic question. I recently installed Ubuntu 14.04 after using 12.04 for a few years. It seems I can no longer create a new document or folder by right-clicking a window in list view when it's full of files.

I need to get to the "New Document" option where I have a couple of rtf and txt templates made. When the window is full of files, there's no clear area to right-click. You're forced to highlight something, which leaves you with only the "Open, Cut, Copy" etc options for the file that you unavoidably highlight. I used to be able to click in a clear spot to the left of one of the existing files.

In the interest of workflow, I prefer not to switch to Icon View just to create a new document. The File Menu > New Document path only gives me "Empty Document" and the templates aren't available there. I've tried creating new ones and they don't show up there, either, so there's nothing wrong with the templates. Besides, workflow - I need the right-click function.

Am I missing something? Since that function is available and works fine when a window has an open space, I'm sure there's still a way to do it when the window is filled up with files. Anybody have an answer?

---

### Post by grahammechanical on 2014-06-19
Use the File menu>New Document>Empty Document. Or File menu>New Folder. Those will place a new document or new folder within the list of other documents. Just tested it.

Regards.

---

### Post by mc4man on 2014-06-19
I believe you're currently out of luck here.
The nautilus menu " File > New Document" was added back in late in 14.04 dev for a ubuntu session but it does not 'access' the Templates folder.

---

### Post by vanadium on 2014-06-20
The bug for "File - New Document" is filed [here](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1317312). It had only two subscribers in the mean time. That there is no possibility anymore to cal the right-click context menu in list view indeed is a bug for which I did not find a report.

---

### Post by Kenkoy on 2014-06-20
The idea of using a template is that you have a pre-formatted file immediately ready for you. For example, I need a txt file that has "Windows" vs "Unix/Linux" as the "Line Ending" option, so that it appears the same when opened in Windows. Try opening the latter in Windows and see the mess that it is. There are several other things which I prefer to have ready-made for various files. I take quick notes while doing research in Linux online. I take those notes to Windows offline and follow through with them.

I agree that it must be a bug, since the function exists in a window that's not filled up. Someone just overlooked allowing for a space to right click when too many files fill the window. If I can find time in the next month (I'm horribly behind schedule), I'll research how to file a bug report. If anyone else cares about this, though, please go ahead and do so. Thanks everyone for your responses.

---

