---
title: "Need help with libre office draw"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by Snaz31 on 2012-05-28
I'm pretty new to ubuntu but I'm liking it so far. Any way I downloaded some clip art from a site and wanted to ADD it to the gallery within office draw. I started a new theme and added the file, problem is the file contained 27,000 pictures! It was taking ages and the notification box kind of mirrored what was behind it rather than give me information. Eventually I saw cancel pop up so I hit that. I tried to add these cliparts multiple times in different ways.

Any way now I can not delete new themes that I have made, and everything within the gallery is acting a bit weird. I want to just delete the whole lot and start again but I can't seem to figure out how to do it. I've been to the software center and removed it. Then re-installed and it did nothing. The themes are still there. I have managed to wipe some stuff off by going to the extension manager. But not those new themes I created. Btw there is nothing in those themes. At least nothing displays. 

It's doing my nut in! I just want to delete and start again! lol HELLLLLLLP.

---

### Post by Senior_Buckethead on 2012-05-28
dumb question but have you looked in /home/user/.config/libreoffice/3/user/gallery/
(user being your user name)
what files are in there? Can you recognise the offending file?

Glenn.

---

### Post by Snaz31 on 2012-05-28
> **Senior_Buckethead said:**
> dumb question but have you looked in /home/user/.config/libreoffice/3/user/gallery/
(user being your user name)
what files are in there? Can you recognise the offending file?

Glenn.

It's not a dumb question at all and no I have not looked there, I did try going through some of the system files to see if it was there as I didn't see anything libreoffice related in the home section. 

Anyway after your message I tried to have a look but I don't see anything relating to my username. There is no user file, or is it hidden? I'll check that just now. Thanks for trying to help anyway.

---

### Post by Snaz31 on 2012-05-28
You're a genius! Thanks a lot! Finally got rid of those pesky files! I wouldn't of had a clue how to do that! Hopefully I didn't delete anything important because I just wiped out the lot in the gallery file! lol... 

Any way BIG thanks again, saved me much headache! And taught me something in the process. :)

EDIT: One more thing, I still think something is wrong. Libre draw still says it's waiting to install (after I uninstalled and re-installed yet it is there and working fine. Any ideas what's causing this?

---

### Post by Senior_Buckethead on 2012-05-28
You mentioned that you installed it via. ubuntu software centre, is that correct?
Can you find the filename of the file you installed? Or atleast the name of the package or application that you installed. 
If you have that then it might be possible to remove it via. apt.

Glenn.

---

