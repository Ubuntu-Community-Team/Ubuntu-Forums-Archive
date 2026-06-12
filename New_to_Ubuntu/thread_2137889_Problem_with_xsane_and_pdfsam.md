---
title: "Problem with xsane and pdfsam"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by mefistochen on 2013-04-22
Hallo, 

I was creating a pdf file via an export of an open office document and another pdf file via xsane (scanned). I merged those 2 files via pdfsam but unfortunately the pdf-file (which consists of 2 pages) shows one little and one very big pdf page. Do you understand the problem? 

I don't know if the problem is because of settings in xsane or because of pdfsam. But pdfsam works fine when I work with files of the same type (pdf files which are all exported word-documents). Do you know what I can do so that all pages have the same size?

Btw: I wanted to attach an example of such a mixed pdf file her and clicked on "attachments". I was able to do step 1 (upload my file), but wasn't able to do step 2 (drag the file); I don't know how to do this.

Thank you very much for every help!
Mefistochen

---

### Post by r.stiltskin on 2013-04-22
I haven't actually had this problem but the first thing I would check is the image resolution of both documents.  My guess is that you used different settings.  Both programs allow you to specify the resolution: in open office in the "export as pdf" dialog on the "general" tab, check the "reduce image resolution" box and it will offer you several choices of DPI settings.  In Xsane, the main dialog window, just above the "Scan" button, there's a drop-down menu where you'll find choices like 75, 150, 300, etc.

Choose the same setting in both programs.

---

### Post by cmcanulty on 2013-04-22
Install and try pdf mod it makes pages real easy to manipulate

---

### Post by mefistochen on 2013-04-24
Thank you for your answers. I think the reason was the resolution. I had big values there with 1500*1500. 

But I managed it alternatively by scanning the document as jpg and inserting directly into the openoffice document. This also works well for Scribus. So I mark this thread as "solved".

Btw: Today I was able to upload files from a different computer (where I am sitting at the moment and which uses windows vista) to this forum but I don't know why this didn't work with my gnome and ubuntu(12.10). One difference in the behavior was that after uploading the file from ubuntu it didn't appear as an icon in the upload-window so I couldn't remark it for posting. With my windows vista (in both cases I used firefox) it worked better.

Mefistochen

---

### Post by mefistochen on 2013-04-24
Sorry; I am not able to mark the thread as solved. Here

[http://ubuntuforums.org/attachment.php?attachmentid=62807&d=1205686817](http://ubuntuforums.org/attachment.php?attachmentid=62807&d=1205686817)

is an instruction how to mark a thread ad solved but this doesn't work for me because in "Thread tools" I have only the possibilities to choose between 3 possibilities:
- Show printable version
- Email this page...
- Subscribe to this thread...

Would be nice if someone could tell how to mark it as "solved". Thank you!

Mefistochen

---

### Post by r.stiltskin on 2013-04-24
Go to your first post in this thread, click on "edit post", then click on "go advanced", and change the thread Prefix from "Ubuntu" to "Solved".

---

