---
title: "Can't open 'Places' folders."
date: 2012-02-21
forum: New to Ubuntu
---

### Post by backflip on 2012-02-21
ubuntu 10.10
I was using calibre and now I can't open any folders in 'Places,' Home Folder, Documents, Music, Pictures etc. I get a box informing me  'No application is registered as  handling this file.'
I can access by opening nautilus in terminal. I then tried right clicking and choosing 'open with other application' and opting for 'file browser' from the list, but that didn't work.
Thanks for any help.

---

### Post by SlugSlug on 2012-02-21
[http://ubuntuforums.org/showthread.php?t=1631961](http://ubuntuforums.org/showthread.php?t=1631961)

---

### Post by backflip on 2012-02-21
Thanks, I tried the suggestions in that thread but they didn't work. Everything opens OK with nautilus and I put a shortcut of the file browser on the desktop and that opens the 'Places' folders fine. It's  just when I go  to 'Places' and then try and open a folder from the dropdown menu that the problem starts.

---

### Post by thirnick on 2012-02-21
try the trash bin  its also a browser

---

### Post by JC Cheloven on 2012-02-21
Mmm... the thread is tagged as LUbuntu, but you talk about Nautilus, places&folders... you should be on pcmanfm (not nautilus) if you were using lubuntu. 
Perhaps is there any history of desktops installations in your system that is worth to mention?

(side note: calibre works fine for me on lubuntu 11.04)

---

### Post by backflip on 2012-02-22
Sorry, I didn't notice Lubuntu in the heading.
It is definitely Ubuntu 10.10 as I noted at the start of my first post.
I've put a launcher for the file browser in the panel and that works OK. The dropdown menu under 'Places' still shows all the various folders but won't open any 'not registered to open.'
Thanks for any ideas.

---

### Post by Krytarik on 2012-02-22
> **backflip said:**
> The dropdown menu under 'Places' still shows all the various folders but won't open any 'not registered to open.'
As a follow-up on *SlugSlug*'s suggestion, please post the content of your "~/.local/share/applications/mimeapps.list" (Notice: yours, not root's! So don't use "gksudo" or "sudo" for that; just open it with your text editor.)

Regards.

---

### Post by backflip on 2012-02-23
> **Krytarik said:**
> As a follow-up on *SlugSlug*'s suggestion, please post the content of your "~/.local/share/applications/mimeapps.list" (Notice: yours, not root's! So don't use "gksudo" or "sudo" for that; just open it with your text editor.)

Regards.

Sorry I took so long, but is this what you want?

[Added Associations]
audio/mpeg=vlc.desktop;
application/pdf=userapp-FoxitReaderPortable.exe-RVCGVV.desktop;evince.desktop;
application/x-sqlite3=wine-extension-jfif.desktop;
application/x-ms-dos-executable=wine.desktop;file-roller.desktop;userapp-wine-Y0UIVV.desktop;
audio/x-wav=rhythmbox.desktop;

[Removed Associations]
audio/mpeg=userapp-promoe-2Q76KV.desktop;userapp-xmms2-A29ILV.desktop;
application/pdf=userapp-Foxit Reader.exe-N103PV.desktop;userapp-Foxit Reader.exe-0CEIQV.desktop;userapp-FoxitReaderPortable.exe-4AZ0PV.desktop;userapp-FoxitReaderPortable.exe-BC8PLV.desktop;userapp-Foxit Reader.exe-9U22LV.desktop;userapp-Foxit Reader.exe-Y6CVLV.desktop;wine-extension-pdf.desktop;

[Default Applications]
text/html=chromium-browser.desktop

I can't see anything similar to what Slug Slug suggested.

Thanks

---

### Post by nothingspecial on 2012-02-23
> **backflip said:**
> Sorry, I didn't notice Lubuntu in the heading.
It is definitely Ubuntu 10.10 as I noted at the start of my first post.


Fixed :)

---

### Post by backflip on 2012-02-23
> **nothingspecial said:**
> Fixed :)

Thanks for that, I tried, but couldn't see how I could change the heading.

---

### Post by Krytarik on 2012-02-23
> **backflip said:**
> Sorry I took so long, but is this what you want?
No worries, it's well under the 'late response' threshold. ;-) - Yup, exactly, thanks.

> **backflip said:**
> I can't see anything similar to what Slug Slug suggested.
Yeah, me neither. Please check if the issue is also present in the "Guest Session" or a newly, fresh user account. Also, do you possibly have XFCE installed additionally, side-by-side?

---

### Post by backflip on 2012-02-24
XFCE not installed and no guest sessions etc.

Many thanks.

---

