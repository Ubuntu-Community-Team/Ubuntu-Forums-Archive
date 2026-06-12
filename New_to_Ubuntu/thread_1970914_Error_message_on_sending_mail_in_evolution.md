---
title: "Error message on sending mail in evolution"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-01
Hi all, 
when I send mail in evolution, after the mail has been sent successfully, I get the following error message:
```

The reported error was "Failed to append to mbox:/home/glenn/.local/share/evolution/mail/local#Sent: Invalid folder URI 'mbox:/home/glenn/.local/share/evolution/mail/local#Sent'
Appending to local 'Sent' folder instead.".

```
Has anyone else experienced a similar error? What can I do to fix this?

Glenn.

---

### Post by Snoopy_5_1 on 2012-05-06
Hy there,

have the same problem but still dont know how to fix it :(

---

### Post by Senior_Buckethead on 2012-05-06
Hey Snoopy,
It's just telling you it can't copy the email to your local folder 'sent' because it doesnt recognise the address, so its putting the mail in the default 'sent' folder.
All you have to do if you want the mail in your local folders sent folder is click and drag or right mouse click and go 'move to folder' and select 'sent' or 'sent items' or whatever you call your local mail sent items folder.
The error message is just an annoyance.

Glenn.

---

### Post by pablo180 on 2012-05-07
Did either of you recently upgrade, e.g. to 12.04? If so it is due to Evolution no longer using mbox for mail storage, you should have had a warning about the change the first time you opened Evolution after the upgrade. 

[This thread has an explanation of how to stop this message]("http://ubuntuforums.org/showthread.php?t=1860994")

Basically evolution is still trying to use your old folders for drafts and sent items and you need to re-select the draft and sent folder under Edit > Preferences > Email Accounts > Edit > Defaults and ensure you select the ones under **On This Computer** and not the localhost ones (e.g. not pablo@localhost). You can then also untick the localhost account to stop it from appearing.

---

### Post by Senior_Buckethead on 2012-05-07
> 
Did either of you recently upgrade, e.g. to 12.04? If so it is due to Evolution no longer using mbox for mail storage, you should have had a warning about the change the first time you opened Evolution after the upgrade. 

Would be nice to have a warning BEFORE we upgrade, so we are not pointlessly posting to forums on a problem bought about by some brainless developer who has no foresight.

---

### Post by Snoopy_5_1 on 2012-05-12
Thanks that solved my problem ;)
That massage was really anoing glad they is gone ;)

---

