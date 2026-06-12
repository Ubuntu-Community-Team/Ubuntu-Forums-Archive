---
title: "[SOLVED] migrating from WIndows mail on Vista to Evolution"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by austinium on 2008-06-14
I have just installed Ubuntu 8.04 using Wubi. How do I copy all my mail and settings from Windows Mail onto Evolution? I have tried installing Mozilla Thunderbird and importing mail into it so that i can then import into Evolution(Linux) from Thunderbird(Vista) ... it didnt work.

is there a how-to for this?

help!!!

---

### Post by the_doc on 2008-06-14
Can you export/import as a CVS file or something of that nature?

---

### Post by mdpalow on 2008-06-14
Did you try the IMPORT option under FILE in the Evolution menu?

---

### Post by austinium on 2008-06-14
@the_doc - Windows mail Has two options for exporting mail 1.Microsoft Exchange Server 2.Microsoft Outlook(or something similar, i would have to reboot to tell u the exact text) i chose the 2nd option, exported stuff into a folder. Windows mail seems to save emails in .eml format.

@mdpalow - i have tried File > IMport - both options - none work.

---

### Post by the_doc on 2008-06-14
If you can't export directly from Windows Mail as a CSV file, maybe try exporting as option 2 (as you did already) but then import into MS Outlook (assuming you have it) as I'm pretty sure that will the be able to export as a CSV.

Are you sure you can't export as a CSV?

---

### Post by austinium on 2008-06-14
> **the_doc said:**
> If you can't export directly from Windows Mail as a CSV file, maybe try exporting as option 2 (as you did already) but then import into MS Outlook (assuming you have it) as I'm pretty sure that will the be able to export as a CSV.

Are you sure you can't export as a CSV?
i exported as Microsoft exchange, it exported to Outlook Office 03 from there i exported to .csv Now when i try importing the CSV file Evolution hangs(goes grey), and then comes back after a while but i am unable to find the stuff i imported. the csv file is around 10mb, i dont think theres a size limit or is there???

---

### Post by the_doc on 2008-06-14
I don't think so.  Does that file include contacts as well as emails etc?  Try doing them seperately and see if the reduced files size helps.

At least you're making some kind of progress!


EDIT:

Have you restarted Evolution since the import?  I doubt that will hellp but you never know.

---

### Post by austinium on 2008-06-14
thanks for the response

Well its over 3500 emails from the Windows Mail inbox(via Outlook 2003) in a .CSV file.So no it doesnt include contacts. I have tried jst about evrything including rebooting(old windows habits die hard ;))... no luck so far...where does the stuff we import into evolution go anyway? i have tried draggin the .csv file and dropping it onto the inbox frame on evolution, it only copies 32 messages.
:(

---

### Post by the_doc on 2008-06-14
I have to be honest, I'm not an Evolution expert.  I just know that most, if not all, email clients handle CSV files for import/export.  If Evolution doesn't throw an error when it opens that file then that would indicate that the problem lies elsewhere perhaps. 

Have you tried manually opening the file and deleting all but a few entries, see if it will work with only a few emails?

---

### Post by austinium on 2008-06-16
hi
its fixed, heres how :
-Export to Micrisoft Exchange from Windows mail(that got it into Outlook 03)
-Export in CSV(Windows) from Outlook 2003
-THen i imported the .CSV into Mozilla THunderbird for windows
-Now if u right click the inbox icon on the left panel on Moz. Tbird, and select copy path and navigate to the folder where the Inbox is stored u'll find a file named Inbox (no extensions).
I found it here:
C:/Users/UseName/AppData/Roaming/Thunderbird/Profiles/1svkyvpv.default/Mail/Local Folders/Outlook Mail.sbd/Local Folders.sbd/

-Reboot into Ubuntu paste the inbox file into /home/UserName/.evolution/mail/local/


I did try (on Evo.) File>Import>single file but it kept getting stuck probably 'coz the inbox(file in Moz. Tbird.) was above 1GB, so i manually copied and pasted the Inbox.

srry if it doesnt make too much sense, it worked for me, hope its of help to others.

---

### Post by michaeljf on 2009-12-12
Or you can export Windows mail (which saves everything as a lot of .eml) files, then use 
[http://www.broobles.com/eml2mbox/](http://www.broobles.com/eml2mbox/)
to convert them to mbox format, which will read into Evolution

Michael

---

