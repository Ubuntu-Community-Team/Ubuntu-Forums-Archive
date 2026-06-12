---
title: "evolution problems"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Falc7 on 2008-05-28
I am trying to set up evolution so that it can see all my old mails (i used outlook express before in windows) as well as do the obvious like send and recieve emails now.
However i think i put some wrong information in when it asked me for the server and stuff, because now when i try to send an email through evolution, or check for new emails. Evolution just seems to be eternally 'waiting' or 'sending'. However the progress meters don't even start.

Also, when setting up my account (using the old email address ofc) it didn't ask me for my password for the email address :confused:

When i click preferences, and click this email address, edit, and look at the receiving email configuration, and i try to check for supported types of authentication, it never seems to get back to me with an answer.

---

### Post by stchman on 2008-05-28
> **Falc7 said:**
> I am trying to set up evolution so that it can see all my old mails (i used outlook express before in windows) as well as do the obvious like send and recieve emails now.
However i think i put some wrong information in when it asked me for the server and stuff, because now when i try to send an email through evolution, or check for new emails. Evolution just seems to be eternally 'waiting' or 'sending'. However the progress meters don't even start.

Also, when setting up my account (using the old email address ofc) it didn't ask me for my password for the email address :confused:

When i click preferences, and click this email address, edit, and look at the receiving email configuration, and i try to check for supported types of authentication, it never seems to get back to me with an answer.

OE uses dbx files and Evolution uses mbx files.  Two completely incompatible formats.

You will need to convert the dbx to mbx.  There is a free CLI utility for Windows that you can use.

The easy way is to install Thunderbird on your Windows machine and import the OE files.  Thunderbird will convert them.

---

