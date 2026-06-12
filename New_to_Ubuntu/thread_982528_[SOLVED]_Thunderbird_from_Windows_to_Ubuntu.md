---
title: "[SOLVED] Thunderbird from Windows to Ubuntu"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by ColeJayStooks on 2008-11-14
hello, I am going to do a ubuntu installation but first I would like to archive/backup my thunderbird's gmail inboxs from Windows XP. it would be nice if I could then use the backed up letters on my new Ubuntu box. any help??

---

### Post by nhasian on 2008-11-14
is your mail server POP3 or IMAP?  if its IMAP then you dont need to backup anything.  just enter your settings in thunderbird on the new machine.  if its pop3 then you can backup and restore your inbox/folders from one thunderbird to another.

---

### Post by ColeJayStooks on 2008-11-14
> **nhasian said:**
> is your mail server POP3 or IMAP?  if its IMAP then you dont need to backup anything.  just enter your settings in thunderbird on the new machine.  if its pop3 then you can backup and restore your inbox/folders from one thunderbird to another.

yep it is POP3 but how would i back up messages? when i backed up from linux before i could just copy the .mozilla-thunderbird file and then copy it over the next linux install but that didn't work out for windows and when i look at the windows install it's different from the linux one too so i don't know if there is something i am missing from the GUI or what...

---

### Post by b0b138 on 2008-11-14
i think you can just copy the profile folder and file. Not the whole mozilla-thunderbird folder, just the profile folder

---

### Post by chrisod on 2008-11-14
Copy your profile folder, and then on the new install copy the contents of the folder into the new profile folder that Tbird creates. Everything will be there just fine. You can do the same for Firefox if you want to keep your cookies, saved passwords, etc.

---

### Post by SunnyRabbiera on 2008-11-14
> **b0b138 said:**
> i think you can just copy the profile folder and file. Not the whole mozilla-thunderbird folder, just the profile folder

that is what worked for me in the past, I just took out my mailbox data files and imported them.
Just make sure to set up a profile first in the ubuntu that will create a profile in the hidden thunderbird directory and then copy/paste :D

---

### Post by ColeJayStooks on 2008-11-15
looks like that did it, thanks guys

---

### Post by humanx on 2009-01-06
Hi, 
Newbie here, so these might be stupid questions.  

On my XP install, the Profiles folder contains a xxxxxxxx.default folder.  Is this what is copied over to the Ubuntu install to replace the yyyyyyyy.default folder?  Then do I edit the profiles.ini file to point to the xxxxxxxx.default folder?  (xxx....yyy...being random generated file names)

I'm currently using 8.10 on USB w/persistence.  If I install 8.10 to HDD using my USB, do all my settings and data automatically go to the new install? 

Thanks.

---

### Post by chrisod on 2009-01-08
You should post a new thread for your question, this one has been marked as solved. But to answer your question, copy the contents of the profile folder, not the folder itself. That was you don't have to mess with editing profiles.ini.

---

