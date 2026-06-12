---
title: "auto renamed and 'blocked' (internal and external) drives"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by mark128 on 2015-09-02
i am not sure how to explain this so it will be understandable, and dont even know how to call it, therefore i didnt know how to search the forum for this problem. sorry..

since today Xubuntu has renamed one of my internal drives' partitions from DATA_1 to DATA_11, and has placed a little cross on the icon of DATA_1, that is still and constantly visible in the /media/me/ dir. in itself this is not really a horrible problem, because i can still access the drive under its new name, but some of the installed software is no longer functioning properly because it cannot find the DATA_1 drive (like thunderbird email). i could change the the settings for all these softwares, but i'd rather fix the problem at the source, especially because this has happened before with an external drive (which had little concequences), and so i think it is likely to happen again.

is there a way i remove the now inaccessable and crossed out DATA_1 instance, so the actual drive can be recognized as DATA_1 again? or something to that effect?
hope you can understand what i mean. because saving screenshots is one of the things that now seems to be a problem, the picture with my old phone is all i can do..
[http://postimg.org/image/s84jea0ip/](http://postimg.org/image/s84jea0ip/)

thanks! :)

---

### Post by TheFu on 2015-09-02
The best way I know to deal with this is to NOT use automatic mounting.  You can mount any storage you like anywhere you like.  But it is best to NEVER mount anything under /media/.

If this storage is USB and might be moved, then caution is needed. All other permanent storage is mounted through the fstab.  Use an editor to make the changes. Lots of how-tos for that exist.  Search "ubuntu fstab" for a guide.

If you need to connect and disconnect the storage, look into autofs - but that is a non-trivial thing for an end-user.

---

### Post by mark128 on 2015-09-03
thanks for your answer TheFu! :)

please forgive my noobness, trying to understand what you are saying is already a challenge for me. i've been reading things about fstab, automatic mounting and even just mounting for about 2,5 hours now; my mind is kinda spinning. sorry, it's just that all of it is so completely new to me! :o

from what i think i do understand, let me check the following:

> **TheFu said:**
> The best way I know to deal with this is to NOT use automatic mounting.  You can mount any storage you like anywhere you like.  But it is best to NEVER mount anything under /media/.

is automatic mounting what happens when i doubleclick on one of the partition icons on the desktop, or when i rightclick on one in the dir tree and then select "Open (in new tab)"? (and not automatic would be by typing a mount command in a terminal?)

> **TheFu said:**
> If this storage is USB and might be moved, then caution is needed. All other permanent storage is mounted through the fstab.  Use an editor to make the changes. Lots of how-tos for that exist.  Search "ubuntu fstab" for a guide.

the storage i have trouble with is a partition on an internal, non USB, HD, it is not moved (as far as i understand).

do i understand it correctly that you are suggesting it would probably work best if i edit the fstab file, adding the partition i have troubles with to mount (to a different location than /media/) at boot?

that would involve me pointing the 'confused' software to the new location of the partition, right?

> **TheFu said:**
> If you need to connect and disconnect the storage, look into autofs - but that is a non-trivial thing for an end-user.

luckily, i don't think that is needed.

---

### Post by mark128 on 2015-09-03
i have been thinking along a different path, from the things i think i do sortof understand, and that raises these questions:

do de little crosses on the icons (see: [http://postimg.org/image/s84jea0ip/](http://postimg.org/image/s84jea0ip/) ) mean these drives/directories are only accessible by root? and if so, is there a way to reverse that setting for these partitions and make those namingshemes available for all again?

that seems the most understandable solution for me, and the closest to how it was before and it would not involve me having to redirect all the affected softwares to a new location.

---

### Post by TheFu on 2015-09-03
Sorry - I cannot answer any GUI questions. Don't use those much and my GUI isn't the same as yours, almost certainly. That is my ignorance.  GUIs change every few years, but the shell way for most things doesn't change over 20 yrs.  For example, the fstab file has basically been the same all this time.

Yes - you should NOT mount anything under /media/ ... or any subdirectories under there. Sorry if that wasn't clear. That area of the file system is for automatically mounted storage ... which I generally think of as USB storage.  In a Linux directory structure, there is a place for everything and everything has its place.  Permanent mounts do not belong under /media/ ... ref: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

For "data", I mount storage under /D/ ... with a different subdirectory for each mount - some are local, some are NFS, some are CIFS, ... you get the idea.  I use autofs myself, that way USB storage on some other system can be NFS mounted, but only gets mounted as needed, not always.  It is hard to explain, but once you see it in use, makes perfect sense.

Programs should never be installed under /media - NEVER.  

  >   /media - 	Mount points for removable media such as CD-ROMs (appeared in FHS-2.3).
It isn't just me - this is from the 'standards document'.

---

### Post by mark128 on 2015-09-03
ah! thanks! things are slowly getting a little clearer in my mind, thanks.

i guess diving deeper into linux, the use of the terminal and command lines, would be good if i wanna keep using it (which seems likely given the path microsoft is going). it's just that it is a lot to take in sometimes and everything is connected to everything with these subjects, even in the use of the language discussing linux (and computerstuff in general).

i am gonna need to puzzle and study a bit more, but your directions have helped me along, and i am probably gonna set it up that way at some point. thanks!

---

### Post by mark128 on 2015-09-03
anyone have an answer to my GUI question?
> do de little crosses on the icons (see: [http://postimg.org/image/s84jea0ip/](http://postimg.org/image/s84jea0ip/)  ) mean these drives/directories are only accessible by root? and if so,  is there a way to reverse that setting for these partitions and make  those namingshemes available for all again?
it still seems the easiest and quickest path/kludge  for me right now, since i need my email working as soon as  possible, and for the proper solution i still need to do (a lot) more  studying, and ajusting settings in all affected programs..

---

### Post by TheFu on 2015-09-03
When you are really new to Linux, gaining the background and little history and some basic ideas in a directed way (either from training or a beginners book) is something we forget.  Everyone has gaps in our knowledge, because there is way to much to know.  I think I know about 5% about Linux servers and even less about desktops.

Anyway - a good book to get that beginning-level, basic knowledge: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
Read the first 240pgs, then skim the rest in about an hour just to know what it covers and what is possible.  This is NOT about point-n-click knowledge which will all change with the next release. This is long-term knowledge.

As to an easy way to make your email start working ... you can use symbolic links from the new storage location to the old location.  Almost always, that will work. If that link gets removed for any reason, things will break, but ... you can figure that out later.  I don't remember what email (client or server or something else) you are trying to solve.  Keeping anything other than media files on non-Linux storage is a really bad idea for a number of reasons.  Trying to make Linux work with non-Linux storage will always be a hassle.  At the core, Linux and linux files are multi-user - PERIOD.  That is central to security of the system. For non-Linux mounts, the only way to control permissions is during the mount. That is where you set the owner, group, and any directory and/or file permissions.  The automatic mounts made all sorts of assumptions for you. 

If you need help with mount options, please post the **ls -al** and **df -h** and **lsblk** output and contents of **/etc/fstab** for the directories/files that aren't working.  fmask, dmask, uid and gid are probably the important options. Can't be sure from here.

---

### Post by mark128 on 2015-09-04
ja, when i began to realize that the depth of 'computer knowledge' is pretty close to infinity and i really know nothing (while i was really trying to understand and work with Win XP) i pretty much gave up on becoming knowledgeable on the subject and switched to merely being an end user, just wanting to use the buttons without much desire to know too much about what they do exactly. though to many of my friends i am still 'the guy who knows about computers'. :o

thanks for the link to the book, it looks like a good start! i am gonna spend time with it.

as for the rest of the problem(s), i am gonna need to process the info you gave, but have so much other things i need to do today and this weekend, that i need to come back to that later (and check my mail online). that might be after the weekend. hope you don't mind and that your offer to help with the mount options will still stand at that time.

thanks for your help so far! :)

---

### Post by mark128 on 2015-09-08
hello there [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"),

i have not had the time and attention to read into this subject matter so far, but i spoke to a friend who turns out to be knowledgeable about linux and said that he would gladly help me figure things out and explain a few things. he's coming over Thursday, so i'll go ahead an consider this thread solved. thanks for your help.

---

