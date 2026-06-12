---
title: "Using a common mailbox in Ubuntu and XP (dual boot)"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by leifoelgaard on 2006-06-11
Hi all

Having learnt so much from this forum i just want to give a little something back.

I have a PC with a dual boot into Ubuntu (6.06) or XP. A partition is formatted in FAT32 and shared between the two systems (automounted in Ubuntu - see the "Ubuntu Guide").

What i wanted was a common mailbox when using Thunderbird in either Ubuntu or XP so that i had all mails available in both systems. I know this can be done via setting up a mail server, using IMAP etc. but that's overkill in my case, having only one PC in the house ;) 

Here's what i did:

1. Install Thunderbird in both systems.

2. Make a directory on the shared partition (we could call it "MailBox")

3. Open Thunderbird (in either Ubuntu or XP) and enter settings. Under "Local Folders" point to the new directory you've just made.

4. Do the same thing in the other system - et voila - a common mail box  :p 

You can now see all your mails (incl. sent mails and special folders)

(Don't ask me how you import your old mails but i'm sure you will some how figure that out - i did from Incredimail - via Outlook - to Thunderbird)

Good Luck

Leif

---

### Post by chrism7 on 2006-06-12
Before I saw the light and stopped dual booting and started using VMWare for Windows I used the same profile for both Windows and Ubuntu.  The profile keeps everything, mail, preferences, address book etc.  I can't remember where Windows keeps the profile info, but in ubuntu it's in ~/.mozilla-thunderbird/ (I think).  The profile is usually xxxxxxx.default (where xx is a string of numbers and letters) and the profiles.ini file can be edited to point it to whichever profile you want.  If the Windows and Ubuntu profile.ini file are pointing to the same profile, voila all shared.

[http://www.mozilla.org/support/thunderbird/profile#new](http://www.mozilla.org/support/thunderbird/profile#new)

The above link explains it better.

---

