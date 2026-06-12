---
title: "deleting is not moving to trash"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by terrordrone on 2008-06-18
Hi

i have a peculiar problem and mostly the other way what many want.. 

when i highlight/select any thing (file etc) in nautilus, and when i press delete.. its not moving to trash..

rather its like shift+del..

how do i make pressing del making the file to be moved to trash can

---

### Post by steve101101 on 2008-06-18
try rebooting.

---

### Post by RomeReactor on 2008-06-18
Hi. In Nautilus, go to 'Edit->Preferences->Behavior' and make sure 'Ask before emptying the trash or deleting files' is checked, and 'Include a Delete command that bypasses Trash' is unchecked.

---

### Post by terrordrone on 2008-06-18
i noticed something...

i tried deleting some small files like a pic or a txt file and it goes into trash

i tried deleting a movie and it go into trash

> 
try rebooting.

   its been like this for a while


> 
Hi. In Nautilus, go to 'Edit->Preferences->Behavior' and make sure 'Ask before emptying the trash or deleting files' is checked, and 'Include a Delete command that bypasses Trash' is unchecked.

its as in the thumbnail..

---

### Post by terrordrone on 2008-06-19
i happened to boot into windows 

there i saw .Trash folders in every drive where i had deleted something or the other and the files that i had deleted were in that folder.. 

if thats the case shouldnt it be shown in the trash can?

---

### Post by terrordrone on 2008-06-22
bump :|

---

### Post by RomeReactor on 2008-06-22
So the files you deleted were from a windows partition or drive? If so, that's the usual behavior for Nautilus. It also happens when you plug in a USB memory or drive; it doesn't show those files in the trashcan since--technically--they're not *in* Ubuntu. You can delete the files in the .Trash folder there and you'll get back the space. Since that folder is hidden you don't normally see it when browsing that partition/drive in Nautilus, unless you press CTRL+H.

---

### Post by terrordrone on 2008-06-22
> **RomeReactor said:**
> So the files you deleted were from a windows partition or drive? If so, that's the usual behavior for Nautilus. It also happens when you plug in a USB memory or drive; it doesn't show those files in the trashcan since--technically--they're not *in* Ubuntu. You can delete the files in the .Trash folder there and you'll get back the space. Since that folder is hidden you don't normally see it when browsing that partition/drive in Nautilus, unless you press CTRL+H.
Yea.. they are NTFS drives ( if thats what you meant by windows drives ). 

i use them as common drives between OSes.

ive seen the same thing with USB drives as well.. like u said.


but what i didnt understand is.. even if it is put in the .Trash folder in the same drive.. why is not being displayed in the trash can ? coz some files are shown.

is there anything that i can do ?

---

### Post by RomeReactor on 2008-06-23
> **terrordrone said:**
> but what i didnt understand is.. even if it is put in the .Trash folder in the same drive.. why is not being displayed in the trash can ? coz some files are shown.
You mean the trashcan in windows? If so, I gather that's because windows didn't delete those files, so the system doesn't have a record of those files being in the trash, nor are they in the windows trash (if there's such a location; can't remember :P)

> is there anything that i can do ?
Not as far as I know, except keep deleting those files from the .Trash folder. Maybe someone else will post a more adequate answer.

---

### Post by terrordrone on 2008-06-23
> **RomeReactor said:**
> You mean the trashcan in windows? If so, I gather that's because windows didn't delete those files, so the system doesn't have a record of those files being in the trash, nor are they in the windows trash (if there's such a location; can't remember :P)


Not as far as I know, except keep deleting those files from the .Trash folder. Maybe someone else will post a more adequate answer.
lol no.. my trashcan in ubuntu..  ( maybe i can put my windows in ubuntus trashcan :P )

since i had set show hidden folders in windows.. i came to know that these files are moved to the .Trash folder ( in linux ) on the same drive.

Why i want this option is..  suppose i delete something by mistake.. i will have the opportunity to recover it. Itll be troublesome to goto .Trash folder and check, and then restore the file manually requiring me to remember the path where it was originally present.. ( im assuming )

---

### Post by Victormd on 2008-06-23
> **terrordrone said:**
> but what i didnt understand is.. even if it is put in the .Trash folder in the same drive.. why is not being displayed in the trash can ? coz some files are shown.

is there anything that i can do ?

There really isn't anything you can do since the trashcan in ubuntu is an applet linked to the .trash folder in your home folder. Anything you delete in a different partition/drive/USB, goes to the .trash folder of that partition/drive/USB. The only way to get files you would like to delete (from other partitions) into your trash can, would be by dragging them into it.

---

### Post by terrordrone on 2008-06-24
lol

drag them from that drive into the trash folder and then delete from trash can :lolflag:

---

