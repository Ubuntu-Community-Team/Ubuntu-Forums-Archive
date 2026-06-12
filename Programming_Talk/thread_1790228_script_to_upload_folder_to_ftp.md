---
title: "script to upload folder to ftp"
date: 2011-06-24
forum: Programming Talk
---

### Post by mbeltoft on 2011-06-24
I'm looking for a script that will upload a folder and all subfolders to a ftp via cron

uploading a single file is easy but i can't figure out how to upload a whole folder structure.

also i don't want it just to upload everything, if the same file already exist on the ftp (name and size check) then it should be skipped but if something is deleted in the local folders it should be deleted on the server too. Also it should skip files that are larger than 15MB

I want this because a have a bunch of photos I want to backup to a external FTP. I already have local backup so to save space and transfer time my idea is just to have a mirror of my current photo folder. 

I've tried with rsync but my host only provides ftp access so I'm a bit lost here.

Hope someone can help me.

---

### Post by yotam on 2011-06-25
Consider
  weex - A non-interactive FTP client for updating web pages

---

### Post by hakermania on 2011-06-26
consider that some hosts can extract archives themselves from the file manager they have.
You could try to zip the folder and then extract it from the server. At least in t35 this worked as far as i remember

---

### Post by mbeltoft on 2011-06-26
Thanks. :)
weex do almost want i want but it'll do fine.

Had been searching all over to find something like that but gave up and thought I had to do a script myself

---

