---
title: "[python] How can I display images of the email body content in gtk application ?"
date: 2011-04-15
forum: Programming Talk
---

### Post by Yoana148 on 2011-04-15
Hello everyone,

  I need to display email body content in gtk application.
  I am using following code for that:

  ```

  obj = imaplib.IMAP4_SSL('imap.gmail.com', 993)
  obj.login('username', 'password')
  obj.select('INBOX', readonly=True)
  resp, msg = obj.uid('FETCH', uid, '(RFC822)')
  msg_str = email.message_from_string(msg[0][1])
  
```
  
  here, "msg_str" contains binary data and <img> tag for the images. as shown below:

  <img height=3D"336" src=3D"cid: xyz" width=3D"509" border=3D"0">

  I have few questions from this:
  1) How can I display original images from the binary code in gtk widget?
   Note : I am using webkit view for displaying html email body content.
  2) Is it possible to display images from the content id and it's server address (here, xyz)
  
 could anyone guide me ?

---

