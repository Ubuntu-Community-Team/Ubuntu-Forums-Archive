---
title: "poblem with &quot;document&quot;"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by davidhopton on 2012-08-01
Until two days ago When I double clicked one of my personal documents it would open.
NOW, I get a message "press start recovery to start recovery process" After clicking "start recovery" I get a new window "Recovery finished" and when I click "finish" my document opens. 
Question-Why do I have to go through this process simply to open a document?

I am not very computer literate and clearly a newbie  I don't even know what a tag is

---

### Post by kabukiM0n0 on 2012-08-01
Even though I'm not extremely computer literate, so I could be wrong. But I recall there being an option within Libre where you can deactivate this. Mine does the same, but I find it's handy, just in case you're system crashes and it didn't previously save.

---

### Post by gifford on 2012-08-01
Is the document in libreoffice format? Sometimes the error occurs in saving and Libre tries to recover it the next time the document is opened. Did you save the document after it was recovered? Is the recovery process running every time you try to open this particular document?

---

### Post by levlaz on 2012-08-01
This usually happens when the document was not saved properly before you exit LibreOffice. Did you save it correctly?

---

### Post by davidhopton on 2012-08-03
Well, to my surprise, I no longer have this problem. When I open a document it opens without the extra steps I originally described.
It is odd as I did nothing diferently

---

### Post by drs305 on 2012-08-03
> **davidhopton said:**
> Well, to my surprise, I no longer have this problem. When I open a document it opens without the extra steps I originally described.
It is odd as I did nothing diferently

As *levlaz* says, if it isn't a constantly reoccuring event it was probably that you closed LibreOffice or shut down the computer while a document was still open. When LibreOffice opens a file it generates a .~lock... file which remains until the document is closed. If the computer shuts down and the lock file remains LibreOffice normally will ask if you want to recover the file.

Very rarely I can't clear the message and have to find and delete the .~lock* file. Removing it will eliminate the recovery message, but it will also prevent you from recovering any changes you made to the document after your last save.

---

