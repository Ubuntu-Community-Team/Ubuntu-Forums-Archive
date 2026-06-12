---
title: "How to import my &quot;Home&quot; folder from Feisty to Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by swarup on 2008-05-01
I have two hard drives-- one with my Feisty install on it, which I've been using for the past year, and one with the Hardy install on it which I've just installed today. What is the way to bring in my "Home" folder from Feisty to Hardy so that I will have all my data, my Evolution mail, my Firefox bookmarks etc. Do I just copy the entire Feisty "Home" folder and paste it into Hardy? Or is there another certain way it is supposed to be done?

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> I have two hard drives-- one with my Feisty install on it, which I've been using for the past year, and one with the Hardy install on it which I've just installed today. What is the way to bring in my "Home" folder from Feisty to Hardy so that I will have all my data, my Evolution mail, my Firefox bookmarks etc. Do I just copy the entire Feisty "Home" folder and paste it into Hardy? Or is there another certain way it is supposed to be done?

I think that should work, but a better way is to have the /home directory on (eg) disc 2 and the / directory & swap directory on (eg) disc 1.

Then, when you reinstall/upgrade only the directories/partitions on disc 1 need to be formatted/written over.

---

### Post by swarup on 2008-05-01
> **drsox1899 said:**
> I think that should work, but a better way is to have the /home directory on (eg) disc 2 and the / directory & swap directory on (eg) disc 1.

Then, when you reinstall/upgrade only the directories/partitions on disc 1 need to be formatted/written over.

Yes, that would be great. But actually I didn't give you enough info. These are not both internal drives. Mine is a laptop, and the Feisty drive used to be my internal drive. Now I've put another HD in and put Hardy on it. The Feisty I will hook up externally just to copy and paste the Home folder over from Feisty to Hardy. 

I just didn't know whether the format was completely parallel in that way, or whether one was supposed to use some sort of import wizard instead which would browse to the old home folder and extract what it needed from there.

---

### Post by Hospadar on 2008-05-01
what I would do, is go into your fiesty home folder (/media/wherever it got mounted/home/<your username>) and copy all the files there (including hidden files, if you do this graphically, Ctrl-H will show hidden files, and copy them to your own home directory in hardy, overwriting any files there already.  you should be able to do this while logged in as you, but I would restart right after, and try not to do anything else while you are copying them.

What most people do for this kind of thing, which you may have heard of, is they have two partitions on their drive, one for / and one for /home, that way, when I do a new installation, I can just leave the home partition untouched, and install to the / partition, and you don't have to bother with this copying stuff.

If you want to go that route, during the installation, do manual partitioning, create a swap partition of appropriate size (~ 25% -50% of the size of your memory), then create a smaller primary partition (mine is about 5gb) ext3, and mount it to "/" and then create another primary ext3 partition with the rest of the drive, and mount it to "/home"

Then, if you install a new version, you just go into the manual partitioner, set the mount points where you want them, and wa-la

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> Yes, that would be great. But actually I didn't give you enough info. These are not both internal drives. Mine is a laptop, and the Feisty drive used to be my internal drive. Now I've put another HD in and put Hardy on it. The Feisty I will hook up externally just to copy and paste the Home folder over from Feisty to Hardy. 

I just didn't know whether the format was completely parallel in that way, or whether one was supposed to use some sort of import wizard instead which would browse to the old home folder and extract what it needed from there.

If you can see both drives from your new Hardy install, then yes it's easy.
  
Just try to ensure that all your data is copied - including anything that is important that is "hidden".  

See other forum post.  You may have to reinstall a few apps that have been installed by default to your /home directory.  

Just ensure that any data that you want to preserve is collected before.  Reinstall may be needed as the dependencies of the app may be treated differently from Feisty to Hardy.

---

### Post by swarup on 2008-05-01
(this is a reply to Hospadar's post)

I see. That is great info. For now, I think I need to go ahead and copy the Home folder over from Feisty to Hardy. So I'll do it the way you said to. In the future though, I may try what you've said. 

Now, one important question: I had to install a driver for my Netgear dongle in Feisty in order to get my dongle to work. I Hardy, the default driver seemed to work for a few minutes, but then it cut off and stopped. I think I'm going to need to bring in the driver again as I did in Fiesty. It was a Win98 driver which Linux has an adapter for. If that stuff is in my Home folder, will it just start working? Or will I have to do the install again as I did previously in Feisty?

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> I see. That is great info. For now, I think I need to go ahead and copy the Home folder over from Feisty to Hardy. So I'll do it the way you said to. In the future though, I may try what you've said. 

Now, one important question: I had to install a driver for my Netgear dongle in Feisty in order to get my dongle to work. I Hardy, the default driver seemed to work for a few minutes, but then it cut off and stopped. I think I'm going to need to bring in the driver again as I did in Fiesty. It was a Win98 driver which Linux has an adapter for. If that stuff is in my Home folder, will it just start working? Or will I have to do the install again as I did previously in Feisty?

That's the kind of thing that is best reinstalled !

---

### Post by swarup on 2008-05-01
> **drsox1899 said:**
> If you can see both drives from your new Hardy install, then yes it's easy.
  
Just try to ensure that all your data is copied - including anything that is important that is "hidden".

Yes, I'll be sure. Thanks.

> **drsox1899 said:**
> See other forum post.  You may have to reinstall a few apps that have been installed by default to your /home directory.  

Just ensure that any data that you want to preserve is collected before.  Reinstall may be needed as the dependencies of the app may be treated differently from Feisty to Hardy.

What about the Evolution mail? I just copy and paste that folder? Or does one have to do an import via the Evolution import wizard? I'm guessing in ordinary circumstances such an import would in fact not be needed as it is the exact same application, perhaps just a later version. But in my case, one of the reasons I've switched hard drives is that I started having trouble closing Evo on the other HD in Feisty. It would take a minute to close every time, and the HD would start clicking and then it would close. I ultimately found that the trash in Evo was not emptying on closing as I had set it to do, and when I tried to manually empty the trash it again gave me an error--which I don't have in front of my right now cause its recorded on the other HD. But something about the map not matching up or something. Is there a way I could manually import my mail folders into Evo, so that it would screen all the mail data and make sure there is no bad data?

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> Yes, I'll be sure. Thanks.



What about the Evolution mail? I just copy and paste that folder? Or does one have to do an import via the Evolution import wizard? I'm guessing in ordinary circumstances such an import would in fact not be needed as it is the exact same application, perhaps just a later version. But in my case, one of the reasons I've switched hard drives is that I started having trouble closing Evo on the other HD in Feisty. It would take a minute to close every time, and the HD would start clicking and then it would close. I ultimately found that the trash in Evo was not emptying on closing as I had set it to do, and when I tried to manually empty the trash it again gave me an error--which I don't have in front of my right now cause its recorded on the other HD. But something about the map not matching up or something. Is there a way I could manually import my mail folders into Evo, so that it would screen all the mail data and make sure there is no bad data?

A sure fire way is to do a backup of your existing Evolution and then do a restore to your new install.  As long as you can find the backed-up file and "preserve" it (copy it onto a floppy/USB stick), then you're safe.

I don't know Feisty that well but Gutsy and Hardy versions of Evolution can deal with this OK.

As long as you're not overwriting the old disc then you can try other options as a last resort if the reinstall doesn't work.

---

### Post by swarup on 2008-05-01
> **drsox1899 said:**
> A sure fire way is to do a backup of your existing Evolution and then do a restore to your new install.

When you say "do a *restore* to my new install", does "restore" mean a straight copy-paste of the .evolution folder from the old Home folder to the new one? Or instead does it mean to do an import using the Hardy Evo's import wizard?

> **drsox1899 said:**
> As long as you're not overwriting the old disc then you can try other options as a last resort if the reinstall doesn't work.

Again, just want to make sure I understand the term "reinstall". Are we talking about a straight copy-paste here of the .evo folder, or about the use of an import wizard?

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> When you say "do a *restore* to my new install", does "restore" mean a straight copy-paste of the .evolution folder from the old Home folder to the new one? Or instead does it mean to do an import using the Hardy Evo's import wizard?



Again, just want to make sure I understand the term "reinstall". Are we talking about a straight copy-paste here of the .evo folder, or about the use of an import wizard?

OK.  If I fire up my copy of Evolution on Gusty, under File, there is Backup Settings and Restore Settings.  

Selecting Backup will convert all your Evo files into a tar.gz file.  This will usually be found in your /home/<yourname>/ directory.  

Do you see this on Feisty ?

I haven't had to do this, but I assume that Restore will do the inverse.

So do a Backup in Feisty and a Restore in Hardy and see what you get.  If It's more complicated then you need an Evo specialist to help.

---

### Post by swarup on 2008-05-01
(This post deleted because it was rendered unnecessary by the above post)

---

### Post by swarup on 2008-05-01
> **drsox1899 said:**
> OK.  If I fire up my copy of Evolution on Gusty, under File, there is Backup Settings and Restore Settings.  

Selecting Backup will convert all your Evo files into a tar.gz file.  This will usually be found in your /home/<yourname>/ directory.  

Do you see this on Feisty ?

I haven't had to do this, but I assume that Restore will do the inverse.

So do a Backup in Feisty and a Restore in Hardy and see what you get.  If It's more complicated then you need an Evo specialist to help.

Oops, we cross posted. But now I see exactly what you mean. I didn't know there was such a backup command in Evo. --Sure, I can do what you suggest. However, can I fire up the copy of evo located on my external HD (the Feisty one), from the Hardy HD (now my internal HD)? Otherwise I'll have to swap out the two HD's to boot back up into Feisty--which is a bit of a job on this old laptop where the HD is screwed in under the floppy with ten teeny tiny screws.

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> Ok--Now I see what "restore" means. When you open Evolution, it offers to restore evolution from a backup file. And that is what I want. But my backup is the .evolution folder on my external hard drive. That is, it is a hidden folder. And the browser window of the restore wizard is not showing the hidden folders in my home folder on the external drive. Is there a way to request the browser window to show hidden files?

Fire up Places on the top menu. Go to Computer and then check "Show Hidden Files" on the View menu.  Then you should be able to look at your other disc and it should show all the .Files (normally hidden).  To look at all directories select File System and that will give you all the directory details.

I guess your old files are in the /home/<username>/.evolution directory on your other disc.  To make it work properly you will need to boot from the Feisty install on the old disc and fire up the evo copy that was installed under Feisty.  Then do a Backup and copy that backup to another location.

Then boot up the Hardy install.  Fire up the Evo copy installed with Hardy and restore from the backup.

---

### Post by drsox1899 on 2008-05-01
> **swarup said:**
> Oops, we cross posted. But now I see exactly what you mean. I didn't know there was such a backup command in Evo. --Sure, I can do what you suggest. However, can I fire up the copy of evo located on my external HD (the Feisty one), from the Hardy HD (now my internal HD)? Otherwise I'll have to swap out the two HD's to boot back up into Feisty--which is a bit of a job on this old laptop where the HD is screwed in under the floppy with ten teeny tiny screws.

You will need to swap discs.  I hope you have a third medium to hand - floppy or USB for storing the backup ?

I know the problem - I have an old Toshiba laptop that has a broken disc caddy - so fiddly to change discs !

PS Have to go off-air now for 8 hours or so.  I'll check back later.

Luck

---

### Post by swarup on 2008-05-01
My above thanks is for this entire exchange. Many thanks--it was very enlightening. I think I have an approach now, on which to proceed. 

I'll try doing the export of the backup file now from my Feisty evo, and we'll see if it is willing to make it. Thanks again.

---

