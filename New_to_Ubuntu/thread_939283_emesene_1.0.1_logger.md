---
title: "emesene 1.0.1 logger"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by joe56 on 2008-10-05
The stock emesene 1.0 ubuntu package wouldn't log conversations for me. I've read that others have had this problem but I could find no solution. I purged emesene and d/led the newest source 1.0.1. I have emesene running and logger enabled. Where should emesene be writing the .db?

---

### Post by meborc on 2008-10-06
there should be a folder caller .emesene in your home folder... it is "hidden" so hit ctrl+H to see them in nautilus

EDIT: hmm, just tried it and it is not there... must think some more :)

---

### Post by joe56 on 2008-10-06
in emesene 1.0 the directory was:

 /home/joe/.config/emesene1.0/user_hotmail_com/logs

but it would never log to that folder. 

emesene 1.0.1 i d/led and extracted the .tar to my home folder. no installation is required i just run ./emesene to start the app 

it never created a similar /home/joe/.config/emesene1.0.1 and as far as i can tell its not logging anywhere in the folder im running it from:

 /home/joe/emesene-1.0.1

---

### Post by kwo on 2008-10-15
I found the .emesene folder.  It's under ~/.config/emesene1.0

But nothing seems to be logged :(

---

### Post by kwo on 2008-10-15
Oops...sorry, didn't realize previous poster said the same thing :lolflag:

---

### Post by stmartin on 2008-12-29
Why emesene doesn't store the chat logs?

---

### Post by Gias Kay on 2009-01-18
Currently, emesene does provide a logging feature, *however* a way to view that log through emesene itself seems to be nonexistent. The log is stored as an SQLite3 database, hence an SQLite database viewer is required to properly access the log.

First, you need to enable the logging feature. In emesene, Options &#8594; Plugins, check Logger. Events and messages will now start to be logged and you can view them through your favorite SQLite database viewer, me using SQLite Manager add-on for Firefox personally. The log can be located in [FONT="Courier New"]/home/[USER]/.config/emesene1.0/[MSN_ACCOUNT]/cache/[MSN_ACCOUNT].db[/FONT].

---

