---
title: "email notification of backup logs.."
date: 2008-12-05
forum: Programming Talk
---

### Post by Mia_tech on 2008-12-05
guys I have a script that backsup my home folder and I would like to add a mail command that emails me the logs after backup is done... could anyone suggest a simple way of doing this?...

thanks

---

### Post by slavik on 2008-12-05
I think sendmail can be used as a simple command line mail program :)

EDIT: nvm, just tried the above, it didn't work ...

---

### Post by ghostdog74 on 2008-12-05
```

mailx -s "test" root < file

```

---

### Post by Mia_tech on 2008-12-05
> **ghostdog74 said:**
> ```

mailx -s "test" root < file

```

yes.. but I actually need that msg to go out to a real smtp server and be delivered to my email address.... I type mailx --help but I see no settings for specifying mail server, email address etc..

---

### Post by ghostdog74 on 2008-12-05
> **slavik said:**
> I think sendmail can be used as a simple command line mail program :)

EDIT: nvm, just tried the above, it didn't work ...

it should work, most simplistically
```

sendmail  root < file

```
otherwise, you need to check your sendmail setup.

---

### Post by slavik on 2008-12-05
```

slavik@slavik-desktop:~$ sendmail
Exim is a Mail Transfer Agent. It is normally called by Mail User Agents,
not directly from a shell command line. Options and/or arguments control
what it does when called. For a list of options, see the Exim documentation.
slavik@slavik-desktop:~$ 

```

---

### Post by ghostdog74 on 2008-12-05
> **Mia_tech said:**
> yes.. but I actually need that msg to go out to a real smtp server and be delivered to my email address.... I type mailx --help but I see no settings for specifying mail server, email address etc..
mailx is a client. if you are sending emails internally in your network, you should setup your MTA properly. Check your sendmail documents. Otherwise, you should have no problem sending out emails to the internet

---

### Post by ghostdog74 on 2008-12-05
> **slavik said:**
> ```

slavik@slavik-desktop:~$ sendmail
Exim is a Mail Transfer Agent. It is normally called by Mail User Agents,
not directly from a shell command line. Options and/or arguments control
what it does when called. For a list of options, see the Exim documentation.
slavik@slavik-desktop:~$ 

```

you are using Exim as MTA, while i don't have Exim. I only have sendmail. So you should probably use something like
```

exim <options>

```
and not 
```

sendmail <options>

```
unless maybe you have some aliases.

[Reference](http://www.exim.org/exim-html-3.20/doc/html/spec_5.html)

---

### Post by psusi on 2008-12-05
If you have cron run the backup script, it mails you the output of jobs by default.  You just need to install and configure a mail server to get it.

---

### Post by Mia_tech on 2008-12-05
guys I just need a simple smtp mailer application...... who can send mail to my mail server out on the internet like eg: mail.google.com NOte: don't send mail to that server it is just an example"... and in turn that server would relay the email to the appropiate address.. maybe I'm just thinking windows here... but there is a ton of smtp mailer application in windows like "sendmail", "mailsend", "blat" etc.. that you can script, and I"m looking to do the same in ubuntu without installing any services like mail servers, postfix or what have you...

---

### Post by mssever on 2008-12-06
> **Mia_tech said:**
> I"m looking to do the same in ubuntu without installing any services like mail servers, postfix or what have you...
That's what Postfix and friends are for. Of course, you could also use Python's excellent smtplib module and write yourself a little mailer with very little effort. Maybe one exists already, but it would be merely a special case of an MTA such as Postfix.

EDIT: Here's a (slightly-modified) code snippet from one of my projects to illustrate what I mean:
```
[COLOR=#008000]**import**[/COLOR] [COLOR=#0000ff]**smtplib**[/COLOR]

[COLOR=#408080]*# snip*[/COLOR]

msg [COLOR=#666666]=[/COLOR] [COLOR=#ba2121]"From: [/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#bb6622]**\r\n**[/COLOR][COLOR=#ba2121]To: [/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#bb6622]**\r\n**[/COLOR][COLOR=#ba2121]Subject: [/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#bb6622]**\r\n**[/COLOR][COLOR=#ba2121]Date: [/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#bb6622]**\r\n**[/COLOR][COLOR=#ba2121]Content-Type: [/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#bb6622]**\r\n\r\n**[/COLOR][COLOR=#bb6688]**%s**[/COLOR][COLOR=#ba2121]"[/COLOR] [COLOR=#666666]%[/COLOR] (
    config[[COLOR=#ba2121]'email_from'[/COLOR]],
    toaddrs,
    message_subject,
    message_date,
    [COLOR=#ba2121]"text/plain"[/COLOR],
    message_body,
)

[COLOR=#408080]*# smtpinfo is a dictionary containing connection and message info*[/COLOR]

s [COLOR=#666666]=[/COLOR] smtplib[COLOR=#666666].[/COLOR]SMTP(smtpinfo[[COLOR=#ba2121]'server'[/COLOR]], smtpinfo[[COLOR=#ba2121]'port'[/COLOR]])
[COLOR=#008000]**if**[/COLOR] DEBUG:
    s[COLOR=#666666].[/COLOR]set_debuglevel([COLOR=#666666]1[/COLOR])
s[COLOR=#666666].[/COLOR]ehlo()
[COLOR=#008000]**if**[/COLOR] smtpinfo[[COLOR=#ba2121]'authentication'[/COLOR]]:
    [COLOR=#008000]**if**[/COLOR] smtpinfo[[COLOR=#ba2121]'use_tls'[/COLOR]]:
        s[COLOR=#666666].[/COLOR]starttls()
        s[COLOR=#666666].[/COLOR]ehlo()
    s[COLOR=#666666].[/COLOR]login(smtpinfo[[COLOR=#ba2121]'login_name'[/COLOR]], smtpinfo[[COLOR=#ba2121]'password'[/COLOR]])
result [COLOR=#666666]=[/COLOR] s[COLOR=#666666].[/COLOR]sendmail(config[[COLOR=#ba2121]'email_from'[/COLOR]],toaddrs,msg)
s[COLOR=#666666].[/COLOR]quit()
[COLOR=#008000]**if**[/COLOR] result: [COLOR=#408080]*# This means that one or more destination addresses were unsuccessful*[/COLOR]
    [COLOR=#008000]**for**[/COLOR] i [COLOR=#aa22ff]**in**[/COLOR] result:
        [COLOR=#008000]**print**[/COLOR] i

```

---

### Post by Mia_tech on 2008-12-06
wow, this has proven to be more difficult than what I thought, one of my server is running 2003 server and no sort of exchange or mail server is running, and I manage to send myself all sort of emails notifications.... and wanted to take the same approach in my ubuntu box, but I'll guess I will install postfix..

thanks all

---

