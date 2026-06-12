---
title: "Received calendar invite: What's the most professional way to respond?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-03-19
I just received the first calendar invite I've ever gotten once I moved to Ubuntu.

I need to 'look' professional. In the olden days (years ago, on Windoze), I'd simply accept with Outlook; but ... I'm not using Outlook. I'm using Thunderbird for email and nothing for a calendar manager.

To 'professionally' handle a calendar invite, what software on Ubuntu is recommended?

```

BEGIN:VCALENDAR X-LOTUS-CHARSET:UTF-8 VERSION:2.0 PRODID:-//Lotus Development Corporation//NONSGML Notes 8.5.2//EN_S METHOD:REQUEST BEGIN:VTIMEZONE TZID:Pacific BEGIN:STANDARD DTSTART:19501105T020000 TZOFFSETFROM:-0700 TZOFFSETTO:-0800 RRULE:FREQ=YEARLY;BYMINUTE=0;BYHOUR=2;BYDAY=1SU;BYMONTH=11 END:STANDARD BEGIN:DAYLIGHT DTSTART:19500312T020000 TZOFFSETFROM:-0800 TZOFFSETTO:-0700 RRULE:FREQ=YEARLY;BYMINUTE=0;BYHOUR=2;BYDAY=2SU;BYMONTH=3 END:DAYLIGHT END:VTIMEZONE BEGIN:VEVENT DTSTART;TZID="Pacific":20120329T140000 DTEND;TZID="Pacific":20120329T150000 TRANSP:OPAQUE DTSTAMP:20120319T230337Z SEQUENCE:0 ATTENDEE;ROLE=CHAIR;PARTSTAT=ACCEPTED;(PERSONAL STUFF DELETED)";RSVP=FALSE (PERSONAL STUFF DELETED) -Lotus_Notes_Generated X-LOTUS-BROADCAST:FALSE X-LOTUS-UPDATE-SEQ:1 X-LOTUS-UPDATE-WISL:$S:1;$L:1;$B:1;$R:1;$E:1;$W:1;$O:1;$M:1 X-LOTUS-NOTESVERSION:2 X-LOTUS-NOTICETYPE:I X-LOTUS-APPTTYPE:3 X-LOTUS-CHILD-UID:(uid deleted) END:VEVENT END:VCALENDAR 
```

---

### Post by TeoBigusGeekus on 2012-03-19
Install [this]("https://addons.mozilla.org/en-US/thunderbird/addon/lightning/") add on in Thunderbird.

---

### Post by rocksockdoc on 2012-03-20
Thanks for the advice.

Here are the instructions for installing Lighting into Thunderbird (I have TB 3.1.19).

**How to Install Lightning in Thunderbird:** 

[LIST=1]
[*]Download and save the lightning xpi file to your hard disk.
[LIST]
[*]lightning-1.3-tb+sm-linux.xpi
[/LIST]
[*]In Mozilla Thunderbird, open Add-ons from the Tools menu.
[LIST]
[*]Tools -> Add-ons
[/LIST]
[*]From the options button next to the add-on search field, select "Install Add-on From File..." and locate the downloaded add-on.
[/LIST]
Hmmm... I don't see that "options" button anywhere!


First I read the instructions:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214644&stc=1&d=1332271517[/IMG]




Then, I downloaded the file:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214645&stc=1&d=1332271516[/IMG]

But I don't see the "options" button that is described in the instructions:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214646&stc=1&d=1332271516[/IMG]

Q: Do you know where this Thunderbird options button lies to load the XPI file?
(Is there another way to load the XPI file?)

---

### Post by TeoBigusGeekus on 2012-03-20
It should be up there...
See screenshot.

---

### Post by rocksockdoc on 2012-03-20
I'm using Thunderbird 3.1.19 on Ubuntu 10.04 (which is what came from the Ubuntu Software Center, IIRC).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214648&stc=1&d=1332272087[/IMG]

Thanks to your tip, I found that the "install" button in the bottom-left of the Tools-> Add-on screen is what is used to locate the XPI file. So now I can easily locate the XPI file to install it.

But, when I install the XPI file, I get this error:
**Lighting 1.3 could not be installed because it is not compatible with Thunderbird 3.1.19**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214649&stc=1&d=1332272087[/IMG]
Lighting 1.3 could not be installed because it is not compatible with Thunderbird 3.1.19

---

### Post by TeoBigusGeekus on 2012-03-20
I'm using the 11.00 version.
Perhaps you could update straight from thunderbird's site?

---

### Post by rocksockdoc on 2012-03-21
The latest version of Thunderbird worked like a charm!

I had to change the link to /usr/bin/thunderbird
FROM:
/usr/bin/thunderbird -> ../lib/thunderbird-3.1.19/thunderbird.sh
To:
/usr/bin/thunderbird -> ../lib/thunderbird-11.0/thunderbird

I wonder why the old Thunderbird ran a (relatively complex) shell script while the newer thunderbird does not???

---

### Post by rocksockdoc on 2012-03-21
I accepted the calendar invite and then called the inviter who said it worked fine on Outlook!

Thanks.

Now I have to look into a calendar manager! :)

---

