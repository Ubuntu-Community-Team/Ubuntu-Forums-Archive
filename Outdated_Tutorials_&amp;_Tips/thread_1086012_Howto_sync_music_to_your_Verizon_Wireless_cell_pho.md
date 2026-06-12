---
title: "Howto: sync music to your Verizon Wireless cell phone using Amarok!"
date: 2009-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by greyfox1 on 2009-03-03
**Note: this guide covers only Amarok 1.4.**

I have found that there is a dearth of information on ways to get music onto cell phones under Linux, so I'm hoping this tutorial will help many of you out there.  I have tested this method and verified that it works with my LG Dare from Verizon Wireless as well as my girlfriend's LG Chocolate II (also from VZW).  This method will probably work with Verizon's other BREW handsets (just about everything they sell that isn't a smartphone) because the music player software is very similar across the board but again, I've only tested using the two phones mentioned above.  VZW phones are the focus of this tutorial.

As to be expected, VZW provide no support for anything other than Windows and leave users of other OSes in the cold (and even their Windows solution is god-awful).  My phone never even recognized MP3 files that I manually copied over to the proper folder on the memory card either.  Even if that did work, who wants to manually copy over songs one by one?  I created a playlist and wanted to send the playlist to the phone without a lot of copying and pasting.

This method may work with other phones as well-- so if you have luck with your phone, please post your results and comments in this thread.

For the purpose of this tutorial, we will assume that you already have Amarok and have scanned your collection into the library.  We will be using Amarok 1.4.10, the last 1.x release, since as of this writing Amarok 2 does not offer mobile device support.  I have verified everything listed here under Ubuntu Intrepid, but other variants should work as well.

What you will need:
-External Memory Card (sorry, no way to do this with the phone's internal memory AFAIK)
-Card Reader
-AmaroK 1.4.10 (currently available in the repositories)

What you will [COLOR="Red"]NOT[/COLOR] need:
-USB Cable/driver
-Verizon's Rhapsody crapware
-DRM-protected music.  Sorry, but DRM-protected files are outside the scope of this tutorial.


Ok, down to business!



[COLOR="Red"]**Part A**[/COLOR]: Make sure your memory card is set up properly

1. Formatting
The phone expects a specific set of folders on the memory card in order to handle media properly (my_music, my_pix, my_flix, etc).  If you have just bought a memory card, you may need to format it in order to ensure that these folders exist.  The easiest way to do this is to insert the card into your phone and then just turn the phone off and back on again.  The phone will probably create the folders for you at this point.

2. Mount the card
Insert your memory card into your card reader and mount it, then check the mount point if you don't know it already by navigating to it in Nautilus and checking the address shown (usually something similar to /media/disk/ ).  Open the card and make sure the folders mentioned above exist.  If not, create them manually.

[COLOR="Red"]**Part B**[/COLOR]: Configure your memory card as a media device in Amarok

1. Choose Settings - Configure Amarok - Media Devices

2. Choose Add Device...
    You will be presented with 3 options:
    -"Select the plugin to use with this device:" -> Choose Generic Audio Player
    -"Enter a name for this device (required):" -> Name the device whatever you like
    -"Enter the mount point of the device, if applicable": -> Enter the mount point from Part A, step 2
    Click OK

3. Click the Devices tab, then click the gears icon (to the right of the Transfer button) to configure additional settings for the device:
    -Ignore pre&post-disconnect commands, transcoding options
    -Leave all checkboxes at defaults (all unchecked)
    -Song location: This part is important.  You must tell Amarok to place the files in the my_music folder in the phone.  Configure the filenames however you please but make sure that the files will NOT be nested in any folders underneath my_music.  For example if you leave it at the defaults, Amarok will create a hierarchy of my_music/artistname/albumname/filename.mp3.  If you sync using this hierarchy, the phone won't see your music when you are finished. 

The path asked for here is relative to the root directory of the memory card (e.g. /media/disk/ in this example) so you don't need to specify the path to the card.  The format I use is simply: my_music/%artist-%title.%filetype.
    Click OK

[COLOR="Red"]**Part C**[/COLOR]: Sync your tunes

1. Under the Collection or Playlists tab, choose the songs or playlists you want to sync, right-click and choose transfer to device or sync to device.

2. In the Devices tab, Choose audio player you set up in part B from dropdown at the top of the Devices section, then choose Connect.

3. Click the Transfer button and watch your music sync!

4.  Once the transfer has completed, click the Disconnect button, unmount the disk in Nautilus, remove it from the reader and insert it into your phone.

5. Start your phone's music player.  There should be a one-time initialization where it reads through the track info and loads up your songs.  Once you see that, you know the phone has successfully recognized the music on your memory card.

6. Enjoy your music! :guitar:


That's really all there is to it.  Once you have done the initial setup, just repeat Part C to sync/resync additional music as you please.  If you find alternative methods or find any issues with this tutorial, please post a reply.  I will update this post as necessary.

**Troubleshooting**:
If you have issues, please post as much info as you can, including:
-The symptom you ran into (such as "my phone doesn't see my music")
-Whether you received any errors from Amarok (and if so, what the errors are)
-Wireless carrier and phone brand/model
-Phone software version: where this can be found depends on the phone.  For example on my LG Dare, I find this under Main Menu->Settings&Tools->Phone Info->SW/HW Version.  My firmware version is VX970V05.

I can't guarantee I'll be able to help, but having worked for the big "V" for 3 years (not anymore, thank goodness) I have a fair amount of phone-savvy and I'll help if I am able.

Notes:

   1. The tracks I transferred were all mp3 files with data stored in ID3 tags.  I have not experimented with other formats.
   2. Album Art embedded in the ID3 tag will be read by the phone's music player automatically!  This seems to be the only way to get artwork onto the phone in a format that the phone will recognize.
   3. The phone didn't recognize any of my genre tags, although it did pick up on Artist/Album/Song Title.
   4. Make sure not to use nesting of files under my_music - they must ALL be in my_music and NO other subfolders.
   5. As I mentioned, I used this method to sync a playlist I created from my library on my desktop to my phone, but the playlist itself did not end up being visible in the phone's music player.  This wasn't a big deal to me, so I left it at that.

**Further Reading:** [Howardforums.com]("http://www.howardforums.com") is an excellent source of information for cell phone enthusiasts.  You will be able to find a lot of related info such as how your music player works, other known tricks, etc.  Couldn't hurt to read up on your phone!

---

### Post by bailunrui on 2009-03-14
Thank you so much for writing this! Your instructions are very easy to follow. And it worked!

---

### Post by honeybee0615 on 2009-03-25
Hello I followed your instructions on how to sync music.  I formatted my card to FAT on my windows desk top computer as I did not know how to do it on ubantu 8.10 as I am new. I did all you said.  But when I place the micro sd card into my verizon lg dare VX970V06, the songs came up that were transferred from Amarok, I would touch the song to play, then the phone would freeze up and it would show the player for a quick second then tell me "initialization error please try again".  I am unable to get it to work.  I have tried over and over even from square one.  Any help?

Blythe

---

### Post by greyfox1 on 2009-03-27
Sorry to hear about this problem.  I think it may be either your newer firmware or a problem with the card.  Did you confirm that the mp3 files are in the correct folder on the card once you finished Syncing?  Did you unmount the card through Nautilus before you put it in the phone?  Does this happen regardless of which song you try to play?

That's all I can think of at the moment.  I'm not sure what file system I've got on my card, but I'll check this weekend while I'm at home and post back here.

Edit: my card is formatted to fat16.  A cursory bit of googling suggests that you might need fat16 or fat32, but I'm not sure about this.

Also, the best way to format media under Linux is with [gparted]("http://gparted.sourceforge.net/").  This program is in the repos.  Just issue:
```
sudo apt-get install gparted
``` to install it.  Good luck!

---

### Post by gallagherpet on 2009-04-06
thank you so much for this, this is exatly what i've been looking for. the only problem is that once i put songs on it once, it wont let me take them off or put new songs on. please help, i can't figure this out

---

### Post by greyfox1 on 2009-04-23
Hi there gallagherpet,  what exactly are you trying to do to add more songs/ take them off?  I was able to delete songs without any problems (either through Nautilus or by right-clicking the file in Amarok and choosing delete).  I was also able to sync songs multiple times without any trouble.  

Maybe if you could provide some info about what exactly you are doing and what seems to be going wrong, I would be able to help you better.

---

### Post by lilkbiggs on 2009-07-16
Is the AmaroK 1.4.10 safe to download because it had no known publisher and is not official for windows and mac?

---

### Post by Topher88 on 2009-07-19
my version (which SHOULD be the newest) doesn't have a "Media Devices" option...  What gives???

Edit: Nvm, upon further inspection, I have Amarok 2...

---

### Post by greyfox1 on 2009-07-20
> **lilkbiggs said:**
> Is the AmaroK 1.4.10 safe to download because it had no known publisher and is not official for windows and mac?

I'm not sure what you mean by "safe" but it should be fine.  The Windows/Mac versions are just not "officially supported" according to the Amarok wiki.  If you can get your hands on v1.4 for either of those platforms, I imagine it would work fine.

That said, I can't help you with those versions as I haven't tried it myself.  This being a Linux board, my presumption in writing the tutorial is that you are running Linux.  You might need to make small changes to what I've written if you are using Win/Mac.

---

### Post by seventyx7 on 2009-08-26
how do you do this in Amarok 2? it is set up quite differently than Amarok 1.4. please let me know asap.

---

### Post by greyfox1 on 2009-08-31
Hi seventyx7,

This is taken from the introduction (first post):

> For the purpose of this tutorial, we will assume that you already have Amarok and have scanned your collection into the library. We will be using Amarok 1.4.10, the last 1.x release, since as of this writing Amarok 2 does not offer mobile device support.

I understand that Amarok 2 has some sort of support now, but that is outside the scope of the tutorial.  I haven't tried it personally so I wouldn't be a good person to ask.  Also, using Amarok 2 would likely require writing a completely new tutorial, which is something I have not found the time to attempt.

Good luck.

---

### Post by manat2 on 2011-01-23
Hey!!!really informative thraed   thread...this thread provides really helpful and useful information for what   i am looking from long time....great work ,thanks for sharing with us.

[touch screen protectors]("http://www.decalskins.com/")

---

