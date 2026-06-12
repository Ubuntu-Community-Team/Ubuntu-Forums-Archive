---
title: "HTML 5 Contact Form"
date: 2014-05-12
forum: Programming Talk
---

### Post by erotavlas on 2014-05-12
Hi,

I'm new of HTML especially the latest version. I would like to know if it is possible to write a simple contact form in HTML 5 without using PHP. I don't want to use server if it possible.
Thank you

---

### Post by Erik1984 on 2014-05-12
What do you want to do with the entered data? If you want to process it into a central storage you need server side code. But that doesn't have to be PHP, it can be any language. It is possible to have small server side code with for example node.js [http://nodejs.org/](http://nodejs.org/) So in that case you can use the JavaScript syntax on both sides (client and server). But that situation is not so different from having an apache server with PHP running, or a Java server, or Python or...

You can use jQuery to easily write code to send custom data to a server, for example : [http://api.jquery.com/jquery.get/](http://api.jquery.com/jquery.get/)

---

### Post by SeijiSensei on 2014-05-12
You can POST a form to an email address with:
```
<form action="mailto:someone@example.com" enctype="text/plain" method="POST">
```

 See [http://www.techrepublic.com/article/set-up-an-html-mailto-form-without-a-back-end-script/](http://www.techrepublic.com/article/set-up-an-html-mailto-form-without-a-back-end-script/) for an example.

---

### Post by erotavlas on 2014-05-13
Yes, I tried your solution but when I click on send message, the browser open the email client as  thunderbird instead to send directly the message.
For instance my code is:
```

<form id="ContactForm" action="mailto:photo_music_frandina@libero.it" enctype="text/plain" method="post">
<div>
    <div  class="wrapper">
        <span>Full Name:</span>
        <input placeholder="Please enter your name" type="text" class="input" tabindex="1" required autofocus>
    </div>
    <div  class="wrapper">
        <span>E-mail:</span>
        <input placeholder="Please enter your email address" type="email" class="input" tabindex="2" required>
    </div>
    <div  class="textarea_box">
        <span>Message:</span>  
        <textarea name="textarea" cols="1" rows="1" tabindex="3" required></textarea>
    </div>
    <div class="wrapper">
        <span>&nbsp;</span>
        <!-- <a href="#" class="button1" onClick="document.getElementById('ContactForm').reset()"><span></span><strong>Clear</strong></a>
        <a href="#" class="button1" onClick="document.getElementById('ContactForm').submit()"><span></span><strong>Send</strong></a> -->
        <input type="submit" name="submit" id="submit" value="Send Message" />
        </div>
    </div>
</form>     
           

```
Do I make some mistakes?
Thank you

---

### Post by ofnuts on 2014-05-13
> **erotavlas said:**
> Yes, I tried your solution but when I click on send message, the browser open the email client as  thunderbird instead to send directly the message.


That's the expected behavior if you have a mailto: url. 

Maybe you should ask yourself what is the purpose of the contact form. Either it is used to send an email to someone in the end, then the mailto: solution isn't that bad, even if it assumes industrial-grade spam filters for the target mail address, or it's just strings of characters that you put somewhere (DB, flat files) but then something has to handle this, which means server-side code.

---

### Post by erotavlas on 2014-05-16
Ok, you are right. Thank you

---

