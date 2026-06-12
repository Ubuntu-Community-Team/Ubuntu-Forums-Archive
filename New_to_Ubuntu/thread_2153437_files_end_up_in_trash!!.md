---
title: "files end up in trash!!"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by mlempenau on 2013-06-11
Right now I'm using ubuntu 12.10 with all the updates.  But I remember this happening before and it was not on the version of ubuntu.  I have one directory backed up to ubuntu one. In the last year or so I have suddenly noticed that some of my data files are missing.  I accidentally found them in the trash both times!!  How can this be?  The files ... a significant number of them from several directories are all located in the one directory that I back up using ubuntu one.  Anyone else have this problem?

---

### Post by tbid18 on 2013-06-11
You're seeing files randomly disappear then appear in ~/.local/share/Trash/files?

---

### Post by mlempenau on 2013-06-11
I don't think I would call it random.  To my knowledge it has happened two times.  I go to search or access data on my computer and it's not there.  So I go looking for it and find it and a whole bunch of other files in the trash.  I guess it depends on what you consider random.  The first time it happened I figured I might of done something but this last time I find it hard to believe.

---

### Post by tbid18 on 2013-06-12
Hmm, I'm afraid I have little experience with ubuntu one, and I don't know why files would be moved to the trash for no apparent reason. A cursory search indicates some similar problems for other users, but there was little resolution. You could try checking the logs at .cache/ubuntuone/log[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif][COLOR=#000000] to see if there's anything obvious there. I'm sorry I can't be of more help.[/COLOR][/FONT]

---

### Post by howefield on 2013-06-12
Ubuntu One doesn't put files in the rubbish bin of its own volition, only when files are deleted on the Ubuntu One server by you or someone else using your (or another) machine with access to your account.

If you really believe otherwise, please file a bug by using the terminal command... 

```
ubuntu-bug ubuntuone-client
```

Or complete the support form at [https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)

---

### Post by mlempenau on 2013-06-12
There is no proof that ubuntu one is doing this.  But on the other hand what other reason is there?  That is really one of the main reasons I posted this on this form.  

I have given no one my password.  I do have ubuntu one loaded and working on my travel laptop.  

I guess I will change my password and watch things even more carefully.  Without more evidence I'm not sure what a bug report would accomplish.

---

### Post by mc4man on 2013-06-12
If you share the same ubuntuone account on more than one install & delete a file(s) on for example install A in a synced folder, then when you use install B, C, ect. that file or files will be moved to trash folder.
This will happen automatically without notice or comment.

---

### Post by mlempenau on 2013-06-13
I understand that when syncing to two computers what happens on one will happen on the other.  But this got me to thinking ... what is in the trash on my laptop?  When I looked I found that everything that was in the trash on my desktop was also in my trash on my laptop.  Furthermore, ubuntu one was syncing everything in my trash on the laptop to trash on my desktop ... again!  This is crazy.  I have tried in the past to restrict ubuntu one to sync only one way, but it wouldn't let me.  

How do I resolve this situation?

---

### Post by mc4man on 2013-06-13
> **mlempenau said:**
> I understand that when syncing to two computers what happens on one will happen on the other.  But this got me to thinking ... what is in the trash on my laptop?  When I looked I found that everything that was in the trash on my desktop was also in my trash on my laptop.  Furthermore, ubuntu one was syncing everything in my trash on the laptop to trash on my desktop ... again!  This is crazy.  I have tried in the past to restrict ubuntu one to sync only one way, but it wouldn't let me.  

How do I resolve this situation?
I've never had any folder synced that wasn't specifically marked to sync. Is  .local/share/trash or a parent folder marked on both installs?
Don't understand "but it wouldn't let me", either a folder is synced or not.
 (other than ~/Ubuntu One, it's your choice, not ubuntu one's

---

### Post by mlempenau on 2013-06-14
What seems to be happening is that I somehow accidently deleted a folder that was synced as part of the larger directory.  I didn't notice it right away and turned on my laptop to work.  It automatically synced that folder to the trash.  When I originally found the deleted folder in my trash on the desktop I moved it back.  But I forgot about the laptop.  So when I turned it on it synced to what was on the laptop at the time getting rid of the folder.  When I looked on my desktop the folder was now gone completely.

---

