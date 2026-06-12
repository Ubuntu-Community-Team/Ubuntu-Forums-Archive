---
title: "HOWTO: Import Outlook to Evolution"
date: 2005-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Yoda_Oz on 2005-11-17
This is my first howto...
I did it because no matter how many times i need to reinstall linux i forget how this process works. So I've decided to write myself a little howto to remind myself how I did it. You may with to use this sometime yourselves. Hope it helps!

1. Install Thunderbird in Windows.
2. Import all your Outlook folders into Thunderbird. Easy process, don't worry!
3. Restart computer into linux and open up Evolution.
4. In Evolution go: File/Import/Single File
5. Browse to the Windows partition: "Documents and Settings/Your Windows Username/Application Data/Thunderbird/Profiles/blahblah.default/Mail/Local Folders(or Local Folders-1 maybe?)/Inbox (single file with no extension).
6. Next, choose destination folder and import!
7. Repeat for different folders but goto the directory after /Local Folders/Inbox.sbd/ then choose the single file with no extension corresponding to the folder's name you want to import.
8. That's it!

Importing address book.
1. I did this with Plaxo. I installed Plaxo onto Windows and then synched. Then i rebooted into Linux and exported my address book from the Plaxo website in the .vcf (vCard) format.

HOPE THIS HELPED ANYONE...

---

### Post by rsankuratri on 2005-11-17
Thanks for the HOWTO.  One wuestion though.  Are you really rulling "Dapper Drake"?

---

### Post by Yoda_Oz on 2005-11-17
rulling? or running?
yes, im really running dapper drake... whats done of it so far. its in the testing phases at the moment and isnt set for release til april next year.

goto this part of the forum for all info on dapper.
[http://www.ubuntuforums.org/forumdisplay.php?f=111]("http://www.ubuntuforums.org/forumdisplay.php?f=111")

---

### Post by rsankuratri on 2005-11-17
Sorry for fat-fingering...due to excitement about Dapper Drake.  Thanks for the info on Dapper Drake.  I have a Dell 9100 laptop with ATI Mobolity 9100 video card and even though I have the ATI drivers installed the 3D acceleration does not seem to be what it was when I was running Windows.  How's your experience with Dapper and your video card?:)

---

### Post by Yoda_Oz on 2005-11-18
nvidia works great. havent really had the chance to test it though because i dont play high end 3d games. i used to do a lot of video editing in windows in adobe premiere pro. this is what linux lacks, a great video editing program. cinelerra and kino just dont cut it. kino is more like windows movie maker (so its linear) and cinelerra is just too resource heavy and uses too much hard drive space when ripping from dvcam, plus its not very stable either.
havent had the chance to do tv-out yet either.

anyway, im probably not the right person to be talking to about this sort of thing. im not realyy a hardware person when it comes to linux, as im not very experienced with it. all i know is how to setup my own computer so it works...

---

### Post by BLTicklemonster on 2005-11-21
You know, it's funny, this is the first time I've booted to my xp disk in a week and a half and browsed in here, and not only did I find this, but I found a way to set some wizardry into the xp mbr so that I can dual boot finally.

Now tbird doesn't like the address I put for hotmail. Is there a way around that? My gmail account did just fine. I don't see why MS can't just do away with the automatically remembering passwords for email. That would cut down on a lot of virus emails, would it not? And wouldn't there be other ways around allowing outgoing mail that isn't authorized to be sent, like show what's going out and ask for authorization first on each one? Oh, wrong forum, I'm asking smart people a question that ought to be directed towards sloppy people, sorry.

---

### Post by Yoda_Oz on 2005-11-22
i would find it kind of annoying to be typing in my password everytime i wanted to check my email. if i wanted to do that i would used web-based email.

i wouldnt have a clue why your tbird doesnt like your hotmail address. i thought you could only check hotmail through outlook/outlook express unless you had a hotmail pop program running in the system tray... hehe, thats my limit to stupid hotmail. i think hotmail is stupid. i havent used my hotmail address for years and my account is still active! what a waste of space!

anyway, my only suggestion to you is to rid yourself of hotmail... sorry.

---

### Post by BLTicklemonster on 2005-11-22
So ah ... do you like hotmail?


Oookay, so its mail pure and simple, I already have it, so why not use it. Gmail, used in outlook express, asks for a password on the first email you send on each session. (you got to enter a password to use ubuntu, right? then use a password to send email) Anyway, it's outlook express that's the security risk, not hotmail, so I don't see why ms doesn't do something about it.

---

### Post by rddaugherty on 2007-03-23
> **Yoda_Oz said:**
> 
...
Importing address book.
1. I did this with Plaxo. I installed Plaxo onto Windows and then synched. Then i rebooted into Linux and exported my address book from the Plaxo website in the .vcf (vCard) format.
...


I tried this, and found that many important things were NOT brought over from Outlook, such as (but not limited to):

the Comment field - VERY important!
the Category field - needed for sorting contacts
Contact Lists - used for bulk emailing to a select group of contacts

I'm desperately looking for a utility of some kind that will INTELLIGENTLY parse a file exported from Outlook so that no data is lost when importing into Evolution (or any other decent contact manager).

I can't be the only one in need of such a tool. Indeed, there must be thousands or tens of thousands of disgusted Outlook users out there clamoring for a utility to cleanly and safely free them from the bondage of M$.

Any ideas? Anyone? Help!
](*,)

---

### Post by jorgealfonso on 2007-04-24
I have too all my PIM data taken as hostage from Outlook!!  (mail/calendar/contacts/notes)

I am expecting that there should be a SAFE way to do this, as I (and most of the people, I guess) have very valuable information in there! (both personal and professional!)

[INDENT]
1) I don't want to lose data in the transference
2) I don't want to pass though this pain ever again! (I want a standard format, etc...)
[/INDENT]

Would be great to be sure that my data could go INTACT from Oulook to Linux, and then back to Outlook INTACT (you never know when you could need to do this).

Would be also great to have a single file that I could read both from windows and linux (guess a cross-platform SW could do this... I think evolution is...)

Well, as the person on the last post, I guess there should be a proven way to do this, but I have been looking all over the internet and the process through thunderbird looks (maybe it's not) kind of unsafe, not very straightforward, and **still doesn't does the job for calendar/contacts/notes**.

[LIST]
[*] I heard about a program called Outport; have anyone tried this?
[*] Isn't there a format that Outlook can EXPORT, that I could IMPORT later on on Evolution/other? (without losing data)
[*] Do you think this would be possible to be done though my PocketPC? all the data is in there, so I wonder if I could just synchronize my data with Evolution and have the job done! (Yet, I don't know which would be the right synchronizing SW)
[/LIST]

Your comments and feedback will be greatly appreciated! :D

---

### Post by Fifilein on 2007-05-17
Hi all,

i am thinking about moving from windows to linux; in the meanwhile more or less everything in terms of hardware is running (beside my dvb-t card), but i have a huge problem with mails; which makes the whole story completely senseless at the moment.

i have managed to export outlook mails -> thunderbird 2.0 windows -> copy it to linux; so i have it in linux now; but thunderbird is no option, as i need an integrated software with pim/sync functionality. the process mentioned below is not possible, i have a huge amount of sub-folders, so doing this manually is no way; in thunderbird everything is as it should be; but evolution can only import single folders. 

any clue? would korganiser be an alternative? btw. outport works only with o2k3, not with o2k7!

> **Yoda_Oz said:**
> 
4. In Evolution go: File/Import/Single File
5. Browse to the Windows partition: "Documents and Settings/Your Windows Username/Application Data/Thunderbird/Profiles/blahblah.default/Mail/Local Folders(or Local Folders-1 maybe?)/Inbox (single file with no extension).
6. Next, choose destination folder and import!
7. Repeat for different folders but goto the directory after /Local Folders/Inbox.sbd/ then choose the single file with no extension corresponding to the folder's name you want to import.


kr
christian

---

### Post by Fifilein on 2007-05-23
no one any help on my topic?
without email database its not really usefull.. unfortunately...

kr
christian

> **Fifilein said:**
> Hi all,

i am thinking about moving from windows to linux; in the meanwhile more or less everything in terms of hardware is running (beside my dvb-t card), but i have a huge problem with mails; which makes the whole story completely senseless at the moment.

i have managed to export outlook mails -> thunderbird 2.0 windows -> copy it to linux; so i have it in linux now; but thunderbird is no option, as i need an integrated software with pim/sync functionality. the process mentioned below is not possible, i have a huge amount of sub-folders, so doing this manually is no way; in thunderbird everything is as it should be; but evolution can only import single folders. 

any clue? would korganiser be an alternative? btw. outport works only with o2k3, not with o2k7!

kr
christian

---

### Post by gerardo1967 on 2007-06-23
[http://www.howtoforge.com/converting_outlook_pst_to_maildir](http://www.howtoforge.com/converting_outlook_pst_to_maildir)

Check this out, I'm going to try it right now, and let you know later how it worked

---

### Post by digivouk on 2007-07-23
Hi,

I am new to Ubuntu and have used XP before.

I am trying to somehow import my outlook pst file to thunderbird and then to evolution but it seems like I should have done that in windows first and then switch to linux.

Is there any workaround, that is not too complicated (I am not very proficient in linux) or do I have to do in on a friend's xp machine first, like some posts are suggesting.

Thanks.

Tom

---

### Post by juanbretti on 2007-07-31
**Yoda_Oz**, thanks for your simple and complete "HOWTO".

---

### Post by hartdg on 2007-08-11
**Moving your Contacts**

After several attempts I found the best way to migrate my Contacts from MS-Outlook was as follows:

**Within MS_Outlook, display your Contacts:**
File / Import and Export 
Option: Export to a File
Option: Tab separated values (Windows)
select the contacts folder you want to export
provide a name and location for the exported file
NB: Check the "Map customfields" option and confirm that all the fields used in Outlook (or those important to you) have been selected for the mapping.
Finish

**Copy the exported contacts file** to a suitable location in Linux (using a memory stick, network file transfer / or by  reaching across a disk partition...)
[B]
Within Linux / Evolution:[/B]
(if you have more than one address book) Create a new address book folder: File / New / Address Book

File / Import / Single File / identify file to import / identify destination address book folder

**Repeat** for each contacts folder that you want to migrate.

The key for me was ensuring that _all _fields were mapped for export in Outlook.

Using this method I was able to copy across 5 separate address books. The largest of these contained over 23 000 entries.


It appears that Thunderbird also preserves all the fields when it imports details out of Outlook.

**TIP:** One thing that Thunderbird does not appear to do is import e-mails sitting in the top folder of a .pst file If you have any e-mails like this you should (from within MS-Outlook) move them into a sub-folder and no leave any e-mails in the top level folder.

---

### Post by hartdg on 2007-08-12
> **Fifilein said:**
> Hi all,

i am thinking about moving from windows to linux; in the meanwhile more or less everything in terms of hardware is running (beside my dvb-t card), but i have a huge problem with mails; which makes the whole story completely senseless at the moment.

i have managed to export outlook mails -> thunderbird 2.0 windows -> copy it to linux; so i have it in linux now; but thunderbird is no option, as i need an integrated software with pim/sync functionality. the process mentioned below is not possible, i have a huge amount of sub-folders, so doing this manually is no way; in thunderbird everything is as it should be; but evolution can only import single folders. 

any clue? would korganiser be an alternative? btw. outport works only with o2k3, not with o2k7!



kr
christian

I had a similar challenge (120 e-mail folders spread over 10 .pst files totalling 2GB of e-mail). The "one folder at a time" import into Evolution looked like a show stopper.

Then I found a brilliant gem of information here:
[http://ubuntuforums.org/showthread.php?p=3178111#post3178111](http://ubuntuforums.org/showthread.php?p=3178111#post3178111)

Here is a step-by-step implementation summary. If you still have a working installation of windows / Outlook on your own PC then skip steps 0 - 2 and 9.

0. Find a friend who has Windows and MS-Outlook running on a PC who's prepared to let you use the PC for a couple of hours (& install Thunderbird on it). The PC should have enough free space to accommodate double the size of your .pst files and the Thunderbird installation.

1. Take a copy of the MS-Outlook .pst files on to a friend's PC.

2. Create a new profile in Outlook and open your .pst files in that profile. For the duration of the operation make the profile the default profile in Outlook. To create a profile (right-mouse on the MS-Outlook icon in the menu system and select "Properties". Then select "Show Profiles". Check the "Prompt for profile to be used" button. Click "Add" .... (I assume that you know how to add .pst files into Outlook, if not, I can help).

3. Make sure that none of your .pst files have e-mails in the top level of the file. If there are some then move them into a sub-folder (otherwise Thunderbird will miss them). When this is done, close Outlook.

4. Install Thunderbird. It will then offer to import address book & e-mails from Outlook. Depending on the size of your .pst files this could take some time (several hours).

5. When it's done Thunderbird will have created a set of subdirectories in the path "Documents and Settings/<user>./Application Data/Thunderbird/Profiles/<profile code>/Mail/Local Folders" (or something similar)

6. Copy all the .sbd folders that are in /Local folders (there should be one for each of your .pst files) into the folder "/home/<user>/.evolution/mail/local" on your Linux system
(see post 13 by muguwmp67 in [http://ubuntuforums.org/showthread.p...11#post3178111](http://ubuntuforums.org/showthread.p...11#post3178111) for this brilliant tip)

If you can not see the .evolution folder in /home then select "Show hidden folders" in the View menu of Nautilus (or whatever file manager you are using).

7. Start Evolution. Next to your Inbox and other folders you should now see a folder for each .pst As you browse through them there will be a short delay (depending on folder size) as Evolution updates its indices.

8. My earlier post in this thread also addresses the the issue of moving "contacts" from Outlook to evolution.

9. Clean up your files from your friend's PC and uninstall Thunderbird (unless he wants to keep it). Delete the profile you created in Outlook and restore his default profile.

10. I've not discussed migrating Tasks, Notes or Calendar items here. You'll need to look elsewhere for support on that if required.

Dave

---

### Post by juanbretti on 2007-09-01
**hartdg**, Just cool! Thanks!

---

### Post by neilevan814 on 2008-05-17
I have been using yahoo auto sync with ms outlook ...so I am hoping to be able to import to evolution from yahoo.  Plaxo, as mentioned earlier is another of this type of auto sync program.  I will post here on my results tomorrow as soon as I have tried this.\
Neil

---

### Post by Rafiek on 2008-06-27
I'm having another problem.
I used to have outlook 2007 I exported my data to a .pst file becaus eI had to reinstall my windows. After that I found out my office install dvd was damaged. Now I want to move to Ubuntu and import the data into evolution. I don't have a installation dvd for outlook so I can't use outport. 
How can I import the data of a orphaned pst file into evolution??
I need my calander, contacts and mails.
I hope someone can help me.

---

### Post by Rafiek on 2008-06-27
The solution was painfully simple.
Just go to my neighbor, borrow his office 2003 installation disk. install outlook office and follow the rest of the steps described here :lolflag:

---

### Post by dkorz on 2008-09-07
If you are doing this procedure from Windows Vista the folder to copy from is /Users/{name}/AppData/Roaming/Thunderbird/Profiles/blahblah.default/Mail/Local Folders. I was able to import all of my mail to evolution on 8.04.

---

### Post by jack frost on 2008-09-18
this may be an old post..but It helped me take my outlook contacts in just like that using the plaxo. I just synced in windows and then exported as vcf as stated.. imported in evolution with no issues and it kept all the fields in place.. THANKS.

---

### Post by jack frost on 2008-09-18
> **jack frost said:**
> this may be an old post..but It helped me take my outlook contacts in just like that using the plaxo. I just synced in windows and then exported as vcf as stated.. imported in evolution with no issues and it kept all the fields in place.. THANKS.
took me only about 8 min.. created plaxo account.. then signed in. under address book I chose sync with outlook.(in vista). then once it synced (2 min) I then went back in the program and chose to export as vcf (it does all the contacts in outlook)..then just imported to evolution.. 

just wanted to add that.

---

### Post by thirdd on 2008-11-09
Thanks for all those HowTos, they helped me to evolve 
**my personal Outlook 2007 to Evolution migration that worked out very nice** (in the end):

1. Copy all mails via Thunderbird(Win) like Yoda_Oz describes in post 1
2. Copy Calendar via Outpod (categories will NOT vanish but different calendars are better for coloring and hide/unhide "categories" in Evolution)
3. Export your Contacts in Outlook into seperate psts for each category (there is a nice filter option)
4. Open/Link those new psts within Outlook
5. Let Thunderbird import Contacts from Outlook (it will create seperate Adressbooks for each pst)
6. Export each Thunderbird adressbook to a ldif file and import those in Evolution


Even if it is a little bit tricky for the contacts it was the only possible solution for me to keep my contact categories.
Thunderbird doesnot know anything like categories for contacts and Outpod simply didnot work with my contacts.

**Like this I was able to migrate mail,calendar and contacts from Outlook 2007 to Evolution without lossing a single piece of information.**

Good Luck

---

### Post by acreech on 2008-11-14
You can move your email from Outlook to Evolution without having to install Thunderbird by using a gmail account. You can setup an IMAP account on your existing MS Outlook. Then transfer messages into it and they will be sent to your gmail account. Evolution can be setup to download the gmail account and then your messages will have been transfered. 

On your web based Gmail go to settings>forwarding and POP/IMAP. At the bottom of the page enable IMAP and then click the "configuration Instructions" for more instructions.

---

### Post by goslings on 2008-11-23
Good to see this has attracted a few interesting post over the months
Does 8.10 offer any better (automatic?) migration from outlook to evolution 
still holding off from upgrade from 8.04 to 8.1 (nvidia cards)
goslings

---

### Post by rupert160 on 2008-12-25
Unfortunately there is a confirmed bug on the import system in Evolution:
[http://bugzilla.gnome.org/show_bug.cgi?id=419921](http://bugzilla.gnome.org/show_bug.cgi?id=419921)

Thus the Outlook>Thunderbird(Win)>Thunderbird(Linux)>Evolution 2.10.x will not be as simple import at the point of Evolution>File>Import>Single file. Below I have documented the manual work around that I used...

After a successful Import into Thunderbird(Linux) the directory for all your old outlook folders will have file paths similar the following:

```
/home/yourUserName/.mozilla-thunderbird/989wzmgf.default/Mail/Local\ Folders/Outlook\ Mail.sbd/Personal\ Folders.sbd/yourSubFolderNameFile
```

And Evolution stores mbox files in the following directory:
```
/home/rupert/.evolution/mail/local/
```

Put simply the "Folders" of outlook are stored in mbox format "Files" for both Thunderbird(Linux) and Evolution(Linux). So...

(1) I manually added subfolders in the Evolution Application under "On This Computer" such as "Personal" "Work" etc.
(2) I then copied the matching mbox files from thunderbird right over the top of the created mbox files within Evolution from procedure (1).

Eg:
```
cp /home/myUserName/.mozilla-thunderbird/989wzmgf.default/Mail/Local\ Folders/Outlook\ Mail.sbd/Personal\ Folders.sbd/Work Work
```

I did this for all my other folders and it worked for me. I hope this helps somebody.

---

### Post by shk76 on 2009-01-11
You dont need to install mozilla in windows. Follow the steps in 

[http://sayeed-linux.blogspot.com/](http://sayeed-linux.blogspot.com/)

It worked for me and hopefully will work for you

---

### Post by ronewolf on 2009-02-05
> **hartdg said:**
> 
3. Make sure that none of your .pst files have e-mails in the top level of the file. If there are some then move them into a sub-folder (otherwise Thunderbird will miss them). When this is done, close Outlook.


6. Copy all the .sbd folders that are in /Local folders (there should be one for each of your .pst files) into the folder "/home/<user>/.evolution/mail/local" on your Linux system

Thx for the clear and wonderfully helpful instruction. When Importing from Outlook, Thunderbird generated files such as *Inbox, Sent, & Unsent Messages* in addition to an * Inbox.SBD*. I found that if I overwrote the existing evolution *Inbox, Sent, & Unsent Messages* files with the ones with the Thunderbird generated files, that my Inbox, Sent, and Unsent mail came across in addition to all of the sub-folders under Inbox. So, unless there is something wrong here, I'd rewrite step 6 to:

6. Copy all the contents of /Local folders into the folder "/home/<user>/.evolution/mail/local" on your Linux system]

And, unless I'm missing something, step 3 is not needed. At least not for a fresh clean unused evolution instance.

---

### Post by Javier Tapia on 2009-07-31
Thank you Yoda_Oz, It works for me...

---

### Post by petermck on 2009-08-01
Has anyone tried readpst? If it works OK it would save a lot of mucking around with Thunderbird.

---

### Post by loowens on 2009-09-03
I actually used readpst today to do the migration.  I had tried the Thunderbird trick, but every time I would loose messages or entire folders.  I tried multiple utilities like O2M and MailNavigator all with disappointing results.  I finally found a snippet about readpst and tried it.  While it wasn't perfect it did capture all my outlook mail and created a seperate mbox file for each folder.

The trick to getting all this in evolution easily is to create the directory structure in evolution then just drag and drop the individual mbox file on the evolution folder.  This saves a considerable amount of time over using the evolution import tool.

the other alternative is running crossover with MS Office, the only problem I had with that was that I couldn't attach files to new messages for some reason. I reported it to Codeweavers, but no response yet.

---

