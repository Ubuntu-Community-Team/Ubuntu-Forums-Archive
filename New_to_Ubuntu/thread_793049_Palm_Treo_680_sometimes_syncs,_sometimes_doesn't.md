---
title: "Palm Treo 680 sometimes syncs, sometimes doesn't"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by chchandler on 2008-05-13
As the title says...

I have it set in Palm OS Devices|Gonme Pilot Settings|Devices as Type: USB Device: usb:

First try it connected and found the Palm, got it's serial number and name and all that, sync'ed my calendar and stuff.  It hung at Tasks/ToDo.  After that, no sync.  Just times out.

Suggestions appreciated...

---

### Post by lazyart on 2008-05-13
J-Pilot is what I used on my TX and what I currently use for my 680.  Give it a whirl (it aims to be a replacement for Palm Desktop on the Windows side).

---

### Post by chchandler on 2008-05-13
J-Pilot is going to be my backup choice.  First choice would be to get the Evolution link working - my calendar and addressbook, at least...

It's worked a second time.  Then stopped.  So, I re-booted, thinking that might do it.  No joy.

---

### Post by stinger30au on 2008-05-13
my palm treo 750 does not sync... ever :-(

---

### Post by Brerlapn on 2008-07-19
Have you checked your data in JPilot to make sure it's backing up all your contact information?  The fields on the desktop are from the old Palm OS, and newer Treo's have a lot more data fields that can contain information which are not shown in JPilot.

I know this isn't the answer the original poster was asking about, but I opted to install KPilot and Kontact over JPilot so that I wouldn't have data that wasn't backed up to the computer.  I saw similar data integrity issues when I tried using Evolution, as it placed contact information in the wrong field.  (Mobile numbers would show up in Evolution as Home numbers, faxes and phone numbers, etc.)  If you are using JPilot or Evolution, I would strongly recommend doing some spot checking of data from your Treo to the desktop application to make sure that the desktop isn't losing or jumbling your data.

I did a longer post over on Treocentral back when I originally was working through this, but Kontact syncronizes Palm data from your Treo using a protocol that either is vCard, or acts like vCard, while Evolution uses a protocol that either is or acts like a .csv (comma separated values) file.  The difference is important--csv exports a Palm contact into a set of fields that will get synced according to their order in the fields--*not* their label.  For things like phone numbers and emails, if you used the little pulldown menu to change the label for a number or email on your Treo, then that number will be out of order in the csv file.  If you put your contact's mobile number in the second phone field, which is by default for the home number, then when you sync to Evolution it will put the number in its field for home number, even though the label for that number on your Treo is "mobile".  Because Kontact uses the vCard format, it syncs your data based on how it's labeled, not on what order it occurs in the csv file.

My only issue with Kontact is that it doesn't display Palm's 'custom' fields.  Since I don't use those a whole lot, I just went through and copied my custom fields into the "Notes" field, which Kontact does sync.

ToDo's and memo's synced just fine for me.

The original request for information was a little old, but I thought I'd post something for the record if anyone else is having the same problems.

---

