---
title: "Need to Restore iPod-- no Windows Partition"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by turtlesarefunny on 2008-04-21
When I first mounted my iPod with Ubuntu, I thought everything was working well. However, as soon as it was disconnected, my iPod would display "Use iTunes to restore".

I've been looking for solutions for a while now, and I don't have a Windows computer available to restore it since when I first installed Ubuntu, I ruined the Windows partition, nor does iTunes run on Wine (it doesn't for me). Is there any way to restore it, short of manually reflashing it? (I saw it online, but it looks way too complex for me to grok)

---

### Post by crs0328 on 2008-04-22
This looks to be a pretty tough situation.  On the Apple support site, it looks like you need iTunes to restore your iPod.  I might be wrong, but it seems like iTunes used to work in Wine, but it hasn't for awhile.

For the offical Apple support answer, look here: [http://support.apple.com/kb/TS1441](http://support.apple.com/kb/TS1441)

Surely you have a friend/family/teacher/co-worker that has a windows machine...right?  If you can't find anyone, my only suggestion would be to go to an Apple store if you have one near you or call Apple support.  You might also be able to take it to some other hardware support locations.

---

### Post by amazingtaters on 2008-04-22
I believe that you can restore the ipod with GTKpod. Get it from the repos today.

---

### Post by abhiroopb on 2008-04-22
This has worked for me, but I wouldn't necessarily recommend it (as it may damage your iPOD). But again it worked for me.

Connect your iPod. Navigate to the iPod directory.

You should see a bunch of folders. 

If you have NO music saved on the iPod: delete the iPod_Control Folder
If you have Music saved on the iPod: navigate into the iPod_Control Folder, and delete the iTunes folder.

Essentially what this does is delete the database file. Then if you use amarok or GTKPod, you should get the initialise option which rebuilds it. This has ALWAYS worked for me. So give it a go if you like.

---

### Post by potion on 2009-06-19
> **abhiroopb said:**
> This has worked for me, but I wouldn't necessarily recommend it (as it may damage your iPOD). But again it worked for me.

Connect your iPod. Navigate to the iPod directory.

You should see a bunch of folders. 

If you have NO music saved on the iPod: delete the iPod_Control Folder
If you have Music saved on the iPod: navigate into the iPod_Control Folder, and delete the iTunes folder.

Essentially what this does is delete the database file. Then if you use amarok or GTKPod, you should get the initialise option which rebuilds it. This has ALWAYS worked for me. So give it a go if you like.

Just as a warning to others, this didn't work for me. Deleting those directories deletes files that Amarok and GTKPod are not able to recreate.

---

### Post by mike555 on 2009-06-19
You could install "RockBox" ...
[http://www.applesource.com.au/ipod/soa/Video-Free-your-iPod-to-play-OGG-and-FLAC/0,2000070791,339287528,00.htm](http://www.applesource.com.au/ipod/soa/Video-Free-your-iPod-to-play-OGG-and-FLAC/0,2000070791,339287528,00.htm)

---

### Post by abhiroopb on 2009-06-19
> **potion said:**
> Just as a warning to others, this didn't work for me. Deleting those directories deletes files that Amarok and GTKPod are not able to recreate.

did you not get an option to "initialise" in amarok? I usually get this. Can you mount the iPod in Amarok?

---

### Post by potion on 2009-06-19
mike555, great minds think alike... Soon after I posted, I decided to give Rockbox a try, since I don't have easy access to a Windows/iTunes setup for a restore. Still learning the ropes with Rockbox, but I love it already. Thanks for the tip!

abhiroopb, yeah, both Amarok and GTKPod saw that something was missing and offered to initialize. Or as GTKPod put it, to create iPod directories. But there was some stuff missing. Both of them recreated the iPod_Control folder and its subdirectories, but in the iTunes subdirectory, there was only one file, the database file. Originally, there was other stuff in there... I gather it's stuff that links a particular iPod to a particular installation of iTunes?

Without that stuff, I could load the iPod in either program, and it seemed like I could add files, but they wouldn't actually get transferred, just added to the database. When I looked in the Music subdirectory or checked via the iPod itself, the files hadn't made it over.

Anyway, I don't know what possessed me to delete the iPod_Control directory without making a backup first, especially since you were very clear that there might be a risk involved. But it all worked out for the best, since I think I'll end up preferring Rockbox.

I wonder, would it work to just delete the one database file, leaving the rest of the iPod_Control structure intact? Seems like Amarok and GTKPod have no problem replacing the database file.

By the way, this is all on a 30GB iPod Video.

---

### Post by abhiroopb on 2009-06-19
Ok I think you missed something out. Something I forgot to mention, basically you have to set your iPod model in Amarok.

I've written a fairly thorough guide on my blog...

[http://ubuntuextreme.blogspot.com/2008/12/how-to-ipod-classic-6g-with-amarok-14_18.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-ipod-classic-6g-with-amarok-14_18.html)

---

### Post by potion on 2009-06-19
Thanks, abhiroopb, I see now what happened. I was mostly focused on GTKPod, since that's what I've always used to manage my iPod. In GTKPod, when I plugged in the iPod after deleting the iPod_Control directory, it would ask me if I wanted to create the iPod directories, and I would say yes, but it wouldn't really work. I could see that the iPod_Control directory and its subdirectories had been created, but the only file in the iTunes subdirectory was iTunesDB. And the next time I started GTKPod, I would get this error...

Could not open "(null)" for reading extended info.
Extended info will not be used.

...and it would behave as I described earlier. I would try to add some files, and it would add them to the database, but no actual mp3s would get transferred to the iPod.

Anyway, that's all in GTKPod. When I then tried the same thing in Amarok, it asked me if I wanted to initialize, and I said yes, and then I did set the model correctly. The problem was, I had never used Amarok for iPod management, and I was half expecting the same problem I was having in GTKPod. So when I saw that the Transfer button was grayed out, I thought something wasn't working. I didn't realize you had to highlight certain files in the collection, right click, and transfer them that way. I should have been clearer about the exact problem I was having in Amarok, but in my mind I was running into the same kind of trouble in both programs.

Anyway, I tried it all again, following your excellent tutorial, and it worked great. One or two minor issues: When I tried transferring some music to the re-initialized iPod in Amarok, it got saved in a somewhat unusual way. It created a bunch of those numbered directories (f00, etc.), but they weren't consecutive, and it put only one or two files in each. If I remember correctly, GTKPod always started with f00, filled it up, then created f01, filled it up, etc.

Another minor issue: When I tried GTKPod after getting the iPod to work in Amarok, I got this error:

Error reading iPod photo database (Photos directory not found: '/media/IPOD/iPod_Control/Photos' (or similar).).

I tried just creating the Photos directory that it expected to find, but the same error keeps coming up anyway. Also, I added some files in GTKPod, and then I tried "Check iPod files," and the ones added in GTKPod were fine, but it said the ones added in Amarok were dangling and offered to delete them. When I said OK, it deleted all the files that were scattered about in non-consecutive directories, but kept the one file from the same album that Amarok had put in f00.

Anyway, I'm sure this is way more detail than necessary... The main thing is that your method of re-initializing the iPod in Amarok works great, meaning that there's no need for Windows or iTunes. :) I'm still not sure why GTKPod didn't re-initialize successfully, but it works with an iPod re-initialized in Amarok.

Now the only question for me is whether to use the Apple firmware or Rockbox. But it's great to have both as options...

Thanks for all your help and for that excellent guide! Lemme know if any of the above doesn't make sense...

---

### Post by abhiroopb on 2009-06-19
> **potion said:**
> 
Anyway, I tried it all again, following your excellent tutorial, and it worked great. One or two minor issues: When I tried transferring some music to the re-initialized iPod in Amarok, it got saved in a somewhat unusual way. It created a bunch of those numbered directories (f00, etc.), but they weren't consecutive, and it put only one or two files in each. If I remember correctly, GTKPod always started with f00, filled it up, then created f01, filled it up, etc.

Another minor issue: When I tried GTKPod after getting the iPod to work in Amarok, I got this error:

Error reading iPod photo database (Photos directory not found: '/media/IPOD/iPod_Control/Photos' (or similar).).

I tried just creating the Photos directory that it expected to find, but the same error keeps coming up anyway. Also, I added some files in GTKPod, and then I tried "Check iPod files," and the ones added in GTKPod were fine, but it said the ones added in Amarok were dangling and offered to delete them. When I said OK, it deleted all the files that were scattered about in non-consecutive directories, but kept the one file from the same album that Amarok had put in f00.



Glad to be of help, and glad you found the guide useful. Its a bit outdated (i.e Hardy), but since its Amarok it works fine.

Unfortunately, I have no experience with photos (as I don't use it for photos).

Does the folder structure really matter? I mean since you will be browsing the music through the iPod's interface anyway...? I'm sorry but I don't really understand the problem here. I guess it does mean that you will have to use Amarok as your main music manager (esp to transfer music to your iPod).

I don't really use GTKpod, so I'm unsure what the problem is. I have been completely successful using Amarok, so unfortunately my knowledge is limited to that program. 

Again glad to be of help.

Good luck!

---

### Post by aysiu on 2009-06-19
You can try using Songbird with the iPod Device Support extension:
[http://addons.songbirdnest.com/addon/12](http://addons.songbirdnest.com/addon/12)

---

### Post by potion on 2009-06-20
> **abhiroopb said:**
> Glad to be of help, and glad you found the guide useful. Its a bit outdated (i.e Hardy), but since its Amarok it works fine.

Unfortunately, I have no experience with photos (as I don't use it for photos).

Does the folder structure really matter? I mean since you will be browsing the music through the iPod's interface anyway...? I'm sorry but I don't really understand the problem here. I guess it does mean that you will have to use Amarok as your main music manager (esp to transfer music to your iPod).

I don't really use GTKpod, so I'm unsure what the problem is. I have been completely successful using Amarok, so unfortunately my knowledge is limited to that program. 

Again glad to be of help.

Good luck!

Sorry, I was probably a bit unclear... It's not that I want to use the iPod for photos... It's just an error screen that comes up in GTKPod when loading the "Amarok-initialized" iPod. I just wanted to provide a full report for anyone who might be in this situation down the road.

But I don't have any problems at all at this point... I'm actually quite impressed with Rockbox, and I think I'm gonna use that instead. Still, good to know that it's possible to go back to the default system without Windows and iTunes.

Thanks again, abhiroopb, and to you too, aysiu.

---

### Post by powel212 on 2009-06-20
For my ipod I use Sun Virtualbox to run a guest xp in which i have itunes installed. This way I can use the ipod's prefered application for syncing and I still don't have to reboot into windows.

Here is what it looks like.

[http://www.flickr.com/photos/sunrisefoto/3567107074/](http://www.flickr.com/photos/sunrisefoto/3567107074/)

Powel

---

### Post by jdforsythe on 2009-09-11
If you need to actually "restore" your iPod, i.e. take it completely back to factory settings, like you just took it out of the box (and thus all your data will be deleted), it is very simple under Ubuntu to do so.

[http://ubuntuforums.org/showthread.php?t=1263715](http://ubuntuforums.org/showthread.php?t=1263715)

---

### Post by ptn107 on 2009-09-11
iTunes - iTunes Store = Songbird

[http://getsongbird.org/](http://getsongbird.org/)

---

### Post by peterson2k4 on 2010-03-31
> **abhiroopb said:**
> This has worked for me, but I wouldn't necessarily recommend it (as it may damage your iPOD). But again it worked for me.

Connect your iPod. Navigate to the iPod directory.

You should see a bunch of folders. 

If you have NO music saved on the iPod: delete the iPod_Control Folder
If you have Music saved on the iPod: navigate into the iPod_Control Folder, and delete the iTunes folder.

Essentially what this does is delete the database file. Then if you use amarok or GTKPod, you should get the initialise option which rebuilds it. This has ALWAYS worked for me. So give it a go if you like.


Let it be known that if your ipod says it is full this works.  I owe you a beer my friend.

---

### Post by Chronon on 2010-03-31
There are instructions on how to manually restore an iPod in Rockbox's wiki.

[http://www.rockbox.org/wiki/IpodManualRestore](http://www.rockbox.org/wiki/IpodManualRestore)

---

