---
title: "Open RTF with RCP application"
date: 2008-09-04
forum: Programming Talk
---

### Post by pjmorce on 2008-09-04
Hello

I have made a little application which uses the OleClientSite object.

I use it to open a RTF file.

My RTF file has a reference to an image on it: ...{INCLUDEPICTURE "img/logo.gif"...

When I open this file directly using MS Word, everything is ok. The image in the document is displayed.

However, when I use my Java Application, the file is displayed but not the image on it. It seems that the image cannot be found.

I modified the RTF file to have the absolute path to the image: ... {INCLUDEPICTURE "d:/img/logo.gif"...

Then I opened the RTF file with my Java application. The document was displayed and also the image on it.

The problem seems to be that when the image is described in the RTF file with a relative path, the image cannot be found.

How can I resolve this problem?

Thanks

Best regards.

[http://greatesttravels.blogspot.com](http://greatesttravels.blogspot.com)

---

### Post by Zugzwang on 2008-09-04
Quick'n'dirty solution: Start your java program from the path your .RTF document is in.

Apart from that: Did you try loading your .rtf file using some non-Windows-only method (note that you're in a Linux forum, so we can't help you here), like lets say into a JEditorPane? You might need to create your own Editor kit based on the one in the JDK that takes care or the directories.

---

