---
title: "Get rid of gedit as default for PDF files."
date: 2013-10-02
forum: New to Ubuntu
---

### Post by mrjacque on 2013-10-02
when I try to open a PDF on Yahoo Mail, gedit is the default for opening the file. Every time I have to search for the Document Viewer. 
How do I change the default or add additional options?

---

### Post by deadflowr on 2013-10-02
The file properties should have an "open with" tab.
Click on that and then there should be a other applications option.
Choose that and slect document viewer.
Then back at the opens with screen, highlight the document viewer and select set as default.

Once affected. the viewer will open for any PDFs.

You can set the defaults for any other file type, like music files.
(Have ogg/or flac files open in one music player, and maybe set mp3s in another.)

Right click to access properties( at the bottom of the dropdown)

---

### Post by mrjacque on 2013-10-04
When I click on the "Open with" tab, the file manager is what comes up and I have to remember which folder and name of the file in order to choose it. The only open option is the gedit, which does not read PDF files.

---

### Post by deadflowr on 2013-10-04
I think our signals are mixed up here.
For some reason I forgot you're using a browser.
I though the file was downloaded.

Which browser are you using?

If you're using firefox, open "edit" then go to preferences.
Now go to Applications and scroll to the Portable Document Format (PDF) 
and see what the setting is.

---

### Post by mrjacque on 2013-10-05
I originally had the preferences set to "Preview in Firefox", changed it to evince, stopped and started Firefox, and it still only has the gedit option for opening it.

---

### Post by Frogs Hair on 2013-10-05
When you right click a down loaded pdf and select open with are you offered a list of applications ? Document Viewer should be on that list and it should remain default when selected.

---

### Post by mrjacque on 2013-10-06
When I try to open a PDF, my options for PDF is gedit(default) and Other... which, when clicked, takes me to Nautilus where I need to find the directory and program to run. No list of executables. If there were at least a list of programs, I would be happy. When I choose what file to use for the PDF, the check box for "Do this automatically for files like this" is blacked out, not selectable.

---

### Post by Frogs Hair on 2013-10-06
From Nautilus you can navigate to the file system . I have located  the evince.desktop file in usr/share applications. but that isn't the correct location and I am still looking . I did this from the Firefox download dialog.

---

### Post by deadflowr on 2013-10-06
> **Frogs Hair said:**
> From Nautilus you can navigate to the file system . I have located  the evince.desktop file in usr/share applications. but that isn't the correct location and I am still looking . I did this from the Firefox download dialog.

The executable is in /usr/bin.
Try /usr/bin/evince.

---

### Post by mrjacque on 2013-10-07
For some strange reason, PDF files now have the option of the Document Reader or evince. Have no idea why it finally changed, gedit is no longer even an option.
Did not even do any updates of the system.
Thanks for your efforts. If I ever decide why it finally started working, I will post.

---

### Post by Frogs Hair on 2013-10-07
Glad your up and running .

---

### Post by N0rbert on 2014-09-23
I solved this problem by removing line
[FONT=Courier New]application/octet-stream=gedit.desktop; [/FONT]
from
[FONT=courier new]~/.local/share/applications/mimeapps.list[/FONT]
(from other [thread]("http://ubuntuforums.org/showthread.php?t=1832661&page=2&p=12289034#post12289034")).

---

### Post by oldos2er on 2014-09-23
Old thread closed.

---

