---
title: "Scream of a hardcore office user wants to switch to Linux!"
date: 2022-01-20
forum: New to Ubuntu
---

### Post by w202mg on 2022-01-20
Hey guys!
I'm running now a PC with some servers on Debian that is fully ok for this purpose. Now I was just about switching my working laptop to Linux after I tested all I needed for working will be possible on Linux (and for emergency cases Windows on dual boot) but I found one real obstacle for me. I'm working the whole day with files like pdfs, scans, office files, etc. For this, I'm using the preview of the files with scrolling and text copy possibility in the right sidebar of Windows Explorer which helps me a lot in my work and is speeding it up extremely. I tried all possible file managers and found only Dolphin is offering a kind of preview but in reality, it is only a thumbnail of the first page of the document. I could get also a preview of the first page of MS office. Also, my working neighborhood is using the same working way. For working with office files I'm using Onlyoffice due it has the best compatibility with MS office.

Second thing is that in MS outlook I can insert the last edited or created files which is very helpful. Also the search function in MS Outlook is looking in the files of the attachments. This I couldn't find in any of the mail clients for Linux.

PLEASE! If somebody has a solution for this, this would be great!

Thanks a lot!

---

### Post by ActionParsnip on 2022-01-20
For email you may want to use OWA/O365 in your web browser. This will ensure your emails work as expected. I'm not sure of any email clients that can do al the things that Outlook can do. I've seen a client called prospect-mail but haven't used it (It's installed via a snap)

---

### Post by w202mg on 2022-01-20
Yes, I know about these possibilities. As far as I know they don't catch the last edited or created files to attach them directly to the mail. Also MS...

---

### Post by Impavidus on 2022-01-21
I can't give you a solution, but I can explain why this is hard.

To have the file manager show a preview of the office file, even with the possibility to copy text, the file manager must have a fully-fledged reader and renderer for office files build-in, or it must be able to create a panel and instruct the office program to draw its output into that panel. Both ways require a high degree of integration between the file manager and the office program. There are many file managers and many office programs and many other programs that may want the same treatment.

For your second problem, there are toolkits that keep track of recently opened files and offer those as a quick choice. But that only works if the program you used earlier to open the file and the email program use the same toolkit to create their open file dialogue box. There are multiple toolkits and some applications just use their own routines.

So it's the modular nature of Linux that makes this hard.

---

