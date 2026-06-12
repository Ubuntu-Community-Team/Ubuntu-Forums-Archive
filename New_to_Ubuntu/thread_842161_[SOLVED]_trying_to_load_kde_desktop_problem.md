---
title: "[SOLVED] trying to load kde desktop problem"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-27
in the terminal midinstall I get this message:

postfix configuration

Please select the mail server configuration type that best meets your   needs.  
 No configuration:                                                      &#9618;   
  &#9474;   Should be chosen to leave the current configuration unchanged.        &#9618;   
  &#9474;  Internet site:                                                         &#9618;   
  &#9474;   Mail is sent and received directly using SMTP.                        &#9618;   
  &#9474;  Internet with smarthost:                                               &#9618;   
  &#9474;   Mail is received directly using SMTP or by running a utility such     &#9618;   
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                &#9618;   
  &#9474;  Satellite system:                                                      &#9618;   
  &#9474;   All mail is sent to another machine, called a 'smarthost', for        &#9618;   
  &#9474; delivery.                                                               &#9618;   
  &#9474;  Local only:                                                            &#8595;   
  &#9474;                                                                             
  &#9474;                                 <Ok>     


what should I do here
I cannot find the correct button to select an option
and which option should I select anyway?

---

### Post by mevets on 2008-06-27
I dont know how this is realated to KDE, but it looks like you are trying to install postfix. Postfix is an email server and if you dont know why you are being asked to configure it, then you probably dont need it and might as well remove it. If you use apt-get to install postfix it will launch a script that prompts what you have shown. I think that most likely selecting 'Internet site' would be alright. You mention you cant figure out how to select an option, pressing ENTER doesnt work?

---

### Post by golgo13 on 2008-06-27
no enter didn't work but I used synaptic in the end and that by passed the problem
thanks for your help anyway

---

