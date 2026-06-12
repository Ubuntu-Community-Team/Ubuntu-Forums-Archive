---
title: "[SOLVED] emailing entire folder instead of individual files"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-13
hi
I want to email the contents of a folder, which is not that big size wise, but has lots of files in it.
Is there a way I can mail the entire folder without having to attach files individually, which would take ages.

---

### Post by Dill on 2008-08-13
If you archive the folder in some manner, you can attach it as a single file. Zipping it may be the easiest way...

If you right-click on the folder and choose "Create Archive", a window should appear where you can choose the name of the archive and the way in which you want to archive it. If you click on the drop-down menu just to the right of the name, you'll be able to choose ".zip". Try attaching that to the e-mail. The person on the other end should be able to open the archive fairly easily, no matter what OS he or she is using.

You can also do this from the terminal by moving into the directory where your folder is stored and typing

```
zip -r archive_name.zip folder_name
```

where archive_name is whatever you want to name the archive, and folder_name is the name of the folder you're archiving.

Cheers, 
Dylan

---

### Post by LTFC2020 on 2008-08-13
thanks dill
you just doubled your thanked count in 5 minutes:)

---

### Post by prshah on 2008-08-13
> **LTFC2020 said:**
> I want to email the contents of a folder,

As Dill suggested, you can archive it and email, but there is an easier (/GUI) way; right click your folder, choose "Send To...", Choose "Email (...)" for "Send as", Enter the email address in "Send to", and then, under "Compression", choose "Send packed in", give a filename, and choose ".zip". Then, when you click Send, it will open up a new (blank) message with the attachment already attached ( :-P ).

Fill in the subject, a body if you like, and click send.

---

### Post by Dill on 2008-08-13
Ah, cool man. I assume this utilizes your default mail client to send the message, right?

Cheers, 
Dylan

---

### Post by prshah on 2008-08-13
> **Dill said:**
> Ah, cool man. I assume this utilizes your default mail client to send the message, right?


Which is why I put "email (...)"; if you have two or more active email clients in your computer, the "..." will be replaced with the name of the client; eg, I have:

Email (Evolution)
Email (Thunderbird)

as options in the send to dialog. (See screenshot for clarity)

---

### Post by Dill on 2008-08-13
Cheers for that

---

