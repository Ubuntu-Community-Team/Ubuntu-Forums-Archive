---
title: "[SOLVED] no migration for my installation"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by rfbeck on 2008-08-18
When I installed 8.04 x64 tonight, I got to the point where it asks you if you want to migrate settings from your other operating system. Except in my case the installer didn't recognize the I had WinXP installed. Thus I didn't gt to migrate my bookmarks (like I've done in previous installations). 
So, can I do this manually? I can access my windows drive from Ubuntu, so is there a way to do this? Thanks.

Robert

---

### Post by spin2cool on 2008-08-18
Are these just firefox bookmarks?  If so, you can just migrate your whole profile.

You'll want to copy the contents of your current profile 
(found in:C:\Documents and Settings\<user name>\Application Data\...)

Into your new profile folder:
~/.mozilla/firefox/<randomstring>.profilename/

Alternately, you can use a softlink to make them share a profile:

#make a backup
cp <path of firefox profile> <path of firefox profile>.bak

#create the softlink
ln -s <path to windows profile> <path of firefox profile>

---

### Post by chrisod on 2008-08-18
If they are IE bookmarks you'll need a freeware tool to export them as html. Use Google to find one, it's been years since I had to do it. Then import them into Ubuntu Firefox.

---

