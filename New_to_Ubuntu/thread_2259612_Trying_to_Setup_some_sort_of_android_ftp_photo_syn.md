---
title: "Trying to Setup some sort of android ftp photo sync"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by dc320 on 2015-01-05
Hello all,

I have Lubuntu installed on an old pc running vsftpd ftp server. I would like to set up something that would sync my photos from my android phone (& an iphone) to vsftpd. I have vsftpd setup in passive mode and with ftps , which connects fine, but I need to copy the files manually. I have Andftp (other apps only seem to want to work in active mode) installed on the phone which has a scheduled sync setting, but that doesn't seem to work...

Thanks for any help or suggestions..

---

### Post by mooreted on 2015-01-05
I'm sure someone will come along with an idea. I personally just use my Google account which automatically syncs my photos to Google+. Then I can access them from all my phones, tablet and computer anywhere I am.

There are lots of apps for syncing to the cloud which might be much easier than trying to do it over FTP.

Another possible solution might be Bittorrent sync. Though it seems like it's meant to sync from computer to phone rather than phone to computer.

Hopefully someone who knows more than I do will come along with an idea for your specific requirements. 

Good luck.

---

### Post by mastablasta on 2015-01-06
setup owncloud on your server, install client on android and you are good to go.
other options are various syncs like aforementioned bittorrentsync.

owncloud is still missing some thing i would like it to have, but it does what you want. so you should give it a try. you can then view the photos in gallery. you transfer files via client but access is via browser.

there are also various other syncs like rsync, rdiff, various backup solution that actually include syncs etc. but IMO since you already have a server setup and you are interested in photos why not just go with something that is already made specifically for that - owncloud. you can view photos, share them, create & view documents etc. there are also some plugins available.

---

### Post by dc320 on 2015-01-06
Thank you, I'll take a look at that.

---

### Post by mastablasta on 2015-01-07
there is also Pulse I think this is the website (I have it blocked at work :-) ): *[https://ind.ie/](https://ind.ie/)**pulse**/*
and Syncthing (on which I think Pulse is based on?!)[URL="https://www.google.com/search?q=pulse+sync&sourceid=ie7&rls=com.microsoft:sl:IE-Address&ie=&oe=&gws_rd=ssl#"]
[/URL]Anyway you need something that will sync automaticly - fast, easy, reliable (e.g if connection drops or something)  and secure. I would still go with Owncloud for your case.

---

### Post by sandyd on 2015-01-07
> **mastablasta said:**
> there is also Pulse I think this is the website (I have it blocked at work :-) ): *[https://ind.ie/](https://ind.ie/)**pulse**/*
and Syncthing (on which I think Pulse is based on?!)[URL="https://www.google.com/search?q=pulse+sync&sourceid=ie7&rls=com.microsoft:sl:IE-Address&ie=&oe=&gws_rd=ssl#"]
[/URL]Anyway you need something that will sync automaticly - fast, easy, reliable (e.g if connection drops or something)  and secure. I would still go with Owncloud for your case.

Pulse is a rebranded version of syncthing.

The developer of syncthing gave ind.ie permision to do a rebranded version.

Side note: Syncthing has a crashing thing on some Android devices, see if yours has that issue.
Doing a lot of read/write cycles on a microSD card also reduces the lifespan of the card

---

### Post by dc320 on 2015-01-09
Thank you everyone

---

