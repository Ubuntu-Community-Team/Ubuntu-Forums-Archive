---
title: "search system files for salvage"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by Tazmman on 2013-11-30
Hello I've been using Ubuntu for a while now as a basic user( Web browsing, Music, Video):popcorn:
	 I have dabbled abit with salvaging files from defunked OS's (slaving the hard drive to browse the user & storage files). I 've got a hard drive with A previous of Ubuntu on it, Which went rouge on me.:(    I was wondering  if anyone could direct ,Or describe to me, which folder holds the browser app. such to locate the bookmark file. Hopes of salvaging them. 

Yes I know... I can already image some responses. Which are advising, that I should have done a bookmark back-up:rolleyes:... I've learned I learned my lesson.

 So any hints?

---

### Post by deadflowr on 2013-11-30
Which browser?

The default Firefox browser holds info in /home/username/.mozilla/firefox.
I think(but am not sure) that what you want is in there.

It's a hidden folder (use crtl +h to show)

Other browsers might hold their info in other places, such as .config folder, also hidden in the users home folder.

---

### Post by Tazmman on 2013-11-30
Yes. Firefox is the one . Thanks

---

### Post by electrohandyman501 on 2013-11-30
> The default Firefox browser holds info in /home/username/.mozilla/firefox

Add to the line>>>>   xxxxxx.default/bookmarkbackups

The x's before the .default could be almost anything, but the rest should get you there. BTW I'm using Ubuntu 12.10
In backup folder there may be many entries. Mine has 11 entries, 1 per day for the last 11 days.

Not sure what format the files are, but you should be able to "restore" them thru the bookmarks restore function, or be able to import them thru the restore function.

---

### Post by Tazmman on 2013-11-30
Ok . I've located the backup folder, But... the backup files themselves, look to locked. 
This does not surprise me. While attempting an upgrade with this "Install"(It was 10.04 at the time). It for some reason, it  locked me out. :confused:
Any suggestions.

---

### Post by electrohandyman501 on 2013-12-01
I'm no expert on this part, but it sounds more like the files are owned by another "ownership" group and owner, so you can't open them.
If you can see the files in your file manager application, you could  also right click on the file and select properties. I'm pretty sure you cannot  change ownership this way, but you can add permissions to allow  "others" to access the file, and what group the file belongs to.

There is some command line options that you can change the ownership of the files to unlock them.
The command line command is 'chmod'. you will need to research or ask how it's used as I haven't used it as yet, only read about it.
From a terminal window you can type 'man chmod' and read about it. Or search here on this site, there has to be some posts of others having made file ownership changes like what you are wanting to do.
It's more powerful in that you can use it on the entire directory and all files within the directory, so use it with care.

---

