---
title: "Removed c:drive now WINE shows error &quot;temp folder not valid&quot;"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Ols87 on 2012-08-21
Hello,

I'm new to Ubuntu, I tried once, got frustrated then went back to Windows... I'm trying to give it another go (Ubuntu 12.04) and it's working out well (barring a few small issues).

I installed WINE and everything was working fine, then while exploring the File folders I came across the C: drive. I had wiped Windows and moved all my files that I needed over to Ubuntu so I thought "Oh I don't need this" and deleted it.

Now when I try to install a Windows program I get the error message "temp folder is not valid"

I have tried to Google the problem but I cant find an answer.

I am pretty non-competant when it comes to navigating around/using the terminal.

The last thing I want to do is to give up on Ubuntu again and go back to dreaded Windows but I'm getting that nagging feeling again that Ubuntu feels a little complex in certain areas (sorry, I know that will offend some of you).

Any help is much appreciated.

---

### Post by sandyd on 2012-08-21
You mean you removed the C: drive in WINE, or the C: Drive in your actual Hard Drive?
If you removed the C: drive in WINE, you can't run programs because many Windows programs need a temp folder.

---

### Post by Ols87 on 2012-08-21
I removed the C:drive (Hard drive), so does that mean I can't use wine full stop or is there a work around?

---

### Post by Bufeu on 2012-08-21
> **Ols87 said:**
> I removed the C:drive (Hard drive), so does that mean I can't use wine full stop or is there a work around?You removed the partition, or what?
C:\ isn't a drive, it's a partition.

---

### Post by Ols87 on 2012-08-21
hmmm I was exploring the folders and I opened a folder that had:

C: and Z: next to each other, I deleted C: it had all my old windows files in there.

hope that answers your question (sorry I'm new to installing different OS')

---

### Post by Puttycat on 2012-08-21
try this... open up your home folder... /home/<name> , now press  CTRL + H 

that will show you all your hidden folders, find one that is called          ".Wine "  delete that folder.
then just press the super key ( aka windows key ) and search for wine... 
select " Configure Wine " it should remake the  " .wine " folder and fix the problem as far as installing new programs.

hope that helped.

---

### Post by Ols87 on 2012-08-21
Legend... Thank you very much

---

