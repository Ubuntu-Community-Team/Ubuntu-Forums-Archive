---
title: "Dropbox Script Help"
date: 2011-03-15
forum: Programming Talk
---

### Post by rbishop on 2011-03-15
Hello all.  If this is in the wrong spot I apologise, I wasn't sure where to put this cause it can fall into so many different categories.  

I have finally decided to take that final jump into the Cloud.  I am going to start backing up some of my docs etc into the cloud.  I have currently decided to start using Dropbox.  It looks to be an easy enough service to use plus it has installs for Windows(work PC) and Linux(Ubuntu laptop/home PC's).  First question...

How many of you have tried using Dropbox or any other cloud storage? 
Do you like it?
What problems do you have with it, if any?

I am one of those guys that doesn't backup as often as he should, so I am working on a basic script to back up certain files/folders to my Dropbox folder.  I will add this to Cron to make sure that it runs about every 30-60 minutes to make sure that it is backed up.  Next set of questions....

Do you have a script to back up to your cloud?
How often does it run?
What is your basic script layout?

I have just started a basic script that backs up my Bookmarks and some background pictures, just for testing purposes.  I am also thinking that I would like to have some sort of a check and make sure that what is in my "Cloud Folder" is the latest and only backup those files that have changed.  Here it is...any ideas on how to make it better would be greatly appreciated.

```

D=$(date '+%Y-%m-%d')
HOME=/home/user/

echo "$TD"

cp $HOME/.mozilla/firefox/numetpfc.default/bookmarkbackups/bookmarks-$TD.json $HOME/Dropbox/

cp $HOME/Pictures/backgrounds/* $HOME/Dropbox/Pictures/backgrounds


```

Like I said, it is currently a basic script, I haven't even started commenting the script or anything fancy/important like that.   I really appreciate any help or advice you guys can give.

---

### Post by r-senior on 2011-03-16
Yes, I use Dropbox. Have done so for a while now and never had a single problem with it. Very reliable and I've come to depend on it. The Nautilus extension works very nicely.

I use it more for having documents available on my laptop and Mac when I'm working away and perhaps disconnected for periods. I also use it to provide public links to things that are too large to email to people. I suppose there are some things in there that I would consider backups.

I don't have a specific backup script. I just have folders in my Dropbox where I keep things that I want backed up or shared. If I was making backups, I'd probably compress the archive to make more use of the free 2GB.

I originally started using it because I lacked faith in Ubuntu One (we are talking Karmic/Lucid days here - I think I just uninstalled it as soon as I installed Maverick). However, I'm re-testing Ubuntu One file sync again with Natty and it seems to have improved greatly.

---

