---
title: "[SOLVED] Migrate Outlook to Thunderbird"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by fballem on 2008-05-16
Hope that this is useful.

As part of a conversion from Windows to ubuntu, I had to migrate from Outlook to another e-mail/calendar/contact program. I chose Thunderbird/Lightning as the program for ubuntu.

I'll do a full post later, but the basic steps that I used to migrate Outlook e-mail and contacts to Thunderbird/Lightning are:

1. **Prior to conversion**, install the Windows version of Thunderbird and the Lightning extension on the PC.
2. Setup one e-mail account on Thunderbird and disable automatic send. This is required to setup Local Folder.
3. Tools | Import address book and e-mail. The prompts are easy - it will take time.
4. When done, VERIFY that you have all of the e-mail (including any archives) and contacts. If not, delete them in Thunderbird and close. Then open Outlook and make sure that all Archive folders are also included. Then repeat 3 and 4.
5. When done:
- locate the folder named "Local Folders" that was created by Thunderbird.
- copy all of the files in Local Folders to an external device or network drive. These contain the e-mail and folder structure.
- copy abook.mab (it should be at the same level as Mail) to the external device or network drive. This is the address book.
6. Convert to ubuntu and install Thunderbird and Lightning.
7. Set up all e-mail accounts. Disable all automatic send operations (including the checkbox when you are setting up the accounts).
8. Close Thunderbird.
9. Locate the Local Folders (under .mozilla-thunderbird/{GUID}/Mail). Hidden folders must be enabled (ctrl-h on /home/userid, where userid is your userid). GUID will be a unique identifier generated when Thunderbird is installed.
10. Copy the files from the external device or network drive to this location.
11. Copy abook.mab to the same location as Mail. abook.mab is not part of the Local Folders.
12. Reboot system
13. Start Thunderbird - if all is well, you will have your e-mail and your contacts.

I've attached two screenshots showing the location of abook.mab and the Local Folders.

---

### Post by Rowanmf on 2008-05-16
My 2 cents -

Over the last five years i have moved from fedora , ubuntu , redhat , suse and finally back to ubuntu , all i ever do is save my folder /home to a external drive , remove the extra directories that i dont need to keep , and be sure to save the mozilla folders , skype , kopete and google earth folders  ie .mozilla etc , then after my fresh install , copy the old /home to the new /home , and hey presto everything is where it should be , such that i have emails dateing back to the 1990's , i have never had to use the excuse sorry i lost your email address when i moved to a new machine ...

thanks for the good post , it should help those entering the linux world for the first time ...

---

### Post by fballem on 2008-05-16
I'll have to remember this if I want to move from Linux to Linux. I'm still feeling my way through the Linux world.

One question I wouldn't mind seeing answered is if I have two sets of Thunderbird e-mail files then can I merge them? Don't ask - it's a long story about someone who forgot the most basic rule of learning new stuff - "crawl, walk, run, fly".

---

### Post by Rowanmf on 2008-05-16
ok , been there done it , sort of , yah i had a old copy of /home and i coppied the newer /home onto it , thus merging everything in the mozzila/thunderbird directories , and it did work ...

cheers 

rowan

---

### Post by unicron0827 on 2008-09-24
thanks, ive been trying to kill that last windows box for a while now.

---

### Post by crjackson on 2008-09-24
Can you elaborate on step 4? 

> Then open Outlook and make sure that all Archive folders are also included.

Will this work for Outlook Express or only Outlook?  I use OE and tired something similar about a year ago without success.

---

### Post by atoztoa on 2009-12-11
Here is a full length guide for migrating Outlook in Windows to Thunderbird in Ubuntu...

[How to successfully migrate from Outlook in Windows to Thunderbird in Ubuntu...]("http://www.atoztoa.com/2009/12/how-to-successfully-migrate-from.html")

---

