---
title: "Nautilus was stuck"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by czgirb on 2014-10-25
Dear all ... my Nautilus is often stucked ... (it stucked randomly, not always) ... I cannot do a cut and copy ... why?
Is there any solution how to make all function works as it was?
Please guide me ...
Thank you

---

### Post by yancek on 2014-10-25
Explain what 'stucked' means.  Is it that you cannot copy/paste?  From what directory/folder are you trying to copy and to which directory/folder?

---

### Post by czgirb on 2014-10-25
Yup! it unable to do a cut or copy ... in common folder. not home folder.
but the stucked is NOT normal ... it mostly stucked after it was opened but not used.

---

### Post by ajgreeny on 2014-10-25
I am not sure what you mean by a "common folder", but you can only copy something to a folder outside your /home if you do so as root using **sudo cp**.

You may be able to copy a file or folder from somewhere in the system files and folders to your home, but it will depend on the permissions of those files or folders you are trying to copy.  Many files in the system folders do not have read permissions for anyone other than the owner, ie, root, so to copy those to your /home you will again need to use **sudo cp**, as if you can not read them, you certainly can not copy them.

---

### Post by czgirb on 2014-10-30
SORRY ... SORRY ... for maybe i do not make myself clear

when i JUST open the nautilus, it runs normally
i can do cut/copy/paste ... but if it was left (even 2minutes) ... all function is gone ... and i required to close the nautilus and re-open it again. so, everything wilk works normally ... but after it was left (even it was a minute or two&#65289;... all function will be gone.

---

### Post by JeQhdMD on 2014-10-30
So, if when was the last time period when Nautilus worked OK even after leaving it run for a long time after starting it?  And then, what "changes" (program adds, deletes, desktop changes) were made that could have changed Nautilus to "unstable".   If you install another file manager such as "Thunar" . . . do you see the same problem . . or does it work as normal regarding copy/paste, cut/paste?

Please think, and then provide more information.

---

### Post by czgirb on 2014-10-31
> **JeQhdMD said:**
> So, if when was the last time period when Nautilus worked OK even after leaving it run for a long time after starting it?
  And then, what "changes" (program adds, deletes, desktop changes) were made that could have changed Nautilus to "unstable".

... it seems the Nautilus was like that since I'm using Pangolin
Can we repair it?

> **JeQhdMD said:**
> 
If  you install another file manager such as "Thunar" . . . do you see the  same problem . . or does it work as normal regarding copy/paste,  cut/paste?

SORRY! i never tried the others

---

### Post by Alireza_Zamani on 2014-10-31
if this occur not always ,
you can kill that and run it again :

> $ pidof nautilus
& kill [nautilus-pid]
$ nautilus

---

### Post by czgirb on 2014-11-02
> **Alireza_Zamani said:**
> if this occur not always ,
you can kill that and run it again :

The occurance is ALWAYS
But after I close the nautilus and re-open it ... everything works normally

---

### Post by coldraven on 2014-11-02
Do you have a USB stick or SD card in a slot? Maybe Nautilus is trying to read the contents of a corrupted device and never getting to the end.

---

### Post by czgirb on 2014-11-04
No! I have none

---

### Post by JeQhdMD on 2014-11-04
OK - to see if the issue is nautilus, go and install another file manager like Thunar and try cut/copy/paste.

Then, report your findings.

---

### Post by czgirb on 2014-11-08
> **JeQhdMD said:**
> OK - to see if the issue is nautilus, go and install another file manager like Thunar and try cut/copy/paste.

Then, report your findings.

After give **Thunar** a try for a view days, I confirm ... **Thunar **is never **hang** or **stuck**
How can I **have my Nautilus back** normally?
**PS:**
if i wish for having: **extract here** in right-click menu, **2-pane** mode, and a **clock** in the **modified date coloumn**?
What **File Manager** should i used in **Ubuntu 14.04** ?

---

