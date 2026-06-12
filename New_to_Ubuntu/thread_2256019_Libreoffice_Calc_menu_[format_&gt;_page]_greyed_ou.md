---
title: "Libreoffice Calc menu [format &gt; page] greyed out when opening direct from Thunderbird"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by ultragamer2 on 2014-12-09
Hello,

I am posting to try and find a solution for a newbie that is not experienced with saving and opening files.

The problem is when you receive an email in Thunderbird which contains a speadsheet attachment and you open it directly in Libreoffice Calc, there is no way to set portrait.

Setting portrait in the printer properties has no effect. The way that does work is to go to the format menu and then choose page and then select portrait. However page is greyed out when you have opened the file directly from an email attachment in Thunderbird.

The way to fix it is to save the file first and then page is no longer greyed out, but for a newbie that is inexperienced with saving and opening and using folders, this is a problem. Is there a work around that can be done once so that page is never greyed out when opening from an attachment?

Thanks

---

### Post by ajgreeny on 2014-12-09
I am not aware of a way to overcome this.

I think it is a result of the way in which the file is embedded in the email, making it read-only, and the only way to overcome this is to download the attachment to your disk, as you have done, when it will become read/write.

I have no idea if this is the same in Windows when using TB, or if the situation is related to Linux permissions in some way stopping you writing to these attached files.  I don't have windows to test this out, either, but perhaps you can do so if you run a dual boot.

---

### Post by ultragamer2 on 2014-12-09
Hello,

Actually I forgot that that computer is actually using Windows not linux lol.

So it's the same in Windows.

---

### Post by amanchesterman on 2014-12-09
Suggest you read this: [http://forums.mozillazine.org/viewtopic.php?f=39&t=2162789](http://forums.mozillazine.org/viewtopic.php?f=39&t=2162789)
It's a feature of Thunderbird and it applies to all attachments, not just spreadsheets.
Look at the third and fourth posts in that forum thread and you'll understand why Thunderbird is designed to work this way, how you can change it, and what the consequences might be.

---

### Post by vasa1 on 2014-12-09
I may be remembering incorrectly, but some options just aren't available until the file is "saved as" in the native format of LibreOffice (ODF). I think it's not really so difficult to do. Plus you get to keep your original the way you got it.

---

### Post by ajgreeny on 2014-12-09
Well, at least we now it's not just a Linux related situation!

As to saving attachments from TB, the easiest way it to make a new folder in your home called Attachments and then point TB to that as the save folder in TB's preferences dialogue.  You can then easily find the saved attachment from your file manager (**Files** in the menu or dash).

---

### Post by bapoumba on 2014-12-09
Well, the idea is that when you open a file from a mail attachment, the file is on the mail server, not really on your computer, thus the read only status. Not restricted to TB, not restricted to Linux. So save it and you get read/write access.

---

### Post by ultragamer2 on 2014-12-09
Thanks.

Actually I don't need to be able to write or change the file, I only need to be able to access the format > page menu to change the orientation from landscape to portrait for printing.

It does not actually have to be saved or changed permanently.

I will try the information from the other thread that was posted, but is there a way to just enable changing the page to portrait for printing without resaving?
Printer properties has no effect.

---

