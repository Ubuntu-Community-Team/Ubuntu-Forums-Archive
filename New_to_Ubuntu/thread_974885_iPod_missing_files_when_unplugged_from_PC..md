---
title: "iPod missing files when unplugged from PC."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by RAMDrive on 2008-11-07
I'm running Ubuntu Eee 8.04 on my 901 without problems, and have a 30gig iPod photo.  I've been using anapod on my XP box but I don't have it with me; it's 1000 miles and one week away.  I plugged the ipod into my eee 901 to charge, then Rhythmbox 0.11.5 opened, I was pleased to see my library; I can play from the ipod and charge it without problems.  However when I disconnect the ipod it only shows one Daft Punk song.  My ipod library is 2249 songs total.

How can I can get the ipod to show the complete library when unplugged?  Search and Google have failed me.

thanks

---

### Post by RAMDrive on 2008-11-09
anyone?

](*,)

---

### Post by jia103 on 2009-02-13
I have the same problem with my wife's 4GB iPod, and no solution.

This is my first experience with an iPod; I see songs on the iPod through Rhythmbox and can play them while connected. However, the songs I copied (via Nautilus) seemed to disappear upon disconnection; the playlists were not visible on the iPod.

When I reconnected, the playlists are still there; however, all files I put in them are not there in Rhythmbox. Logs (/var/log/{messages,syslog} don't indicate any problems.

Finally, df output suggests that the files were put on the iPod disk (/dev/sd??) since the available space is now lower than it was before I started. (I tried to copy a significant number of .mp3 files.)

Any hints?

FYI: Ubuntu 8.04, kernel 2.6.24-23-generic; Rhythmbox 0.11.5-0ubuntu8. Don't know much about the iPod except that it's 4GB. The model number on the back is A1137.

Thanks.

---

### Post by adult swim on 2009-02-13
you guys might want to check out the second part of this blog.  
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)
the part that comes after "THIS IS ONLY NEEDED FOR iPOD NANO 3rd GENERATION or iPOD CLASSIC MODELS (FALL 2007 MODELS)"

---

### Post by Kain000 on 2009-02-13
Rythmbox by default starts when your ipod is mounted, unfourtinally rythmbox, as useful of an app as it is, cannot sync with your ipod.


You may want to try a project called songbird, i've had both sucess and utter failure with that app, but that was before the officle 1.0 launch so perhaps the bugs that plauged me are now fixed.

For my ipod (80GB silver classic)  I always use amarok  music player, it can sync do podcasts and handle your library very efficently.  

More over amarok has been the most sucessfull in transfering cover art without itunes.

read this thread:
[http://ubuntuforums.org/showthread.php?t=1022353]("http://ubuntuforums.org/showthread.php?t=1022353")

espacially the last page or so if you need/ want to put video files on you ipod without using Itunes.

hope this helps.

---

### Post by Kain000 on 2009-02-13
Ohh by the way did you remember to un-mount your ipod before pulling the plug?  if not it doesnt flush the transfer logs and can result in what I think is going on with you ipod.

You need to right click the ipod icon on your desktop and select eject or unmount to properly flush the device.

Amarok does this aswell

---

### Post by jia103 on 2009-02-14
ama-roks! Ok, I know...lame.

Anyway, thanks for the tip about amarok; it seems to work. I installed as follows:

   # apt-get install amarok

Then followed the steps here:

   [http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

In Step 2, the device was not already listed; I had to add it before it showed up in the dialog.

Transferring files seems to now work; the new files show up under Artist. It seems playlists are having some trouble. I don't know too much yet, but here's what happened: First, I added some files via amarok to an existing, empty playlist. The playlist didn't show up on the iPod before, and it still didn't after disconnecting. (1)

Next, I moved a file from another playlist to my desired playlist, disconnected, and still nothing. (2)

Then, I created a new playlist in amarok and renamed it. I transferred a file into it, then disconnected. (3)

Now, the (2) playlist appears with the moved file, but the (3) playlist still doesn't.

I'm not going to bother with this yet, but just FYI to anyone searching the forums. Maybe someone knows the answer.

Kain000, I did make sure to un-mount by ejecting from the Desktop or from inside Rhythmbox.

Thanks!

---

### Post by Kain000 on 2009-02-14
> **jia103 said:**
> ama-roks! Ok, I know...lame.

Anyway, thanks for the tip about amarok; it seems to work. I installed as follows:

   # apt-get install amarok

Then followed the steps here:

   [http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

In Step 2, the device was not already listed; I had to add it before it showed up in the dialog.

Transferring files seems to now work; the new files show up under Artist. It seems playlists are having some trouble. I don't know too much yet, but here's what happened: First, I added some files via amarok to an existing, empty playlist. The playlist didn't show up on the iPod before, and it still didn't after disconnecting. (1)

Next, I moved a file from another playlist to my desired playlist, disconnected, and still nothing. (2)

Then, I created a new playlist in amarok and renamed it. I transferred a file into it, then disconnected. (3)

Now, the (2) playlist appears with the moved file, but the (3) playlist still doesn't.

I'm not going to bother with this yet, but just FYI to anyone searching the forums. Maybe someone knows the answer.

Kain000, I did make sure to un-mount by ejecting from the Desktop or from inside Rhythmbox.

Thanks!


no problem glad to help, 

I'm not sure about the playlists I just sort of lump my audio together in the library and pick and choose.  

I know some things are still buggy but for the most part amarok works for me.     

It's been updated and now has great podcast support and puts them into the right places on the ipod by date and wether or not you've listened to them.

If you like audio books, you may need to monkey arround with file extentions to get them to inport to your device correctly

you can check out some more about mpeg-4 container here:
[http://en.wikipedia.org/wiki/MPEG-4_Part_14]("http://en.wikipedia.org/wiki/MPEG-4_Part_14")

basicly if you have trouble with things like audio books try changing their file exetntions, it wont change their format but amarok will pick up on the extention change and perhaps treat them differently.

ex:  audio book  .m4a  try .m4b 



And you may want to give yourself a fresh start now that you've found one program to wright to your ipod and just reset your ipod to its factory settings.

to do this open the ipod from your desktop or where ever to brouse  the files and delete  everything, eject the volume and when it come back it should go threw the first menus when you first bought it.

Double check that info before doing tho it was a while ago and I THINK that deleteing everything was what I did but I could be wrong and just a certian file.

anyone on the forum know for sure?

---

### Post by jia103 on 2009-02-17
> **Kain000 said:**
> no problem glad to help, 

And you may want to give yourself a fresh start now that you've found one program to wright to your ipod and just reset your ipod to its factory settings.

to do this open the ipod from your desktop or where ever to brouse  the files and delete  everything, eject the volume and when it come back it should go threw the first menus when you first bought it.

Double check that info before doing tho it was a while ago and I THINK that deleteing everything was what I did but I could be wrong and just a certian file.

Actually, I was thinking of resetting everything anyway. The wife has a bunch of stuff on the iPod that has accumulated over time, and I don't want to lose all that.

Since we now have my laptop, I was hoping I could simply drag-and-drop all the audio tracks to a folder on my laptop; I assume transferring mp3's from the iPod is as simple as that via amarok. Am I right? (I haven't tried yet.)

Is there anything else I would want to transfer over?

I already used dd to make a backup of the iPod; I don't know how similar it is to a USB drive or SD card, so I don't know if I'd be able to put the dd image back onto the iPod in the future.

I was also considering switching it to Rockbox in the future; I don't know much about it, but it seems like something fun to try if she won't mind. I have no idea yet what will be involved in migrating to that; I'll have to look into it some time.

Thanks again for the help!

---

### Post by jia103 on 2009-02-21
Well, I finally did it. I installed Rockbox very easily and painlessly when I realized it has a dual-boot capability; installing Rockbox does not mean giving up the stock firmware on my wife's 1st generation iPod. Once installed, it was able to quickly pick up the entire music collection from the old iPod_Control/Music/F?? directories and place them in its own database.

Then I went a step further. I can't remember where I saw it, but a Web page described how I can transfer the music from the iPod onto my laptop. I had previously tried simply copying from inside Rhythmbox or inside Amarok onto my GNOME desktop. This didn't work as I wanted since it kept the iTunes-mangled "short" name of the mp3 file.

I wish I hadn't closed my browser so I could reference the URL, but this page described how I could retain more information in the mp3 file names when transferred to the PC. In Amarok, on the Devices tab, I selected all the albums, then dragged-and-dropped in the right-hand playlist pane. I did not select anything under Playlist on the Device; I'm assuming these are simply "links" to actual files and contain no real mp3's.

Once I had the entire iPod collection in the right-hand pane, I selected the Collection tab. Then, I selected all tracks in the right-hand playlist pane, and dragged-and-dropped onto the left-hand Collection pane. Upon drop, a dialog box popped up prompting for options. Once I made my selections, the entire iPod's contents were being transferred to my laptop.

I kept going by removing the iPod_Control/Music/* and replacing with the mp3's transferred from Amarok. Now I should be able to use Rockbox with the new files and still keep meaningful filenames on the FAT file system.

---

