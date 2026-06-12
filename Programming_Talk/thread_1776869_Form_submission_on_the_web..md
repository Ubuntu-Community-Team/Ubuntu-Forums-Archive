---
title: "Form submission on the web."
date: 2011-06-06
forum: Programming Talk
---

### Post by Shibblet on 2011-06-06
I have a form on my website that I need people to be able to fill out, and submit.  The submission form needs to come to my email address.

I have talked with my web-host, and they don't have CGI scripts for handling this kind of thing.  Unfortunately I cannot change my web-host for stupid reasons, but that's a separate issue.

Does anyone know a how I can get this accomplished?

---

### Post by Thewhistlingwind on 2011-06-06
Sign up for an alternate email.

---

### Post by wojox on 2011-06-06
You signed with a web host that doesn't run PHP?

---

### Post by ameertawfik on 2011-06-06
The easiest way is to use mailto function.  a workable example is given in this link: 
[http://www.w3schools.com/html/tryit.asp?filename=tryhtml_form_mail](http://www.w3schools.com/html/tryit.asp?filename=tryhtml_form_mail)

The only problem you have is that  using mailto function  requires  web browsers to be configured with  POP3 protocol software such Microsoft outlook or Mozilla Thunderbird.


  The other way is to have a google account and create a form in there. Then at your web page, you provide the link to the google form.

i hope that solves your problem

---

### Post by lulled on 2011-06-06
Yeah, PHP that's what I was about to say. Your host probably has PHP (even on Windows hosting, they offer PHP). If you need to freelance that form. Cough. Cough. Let me know. Cough. Cough. :D

---

### Post by linuxforartists on 2011-06-07
Not sure if it would fit your needs, but Google Docs allows you create embeddable forms, and the data is automatically sorted into a spreadsheet.  Super useful and convenient, you only need a Gmail account.

There's a nice video tutorial here: [Using Google Docs form as your WordPress contact form]("http://www.dragonblogger.com/demonstration-using-google-docs-form-as-your-wordpress-contact-form/").

---

### Post by s.fox on 2011-06-07
This appears to be a support thread.  I think it would do better in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").  Moved  :D

---

### Post by Petrolea on 2011-06-07
If they have mail server set up you could use 'mail' function in PHP to send mails (which is very easy to use). You just pass it arguments like email, subject and text and it will be sent.

---

### Post by Shibblet on 2011-06-07
They don't have scripting enabled.  So that's out.  I made a form on Google Docs, but I need the form information emailed to my email address at work, not my google account.

---

### Post by Petrolea on 2011-06-08
> **Shibblet said:**
> They don't have scripting enabled.  So that's out.  I made a form on Google Docs, but I need the form information emailed to my email address at work, not my google account.

Wow, so much trouble just for sending mail, I hope you don't have any bigger projects in mind.

Maybe Gmail has a feature that forwards mails. Check out its settings.

---

