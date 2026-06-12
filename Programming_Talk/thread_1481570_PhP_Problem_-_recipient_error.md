---
title: "PhP Problem - recipient error"
date: 2010-05-12
forum: Programming Talk
---

### Post by MasterNetra on 2010-05-12
I'm trying to use the formmail.php script from [http://www.tectite.com/](http://www.tectite.com/) but having some issues, it won't recognize my @live.com address I think.

Here is the form head I have for the page with my email part censored with "me@live.com" to avoid bots picking up on it.

```

<form method="post" action="formmail.php" name="Ask_the_crew">
    <input type="hidden" name="env_report" value="REMOTE_HOST,REMOTE_ADDR,HTTP_USER_AGENT,AUTH_TYPE,REMOTE_USER">
    <input type="hidden" name="recipients" value="me@live.com" />
        <input type="hidden" name="required" value="email:Your email address,realname:Your name" />
            <input type="hidden" name="subject" value="Ask the Crew - Question" />

```

granted the hidden values aren't part of the "forum head" but the recipients hidden field is relevant. 

Here is the emailed message from the script.

> 
To: ***<censored for forum>***
From: [email]FormMail@www.klinestudio.netai.net[/email]
 
The following error occurred in FormMail :
no_valid_recipients
 **********
Error=The form has an internal error - no valid recipients were specified. 
 
 
email: ***<censored for forum>***
realname: ***<censored for forum>***
 
question: 'test'
submit: 'Send'
Referring page was [http://www.klinestudio.netai.net/krumbsnatchercookies/askk.html](http://www.klinestudio.netai.net/krumbsnatchercookies/askk.html)
SERVER_NAME was [www.klinestudio.netai.net](www.klinestudio.netai.net)
REQUEST_URI was /krumbsnatchercookies/formmail.php
 
User IP address was ***<censored for forum>***
User agent was Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0)


---

### Post by roccivic on 2010-05-13
Excuse me, but I was under the impression that the whole point of a mail form was to avoid revealing your email address to the user. But your mail form requires it in a hidden field.

---

### Post by MasterNetra on 2010-05-13
> **roccivic said:**
> Excuse me, but I was under the impression that the whole point of a mail form was to avoid revealing your email address to the user. But your mail form requires it in a hidden field.
 Its for the php script. Its not seen on the page.

---

### Post by MasterNetra on 2010-05-13
Nvm mind figured out the problem. I used dreamweaver to make a quick edit in the php file and dreamweaver did its magic and crapped up the script. Had to redo it in notepad.

---

