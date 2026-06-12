---
title: "transferring outlook express contents to new linux pc"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by furoido on 2008-05-14
Hi guys,

Just taken delivery of a new barebone pc on which I will install and run Ubuntu.

I have one really urgent question, though: does anybody have any ideas how I can transfer the Outlook Express email contents of my old Windows pc to my new one (which will NOT have Windows)?

I know it is possible to back up and transfer Outlook Express contents from one Windows pc to another by converting into a .UNC file, but will Ubuntu/Mozilla Thunderbird recognise this file? Or is there a simpler alternative?

Cheers!

---

### Post by MaindotC on 2008-05-14
I haven't done this myself but I googled "evolution import outlook contacts" and found [this thread]("http://buranen.info/?p=157").  I'm unable to try it so depending on if you already googled this I cannot verify if it works properly.  Good Luck!

---

### Post by furoido on 2008-05-14
from what i can tell, this involves converting your outlook mail/contact list to .csv file, which u can save on cd/usb etc(and then presumably open on ur new linux pc)...the problem is that i can't get it to save my emails (I get a MAPI activation error message), only my contact list.

---

### Post by MaindotC on 2008-05-14
Is the machine running Outlook on a domain?

---

### Post by ubz on 2008-05-14
> **furoido said:**
> Hi guys,

I have one really urgent question, though: does anybody have any ideas how I can transfer the Outlook Express email contents of my old Windows pc to my new one (which will NOT have Windows)?
Cheers!

If you install a copy of Thunderbird on the Windows machine I think you'd be able to import all the OE mail messages/folders.  Try using the Thunderbird 'Import' menu bar option with OE closed.  If that is successful, you can copy the Application Data - Mozilla Thunderbird - xxxxx.defaults - Mail - Local Folders directory over to the Ubuntu box.
Before copy, open Thunderbird in Ubuntu, create an account and close Thunderbird. Then find the /home/YourUserName/.mozilla-thunderbird
/xxxx.defaults/Mail/Local Folders directory.  Overwrite Local Folders directory with the copy off the Windows machine.
I hope the import works as explained. I haven't tried it yet.  If not you might first have to Export the messages from OE menu to a temp directory and then Import using TB.

---

### Post by Ducatiboy Stu on 2008-05-14
Yes Thunderbird will import all your data from outlook, then you can save it, then import it into evolution

---

### Post by timace on 2008-05-14
> **strAlan said:**
> Is the machine running Outlook on a domain?

It's Outlook Express, not Outlook.

---

