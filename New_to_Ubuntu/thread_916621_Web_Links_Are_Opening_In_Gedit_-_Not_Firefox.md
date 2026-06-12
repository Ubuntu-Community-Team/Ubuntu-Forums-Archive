---
title: "Web Links Are Opening In Gedit - Not Firefox"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-11
I'm trying to get Ubuntu to open web links in Firefox - NOT gedit. It seems that almost every other file has an "Open With" tab in the Nautilus Properties box. But there's no "Open With" option on web links. 

How can I get Ubuntu to open web links with Firefox? Thanks.

---

### Post by gvartser on 2008-09-11
See if this works:

1) Open/start up Firefox.
2) Click the "Edit" menu -> Preferences.
3) Select the "General" tab.
4) scroll down to "System Default" section, click on the "Check Now" button.
5) Done.

BR,
/g

---

### Post by bobsmith2 on 2008-09-11
Thanks, but that didn't work. My problem is this: When I drag links from the Firefox address bar to my desktop, and then click on those links, they open in gedit instead of Firefox.

In poking around I found this file:

~/.local/share/applications/mimeapps.list

Here's what's in it:

```
[Added Associations]
audio/x-ms-wma=mplayer.desktop;audacious.desktop;vlc-usercustom-usercustom-usercustom-usercustom.desktop;
audio/mpeg=audacious.desktop;
text/plain=gedit.desktop;ooo-writer-usercustom.desktop;
application/x-trash=gedit.desktop;
text/html=gedit-usercustom.desktop;
x-content/audio-cdda=sound-juicer.desktop;
x-content/blank-cd=nautilus-cd-burner.desktop;

[Removed Associations]
text/plain=gedit-usercustom.desktop;ooo-writer.desktop;
```

I'm thinking that the third line from the bottom (in the "Added Associations" section) may need to be edited, but I don't know if this file controls anything, or is just a log file, and I'm reluctant to mess with it without some assistance. Additional help would be appreciated.

---

