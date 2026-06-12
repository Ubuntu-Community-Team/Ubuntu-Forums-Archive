---
title: "Mapping keys to open a specific folder in Nautilus."
date: 2009-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Saint Angeles on 2009-05-07
I was having a chat with a buddy of mine and were talking about how we map certain keys to certain functions in Ubuntu. for instance, if i press "print screen" it will take a screenshot and if i press "home" it will open a terminal. my buddy wanted to know if there was any way of being able to press a certain key combination to get a folder to pop up in Nautilus. after doing a little bit of research, i found a very easy solution:

i discovered that if you run a command like:
```
nautilus "Desktop"
```it will open up your desktop folder in nautilus. this works for any folder in your home directory. knowing this, you can easily set up a keyboard shortcut by clicking "System->Preferences->Keyboard Shortcuts"

but what if you want to open up a folder thats not in your home folder? easy. create a "symbolic link" of the folder you want to be able to have open and put the link in your home folder. a symbolic link is identical to a "shortcut" in windows or an "alias" for mac.

for example, i have an external USB drive that mounts at:
```
/media/Gideon
```and i have a music folder at:
```
/media/Gideon/My Music
```to create a symbolic link of that folder, i select it in nautilus and click on "Edit->Make Link" or just type "ctrl+m". you will now see a new folder with an arrow emblem on it that says "Link to My Music".

now, all i have to do is drag that link into my home folder and rename it to something easy like "music". then i can go to "Keyboard Shortcuts" and use this command in a shortcut:
```
nautilus "music"
```voila! i hope this is helpful to at least one person here.

NOTICE:
for some reason, you cannot create a symbolic link in a FAT32 drive.

---

