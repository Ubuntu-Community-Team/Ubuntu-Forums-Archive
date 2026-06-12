---
title: "Need help ASAP with Abiword document recovery."
date: 2008-10-24
forum: New to Ubuntu
---

### Post by KaylaF on 2008-10-24
Ubuntu just crashed on me and I lost a paper that's due tomorrow.  I had autosave activated, but I had saved the file on my external hard drive and the file I had saved had disappeared when my computer restarted.  Is there a way I can retrieve the file, or is it lost for good?

---

### Post by igknighted on 2008-10-24
Yikes, that's tough... the problem with the external drives is that if they aren't unmounted properly (as in a hard reboot, or pulling the cord), recent changes are sometimes not written to the disk permanently yet.  The drive holds a cache and then writes when there is enough to justify it, or it gets a signal to unmount.  If it did that, you might have lost the autosave copy.

EDIT: Your computer spontaneously restarted?  That sounds like a hardware issue, or perhaps a power fluctuation.

---

### Post by KaylaF on 2008-10-24
Yeah, it sounds like it's lost.  I'll try to beg an extension off the professor.  Unless there might be a partial copy somewhere?  I've got autosave set often enough that it should have saved somewhere else when I was half way through, before I saved it onto the external hard drive, unless I'm totally off-base about how that function works.   

The system has crashed on me like this once before in the last week or so.  It's kind of an old computer, but I never had this type of crash when I was using Gutsy.

ETA:  How would I determine what's making the system crash?

---

### Post by igknighted on 2008-10-24
Did you try just opening Abiword?  Many word processors (not sure about abiword) try to auto-recover if they were shut down like that, it might know where it is hidden.

---

### Post by KaylaF on 2008-10-24
I did try that; it opened a blank document.  The only think I can think of would be that it may have saved a copy in a different location before I had saved onto the external hard drive.  Is that a possibility?  And if it is, where should I look for the file?

---

### Post by igknighted on 2008-10-24
is there anything that looks promising in your /tmp directory?

---

### Post by KaylaF on 2008-10-24
No.

---

### Post by KaylaF on 2008-10-24
I've poked around a couple other places and it doesn't look like I'm going to find anything.  

If you know of a way to figure out what's making my computer crash so I can work on that over the weekend, I'd really appreciate it.

Thanks for your help.

---

### Post by Baelus on 2008-10-24
I'm not sure when this was written, but it may still work.

> Recovering From Crashes

Your best defence against computer crashes is to save your work frequently. The more frequently you save the less work you will lose in the event of a crash. Having said that, if AbiWord crashes before you have saved your work there may be some hope. Every five minutes AbiWord creates backup files of your working documents. With a bit of luck, you can use these backups to retrieve some of your lost work.

AbiWord appends a .bak~ to the names of the files it backs up. For example, the backup file for demo.rtf will be named demo.rtf.bak~. These backup files are placed in the same directory as the original file.

If your document does not have a name, AbiWord makes backup files called Untitled1.bak~, Untitled2.bak~ and so on. It leaves these files in your home directory.

The next time you start AbiWord, you can open these backup files as you would any other document. [SCREENSHOT] If you find that this file contains lost work, use the Save As button to save the document with a new name. You can then copy and paste the changes to your original document.

You can configure AbiWord to autosave your work more frequently by selecting the Tools->Preferences menu, then selecting the Preference Schemes tab. [SCREENSHOT] Just change the Auto save current file every 5 minutes entry to some other number.

Here's the whole post:

[http://wclp.sourceforge.net/documentation/userguide/ch02.html]("http://wclp.sourceforge.net/documentation/userguide/ch02.html")

---

### Post by dbcooper2013 on 2013-04-18
Thank you!  I just found this thread after losing a Research Paper to an AbiWord crash.  It had stopped autosaving the paper in my dropbox folder because the paper was "open in too many programs" or something to that effect, and when I tried to use "save as" to save to a different location, AW crashed.  But after finding your post, I opened my terminal and ran "ls Dropbox | grep abw" and there my file was!  Thank you so much!

---

### Post by oldos2er on 2013-04-18
Closed, please don't bump old threads.

---

