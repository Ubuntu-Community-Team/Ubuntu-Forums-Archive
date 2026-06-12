---
title: "How to read a Microsoft Outlook Express address file (.WAB)"
date: 2019-01-21
forum: Programming Talk
---

### Post by weyland42 on 2019-01-21
This is a .WAB file from a friend's broken XP computer. I have no access to any Windows machine. I **can** read the hard-disk in a dock attached to my Ubuntu Mate machine.

The file is supposed to contain names, phone numbers, email addresses, and the like, and they do seem to be in there, but not in any discernable way that they can be related to each other. 

I mean they're all in different parts of the file, and the file is in a very peculiar format in any case. For instance the email addresses are fragmented with hex 00 between characters, and the file is well padded with long strings of hex 00s and other non-ASCII bytes.

I can write a program (with Regina REXX) to make the text bits readable, but I won't be able to collate related information. Can't find a description of the file format on the web, including Microsoft "support" sites. I also have a file called wab.hlp, but that's unreadable gibberish as well.

Anyone have any ideas about the format of .WAB files?

---

### Post by lisati on 2019-01-26
Is [this]("https://fileinfo.com/extension/wab") the sort of thing you are after? (N.B. The link is to a Windows program, so it's unlikely to work directly on Ubuntu. Perhaps with Wine or similar?)

**Disclaimer:** I have not tried this program. Neither have I used Wine for some time.

---

