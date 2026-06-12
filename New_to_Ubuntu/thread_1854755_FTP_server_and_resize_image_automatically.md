---
title: "FTP server and resize image automatically"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by completetech on 2011-10-05
I may have missed it by possibly no searching the correct wording but here is what I am looking for / hoping for.

I would like to take pictures from my EVO and instead of uploading them to picasa I would like to upload to a FTP server I have at home or office.

Then of course once in FTP server in a "pending" folder have them resized then moved into a folder named according to day of the week etc. But here is the kicker.

On the EVO when trying to upload to say picasa, you can choose a caption but not a way to rename the file itself. which is what I am looking for. I want to be able to take a picture of some required pictures for a job I am doing then when taking the picture and choose the FTP server have it prompt for a name. then upload that picture with that picture now being named what I choose and put then in a temporary folder which then of course on the FTP server (ubuntu most likely) will resize it to something of a reasonable size I choose and be then put into a different folder.



Any ideas or suggestions? I am kind of at a loss as to what would do something like this.

---

### Post by Lars Noodén on 2011-10-05
Well, [Don't use FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/), use SFTP instead.  For the resizing, ImageMagick will do the job.  I'm not sure how it is for captions, though

---

