---
title: "recovering tmp files"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by kyalee on 2008-06-12
I know (now) that files in tmp get wiped on boot and that's why the file I'm trying to access doesn't exist anymore. Let's suppose that yesterday I accidentally saved a kinda sorta really important file to tmp after I made extensive revisions. And lets suppose that today I turned on my computer and it's gone. Is there any possible way to get it back, or am I just screwed?

---

### Post by spiderbatdad on 2008-06-12
There are some software recovery tools like photorec that come to mind...they tend to recover 1000's of unwanted lost files.

If you now the name of the file there may be hope using this procedure: [http://www.linux.com/articles/58142](http://www.linux.com/articles/58142)

---

### Post by RomeReactor on 2008-06-12
Hi. I'm not sure if this would work on files from the TMP folder, but you could run a Live CD session (avoid using your installed system ,as it decreases the chances of recovering the file) and, in the Live CD session, install [Magic Rescue or PhotoRec]("https://help.ubuntu.com/community/DataRecovery#head-1dfad2443d9c6b29324f4bddb16e4631a713ed4c"). Haven't tried them myself, though. Surely someone else can give you a more definitive answer.

However, one thing is certain: avoid using the installed system until you get back the file.

EDIT: Too slow.

---

### Post by kyalee on 2008-06-12
Thanks. Reading it over, I don't think that procedure will help me. It says you have to make sure you don't close the application editing or playing back the file and I think the file was deleted when I booted the computer at which point OpenOffice wasn't running. So it's probably not floating around on the hard drive, it's probably just gone.

*sigh*

My own fault, but man this makes me cranky.

Thanks for the reply, though.

---

### Post by Sinkingships7 on 2008-06-12
On the contrary, it IS still floating on the hard drive. Data is never erased from a hard drive, only over-written. Might as well give those suggestions a shot, if the only reason you're not is because you think that it's not there.

---

### Post by nowshining on 2008-06-12
Ext3 is diff. than XP, it's quite harder to recover a file on an ext3 harddrive - ext2 was like XP and vice versa. More than likely it's gone - the bits have been changed to where one can't recover it. Next time don't save anything in tmp, save it in ur home folder or the desktop. ;)

Unlike Ext2 and XP, it doesn't remove the file pointer but the erases it with zeroes in ext3 i think as soon as it's deleted.

---

### Post by kyalee on 2008-06-12
> **nowshining said:**
> Ext3 is diff. than XP, it's quite harder to recover a file on an ext3 harddrive - ext2 was like XP and vice versa. More than likely it's gone - the bits have been changed to where one can't recover it. Next time don't save anything in tmp, save it in ur home folder or the desktop. ;)

Oh, believe me, I have learned my lesson. I'm going to give a few of the suggestions a shot, just in case something works, but then I've got to get to work on redoing all the work I already did yesterday. Except this time the file is definitely saved in my home folder.

---

### Post by nowshining on 2008-06-14
watch out - doing so might render your other files in-accessable. I once lost a tmp file I accidently deleted lol

don't worry tho u'll get over it . :)

---

