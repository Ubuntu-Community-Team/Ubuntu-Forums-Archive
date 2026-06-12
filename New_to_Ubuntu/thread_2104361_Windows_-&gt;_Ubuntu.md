---
title: "Windows -&gt; Ubuntu"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by chowse on 2013-01-12
Hi!
This is my first post to this forum.
I have a LOT of experience with FreeBSD and Linux, but it's been a LLOONNGG time.
I'm not really a beginner, but I want to post this in this forum.

I'm bored with Windows 7 Ultimate.  I need to discuss preparing to install Ubuntu and getting all my software "crossed over".

My hardware:
AMD Phenom Quad-Core w/ 8 G on a 100 G SSD.  Also have 2 other spinny HDD's.
Video card is an ATI Radeon HD 5450 and I have a Hauppauge WinTV HVR-1600 TV tuner.

Here's my checklist for Windows before I install:

Create an image of Windows C: for easy restoration.
Export everything that will export so I can import it in Ubuntu.

One thing I'm concerned about is Outlook.  I've read lots of threads on this forum about importing .pst files.
What is the current way to go from Outlook to Evolution?

--
Thanks,
Charles

---

### Post by eenofonn on 2013-01-12
Who hosts your email? If you're setup with IMAP you could just set up Evolution with the server settings and it should download all your mail.

---

### Post by chowse on 2013-01-12
> **eenofonn said:**
> Who hosts your email? If you're setup with IMAP you could just set up Evolution with the server settings and it should download all your mail.

I'm currently using Charter POP, but I could change to IMAP.  Would that work?  I've got several 'other' folders that need to be imported.

---

### Post by eenofonn on 2013-01-12
POP would make things more difficult, google (gmail, google apps) is the only POP host I've ran into that gives you the option of storing your mail online after it's been downloaded. 

If they do offer web access to your mail you could log in and verify that your emails do get removed when they are downloaded to Outlook. You might want to look at the export formats of Outlook and see if any of them are compatible with Evolution (or Thunderbird for that matter).  Also you could always look at using Kontact/Kmail if you're not opposed to KDE instead of Gnome/Unity.

... and now that I've typed all that out a quick google gave me this [YouTube - Import PST to Evolution]("http://www.youtube.com/watch?v=6CiSX3rkl98")

---

### Post by Mark Phelps on 2013-01-13
> **chowse said:**
> ... and getting all my software "crossed over"...

IF that that, you mean learning how to use ALTERNATE applications in Ubuntu to do what you did in MS Windows, then you have come to the right place.

If by that, you mean learning how to use the SAME applications in Ubuntu that you did in MS Windows, you're going to be in for a major disappointment because LOTS of stuff that just ran by default in MS Windows does not work in Linux.

As to OUTLOOK and pst files -- you can't import them directly.  Perhaps some info in the link below will help:

[http://www.ehow.com/how_7356681_import-pst-file-evolution.html]("http://www.ehow.com/how_7356681_import-pst-file-evolution.html")

---

### Post by Frogs Hair on 2013-01-13
The link may be helpful but it is a only a list and not a detailed description of the software. Most of the big four web browsers with the exception IE can sync bookmarks and extensions simply by logging in and/or using sync. [http://www.linuxalt.com/](http://www.linuxalt.com/) 

IE wont run on Linux with out Wine or Crossover which are emulator type programs. The same is true of _some_ Windows games but with Steam gaming choices have certainly improved. [http://steamcommunity.com/linux](http://steamcommunity.com/linux)

---

### Post by chowse on 2013-01-13
> **Mark Phelps said:**
> IF that that, you mean learning how to use ALTERNATE applications in Ubuntu to do what you did in MS Windows, then you have come to the right place.

If by that, you mean learning how to use the SAME applications in Ubuntu that you did in MS Windows, you're going to be in for a major disappointment because LOTS of stuff that just ran by default in MS Windows does not work in Linux.

As to OUTLOOK and pst files -- you can't import them directly.  Perhaps some info in the link below will help:

[http://www.ehow.com/how_7356681_import-pst-file-evolution.html]("http://www.ehow.com/how_7356681_import-pst-file-evolution.html")

I'll be using alternate applications.
I've set Outlook to IMAP.  That will take care of the mail, but I'm not sure about the calendar and contacts.

---

### Post by chowse on 2013-01-13
Workarounds...
Gmail for Mail and Contacts
Google Calendar for Outlook Calendar and Tasks
MS Apps Online (SkyDrive) for OneNote
KeyPass, FeedDemon and FileMaker Pro are backed up on another drive.

I think I'm ready to install!

---

### Post by eenofonn on 2013-01-13
> **chowse said:**
> Workarounds...
Gmail for Mail and Contacts
Google Calendar for Outlook Calendar and Tasks
MS Apps Online (SkyDrive) for OneNote
KeyPass, FeedDemon and FileMaker Pro are backed up on another drive.

I think I'm ready to install!
Good to hear! Don't forget about Google Docs ;)

---

### Post by alphacrucis2 on 2013-01-13
Install Thunderbird under Windows. It has an option to import from Outlook. It doesn't read the the .pst files but does the import by MAPI calls to Outlook itself. Once you have all the data in T'Bird you can directly transfer to T'Bird under Linux. Shouldn't be too hard to then transfer the mail and contacts to Evolution (if you must use that) via export/import. Not sure about the Calendar. Try installing the Lightning add on in Tbird before importing from Outlook then you could try this:

[https://getsatisfaction.com/mozilla_messaging/topics/how_do_i_import_outlook_calendar_items_into_thunderbird_calendar](https://getsatisfaction.com/mozilla_messaging/topics/how_do_i_import_outlook_calendar_items_into_thunderbird_calendar)

---

