---
title: "Nautilus is only helper app"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by pmooney78 on 2012-10-26
Pretty much every application that I use that has the ability to launch files seems to try to use Nautilus as the application to open every single file, regardless of file type. So, when I right-click on a file in Thunderbird's "Saved files" dialog and choose "open file," I get an Nautilus window popping up with an error message saying "Could not display '{name of file}.' The location is not a folder." This also happens in Firefox, Chromium, Zotero (as a Firefox extension and standalone), etc. etc. etc. etc.

I have no idea how to fix this, and haven't been able to find any other threads on the topic that wound up being helpful. Any help is much appreciated.

---

### Post by pmooney78 on 2012-10-29
Bump.

---

### Post by newb85 on 2012-10-29
Not sure how this happened.

Try right-clicking one of these files, Properties>Opens With (tab).  This should allow you to set the default application for all files of that type to something more sensible.

---

### Post by pmooney78 on 2012-10-29
Thanks, newb85. I've already tried this -- they open correctly if I double-click them from Nautilus. They just don't open correctly from any other applications.

---

### Post by pmooney78 on 2012-10-31
Bump.

---

### Post by pmooney78 on 2012-11-03
Bump.

---

### Post by newb85 on 2012-11-03
Do you have either Ubuntu Tweak or gconf-editor installed?

---

### Post by grahammechanical on 2012-11-03
I do not have a clear understanding of your problem. Perhaps this is a reason why people cannot give much help.

Is your problem?

a) Applications using Nautilus to open files.
b) Thunderbird and some other programs not being able to open files listed as 'saved files.' Would 'saved files' be the same as 'recent files?'

Nautilus is not a standalone file manager. It is integrated into the desktop. This is why a right click on the desktop will give the option to create a new folder. Applications use Nautilus to save and open files to do away with the need for the application to have its own method of saving and opening files.

These files that you are trying to open, are they on a separate partition to Thunderbird and the other programs? If so, is that partition mounted?

I use LibreOffice from 12.10 on one partition but the files I access are on another partition. The Libreoffice 'recent files' menu will not open those files until I mount that partition where the files are stored.

Could thhis be your problem?

Regards.

---

### Post by pmooney78 on 2012-11-03
@newb85: Both are now installed. Will happily await further suggestions.

@grahammechanical: the problem is that applications that make filesystem objects visible (Thunderbird's saved files dialog, Firefox's Downloads window, files linked in my Zotero library, downloads from Chromium, etc.) often have an "open this file" option of some kind or another. When I select this option, regardless of what application I'm trying to do it from, I get a Nautilus window complaining that the location I'm trying to open is not a file. So, if I download a spreadsheet in Firefox and right-click the spreadsheet name, then choose "Open," I would expect that LibreOffice would launch, then open the spreadsheet. Instead, what I get is Nautilus coming up and displaying a dialog that says "Could not open Grade sheet.ods. The location is not a file."

I do understand that partitions have to be mounted in order for data stored on them to be accessible. In no case has this been the cause of the problem. In all cases, with mounted partitions, I get the same response: Nautilus complaining "Could not open {file name}. The location is not a file."

I don't know whether "saved files" is the same as "recent files." I can't find a "recent files" dialog box in Thunderbird.

---

### Post by newb85 on 2012-11-03
> **pmooney78 said:**
> Both are now installed. Will happily await further suggestions.

Open Ubuntu Tweak.  Admins at the top.  File Type Manager bottom-left.  Check that the file types in question have an appropriate app associated with them.

---

### Post by pmooney78 on 2012-11-03
I've just checked, and they do indeed seem to have associated applications. I've attached a screen shot showing a section with file types I've been having trouble opening -- OpenDocument files -- but, again, it doesn't seem to be related to specific file types: it's everything. =(

---

### Post by pmooney78 on 2012-11-05
Well, upgrading to Oneiric seems to have overwritten whatever configuration files were causing the problem. Everything seems to be working fine now. Marking the thread solved. (=

---

