---
title: "php to email w/ attachment"
date: 2007-07-06
forum: Programming Talk
---

### Post by x1a4 on 2007-07-06
Hi,

Does anybody know of a good PHP HOWTO detailing how to send email **with an attachment** from a web form?  

Thank you.

---

### Post by Mr. C. on 2007-07-06
You need to MIME encode the attachment and encapsulate it within the email body.  See:

[http://www.phpguru.org/static/mime.mail.html](http://www.phpguru.org/static/mime.mail.html)

MrC

---

### Post by Modred on 2007-07-06
Check out [this article on multipart-MIME messages](http://www.zend.com/zend/spotlight/sendmimeemailpart1.php).  That handles the email itself.  You'll probably need to set up a temp directory that will be used for uploading the files and then mail the message+file after the upload completes, after which you remove the temp file.

---

