---
title: "Can't find recovered files?"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by P-rench on 2011-10-22
This is truly driving me insane for starters. I have used 2 different programs, scalpel and photorec to recover pictures that got deleted (I'm a photographer). The folders that these recovered jpg pics are supposed to be saved in have these little padlocks next to them (apparently this has something to do with the root user?) and when I open the folders they are completely empty but according to the recovery programs I used there was something like 20,000 pictures found and recovered and I'm currently missing about 6 gigs of hard drive space. Wherever these recovered pictures are located is an absolute mystery to me and I could really use some help finding them .

---

### Post by cozumel on 2011-10-22
I think the padlock is saying that you haven't got ownership of the folders.  You would need to change ownership with "sudo chown -R"

Should mention I am also noob, so wait for someone else to reply to confirm.

---

### Post by The Cog on 2011-10-22
Yes the padlock says you don't have permissions to the folder.

You can change the owner of the folder to your username with the command
> sudo chown -R yourname foldername
but I'm not sure if you should do that - you haven't said what directory these files are in. There are some folders that you need to be more careful messing around in.

If there's any doubt, check back here before doing anything.

After you regain access, can I suggest that an external USB disk makes a good backup solution.

---

### Post by P-rench on 2011-10-22
Thanks, I'm gonna try that out. The two folders I'm gonna do it on are"scalpel-output" and "test". I don't believe there should be any problems with this, but if so let me know.

---

### Post by P-rench on 2011-10-22
Wow, really disappointed. I got the folder to work but all of these pictures are like tiny thumbnails from the internet or something. Theres like no pics I've took that I see yet, not even pics I deliberatly deleted in the trash can a one time or another.

---

### Post by cozumel on 2011-10-22
Hi,

If you use nautilus to view the folders, I believe you can configure the way the folders are viewed.  So you should be able to have the thumbnails zoomed so you can see the photos before opening

---

### Post by The Cog on 2011-10-22
Unfortunately, I don't know these recovery programs. Is it possible that they didn't recognise your photos because they were not a file format they know? Like in raw format perhaps? 

I have seen lots of good comments about something called testdisk which I gather can do file recovery. The only thing is, the more you do to the disk, the more you might be making it difficult for programs to recover things.

Maybe you should read up about testdisk while you wait for someone who knows more about recovery to post in this thread.

---

