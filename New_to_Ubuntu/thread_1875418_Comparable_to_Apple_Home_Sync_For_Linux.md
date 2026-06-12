---
title: "Comparable to Apple Home Sync For Linux?"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by cbanakis on 2011-11-04
Does anyone know of a program for linux that is similar to apples home sync?

Something that can run on a server, with multiple users on a network, where all their settings and files are backed up at log out, and restored at log in?
And anyone can log into any computer on the network, and all their settings will be intact.

Trying to convince my boss to switch the office over to Ubuntu instead of apple.

All anyone needs here is internet and email, so Ubuntu would work great, but he wont consider it unless there is a way to home sync.

---

### Post by cbanakis on 2011-11-06
anything?

theres gotta be something out there?

---

### Post by Paqman on 2011-11-06
Can you explain this Apple Home Sync thing a bit more? Is it like a thin client? Or is it just the contents of the home folder that are stored on the server? Both would be very doable, and I'm sure (this being Linux) there's probably 50 other ways of doing something similar.

---

### Post by Exonimus on 2011-11-06
First of all -rather needless to say maybe- a warning. I, of course, do not know how your office looks like, but I would always hesitate to switch to some system I do not really know much about. Again, I of course do not know how good your ubuntu knowledge is, how big your office is, and if you have a dedicated server or not, although judging from your post, I presume you do. It's a great (server) system, but be warned. You need someone who knows what to do in case **** hits the fan :P

Now. If you want more people to reply, it might be handy to specify: what does your (potential?) setup look like. Are we talking about one dedicated server (if so, how powerful?) with the rest only clients? (how many?) are these 'thin clients'? (e.g. no local data, running sessions completely from server) or not?

The solution varies depending on your answer. If all you're really asking for is a way for users basically log in to any pc in the office with the same account, with all their stuff intact (you weren't that specific) then yes, of course this is possible. I'm not even an advanced user by any stretch of the imagination, but still. One such solution is the Linux Terminal Server Projects (LTSP) where this situation applies. Again, I'm no expert, but this hopefully at least offers you some further path to search. I have no experience with LTSP, so if anyone can give some more detailed feedback, please do.

If you're asking for sync at login and logout on ONE pc only (that is, everyone has their 'own' pc, and only works at that fat-client workstation) I'm sure there are other solutions as well. I recently came across a program called 'unison' which backups files and folders, but I'm not sure this really is what you're looking for. In any case, I'm unsure whether such apps are to be used in businesses as opposed to home users.

So, in conclusion: specify, and someone at the forums can probably help you in more detail :)

edit: oops, you actually did mention 'anyone can login to any pc on the network'. Apologies.
edit: if you search google for 'ubuntu terminal server' or 'ubuntu thin client server'you might encounter some interesting links, such as this one
[http://knightwise.com/blog/technology/744-building-my-own-qcitrix-terminal-serverq-with-ubuntu-1004](http://knightwise.com/blog/technology/744-building-my-own-qcitrix-terminal-serverq-with-ubuntu-1004).

---

### Post by cbanakis on 2011-11-06
home sync creates a backup of your system on a network attached server.

it then compares the system your on to the backup at login restoring data as needed.

then at logout, it updates the backup with changes if any to your system.

This acts as a failsafe in the event of a hardware failure, and also allows users to bounce around between systems.  (roaming users)

other than that, our demands are quite simple.
for the most part, all we need is email and internet.

I want to switch us over to ubuntu, because I have grown tired of all the required maintenance to keep our Macs and Windows systems going.

---

### Post by Exonimus on 2011-11-07
You might want to check out rsync. 
([https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync))

It's a command line tool, but with rather straightforward documentation. Since it's command line, it is very easy to make a simple script, and have it run on startup of clients. The startup script would then synchronize files from the 'server' to the 'client'. Executing a script on shutdown basically works the same way, but the other way around, syncing the most updated files from the client to the server.

edit:
[http://kevin.vanzonneveld.net/techblog/article/synchronize_files_with_rsync/](http://kevin.vanzonneveld.net/techblog/article/synchronize_files_with_rsync/) for a tutorial

---

### Post by cbanakis on 2011-11-07
Thank you very much.

Looks like it will take some serious though, but at least I have a place to start now.
(knowing the name of an app)

"And Knowing, Is Half The Battle"

"YO JOE!!!"

---

### Post by mastablasta on 2011-11-07
why not use Ubuntu cloud (can even fit in the pocket: [http://cloud.ubuntu.com/2011/10/ubuntu-cloud-live/](http://cloud.ubuntu.com/2011/10/ubuntu-cloud-live/)) ? it seems to me you only use server to backup your work... imean sicne they have some syncronisation....
 
there are also plenty of backup programmes (some even with browser GUI ) that will do this kind of regular backups.

---

