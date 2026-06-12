---
title: "Help me make a website form!"
date: 2009-09-08
forum: Programming Talk
---

### Post by gjoellee on 2009-09-08
I am working on a several website forms. They shall all be separate. I just need help with two of them.

1. I have the form ready with all except for one thing... I want the form to be sent to an e-mail address when I click the "Send" button. I am using ```
<form action="mailto:gjoellee@stupidreality.org"></form>
``` but that means that the user have to deal with a third party program like Evolution, or Thunderbird.

What I need is a form that just send all the form content to me just be pressing the "Send" button. Not be pressing "Send" then click send again with i.e Thunderbird.


2. All the HTML has been done here as well. What I need is that a user should be able to attach an image with the form, (with size limits of course).

Thanks :P

---

### Post by januzi on 2009-09-08
Is there php on the server ? You could try phpmailer for both 1. and 2. 
As for 2., there should be enctype="multipart/form-data" in the form tag. Attached file will be in the $_FILES.  After that You move_uploaded_file (with is_uploaded_file) to proper dir and:
a) $content = file_get_contents( $path.$file ) + AddStringAttachment()  
b) AddAttachment() 

Don't forget to set smtp login and pass.


No php ? Take a look at form2mail.

---

### Post by gjoellee on 2009-09-08
Thanks. I found a tutorials now anyways....

---

