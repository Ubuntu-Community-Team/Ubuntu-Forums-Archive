---
title: "SMB:// in kubuntu makes CRLF UNIX files from a Windows System"
date: 2007-10-15
forum: Programming Talk
---

### Post by hakre on 2007-10-15
I have got a programming related problem. When I code something on my Windows Box I often use the Unix format for a multiline file (LF).

Now when I copy those files on my linux box (kubuntu), the system there seems to think that any .pl file from a smb:// place MUST have CRLF _and_ converts the Unix-file from LF to CRLF. That really sucks because that produces errors under linux. Any Ideas? I don't know where to look for this option. I've checked smb.conf but haven't found the "auto-convert anylineending to CRLF while copying an 'anykind of textfile' onto a linux box"-smb-fusefs-setting.

I'm using konqueror on kubuntu.

---

