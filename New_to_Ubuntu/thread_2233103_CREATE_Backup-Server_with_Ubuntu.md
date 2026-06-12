---
title: "CREATE Backup-Server with Ubuntu"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by darkfritz2 on 2014-07-06
Hello people,

I'd like to rent a dedicated server or a VDS for backup purposes.

Here's the idea:
I want to install on that server Ubuntu and transform it into a backup server for my personal computer (maybe later to save even the data for my sister).
The idea:
Get the dedicated Server
Install ubuntu, install backup software for server
Install some kind of client on my personal computer (Windows 8)
Every week my personal computer does an entire backup of my PC via internet on that dedicated server where everything is safe and sound.

I've read a few tutorials about BackupPC and Crashplan but i didn't understand if they do what i want to do.
[Lifehack]("http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu") <-this seems promissing but i dont know how and if that tutorial does my backup via internet.
[backupPC]("https://www.digitalocean.com/community/tutorials/how-to-use-backuppc-to-create-a-backup-server-on-an-ubuntu-12-04-vps") <-this seems more proffesional but i have no idea how i install the client on my PC with windows8 or is it just for linux?

Does someone have more tutorials about something like that? A little help?

best regards

---

### Post by TheFu on 2014-07-06
Individuals don't really do this because it is cost prohibitive when compared to the other options.  The cheaper way to address this is by working with a friend and you both agree to be the backup location for the other person - this will drop the $100+/month cost of a dedicated server in a rack somewhere - actually most server are more than that.

I don't know what a VDS is - but a VPS can be had for $5-$20/month.  Then you have the uplink speed issue for your backups.  For the amount of data that most people have, it requires a few weeks to get the first backup finished.  Run the numbers for your data.

So ... by the time we are all done architecting this solution, renting storage, renting cloud resources and getting it to work in a secure way, something like crashplan becomes much more attractive AND less expensive.  There are many other cloud storage options that work too - but very few are actually secure.

Plus cloud storage doesn't remove the need for a local backup. After all, waiting 2-20 weeks for data to be restored over the internet isn't what we all want.

So, if I were trying to do this, a few core requirements would be mandatory for me.
* Local encryption of the data, NOT remote.
* Transfer over private, secured, channels - HTTPS is NOT private enough for me.  ssh/openvpn are.
* Next Day FedEx recovery option.  I'd expect to pay for the 4x4TB HDDs and shipping, but I want the option to get my data back in less than 48 hrs - ALL OF IT.  The trickle download for a month is NOT an option.
* Versioned backups.  I'm addicted to 60 and 90 days of daily backups being stored efficiently (1.1 - 1.2x the original). I don't want to give that up.
* Bare metal restore capability - at least I need to know how to get back to an exact point in time in that 60-90 days.  Viruses go unnoticed for a few days, perhaps weeks and restoring to a point prior to that is mandatory.  File corruption is another reason. We don't always notice it in a few days.
* A mirror is NOT enough.

Does this list match yours?

Windows has me stumped. Sorry.  I'd look for something based on rsync and ssh.  backupPC or backula are enterprise solutions (i.e. hard) and probably assume a secure network, not the internet.

For Linux, there are many methods. duplicity is the shortest distance to the solution. There are win32 versions of duplicity-based tools - duplicati, dejaDup, etc...   I use rdiff-backup to a local backup server, then rsync over ssh to a remote location that I manage (relative's place).  The first backup was hand delivered and setup there to avoid the initial backup delays.

Perhaps the best solution is a hybrid.  Only the most critical data gets pushes to the internet, all other data stays local (at a friend's place, USB disk taken into work, swapped weekly, monthly, and locked in a desk).  Regardless, if it leaves my home, it is encrypted.

I'd love to see how other people do this.

BTW, I know Whitson (tell him I said hello), but that article is for local LAN, not internet, connections. There are huge security issues by just that change. Lifehacker doesn't provide the most secure solutions, but for LAN stuff, that doesn't matter usually.  For internet stuff - it is very dangerous to your privacy, files, LAN. Even when they attempt to address it, they gloss over those details way too much.  That isn't their concern.  BTW, steaming media over the internet is much harder than people understand.  Audio is relatively easy, because of the limited bandwidth needed, but video - not so much.  Don't underestimate how hard it is to securely stream video over the internet.

BTW - this server is for backups, not primary storage of the media, correct?  What happens when 1 HDD fails in the remote server? What happened to the data on it?  Yep - best to pay someone else.

Can't wait to see how others solve this.

---

### Post by sandyd on 2014-07-06
> **TheFu said:**
> Individuals don't really do this because it is cost prohibitive when compared to the other options.  The cheaper way to address this is by working with a friend and you both agree to be the backup location for the other person - this will drop the $100+/month cost of a dedicated server in a rack somewhere - actually most server are more than that.

I don't know what a VDS is - but a VPS can be had for $5-$20/month.  Then you have the uplink speed issue for your backups.  For the amount of data that most people have, it requires a few weeks to get the first backup finished.  Run the numbers for your data.

So ... by the time we are all done architecting this solution, renting storage, renting cloud resources and getting it to work in a secure way, something like crashplan becomes much more attractive AND less expensive.  There are many other cloud storage options that work too - but very few are actually secure.

Plus cloud storage doesn't remove the need for a local backup. After all, waiting 2-20 weeks for data to be restored over the internet isn't what we all want.

So, if I were trying to do this, a few core requirements would be mandatory for me.
* Local encryption of the data, NOT remote.
* Transfer over private, secured, channels - HTTPS is NOT private enough for me.  ssh/openvpn are.
* Next Day FedEx recovery option.  I'd expect to pay for the 4x4TB HDDs and shipping, but I want the option to get my data back in less than 48 hrs - ALL OF IT.  The trickle download for a month is NOT an option.
* Versioned backups.  I'm addicted to 60 and 90 days of daily backups being stored efficiently (1.1 - 1.2x the original). I don't want to give that up.
* Bare metal restore capability - at least I need to know how to get back to an exact point in time in that 60-90 days.  Viruses go unnoticed for a few days, perhaps weeks and restoring to a point prior to that is mandatory.  File corruption is another reason. We don't always notice it in a few days.
* A mirror is NOT enough.

Does this list match yours?

Windows has me stumped. Sorry.  I'd look for something based on rsync and ssh.  backupPC or backula are enterprise solutions (i.e. hard) and probably assume a secure network, not the internet.

For Linux, there are many methods. duplicity is the shortest distance to the solution. There are win32 versions of duplicity-based tools - duplicati, dejaDup, etc...   I use rdiff-backup to a local backup server, then rsync over ssh to a remote location that I manage (relative's place).  The first backup was hand delivered and setup there to avoid the initial backup delays.

Perhaps the best solution is a hybrid.  Only the most critical data gets pushes to the internet, all other data stays local (at a friend's place, USB disk taken into work, swapped weekly, monthly, and locked in a desk).  Regardless, if it leaves my home, it is encrypted.

I'd love to see how other people do this.

BTW, I know Whitson (tell him I said hello), but that article is for local LAN, not internet, connections. There are huge security issues by just that change. Lifehacker doesn't provide the most secure solutions, but for LAN stuff, that doesn't matter usually.  For internet stuff - it is very dangerous to your privacy, files, LAN. Even when they attempt to address it, they gloss over those details way too much.  That isn't their concern.  BTW, steaming media over the internet is much harder than people understand.  Audio is relatively easy, because of the limited bandwidth needed, but video - not so much.  Don't underestimate how hard it is to securely stream video over the internet.

BTW - this server is for backups, not primary storage of the media, correct?  What happens when 1 HDD fails in the remote server? What happened to the data on it?  Yep - best to pay someone else.

Can't wait to see how others solve this.
It depends on how fast your internet is, and how you implement it.

What I would recommend is using a decentralized storage/sync/backup system such as btsync or syncthing (if your paranoid about btsync not being OSS). Sync your data on multiple computers in the same house, and probably a storage VPS from backupsy or securedragon or whereever incase something happens to all your computers. Then, when your computer has issues, and you need to recover data, you can just add the key to btsync which will resynchronize the data by downloading from all the computers.

Note that while btsync's transfer is encrypted, the data in the storage folder is not. Things like Truecrypt (gone now, but as an example) wont work properly because instead of syncing the changed bits, btsync will attempt to sync the whole container. Instead, simply encrypt your home folder so that the folders that btsync syncs (and the btsync config) are unavailable and inaccessible until you login.

---

### Post by darkfritz2 on 2014-07-06
Thanks for your reply.

Here are some specs that maybe you should know:

I've found someone who doesnt limit in anyway the bandwidth or something like that and the price of those servers are pretty good. giving HDD in raid i have the security that if it should fail they swap it without me knowing.
[http://dedicatserver.ro]("http://dedicatserver.ro") is the site and it seems pretty cool.

anyhow. i was not thinking that far with encryption and stuff like that though they are important. i just thought of making a backup of my windows so if my PC is having somekind of problems i just put a new HDD and via internet i just download everything i need.
PLUS should i go somewhere (thats why i thought of ubuntu with GUI) and i need some data fast i can connect via remote control and get it fast.

are there any software that matches my needs? those enterprise software are way to complicated (except maybe there is a good tutorial about that).

---

### Post by sandyd on 2014-07-06
Try clonezilla.

---

### Post by darkfritz2 on 2014-07-06
what i've read now about syncthing should match my needs. i think something like that i was looking for.

Thanks! ^^

edit: found something interesting: [https://owncloud.org/]("https://owncloud.org/") does someone made experience with something like that?

---

