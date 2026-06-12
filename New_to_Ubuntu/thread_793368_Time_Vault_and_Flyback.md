---
title: "Time Vault and Flyback"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-13
Hello

can i have some opinions about these two linux backup tools here.

After reading about both of these tools....it appears to me that they differ from many standard Linux backup tools in one very important way.

these tools take snapshots of whatever you tell them to...
(virtualbox has a snapshot feature)
(i think "system restore" was the winXP attempt at this snapshot idea)

---------------------------------------------------------------

to explain further....about Time Vault and FLyback.

an example would be to create a snapshot of your entire system...

this initial snapshot would take some time (10 mins)...however, 

Any subsequent snapshot that you take only records files that have changed in relation to the previuos snapshot...(thereby, meaning that a whole new system snapshot may only take a very short while...if very little had changed)

other backup systems i have seen...don't do snapshot comparisons...they simply repeat the long winded entire backup process of your system.....

such tools are "Quik-Start" and "Linbaku" and "sbackup".....to name but a few.....

Time Machine is what OSX uses....and these 2 tools above attempt to do a similar job.

I want a tool that can backup my entire system...and quikly...and repeatedly...

i wondered if my understanding is correct...and if indeed, both the tools above....will do the job for me.

thanks

Vince.

---

### Post by abhiroopb on 2008-05-16
Not sure about flyback or timevault, but sbackup does not do a repeated backup like you say.

You COULD configure it to do that. But for me I have set it to do incremental backups. It initially did a full backup but now it incrementally back's up either when I click on it or automatically during the day. The incremental back aps only take whats changed which is of course very useful.

---

