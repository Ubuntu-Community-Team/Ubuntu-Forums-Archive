---
title: "Beginner's Guide to a Sansa e200 MP3 Player"
date: 2006-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by SZF2001 on 2006-12-04
**This tutorial was made with Feisty and Edgy in mind - I have not and will most likely not have time to consider Gutsy and the following releases afterward. I can most likely keep posts updated with future releases, but please remember this little detail.** 

Just a few days ago, I bought a Sansa e260 MP3 player, and ran into some troubles. So, I'm writing this guide for beginners so no one else has to suffer the first few days like I did.

First, we have the Table of Contents. There will be questions (generally asked questions) in the ToC, and then next to the said question will be a set of words. For example, the question would be, "Where are my pants?" before the question, the numbers are, "QQQ001". Do a search in your browser (it depends on your browser, but usually you can just press CTRL+F) and do a search for "QQQ001", which will take you to the question you are looking for.

**_:Table of Contents:_**
SSS001 **Connecting your Sansa e200 player to a Ubuntu (or any Linux) computer**
SSS002 **Disconnecting your Sansa e200 player from Ubuntu (or any Linux) computer**
SSS003 **Putting Music on your Sansa e200 player in any OS**
SSS004 **Putting Music on MicroSD cards**
SSS005 **Deleting Music on your Sansa e200 player in Ubuntu (not sure about other OS's)**
SSS006 **How to add Album Art with playing songs**
SSS007 **Having Rhythmbox/Banshee recognize Sansa player**
SSS008 **Putting Movies, Pictures, etc. on the player**
SSS009 **Updating the Firmware**
SSS010 **Organizing your music**
SSS011 **Playlists**
SSS012 **If your Sansa freezes...**
SSS013 **Using Recovery Mode**
SSS014 **Rockbox Instructions**
SSS015 **Gutsy Users**
SSS016 **Question not answered?**

The guide starts now, from this point:

_________________________________

SSS001 **Connecting your Sansa e200 player to a Ubuntu (or any Linux) computer**

*Rhapsody player people should read [this post](http://ubuntuforums.org/showpost.php?p=1939417&postcount=15) about connecting and disconnecting.*

While on the player, go to "Settings", then "USB Mode". Switch it to "MSC". 

Plug your player in the computer through the USB cord, and (in my experience) the player should say "Connected" and "Disconnected" a few times. After a few seconds, it should stay on "Connected" with arrows on it. If you change anything on the player, it should stay on "Writing" until disconnection.

For Xubuntu users, when you plug in the Sansa and the player says "Connected", you need to go on your desktop - there will be an icon for the Sansa player. Right click on the icon, and select the Mount option. Your player should be able to write and read now.

SSS002 **Disconnecting your Sansa e200 player from Ubuntu (or any Linux) computer**

~*THIS IS VERY IMPORTANT*~ Think about it. After a few hours work, writing tags and changing files, wouldn't you hate to accidentally lose that information?

To disconnect the player, you can rather **A:** go on the Ubuntu desktop, right click the player, and press "Eject". A window should come up, tell you it's writing info on your player, and then there won't be an icon. Even though your player still says "Connected", the little arrows should be gone and you can be good to go. Or, **B:** find another way of unmounting your player, rather through the terminal or whatnot. I'm not very experienced in using other Linux OS's, so just make sure your player is NOT mounted before unplugging it.

Xubuntu users, instead of "Eject", go to the desktop where the Sansa icon is, and click "Unmount". Your Sansa player will (might) still say "Connected" with the little arrows still going across - you can now disconnect the player, even though it still says Connected. The point is, it's not writing, and is now finished writing last details.

For those who are concerned: Just because a player says "Connected" shouldn't mean you should go ahead and unplug it. Make sure you have ejected/unmounted the player, and only after you make sure the player is not getting or sending any information, you should be set and good-to-go with unplugging it.

SSS003 **Putting Music on your Sansa e200 player in any OS**

This is very basic. This player is considered *Drag 'n Drop*, meaning you can just put files into the player just by a simple copy and paste method or literally moving your music folder into the player's MUSIC folder.

But remember - put ALL music in the *MUSIC* folder in your Sansa player.

If you have CD's and want to rip them into .mp3, then you can read the [CDRipping Wiki Page](https://help.ubuntu.com/community/CDRipping), or (especially if you are on Breezy), download a program called goobox (do it through the Synaptic Package Manager or terminal). Also, please note, Breezy people, that you will need lame and the gstreamer0.8-lame package (again, use Synaptic), and use "sudo gst-register-0.8" in the terminal.

People using Fiesty and running the default GNOME interface - Sound Juicer should already have the MP3 option pre-made, so go ahead and change it through the Preferences.
People using Dapper and above use these wiki's for further info: [Multimedia Codecs](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/codecs.html)
People using Breezy use these wiki's for further info: [How do I install multimedia codecs?](https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-music-and-movies.html#codecs)

And don't forget about lame! That's very important. Make sure all your repositories are set correctly so you can get all the packages.

Terminal command for installing goobox:

```
sudo aptitude install goobox
```

It will come up as "CD Player" in Applications -> Sound & Video, if you are running Gnome.

For Kubuntu users:

> **showcaser said:**
> Hi and thanks for the guide. Just thought I would mention that it appears ripping with K3B sets the tags properly. Tried it with two albums so far and I was able to copy paste to the sansa without adjusting the tags with easytag. Has anyone else noticed this?

K3B makes tags already. If you want album art I suggest going with the EasyTag program.

SSS004 **Putting Music on MicroSD cards**

I myself don't have a card, but [Ubuntu Joe does, and his post](http://ubuntuforums.org/showpost.php?p=2079202&postcount=75) will fill you in on some info.

SSS005 **Deleting Music on your Sansa e200 player in Ubuntu (not sure about other OS's)**

There are two ways to delete music. One, a very simple way that Ubuntu forum member *yemu* pointed out, is that you can crop the files you want to delete with your mouse, and while they are selected, press CTRL and DELETE. A prompt will ask if you really want to delete these files, and you can take it from there. (For Kubuntu users, I've found that instead, you can just right click and tell it to move the folders somewhere, then delete them there, so Kubuntu won't make a new library folder in your player)

If you've been deleting music but still find the songs there (or you find you have less room than there should be) try the following:

*FOR GNOME USERS*: Go to the root folder of your player (where there are other folders like *MUSIC*, *MOVIES*, etc). In your file browser, press "View" then "Show Hidden Files". You will see a new folder that will say something like "./trashblahblah". Delete this file. Now your music is officially off.

*FOR KDE USERS*: Go to the root folder of your player (where there are other folders like *MUSIC*, *MOVIES*, etc). In your file browser, press "View" then "Show Hidden Files". You will see a new folder that will say something like "./trashblahblah". You cannot simply delete the folder, since Kubuntu is different for some reason and won't let you, since it considers it a "library folder", or something (I've tried removing it through sudo and the terminal, it still says it can't remove it). Oddly enough, all you need to do is get ride of the period (.) in front of the trash folder - then you can delete it with the simple press of the "delete" key. If that doesn't work, try simply moving the folder (with right-click and using the "move" option) to your Home folder, than delete it there.

SSS006 **How to add Album Art with playing songs**

Taken straight from Ubuntu Joe's mouth:

> **Ubuntu Joe said:**
> Finally!  A question I can answer!

It's very easy to add album art to your songs through EasyTag.

First of all take your .jpg and crop it to exactly 300x300 pixels . . .

Got it?  Good, now open up that awesome EasyTag editor, select the appropriate album, switch over to the Album art tab, add the .jpg, tick the box so all the files get the image, and you're done!

BAM, beautiful, images to accompany your tunes.

:guitar:

So, in a sense, you'll need to have EasyTag. Or maybe there is a way to do it manually... I don't know. EasyTag way is easy enough though, so give it a whirl!

SSS007 **Having Rhythmbox/Banshee recognize Sansa player**

Here is the post from the ABi forum, I give complete credit to this guy:

> **Cgil said:**
> Just added support to banshee... It's quite easy:

1.Set your sansa in MSC mode.
2.Connect it to the computer.
3. In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. This might work for KDE but I'm not sure...)
4.Now, name your file as  [I].is_audio_player
[/I]
Start Banshee and it should recognize it :)

BTW I'm using the CVS version of Banshee

It's really that simple - make a hidden text file called ".is_audio_player" and BAM. Rhythmbox recognized it. Make SURE that you put the hidden file in Sansa's root file (the file you immediately start from, which directs you to the "MUSIC" "PHOTO" etc files)

He did mention he is running the CVS version - fear not, for I am running the version that came with Ubuntu (and Banshee was installed through the Ubuntu repo's): so I've tested it and it indeed works. Makes Rhythembox very handy all of a sudden. :D

SSS008 **Putting Movies, Pictures, etc. on the player**

UPDATE: It seems like Rockbox plays .mpg video formats, but I'm not sure how it handles or anything. If you haven't put Rockbox on your Sansa you are REALLY missing out. The below column is out-of-date but could provide interesting leads to whomever wants to dig into this stuff.

My only knowledge of encoding movies of any kind is by using AcidRip, which is even then very limited. I have found numbers and specifications thanks to the ABi forums. If you are going to change movie files, make sure they are in .mov format - nothing else works. Also, movies can only be 220x176 (when you rotate it to view the movie, final resolution is 176x220 (thank you ABi forum member Norgolam for pointing this out)), 15fps and 22kHz (MJPEGB and A) - once again, thank ABi for this info. [Here is a thread where some people actually know some stuff about encoding I could never possibley understand, hopefully you can...](http://www.anythingbutipod.com/forum/showthread.php?t=81)

As for pictures - still not a clue. There is a way to have album art showing at the same time as you play music (see a few steps above this one), but to add in pictures manually to view whenever in the Picture option - not too sure. Someone, anyone, let's figure this out...

SSS009 **Updating the Firmware**

Many believe you need to be on a Windows machine to install firmware. Well, thanks to the [Anything But iPod Forums](http://www.anythingbutipod.com/forum/forumdisplay.php?f=51), you CAN install firmware through Linux. This entire portion of the guide gets a kudos to them, because I would be lost without these guys. You can see one of my topics there, in the wrong place, and they are still willing to help. Back to the guide;

First off, you will need to have the package "unrar" installed. Here's a terminal command, if you like:

```
sudo aptitude install unrar
```

I'm not sure if it can be installed through Synaptic, so you can give it a try or just use the terminal.

Now, when a new Firmware update comes up, the ABiP forums will post it in a .rar file. Download it. Make sure your player is connected.

Now, through the Archive Manager or whatever unzipper program, extract a file in the rar with a .mi4 extension (example: PP5022.mi4) into your Sansa's root file. Root as in the file before "MUSIC", "PICTURES", etc.

Now, eject the player, and unplug it from the computer. The MP3 player should restart and check for updates, and will tell you it's install firmware. Then it should restart again, with new firmware.

Please note that after firmware updates, the USB mode in the player will switch back to MTC. Put it back to MSC, and Ubuntu can recognize it again.

SSS010 **Organizing your music**

This part got me so frustrated, and I don't want anyone else to ever be so mad like I was. So let's get started...

The Sansa player basically lives off of ID3v2 tags. I've learnt the hard way that Sound Juicer makes ID3v1 tags (unless someone can clear that up for me). I even tried in Banshee and they make those tags the same way...

Even changing tags in Banshee doesn't work. So no there.

There are three awesome programs to try - try each and see which one you take to your liking. They are Cowbell, EASYTag, and TagTool (TagTool comes up as Audio Tag Tool under Applications and Sound & Video)

For a quick install of all three of these, paste this into the terminal:

```
sudo aptitude install cowbell easytag tagtool
```

Of course, these can be install through the Synaptic Package Manager as well. Anyway...

I've had moderate success with Cowbell. Try using it's "Guess Song Information" under "Tools" to fill in tag information. Usually it's right, but if it's completely off, press "Revert" under "Album" to change the changes back to normal, from before. You might want to change the preferences to make it so when you change the tag info, it can change the file name info as well. Helps a lot when TagTool is being dumb.

In EASYTag, it will start scanning your hard drive's music folder. You can just stop it, and follow the tree to your Sansa player (usually under /media). Let it scan through the songs, and if any songs do not have tags they will be red. That is how you will be able to tell if your music has tags on them or not. Make sure you change the settings in Settings -> Preferences to let EASYTag know your media player (Rhythmbox, Banshee, etc)

Once you change a tag in EASYTag, crop the files, or make sure it's selected, and to go "File" and "Save Tag(s)" (or something to that extent). Your tags should be saved.

I highly recommend EASYTag. Why? Because it's so freakin' easy. It took me, well, a few minutes (maybe ten) to sit down, think about what I was doing, and now it's a snap. You can find information on music in a snap - just crop the album, right click, and press CDDB Search File(s). Which usually finds them.

TagTool is okay for a basic tagger. Not the greatest or spiffiest, and sometimes I find it breaking down on me. Use it only if it's your last choice or you want to bash your head against the wall in frusteration.

But, as far as I know, TagTool doesn't do pictures. If you REALLY want album covers when your songs show up, try EASYTag. Cowbell is good at getting the information from the internet and filling it out for you. It's all about preference, so feel free to try whatever tagging program.

[Here is a post detailing EASYTag with pictures so you know how to use it](http://ubuntuforums.org/showpost.php?p=2024567&postcount=53). Hope it works out for you!

SSS011 **Playlists**

This is a somewhat out-dated column and it seems like the playlists issue is fixed with the first link provided here. I'm keeping the other links for the sake of recording old methods and letting people try out different things.

So here are some things that *might* work (UPDATE: With the exception of the first link) - I haven't tried any of them, because, like I mentioned before, I don't really use playlists. I could really use someone's help here.

[The Mazleg Script](http://www.mazleg.com/sansa/) - the Super Awesome Playlist Script.

[This, my friends, is a .m3u conversion script.](http://www.supermario.org/m3u2pla-awk) Except I have no idea how to use it, and couldn't tell you how to use it. Again, please, someone help me out here.

[Here is a ABi thread about a .m3u to .pla conversion program.](http://www.anythingbutipod.com/forum/showthread.php?t=537) Buuut, the catch is, it's an .exe file, so you'll need to grab a copy of Wine (just find it in Synaptic, not to hard). If you think I just told you to go buy some wine, then you're going to need to [read this wiki page](https://help.ubuntu.com/community/Wine) to understand what I'm talking about here.

[Someone made a MSC playlist program...](http://www.anythingbutipod.com/forum/showthread.php?t=2381) But it's only for Windows. Check some posts, I couldn't find out if there were new up-to-date versions...

That's all the info on playlists I could scrounge up at this point. Feel free to help me out, and I'll give credit where it's due.

EDIT: [This looks promising](http://www.mazleg.com/sansa/) - a Sansa Playlist Editor with a GUI. (thanks dumpy)

SSS012 **If your Sansa freezes...**

There is that rare time (or, maybe you are unlucky and it's NOT so rare...), once in a while, where your Sansa player will freeze. Probably because you unplugged it from the USB cord to fast, maybe your little brother or sister repeatedly hit it against the wall... Well, your Sansa is frozen and broken. Right? Wrong.

There are two methods in fixing a frozen Sansa, and I HIGHLY recommend the first, since you'll probably almost never need the second method. The first and easy method is; hold onto the power (menu) button for 15 seconds.

If you've been holding onto the button for a half an hour and it's STILL in a frozen state, looks like you'll need to grab a screwdriver, take out the back, take out the battery so everything shuts off, put the battery back in, make sure you screw everything in good, and it should work. But I only recommend this method in a rare -rare- case that your frozen Sansa does not turn off after holding the power button for 15 seconds.

And if you don't want to count 15 seconds - just hold down the power button. Basically, if it's still frozen after a minute, then maybe you should try the second method.

SSS013 **Using Recovery Mode**

So you accidentally deleted a few important files. Oops. Now your Sansa player won't do jack crap, even if you tried a manual shut off, and it's spouting out weird crap.

First, I recommend going to the [AnythingButiPod](http://www.anythingbutipod.com) forum and downloading some firmware (make sure you find the .zip or .rar file). Maybe you should make a file dedicated to Sansa firmware in case this stuff happens again.

Now, turn the power off on your player by holding the power down on it for 15 seconds. Now, lock your player, and while you turn it on again, hold the REC button on the side of the Sansa. If you did it right, then a little black screen with white words will appear, saying stuff about recovery mode. Insert the player into your computer.

Now it should come up as a "16MB" flash drive, instead of saying usually "Sansa e2XX". Get your firmware and copy the .mi4 file, and paste it into this flash drive. Now eject the flash drive, and your player should talk about installing firmware. Hopefully, that worked.

SSS014 **Rockbox Instructions**

Since this is a Beginners Guide and this seems to be just a little out of a real novice grasp, I will post a link to the post describing Rockbox installation for the sake of keeping this page just a tad bit shorter (and sweeter):

[http://ubuntuforums.org/showpost.php?p=3496631&postcount=116](http://ubuntuforums.org/showpost.php?p=3496631&postcount=116)

If you have any Rockbox questions, feel free to ask them here - [but there is also a whole community aimed at Rockbox with your Sansa e200 (Anything But iPod forums)](http://www.anythingbutipod.com/forum/forumdisplay.php?f=72) if a question is not answered here. There is a wealth of information in their stickies, cool mods, and other things...

**I am not responsible (sp) for your modding and your actions in which you modify your own Bootloader - you make your own conscious choice to modify YOUR Sansa.**

SSS015 **Gutsy Users**

Having problems with mounting the drive? [Check out this post](http://ubuntuforums.org/showpost.php?p=3798461&postcount=118). Hopefully that helps!

SSS016 **Question not answered?**

Refer to [this post](http://ubuntuforums.org/showpost.php?p=3995708&postcount=129).
_________________________________

If anyone would like to help add to the guide, post or PM me, and I'll give credit where it's due, etc.

I'd like to give a big shout out to the [Anything But iPod](http://www.anythingbutipod.com/) website for all there help! Thanks guys!

Hopefully that's helped some of you looking for answers. Enjoy! :-D

---

### Post by mickbw on 2006-12-04
Thanks for this.  

My Sansa is the e200R Rhapsody player and that is one of the reasons I would find it hard to shut off the Windows install, since I can download the music from the Rhapsody client for free to my player becasue of my subscription.

---

### Post by yemu on 2006-12-04
to delete files without having to go to .Trash just select files and press ctrl+delete and then "OK". and they're gone

---

### Post by SZF2001 on 2006-12-04
> **mickbw said:**
> Thanks for this.  

My Sansa is the e200R Rhapsody player and that is one of the reasons I would find it hard to shut off the Windows install, since I can download the music from the Rhapsody client for free to my player becasue of my subscription.
Can you get Wine to work with the Rhapsody client? Do you still use it? I'd love to add any Rhapsody player information on this guide, and will give credit where it's due.

---

### Post by mickbw on 2006-12-04
I wish I could get it to work.  If i hear of any new stuff I will place a comment on this post.  

My total cut over list is:
Rhapsody
Replay Radio 
Visual Fox Pro v.8

---

### Post by SZF2001 on 2006-12-04
Good idea! I'll do some searching as well. If I find anything, it will be posted.

---

### Post by SZF2001 on 2006-12-04
Sorry to double post, but I thought I'd get this around... Not to much luck with searching... I found something, but not something to great.

[http://www.desktoplinux.com/news/NS8866672411.html](http://www.desktoplinux.com/news/NS8866672411.html) - A news article stating that Rhapsody **is** available for Linux users, but music can only be streamed until they get around to making a client. Which is whenever, hopefully never.

[http://www.warpedview.com/rhapsody-on-linux/](http://www.warpedview.com/rhapsody-on-linux/) - Rhapsody can work with Wine, but it's a older version of Rhapsody, so good luck if you are going to try this...

---

### Post by beefcurry on 2006-12-06
wow :D nice, good job on this, i was really finding the Sansa innoying after switching to linux :), nice one here.

---

### Post by SZF2001 on 2006-12-10
Thank you, beef.

I know I'm a little late on this but I'll ask - anyone need anything else covered in this guide? Questions, comments?

---

### Post by civilian on 2006-12-12
Thanks a lot for this guide, very helpful, its one more thing crossed on my list of things I have to have a windows partition to do!

---

### Post by sysop on 2006-12-12
> **yemu said:**
> to delete files without having to go to .Trash just select files and press ctrl+delete and then "OK". and they're gone

In Gnome at least, open a File Browser (doesn't matter where). From the menu bar select Edit/Preferences. You should see a File Management Preferences Window. Select the Behavior tab. At the bottom you should check the box next to "Include a Delete command that bypasses Trash". Now you should be able to right click and immediately delete files without them going to the Trash or creating a .Trash folder anywhere. ;)

---

### Post by Sierra-X on 2006-12-15
> **SZF2001 said:**
> Thank you, beef.

I know I'm a little late on this but I'll ask - anyone need anything else covered in this guide? Questions, comments?

Actually, yes.  Playlists.  Looks as if standard m3u playlists won't work (or show up at all)...  Any info on how to go about that?

---

### Post by SZF2001 on 2006-12-18
Honestly, I have no idea.

I organize everything on my Sansa just by using tags and going through the menu to Music - Albums - and then pick whatever album... But ya, I can understand wanting your own playlist for different songs.

Looks like I got some detective work on my hands. I'll be back on this in a little bit.

---

### Post by SZF2001 on 2006-12-19
UPDATE: Playlist information, even though not a lot, is up. There is also some movie info as well.

---

### Post by Zwack on 2006-12-28
> **SZF2001 said:**
> 

**Connecting your Sansa e200 player to a Ubuntu (or any Linux) computer**

While on the player, go to "Settings", then "USB Mode". Switch it to "MSC". 

Plug your player in the computer through the USB cord, and (in my experience) the player should say "Connected" and "Disconnected" a few times. After a few seconds, it should stay on "Connected" with arrows on it. If you change anything on the player, it should stay on "Writing" until disconnection.



On an e2X0R player Select Rhapsody mode rather than PlaysForSure (This is the same MSC versus MTP but different labels)

Writing may change back to Connected if the data has synched.  This is NOT a problem.

See the next bit for Clarification...

> 

**Disconnecting your Sansa e200 player from Ubuntu (or any Linux) computer**

~*THIS IS VERY IMPORTANT*~ Think about it. After a few hours work, writing tags and changing files, wouldn't you hate to accidentally lose that information?

To disconnect the player, you can rather **A:** go on the Ubuntu desktop, right click the player, and press "Eject". A window should come up, tell you it's writing info on your player, and then there won't be an icon. Even though your player still says "Connected", the little arrows should be gone and you can be good to go. Or, **B:** find another way of unmounting your player, rather through the terminal or whatnot. I'm not very experienced in using other Linux OS's, so just make sure your player is NOT mounted before unplugging it.



I'm paranoid about this so here is what I do.  

Open a terminal window.  Type sync.  Wait for it to finish.  This command flushes the file buffers so your player has everything written to it.  Then right click on the icon and select "Eject" this unmounts the player, but it will still say Connected.  Finally, back in the terminal I type "sudo eject /dev/sg0"  You may need to use a different device.  This actually ejects the USB device and your player will now say Disconnected.

Finally, Upgrading the firmware is even easier than you suggest... Sandisk will put the new version of the firmware up as a zip file on their site.  The e2x0R players will be later than when it's available on Rhapsody, but give it a week or two and it will appear.  Download the .zip file, uncompress it and copy the .mi4 into the root directory of the player.  

I hope that this helps,

     Z.

---

### Post by Ubuntu Joe on 2006-12-28
So, can I just drag and drop my .mov files directly onto my Sansa e200?  Do I HAVE to modify them at all?  And where EXACTLY does one drag them?  For that matter where EXACTLY does one drag one's music?

---

### Post by a12ctic on 2006-12-28
> **saalota said:**
> So, can I just drag and drop my .mov files directly onto my Sansa e200?  Do I HAVE to modify them at all?  And where EXACTLY does one drag them?  For that matter where EXACTLY does one drag one's music?

Everyone is still sort of clueless about this. In mencoder ive gotten this far 

```
mencoder ~/intput.avi -o outputfile.mov -oac pcm -af resample=11025 -ovc lavc -lavcopts vcodec=mjpeg -ffourcc mjpb -vf rotate=1,scale=176:220 -ofps 12 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
```

video works perfectly, but still no sound, if anyone would like to help it would be great. :) Heres a sample output of the file on the player.

---

### Post by SZF2001 on 2006-12-28
And yes, you just drag your music into the MUSIC folder that's on your Sansa. Might wanna make sure your tags are there, as well. And that they are v2.

---

### Post by Ubuntu Joe on 2006-12-28
how exactly can I check that?

---

### Post by Christian_Joe_Linux on 2006-12-28
I'm connecting the Sansa_e260 mp3 player through PCLinuxOS and KDE.  I created a folder named "Jazz"  in the "/mnt/Sansa_e260/music" directory, but it shows up as "unknown" on the Sansa player.  This may have been covered, but how do you get the player to see the true name of the folder ?

I found out that the e260 builds its own database after you set the proper mp3 id tags.  I found the easiest way  to do this is to open it in konqueror after you've plugged it into your USB port and you get the prompt.  You can highlight the folder you want, and right click it and choose "Open With"  and type in "easytag" in the window.  Editing the tags seems tedious as I had to do it one by one.  You have to put in the name of the folder you want in "Album Name" field.   Then when the e260 restarts, it will rebuild it's data base based on the mp3 tags.  

I think it wold be a lot simpler if it just played what's in your folders, as they are named in your file system.  Then it would be truly drag and drop.  The problem with doing it by mp3 id tag is that if you move your songs around from folder to folder, you would have to change the id tag info.  Or is there some id tag program thaqt tags the mp3's on the basis of the folder its in in your file system, and the names you have already given it?

---

### Post by Zwack on 2006-12-28
> **Christian_Joe_Linux said:**
> 
I think it wold be a lot simpler if it just played what's in your folders, as they are named in your file system.  Then it would be truly drag and drop.  The problem with doing it by mp3 id tag is that if you move your songs around from folder to folder, you would have to change the id tag info.  Or is there some id tag program thaqt tags the mp3's on the basis of the folder its in in your file system, and the names you have already given it?

Or you could do it the way I do...

EasyTag will let you set multiple tracks simultaneously.  I store my mp3s in Artist/Album/XX-Title.mp3  You can then use EasyTag to Parse that and store the information in the appropriate fields.  XX is the track number.  You can also select a Genre for each track (Such as Jazz).

Then you can drop them on the Sansa and select them by Artist, by Album, by Name, or by Genre.

If you want to mix Genres up then create a playlist.  I haven't got that far yet, but I've seen enough information about it to know it can't be too hard.

Z.

---

### Post by Christian_Joe_Linux on 2006-12-29
> **Zwack said:**
> Or you could do it the way I do...

EasyTag will let you set multiple tracks simultaneously.  I store my mp3s in Artist/Album/XX-Title.mp3  You can then use EasyTag to Parse that and store the information in the appropriate fields.  XX is the track number.  You can also select a Genre for each track (Such as Jazz).

Then you can drop them on the Sansa and select them by Artist, by Album, by Name, or by Genre.

If you want to mix Genres up then create a playlist.  I haven't got that far yet, but I've seen enough information about it to know it can't be too hard.

Z.

Could you explain in more detail how to say add "Artist" or "Album" to all the tracks on a given ripped CD?

I have now learned that if the CD was in the web based CDDB it's already done.  The problem is with albums you have ripped that aren't in the data base.  In my case I listen to a lot of audo books on CD that I have ripped to mp3 myself.

---

### Post by Zwack on 2006-12-30
> **Christian_Joe_Linux said:**
> Could you explain in more detail how to say add "Artist" or "Album" to all the tracks on a given ripped CD?


In EasyTag you have a portion of the screen to the right that has the tag information in it.

You select all of the tracks on the left that you want to Tag and then enter the information in the Tag area on the right.

Then once you have entered the information in a field that should be the same for all selected tracks click the button to the right of that field.

[IMG]http://www.mutant.net/tags.png[/IMG]


I circled them in red...

I hope that this helps,
    Z.

---

### Post by SZF2001 on 2006-12-30
Despite what I've said in the guide... EasyTag isn't really easy for me. Is there a way to make ***_sure_*** that all tags are v2? I tinkered around with it and had no luck...

TagTool is awesome for the first time you ever use it, because it will actually mass tag albums. But after the first time, opening the program again and trying to mass tag, it never recognizes anything as any kind of music format. Is it just me? If someone could show me the light with EasyTag, I would drop TagTool altogether, and edit the guide so it's not even mentioned (or just slightly).

---

### Post by Zwack on 2006-12-30
> **SZF2001 said:**
> Despite what I've said in the guide... EasyTag isn't really easy for me. Is there a way to make ***_sure_*** that all tags are v2? I tinkered around with it and had no luck...


Settings->Preferences a Preferences window will pop up.  Then you want to select the ID3 Tag Settings tab. Top right you have two check boxes "Write ID3v1.x Tag" and "Write ID3v2 Tag"

Seems fairly straightforward to me.

Z.

---

### Post by Zwack on 2006-12-30
Pictures (from what I can tell) are Bitmap files in 16 pits per pixel mode (5:6:5) which are 176x220.  I haven't found a Linux tool that can create 16BPP BMP files (Or many Windows ones either).  Does this mean that I need to write a conversion tool myself?

Z.

---

### Post by Christian_Joe_Linux on 2006-12-30
> **Zwack said:**
> In EasyTag you have a portion of the screen to the right that has the tag information in it.

You select all of the tracks on the left that you want to Tag and then enter the information in the Tag area on the right.

Then once you have entered the information in a field that should be the same for all selected tracks click the button to the right of that field.

[IMG]http://www.mutant.net/tags.png[/IMG]


I circled them in red...

I hope that this helps,
    Z.
Thanks for the pictures it really helps in a guide.  It's just that I don't know what the buttons actually do.  I know if you click on one, it will put a black dot in the center, but I don't know what that indicates.  Do you activate the buttons for only the fields you want to change?  For example in a mass change you wouldn't want the name of the song or the track number  to all be the same.

---

### Post by Zwack on 2006-12-30
> **Christian_Joe_Linux said:**
> Thanks for the pictures it really helps in a guide.  It's just that I don't know what the buttons actually do.  I know if you click on one, it will put a black dot in the center, but I don't know what that indicates.  Do you activate the buttons for only the fields you want to change?  For example in a mass change you wouldn't want the name of the song or the track number  to all be the same.

If you fill in a field and then click the button then ALL of the selected files will have the information in that field filled in.  The buttons with a # in them will automatically fill the correct numbers in (track number, Number of tracks in folder,...) But the others will copy information from the current tag into all selected tracks.  

So, select tracks, fill in the field(s), and then press the button(s).  All of the tracks should now share some of the information.

I hope that this helps,

Z.

---

### Post by Christian_Joe_Linux on 2006-12-31
> **Zwack said:**
> If you fill in a field and then click the button then ALL of the selected files will have the information in that field filled in.  The buttons with a # in them will automatically fill the correct numbers in (track number, Number of tracks in folder,...) But the others will copy information from the current tag into all selected tracks.  

So, select tracks, fill in the field(s), and then press the button(s).  All of the tracks should now share some of the information.

I hope that this helps,

Z.

Yes, thanks. I'll try that.

---

### Post by Christian_Joe_Linux on 2006-12-31
How do you know what firmware version is installed on your player?

---

### Post by Zwack on 2007-01-01
> **Christian_Joe_Linux said:**
> How do you know what firmware version is installed on your player?

On your player go to Settings -> Info  It will list the Firmware version in there.

Z.

---

### Post by Christian_Joe_Linux on 2007-01-03
Is there a way to save the firmware that's presently installed on your player before upgrading to newer firmware?

---

### Post by SZF2001 on 2007-01-04
Uhm... I really wouldn't know, and I don't think I want to try because:

1 - I'm not made of money and if I screw something up I can't just pick up another Sansa

2 - You'd probably have to mess around with the SYSTEM folder or something like it.

But what I suggest is finding out what your firmware is through your player, then go to the ABi forums and give it a quick search.

---

### Post by Zwack on 2007-01-04
> **Christian_Joe_Linux said:**
> Is there a way to save the firmware that's presently installed on your player before upgrading to newer firmware?

Why would you want to?

Also, it depends on your player from what I can tell.  But the answer is "not really"...

Z.

---

### Post by Ubuntu Joe on 2007-01-05
Been playing around with my Sansa e250, and I love it . . . I use it for podcasts, and it's perfect . . . Here are a few tips:

Believe it or not, SanDisk reps are rather friendly and helpful, AND they don't seem to mind helping out folks with Linux . . . perhaps it was just MY rep . . . anyway!  I asked and agreed to EMAIL me the Firmware upgrade for my device.  To find out what Version your running, on the player go to Settings => Info and spin the wheel to scroll through the different screens.  The most up-to-date version is:  v0102.15A.

Here's a quick guide on how to install new firmware:

1. Make sure the player is off (if necessary, hold down the power button for 15 seconds to turn it off).
2. Move the hold button to ON (move to the right towards the headphone jack).
3. Hold the record button.
4. Connect the player to the computer.
5. Keep holding the record button till the "new hardware is ready for use" comes up, then realease the record button.

You've just entered the recovery mode on your player!

6. Now you should have a 16MB drive appear on the desktop.  Simply download the 2 attached files the rep will send you, then put them onto the 16MB drive (via drag-and-drop, or copy-and-paste).
7. Once that's done, turn off the hold switch, **UNMOUNT THE SANSA***, then unplug the player.  The firmware should update itself.

NOW!  If you don't feel like talking to SanDisk, just shoot me an email, and I'll be more than happy to forward the appropriate files to you with this same rundown . . . 

If anyone knows how to format their player through recovery mode, IN UBUNTU, please let me know . . . I have the updater program for winBLOWS, but I'd like to maintain my Sansa WITHOUT having to regress . . .

---

### Post by Zwack on 2007-01-07
> **saalota said:**
> The most up-to-date version is:  v0102.15A.

You've just entered the recovery mode on your player!

...

If anyone knows how to format their player through recovery mode, IN UBUNTU, please let me know . . . I have the updater program for winBLOWS, but I'd like to maintain my Sansa WITHOUT having to regress . . .

For the e250R the latest firmware version is 1.0.2.21 [Download it here]("http://www.sandisk.com/Retail/Default.aspx?CatID=1449")

You can just copy the .mi4 file onto the e2x0R and when it is restarted it will perform the firmware upgrade.  

Z.

---

### Post by boutros on 2007-01-07
hey there,

thanks to SZF2001 and everyone for all the info in this post. Got a new e260
recently and am glad to find out all this good stuff.

peace,
boutros

---

### Post by SZF2001 on 2007-01-07
If anyone, you should really thank the ABi forums. I just gathered all the info into one topic. But you are welcome and congradulations on your new Sansa purchase!

---

### Post by Ubuntu Joe on 2007-01-07
Any luck with miniSD cards?  I'm looking to EXPAND . . . Does it just show up like another drive on your desktop?

---

### Post by SZF2001 on 2007-01-08
Nothing here, I haven't needed a card (yet). Any details Zwack?

---

### Post by Zwack on 2007-01-09
> **SZF2001 said:**
> Nothing here, I haven't needed a card (yet). Any details Zwack?

Just a guess and some second hand information.  I recall seeing a comment on Anything But Ipod that said the micro SD card appears as a second drive on windows.

If you check dmesg when you connect your sansa you will see it assign two generic scsi devices.  One of those (the first one) is then mounted as you player.  I think the second one is the micro SD card slot.  If there is a formated card in there it would probably mount too.

> [17394745.964000] usb-storage: waiting for device to settle before scanning
[17394750.964000] usb-storage: device scan complete
[17394750.964000] Vendor: SanDisk Model: Sansa e250R Rev:
[17394750.964000] Type: Direct-Access ANSI SCSI revision: 00
[17394750.964000] Vendor: SanDisk Model: Sansa e250R Rev:
[17394750.964000] Type: Direct-Access ANSI SCSI revision: 00
[17394750.968000] SCSI device sda: 3885056 512-byte hdwr sectors (1989 MB)
[17394750.968000] sda: Write Protect is off
[17394750.968000] sda: Mode Sense: 45 00 00 00
[17394750.968000] sda: assuming drive cache: write through
[17394750.972000] SCSI device sda: 3885056 512-byte hdwr sectors (1989 MB)
[17394750.972000] sda: Write Protect is off
[17394750.972000] sda: Mode Sense: 45 00 00 00
[17394750.972000] sda: assuming drive cache: write through
[17394750.972000] sda: sda1
[17394750.976000] sd 2:0:0:0: Attached scsi removable disk sda
[17394750.976000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17394750.980000] sd 2:0:0:1: Attached scsi removable disk sdb
[17394750.980000] sd 2:0:0:1: Attached scsi generic sg1 type 0


Notice that we have both sda/sg0 and sdb/sg1.  

I hope that this helps,

Z.

---

### Post by Ubuntu Joe on 2007-01-09
I'll let you guys know when I try it . . . NewEgg.com has 1 Gb Micros for $21!

---

### Post by SuperMike on 2007-01-09
First off, my Sansa R-O-C-K-S!!! My daughter's iPod sucks compared to this thing. If you're an Ubuntu user, consider a Sansa over an iPod. It's also a heck of a lot easier to get songs on and off.

Some things I noticed:

* If you're watching a video and the screen dims or the unit goes into some weird kind of not-quite-shutoff mode, it's because you might have a song playing in the background. Weird bug on the unit, but if you kill the song from playing the video works okay.

* To force a complete power off if the unit is ever hung up, hold the big round Select button at the same time as the Menu, and hold it there for about 15 seconds. The unit will cut off completely.

* If you try to make a custom icon for the mounted volume on your desktop, it will only last in GNOME as long as the volume is still mounted. If you unmount and remount, it will fall back to the default icon. Kinda sucks, but oh well.

* I use Beep Media Player for MP3 playback. I noticed it has an ID3 editor in it if you open the playlist and rightclick a song and choose details. It works great.

* If you previously wrote a song to the player without an ID3 setting inside the file, and then try to either edit it on the device itself or edit a copy on your desktop, it will not update the Sansa database. You first have to cut the file out of your Sansa, edit the ID3 tag whichever way you know how (such as with Beep Media Player technique), and then unmount the Sansa so that it reboots and any previous version of that song is expunged from its database, remount the Sansa, and then copy the properly ID-tagged songs to the Sansa into the Music folder. When you unmount the Sansa volume and it reboots, it will now come up with the proper tags on it.

---

### Post by Zwack on 2007-01-09
> **SuperMike said:**
> 
* If you previously wrote a song to the player without an ID3 setting inside the file, and then try to either edit it on the device itself or edit a copy on your desktop, it will not update the Sansa database. You first have to cut the file out of your Sansa, edit the ID3 tag whichever way you know how (such as with Beep Media Player technique), and then unmount the Sansa so that it reboots and any previous version of that song is expunged from its database, remount the Sansa, and then copy the properly ID-tagged songs to the Sansa into the Music folder. When you unmount the Sansa volume and it reboots, it will now come up with the proper tags on it.

Or just delete the files in the /system/data folder on the Sansa.  It writes info about each file into a database in there.  If you delete the database it will rebuild it.  It should pick up the new info then.  My guess is that the database just checks to see if the file is already in there, not if it has changed.  So it doesn't refresh the information.

I hope that this helps,

Z.

---

### Post by SZF2001 on 2007-01-10
Something I've noticed, is that if you are a fan of torrenting (legally, right?), than you can torrent music right into the Sansa.

With whatever client you are using, just make sure your music goes to /media/(whatever your Sansa's name is)/MUSIC, make sure you know how much space you have and need for this, and let it go to work.

I've done it on KTorrent, the torrent client that comes with GNOME Ubuntu, so it's all good. Sometimes people leave in stupid files (like playlists and .txt files), so you might have to go clean them up.

---

### Post by DeathOnJuice on 2007-01-10
> **Zwack said:**
> Or just delete the files in the /system/data folder on the Sansa.  It writes info about each file into a database in there.  If you delete the database it will rebuild it.  It should pick up the new info then.  My guess is that the database just checks to see if the file is already in there, not if it has changed.  So it doesn't refresh the information.

I hope that this helps,

Z.

Will this have any negative effects? Are you sure on this one? Will it help the double-song problem in this thread:

[http://www.ubuntuforums.org/showthread.php?p=1991744#post1991744](http://www.ubuntuforums.org/showthread.php?p=1991744#post1991744)

---

### Post by Ubuntu Joe on 2007-01-11
Woah, woah, WOAH!

SuperMike, how did you get video on your Sansa . . . I've tried EVERYTHING!  Including the crappy-poo software that comes with the thing on a winBLOWS box . . . still no luck . . . Teach me!

---

### Post by SZF2001 on 2007-01-11
Holy crap we are close to video.

If I knew anything about encoding or decently running any program with the terminal, I'd gladly help. This is one downfall of Ubuntu, is the basic idiot user who uses icons and flashy crap to get into programs. ](*,)

---

### Post by Ubuntu Joe on 2007-01-11
That's totally me . . .

---

### Post by Zwack on 2007-01-12
> **DeathOnJuice said:**
> Will this have any negative effects? Are you sure on this one? Will it help the double-song problem in this thread:



I don't know about the double-song problem (yet) but this is totally safe.  I have deleted the entire contents of the system folder on my e250R and it rebuilt the database.  It got rid of all of the Rhapsody channels that I don't use as well... :)

Z.

---

### Post by SZF2001 on 2007-01-12
With my way, I've never lost any data, had any wierd double tracks, nothing. Just because it says "connected" doesn't really *mean* it's connected. Or maybe it's just my Sansa, out of the other thousands, that still say connected after ejecting it and KNOWING my system has fully ejected it and written data.

---

### Post by pdog on 2007-01-16
Has anyone had this experience.  I am able to have the sansa e260 recognize Artists, Albums and Genre correctly, but the songs in the album are always in alphabetical order-not the order they appear in the album.  I am using the 6.06 default Sound Juicer (v.2.14.4) to rip and Cowbell (v.0.2.7) to tag. One of the options in "preferences" in Cowbell is to create an album-order playlist, but this is done as an m3u file, which I gather from reading this thread is not recognized by the sansa e series (with updated firmware (01.02.15A).  Does anyone have a workaround for this?  Thanks, and thanks to SZF2001 for a great tutorial.

---

### Post by SZF2001 on 2007-01-17
Ah yes, my very first major problem. I hated this, and I know organize all my music through the Album section of the player...

But anyway. I will address this - you need your music tags to be v2. I'm pretty sure, at this point, that Cowbell will only write tags for whatever tags are currently on your song file (example, if you already have a v2 tag it will write info on it, but if you don't, it won't write for jack crap).

EASYTag is by far awesome. But, at first glance, it can be a little confusing. I'll put up a picture-by-picture guide, but I'll only link the pictures for examples becase a - some people still use 56K modems and it wouldn't be very nice to make them load a bunch of huge pictures and b - for the sake of not stretching the page.

First off, make sure your player is plugged into the computer. I have found that, since using Xubuntu, you have to go to the desktop and mount it with a right click and selecting "Mount". I've found in KDE and GNOME that it just kinda mounts by itself. Anyway...

So, open up EASYTag. EASYTag, by default, writes tags in v1 and v2, which is fine, since that's what I just stick with anyway... You can turn off v1 through the options page, but you have to select an audio player for EASYTag to recodnize - so pick one of your choice (XMMS, Banshee, Rhythmbox, Xfmedia, whatever you use/like). I suggest going into options and make sure EASYTag knows your media player, anyway.

OK. So you are brought to a page like this:

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag1.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag1.png)

To the left, is a tree directory of your files. Please note I have already found a place where (most) Sansa's mount to - /media/(your Sansa's name here), which will lead to MUSIC, and other folders. It doesn't matter if you just click on the Sansa player's name or the MUSIC folder, because once you double click the part of the tree you want to write tags with, a scanner will pop up (unless you've changed your options to make it so you can't), like so:

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag2.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag2.png)

When the scanner is done searching your Sansa, you will get a bunch of music files in the middle box, like so:

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag3.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag3.png)

As you can see, I've basically got all of my music tagged, thanks to this nifty program (please ignore the comment box, lol).

If you have an internet connection, you can have all your tags in an album tagged magically for you. To do so, highlight the album, and press "CDDB Search File(s)...", and click it. It looks like this:

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag5.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag5.png)

A box will come up with results, and you can select whatever you desire.

If, for some reason, the client can't find a album match, can't find jack crap, or you don't have an Internet connection, you can manually change the tags to your liking.

Fill out whatever you wish with the far right box, with such things like Title, Album, etc - in there text files next to them.

For mass manual tagging, highlight the album, and fill out info like Album, and Year, whatever - then click the little box next to it.

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag6.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag6.png)

Make sure to check individual files to make sure you mass tagged correctly.

When you are done tagging, the files will turn red, indicating that you need to save the files. To do so, highlight your album or files, and File and Save File(s)... ...

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag7.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag7.png)

I'm not exactly what Force Save does. If you come across a problem, go for it and try it, but I've had no need for it.

Little boxes will come up, and ask if you really want the file saved. If your confident (or just want to hurry and get this crap done), click the box that says something about repeating the process, then press Yes. Your files won't look red anymore, if done successful, and congradulations - you have v2 tags on your player!

And, in case you want to change the file name while in EASYTag, you can change it here:

[http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag8.png](http://i3.photobucket.com/albums/y88/cheaptrick905/v2tag8.png)

That about wraps it up. Make sure you save tags (when I first started learning the program I didn't know I needed to go to File and all that to save them, I spent frusterated hours wondering what in the hell was wrong with it) like I showed you, make sure all the tags like Album and Artist match if you do it manualy, and you should be set.

And please, FOR THE LOVE OF GOD, make sure you unmount your Sansa player, so all the info can be written into the player successfully.

I have heard complaints of people changing tags in there Sansa players, and after unmounting and letting the database refresh on there player, there are still no tags. Even though that is not the case for me - I've been saving tags within the Sansa since day one, I'm not sure what everyone else is talking about here - you might need to transfer music on your hard drive and write tags there. Or, if they are already on the hard drive, just write them there.

Have fun!

---

### Post by SZF2001 on 2007-01-17
Oh my God I just realized you wanted a solution for playlists and not for EASYTag.

](*,) 

I'm making a new post because I am going to link the last post I made on the tutorial, and it wouldn't make much sense reading all this on that post when people just want to read about EASYTag and not playlists.

Sadly, I have had no success with any sort of playlist. Even when I try to default .plp or any other playlist extention, Sansa has never recodnized any sort of playlist. Sorry, mate. Maybe Zwack would know...

---

### Post by takayuki on 2007-01-17
szf2001 and everyone,

thanks for the sansa how-to and info.

do we have confirmation that video does work?

takayuki

---

### Post by pdog on 2007-01-17
Thanks for the reply "SZF".  It seems there are two issues with playlists. One is creating your own customized list in the file where the "Go" list is, second is the simpler matter of having albums play songs in the order they exist on the album.  I notice that Cowbell ( and perhaps the other tagging programs as well?) creates an m3u file that resides with the individual song files of an album that tranfer to the sansa.  When I read this file in text mode, it seems to be mostly a listing of the songs - in order.  I'm speculating that the sansa used as a mass storage device (as we use it) needs a mechanism (script?) to tell it what order to play the files in a folder, without which, it defaults to reading files in alphabetical or numerical order.  If this is the case, what we really need is a script or program to convert our tagging program's m3u files to sansa's preffered .pla or .pls (I'm not sure).  Once again SZ, thanks for the significant amount of time you've put into this project.  The music does sound good.     P.

---

### Post by Ubuntu Joe on 2007-01-17
Just for fun, I've tried editting the "Go" playlist we all have on our Sansas . . . Within gedit, I've added tracks paying strict attention to the path to each file, and when I saved it back to the Sansa . . . it rewrote itself back to its original default!  WTF, I say . . .

Please, someone get video working . . . SanDisk people don't even know how it works . . .

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Zwack on 2007-01-17
Sorry I haven't replied recently...

I haven't played with playlists yet... Nor have I tried the mencoder-fu that was suggested for getting video to work.

My understanding about tracks playing out of order is that it was an issue with earlier firmware.  The player does need to know what order to play them in though, and I believe will try two sources (both are valid for my files and mine play in order).  First if you have a track number stored in the mp3 file tags then it will follow that order.  You can set those easily with Easytag.  Secondly you can name your files 01-name.mp3 or something similar and they will be played in order.  My files are tagged for the Sansa and other tag aware players and named <track number>-<artist>-<title>.mp3 so that I can look at them and work out what they are.  You can even use EasyTag to change the file names too.

I hope that this helps,

Z.

---

### Post by pdog on 2007-01-17
Z -

Thanks for the tips.  Unfortunately, nothing worked- the sansa still displays album songs by alphabetical order of the song title, even though in the device folder (Music/Artist/Album) the songs are clearly labeled with a track number and (-) before the song title.  In EasyTag (v.1.99.11), under File, I chose "sort list by tag" then "ascending by track number".  I'm using the latest firmware (01.02.15A, with my tail between my legs I used a friends windows box).  I'm going to try and contact Sandisk about this.  I see that you are using 6.10 and I 6.06 which shouldn't make a difference.  What firmware version are you using?   Thanks again.   P.

---

### Post by SZF2001 on 2007-01-18
At this point it really seems like it's the tags, mang. I'm serious.

Make sure that EASYTag can write v2 tags in your options, and to get the information for every song filled out in the right text boxes.

That was exactly my "problem" a while back, I didn't realize it was the tags. Even the SanDisk support said that - then they proceeded to tell me I could only make a Sansa work on Windows. Lol. But anyway, ya... Really, check your tags.

---

### Post by Zwack on 2007-01-18
> **pdog said:**
> Z -
  I see that you are using 6.10 and I 6.06 which shouldn't make a difference.  What firmware version are you using?   Thanks again.   P.

I'm using the latest firmware for the e2x0r series... Sorry it's not the same.  But I'm wondering about the tags.  Can you load EasyTag and try tagging one album to see if that makes a difference.  It  might also help to remove the database, or do the renaming not on the player as we have had mixed reports of it's ability to pick up changes.

Z.

---

### Post by Ubuntu Joe on 2007-01-18
Yeah . . . Within your Sansa Go:  System -> Data, and delete the contents of this folder . . .

And someone get video to work . . . :(

---

### Post by SZF2001 on 2007-01-18
Ya, try changing the tags on a hard drive first (or somewhere else, I suppose) if your Sansa doesn't read it immediatly. Good luck.

---

### Post by pdog on 2007-01-18
Z &SZF,

Thanks for all your help.  I have been doing all that you suggest (I always tag on the PC, not the device).  I have also been anal about purging sansa's "System  " file (and "trash").  On EasyTag I tag one album ("select all", sort by "ascending order") and save it (v1&v2 or v2 alone make no difference).  Always the same results, Album and Artist recognized, songs in neat alphabetical order. Are tags on the mp3 song file itself or somewhere else?  I've tried gedit but it cant read the file.  Thanks again.  If I find a solution I'll post back.  Good luck with the video.

P.

---

### Post by pdog on 2007-01-18
Oh, I forgot thanks to saalota too!

P.

---

### Post by pdog on 2007-01-19
Problem solved.  Your hunches were all correct.  After educating myself via net on the nature and location of id3 tags I downloaded Audio Tag Tool via Synaptic.  It clearly and elegantly allowed me to see which tags- id3v1 & or id3v2 were present or not on my individual songs.  Suprisingly, to me, the songs only had id3v1.  I used Tag Tool to copy the info to the id3v2 format (id3v1 is at the end of the mp3 file, id3v2 resides at the beginning, so they don't conflict).  I'm not sure why EasyTag didn't copy v2, but at least now I can trace my mistake.  Cowbell, the default, compiled tagging app. for 6.06 apparently only writes in v1.
Thanks again.  Now what about this video question?

P.

---

### Post by Ubuntu Joe on 2007-01-19
Guys, I have to be honest . . . I use a winBLOWS box at work, right?  Well, I wanted video on my Sansa (and pictures) that I installed SanDisk's crappy "Sansa Media Converter" software, and *IT* didn't even work!!  WIth the pictures, it says:

"Unable to transfer to device"

What, why?  No idea . . .

AND with the video, it says:

"Unsupported file name"

Trampoline.mov is an unsupported file name?!  WTF?!

So I call the fine, fine "technicians" at SanDisk . . . They have not a clue about this issue, but say it happens to people all the time . . . and they will send me an updated version of the software in the mail . . . nowhere to download it online.

Bizaar.

---

### Post by SZF2001 on 2007-01-19
For one thing, I've heard that some people can't get there Sansa's connected with the Media Converter thingy, for some reason. *But*, it seems like you can still convert movies and they will show up in a place like "My Videos" or something (seriously I haven't been on Windows forever so please forgive me).

Maybe instead of converting directly to the Sansa you could just do it that way and manually put the file in the MOVIES folder.

Also, you say your doing this at work - so maybe you don't have all the administraitive rights? That might be something to look into. Unless you are pretty damn sure you **know** you have the rights, sometimes programs just won't work.

EDIT: Has anyone been able to get the media converter to work in Wine or Crossover (some kind of name like that)? Maybe that would solve our movie woes... I've tried the installation through the flash installation that comes through the CD, but it never even takes me to the installation prompts - so maybe there is another *install* like file that we could try...

---

### Post by ed_d on 2007-01-20
SMC only goes so far on install using wine on mine. Hangs loading quicktime.
As far as SMC on window$, has to be XP as far as I can tell.

Love this thing. Go sansa!

Oh, and rumor has it a 4 gb microSD is coming out that will work with the e200s......

---

### Post by SZF2001 on 2007-01-21
...Is there anything else that should be covered in the beginners guide?

Should I go through with an intermediate and advanced guide?

Anything at all? It seems like almost everything is covered. With the exception that I don't have the Rhapsody version, so maybe I didn't get everything right for those users...

---

### Post by Ubuntu Joe on 2007-01-22
I'd love an intermediate/advanced guide!

:lolflag:

---

### Post by agustin.g on 2007-01-23
could anyone be so kind as to send me the sample pics? i had some trouble with the 1.03.01H BETA firmware (not reccomended) so i formatted the unit but forgot to back up the pictures (the music's fine though)

cheers,
agustin

---

### Post by fedora389 on 2007-01-27
Here Is A xine Stream Sheet For Sansa  Video That I Converted With There Software
I Can Get DeVeDe To Filp It With Your Comand But It Only Goes To Final size 352X288
as You Can See The Xine Stream Said The Size Is 160X208 Real hope some one can get this right
I hate to have to Switch back to windows to convert video heres what i got

[ATTACH]23978[/ATTACH]

[ATTACH]23979[/ATTACH]

---

### Post by Zwack on 2007-01-27
Converting video is tricky as the codecs have to be just right.  The exact codecs are not supported fully in Linux yet (although it is possible that someone is working on it.  Doing some things (such as resizing and rotating) is relatively easy.  Converting to the exact format is much harder.  

Somebody suggested a command which works for him but I can't get it to produce a valid output file.  The closest I've managed so far is this...

```
mencoder -ofps 15 -vf rotate=1,scale=160:208 \
-ovc lavc -lavcopts vcodec=mjpeg:vbitrate=150:mbd=1:gray \
-oac pcm -srate 11025 \
-of lavf -lavfopts format=mov:i_certify_that_my_video_stream_does_not_use_b_frames \
<input file> -o <output file>
```

But it doesn't work on my e250r...

I'm also poking around with bitmap formats at the moment as that is a more interesting issue to me...  

Z.

---

### Post by Ubuntu Joe on 2007-01-29
Well it looks like microSD works fine on this little device, but as always there are a few wrinkles to discuss:
 
Getting music onto the card is easy enough: You insert the microSD card into your Sansa; plug it into your computer, then voilà! You now have *two* USB disks on your desktop (I'm using Edgy Ubuntu, I assume Kubuntu does something similar.) Now make a folder called "MUSIC" (you have to do this,) and fill it with your tunes. No problems at all. I assume when someone figures out how to address picture/video editing, one can also create a "PICTURE" and "VIDEO" folder to populate as well . . . Dismounting both disks is a little clumsy . . . No matter which you dismount first the other is kinda dismounted as well, but the icon remains confusing both you and Ubuntu. But, ultimately, it doesn't really hurt the device so long as you stand on ceremony and dismount them both dutifully . . .
 
Some issues:
 
When you put the little microSD in the side of the device, the Sansa takes a second to load the music from the device . . . This also happens *every time* you turn the device on. So, if you have your microSD in the player, leave it idle long enough to turn off automatically, and then turn on the player, it will load the card's data from scratch. Annoying. I have a half full 1 GB microSD . . . it takes about *5 minutes* to load the 260 audiobook tracks . . . yikes . . . I find that you can side step this annoyance by popping the card out first, turning the device on, find the music/podcast to which you want to listen, playing it, *THEN* pop the micro in all the way . . . at least you can listen to something while it's doing its thing . . . otherwise you're waiting the 5 long minutes in painful silence . . . sigh . . . I'm also pretty certain my card has "misplaced" some of my tracks, as well . . . That's frustrating . . .
 
Quick disclaimer, I have, perhaps, the *cheapest *microSD available (the CORSAIR 1GB MicroSD Flash Card Model CMFSDMICRO, only $16 on NewEgg.com . . . I can't really complain,) so, this all may be due to the crappy quality of my card . . . I'll get back to you on that.
 
For the most part, this added layer of functionality/customizability is certainly an overall ***PLUS ***if you're deciding whether or not to get one of these little devices . . . you can get the microSD is as much as 2 GB. . . but those guys are pretty expensive. Remember the CORSAIR 1GB for $16? The 2 GB version is $61 on NewEgg.com!! WTF!
 
:guitar:
 
 
 
****UPDATE****
It seems my constant popping in/out of the micro was the cause of the "lost" files . . . They weren't *lost* per se . . . rather they were *fouly*corrupted . . . Very strange stuff . . . I have to put the micro into my Treo just to format it!! Now it seems to be fine . . .

---

### Post by SZF2001 on 2007-02-02
Anyone got anything on movie formatting? Even pictures?

---

### Post by Zwack on 2007-02-02
> **SZF2001 said:**
> Anyone got anything on movie formatting? Even pictures?

Pictures are 16bpp bitmaps.  The gimp doesn't handle them but someone on anything but Ipods mentioned a perl script to change the bitmaps.

I haven't been able to find it and the python script I found doesn't work very well... Oh well, time for me to learn more...
Z.

---

### Post by Zwack on 2007-02-03
Well, I have Photos working... Sort of.  I still need to do more to make it usable, but I have hacked the python program I found to produce 5-6-5 16 bit per pixel bitmaps.

And it works, but I think I'll spend a little time writing a version from scratch for three reasons...

1) I don't know the copyright on the program I found online so I don't feel comfortable releasing a hacked version of it.

2) The resulting bitmap is upside down

3) The resulting bitmap is back to front.

So, I'll write a program from scratch to flip the bitmap while I'm fixing the colours and try it with a few samples.  Once I've got that working I'll post it.  You'll still need to use another graphics program to produce a 24bpp bitmap of the size you want before you run it through the python script.

Z.

---

### Post by Zwack on 2007-02-07
Photos!!!

Not just me, but several people have written photo conversion utilities in the last few days.  If you want something else go to the Anything but ipod forums and look at the offerings.  

However, here is my option.  It's a simple python script (I needed an excuse to learn python) and it converts a 24bpp bitmap into a 16 bit one suitable for the Sansa (if you read the script it also flips it vertically and then multiplies the height by -1, don't ask me why, but that gives the right results and if you check the bitmaps that came on the sansa they all have negative heights)...

Anyway, here you go...

Z.

---

### Post by Ubuntu Joe on 2007-02-08
Lowest common denominator here . . .

How do we use the script?

\\:D/

---

### Post by Zwack on 2007-02-08
There is a readme inside the zip file... It's the file called Usage.

But simple answer, unzip the file and you will have four files.  Put them in the same directory (whichever that is) then make sure that all of the .py files are executable...  You will need to have Python installed, but it's "important" so it's probably already installed.

Open a terminal, change to that directory and type "chmod a+x *.py" to do that

The four files are Usage which contains instructions, BMPclass.py which is a bitmap class definition used by the other two programs, bmpinfo.py which just reports information about a bitmap and bmp2sansa.py which is the actual conversion script.

If you're interested in looking at the header information in a bitmap just run bmpinfo.py <name of bitmap>

Otherwise... 

Take your graphics file and convert it into a 24 bits per pixel bitmap file.  I use GIMP for that.  You might also want to change the size so it fits in 176x224.  You may want to rotate it while you're changing the size.  But that's your call.

Once you have a bitmap to convert you run 
bmp2sansa.py <input_file_name.bmp> <output_file_name.bmp>
Then you just copy the output file onto your Sansa in a sub directory of the PHOTO folder.

For example suppose you had a file called James.bmp and you wanted it in an album called Jimbob, you would convert it like this bmp2sansa.py James.bmp James2.bmp
and then copy James2.bmp to <sansa>/PHOTO/Jimbob/James.bmp

You could also type bmp2sansa.py James.bmp <sansa>/PHOTO/Jimbob/James.bmp

I hope that this makes sense.  

The Sansa expects photos to be arranged in Album folders underneath /PHOTO/ so let's give it what it wants.

If you have any further questions, don't hesitate to ask.

---

### Post by Ubuntu Joe on 2007-02-09
Thanks, bro, this totally clears it up for me, and I can't wait to try it . . . do they *have* to be .bmps though?

:popcorn: 
(wtf!)

---

### Post by Zwack on 2007-02-09
The Sandisk guys have done a fabulous job of confusing the entire issue...

For Album Art the Sansa can handle Jpegs or BMPs, but for Photos it can only handle BMPs.  My advice would be to store whatever format you want of images, and deliberately convert images that you want to carry on your Sansa to bitmaps, keeping the originals, but shrinking/rotating the bitmaps to save space on your Sansa..

Z.

---

### Post by barthel on 2007-02-10
> **pdog said:**
> Problem solved.  Your hunches were all correct.  After educating myself via net on the nature and location of id3 tags I downloaded Audio Tag Tool via Synaptic.  It clearly and elegantly allowed me to see which tags- id3v1 & or id3v2 were present or not on my individual songs.  Suprisingly, to me, the songs only had id3v1.


Unfortunately, I have the same problem: all tracks are sorted by title instead of by track number. On the off chance that eyeD3 was giving me a bogus readout, I installed tagtool as well. Here's the output on a sample track:

```

$ eyeD3 103-junk_food_junkie.mp3

103-junk_food_junkie.mp3        [ 2.85 MB ]
--------------------------------------------------------------------------------
Time: 3:05      MPEG1, Layer III        [ ~128 kb/s @ 44100 Hz - Joint stereo ]
--------------------------------------------------------------------------------
ID3 v2.3:
title: Junk Food Junkie         artist: Groce, Larry
album: Dr. Demento: 20th Anniversary Collection         year: 1991
track: 3
$ tagtool --dump 103-junk_food_junkie.mp3

File type: MPEG Audio

First frame found at 0x000000A1 (header: 0xFFFB9064):
MPEG type   : Version 1.0, Layer 3
Bit rate    : 128 kbps
Sample rate : 44100 Hz
Channel mode: Joint Stereo
Copyrighted : No
Original    : Yes

---- ID3 v1 ----

TIT2 (Title/songname/content description)
        Junk Food Junkie
TPE1 (Lead performer(s)/Soloist(s))
        Groce, Larry
TALB (Album/Movie/Show title)
        Dr. Demento: 20th Anniversary
TYER (Year)
        1991
TRCK (Track number/Position in set)
        3

---- ID3 v2 ----

TSSE (Software/Hardware and settings used for encoding)
        LAME v3.96.1
TIT2 (Title/songname/content description)
        Junk Food Junkie
TPE1 (Lead performer(s)/Soloist(s))
        Groce, Larry
TALB (Album/Movie/Show title)
        Dr. Demento: 20th Anniversary Collection
TYER (Year)
        1991
TRCK (Track number/Position in set)
        3

$

```

Any ideas?

I just got my e250 on Thursday and am pretty satisfied. This isn't a show-stopper glitch for me--just an annoyance. (Although I'd be even happier if I didn't have to re-encode my music to MP3.  But do I really want to go the rockbox route....) 

TIA,

Barthel

---

### Post by Zwack on 2007-02-10
I don't see anything different about the outputs of those tools compared to one of my tracks...
Nothing that might cause problems anyway...
But what do I know...

Here's one of my tracks that works properly...

in eyeD3:
```

arm10@rogue:~$ eyeD3 /var/music/Raven/A_Soft_Wind_Blows/09-raven-chronologically_gifted_and_bony.mp3 

09-raven-chronologically_gifted_and_bony.mp3    [ 3.59 MB ]
--------------------------------------------------------------------------------
Time: 3:55      MPEG1, Layer III        [ 128 kb/s @ 44100 Hz - Joint stereo ]
--------------------------------------------------------------------------------
ID3 v2.3:
title: Chronologically Gifted And Bony          artist: Raven
album: A Soft Wind Blows                year: None
track: 9/12             genre: Celtic (id 88)
arm10@rogue:~$ 

```
and in tagtool:
```

arm10@rogue:~$ tagtool --dump  /var/music/Raven/A_Soft_Wind_Blows/09-raven-chronologically_gifted_and_bony.mp3 

File type: MPEG Audio

First frame found at 0x000003C3 (header: 0xFFFB9064):
MPEG type   : Version 1.0, Layer 3
Bit rate    : 128 kbps
Sample rate : 44100 Hz
Channel mode: Joint Stereo
Copyrighted : No
Original    : Yes

---- ID3 v1 ----

TIT2 (Title/songname/content description)
        Chronologically Gifted And Bon
TPE1 (Lead performer(s)/Soloist(s))
        Raven
TALB (Album/Movie/Show title)
        A Soft Wind Blows
TRCK (Track number/Position in set)
        9
TCON (Content type)
        (88)

---- ID3 v2 ----

TIT2 (Title/songname/content description)
        Chronologically Gifted And Bony
TPE1 (Lead performer(s)/Soloist(s))
        Raven
TALB (Album/Movie/Show title)
        A Soft Wind Blows
TRCK (Track number/Position in set)
        09/12
TCON (Content type)
        (88)
TLEN (Length)
        235000


```

I see some differences, but nothing that concerns me too much.  I'm wondering if the TSSE header confuses it.  

Oh, and as for Rockbox... Ummm... the Audio Codec doesn't work yet, so you don't want to go there yet.

Z.

---

### Post by Ubuntu Joe on 2007-02-11
EasyTag has been perfect for tagging . . . I've never had a single issue.  The Sansa *always* to EasyTag's tagging.  Get EasyTag!

:popcorn:

---

### Post by Ubuntu Joe on 2007-02-11
Grrrrrr . . .

```
thom@ubuntu-joe:~$ cd ~/PhotoScript
thom@ubuntu-joe:~/PhotoScript$ bmp2sansa.py Em03.bmp Em03.bmp
bash: bmp2sansa.py: command not found
thom@ubuntu-joe:~/PhotoScript$ 



```

---

### Post by SZF2001 on 2007-02-11
I'd have to agree, EasyTAG seems to be the way to go. Tags started working with it and I've never looked back...

---

### Post by Zwack on 2007-02-11
> **Ubuntu Joe said:**
> Grrrrrr . . .

```
thom@ubuntu-joe:~$ cd ~/PhotoScript
thom@ubuntu-joe:~/PhotoScript$ bmp2sansa.py Em03.bmp Em03.bmp
bash: bmp2sansa.py: command not found
thom@ubuntu-joe:~/PhotoScript$ 



```

Easy fix...
./bmp2sansa.py  ...

It's not in your path so you have to say run it from here.  (. being the current directory)

Someone reported an error in the script, but it works for me, so I'd appreciate knowing that it worked.  (or not).

Z.

---

### Post by fedora389 on 2007-03-01
(Formating a sansa E260R)

This is how I formated my sansa E260R on ubuntu edgy 6.10 I pluged it in unmounted it with 
GParted then in terminal I used this command :

sudo mkdosfs -F 32 /dev/sda1

Then inter your password . Worked for mine.
There is one drawback to this now when I plug it in it pops up on desktop as (usb1)
it use to say (SANSA E260R). But it did format it an erase it to start fresh.
For some reason GParted would not format it. It kept saying it had a error. I used GParted to
unmount it tried just ejecting it but it would not format it that way.
Hope this help somebody.

---

### Post by Zwack on 2007-03-04
> **fedora389 said:**
> (Formating a sansa E260R)

This is how I formated my sansa E260R on ubuntu edgy 6.10 I pluged it in unmounted it with 
GParted then in terminal I used this command :

sudo mkdosfs -F 32 /dev/sda1

Then inter your password . Worked for mine.
There is one drawback to this now when I plug it in it pops up on desktop as (usb1)
it use to say (SANSA E260R). But it did format it an erase it to start fresh.


You might want to try adding -n "SANSA E260R" to the mkdosfs string. I don't know if that is the string used by Sandisk, but it seems likely.

Z.

---

### Post by SZF2001 on 2007-03-22
Does anyone know anything about adding pictures yet? Or... album photos when a song starts playing? I'm getting kinda tired of the blue wave screen when you play a song...

---

### Post by Ubuntu Joe on 2007-03-23
Finally!  A question I can answer!

It's very easy to add album art to your songs through EasyTag.

First of all take your .jpg and crop it to exactly 300x300 pixels . . .

Got it?  Good, now open up that awesome EasyTag editor, select the appropriate album, switch over to the Album art tab, add the .jpg, tick the box so all the files get the image, and you're done!

BAM, beautiful, images to accompany your tunes.

:guitar:

---

### Post by SZF2001 on 2007-03-24
Awesome! Thanks man.

I think I'll add that to the guie and quote you off it, if you don't mind (give you credit).

Uh... Man it's been forever since I've updated it or anything... Any new information that should be known for this? School has been a pain in the ***, but now I've got easier classes and the admins FINALLY gave me permission to use the Ubuntu Forums at school...

---

### Post by Greeface on 2007-03-25
To add album art you can also make folders for all of your albums then drop in a jpeg of the album art named 'folder.jpg'

---

### Post by SZF2001 on 2007-03-26
I just found out that not all album art pictures HAVE to be 300x300. But they DO have to be .jpg. Just make sure your Sansa refreshes the data base.

---

### Post by Ubuntu Joe on 2007-03-26
I just have to say again, this little device is so super sweet . . .

---

### Post by SZF2001 on 2007-03-27
It seems to work well with Ubuntu once you get the hang of things. But I gotta ask, since I've never used it... Is iTunes really really REALLY that much worth of praise it gets along with the iPod? I mean, it must tag everything, organize, and even serve you breakfast to make people so happy...

Man. People would make the switch to Ubuntu (and Linux in general) if they made a working version of iTunes for Linux. Wouldn't that make sense - I mean, you are still selling iPods and making money, so why hold a grudge or have a bad attitude against Linux and just make some money? That's all they really want... right?

Not that I am considering buying an iPod. It's just... Doesn't this whole guide seem a little overwhelming for new people? They just wanna listen to their music, man. I honestly don't see what the big deal about the iPod is, my Sansa works just fine, but still... I know a LOT of people who still cling on to Windows or Mac because of their precious iTunes...

And yes I know about GTKPod and Banshee, sillys. But still.

---

### Post by grndslm on 2007-04-14
I just bought an e280, the 8 gig version, from Buy.com for $145....

What do you guys think about the sound quality?

And what is the status of Rockbox on the e200 series??  Is it worth installing now, or should I give it another year or so?

  -Thanks!

---

### Post by SZF2001 on 2007-04-16
Haven't tried Rockbox yet, but I hear it's still in Beta with the Sansa so I would go against installing it for now (unless you plan on developing it/tinkering it/etc).

The best sound quality on the Sansa, imho, is to set the EQ to the "Rock" setting. Seems pretty nice, to me anyway.

---

### Post by Ubuntu Joe on 2007-04-16
I'm with you, Baby with the Boom . . . APPLE, FOR THE LOVE!!!  MAKE ITUNES FOR LINUX!!!!!!!

---

### Post by showcaser on 2007-04-22
Hi and thanks for the guide. Just thought I would mention that it appears ripping with K3B sets the tags properly. Tried it with two albums so far and I was able to copy paste to the sansa without adjusting the tags with easytag. Has anyone else noticed this?

---

### Post by SZF2001 on 2007-04-23
@showcaser: Good point, I never did notice that. I'm pretty lazy as of now, so I'll credit you and add that information in a little while. Does it also do album art?

And get this... I can't find my Sansa. This sucks. I think this one guy stole it but I can't wriggle that info out of him...

---

### Post by showcaser on 2007-04-23
Sorry to hear that your sansa got stolen, that's a real bummer!

Doesn't look like K3b does album art, although I haven't done a terribly thorough search. I'll post something if anything comes up on that end. I should also mention that to put the track # tag you have to add"--tn %n" to the lame encoding settings. Essentially just click the little gear button in filetype where you select "MP3(Lame)", click edit, and add the "--tn %n" to the end of the long text with all the '%'.

---

### Post by timczer on 2007-05-30
For those still looking for a way to get playlists onto their sansa, I found this script by "Gratt" on the anythingbutipods forum.  There are three scripts in the folder.  The sansa-m3u2pla script works great.  You have to update the script with the mount point of your sansa, and the location of your m3u files (the script is documented well so you can find where to do this).  Run the script and it converts the m3u and puts it on your Sansa and appears to take the album art with it.

---

### Post by SZF2001 on 2007-06-14
Anything I should do to or for the tutorial?

---

### Post by Fernanernie on 2007-06-21
Thanks for the great guide. I should've looked here first :D

---

### Post by aldodefilippi on 2007-06-24
SSS002 Disconnecting your Sansa e200 player from Ubuntu (or any Linux) computer

~THIS IS VERY IMPORTANT~ Think about it. After a few hours work, writing tags and changing files, wouldn't you hate to accidentally lose that information?

To disconnect the player, you can rather A: go on the Ubuntu desktop, right click the player, and press "Eject". A window should come up, tell you it's writing info on your player, and then there won't be an icon. Even though your player still says "Connected", the little arrows should be gone and you can be good to go. Or, B: find another way of unmounting your player, rather through the terminal or whatnot. I'm not very experienced in using other Linux OS's, so just make sure your player is NOT mounted before unplugging it.

I have a Sansa e280 Mp3 player and Ubuntu.OS.  I don't know what I'm doing wrong but for some reason I can't seem to find the "Eject" function when I right click the player on my desktop....After I paste the cd recordings into the player music file the player states "writing" but never goes off.

---

### Post by SZF2001 on 2007-06-25
Which Ubuntu OS are you talking, here? There is Ubuntu, then Kubuntu, Xubuntu, Ubuntu Studio...

Basically, what I need to know is - are you using the default GNOME desktop environment, KDE, or XCFE?

---

### Post by aldodefilippi on 2007-06-25
I am using Ubuntu Feisty. Standard Gnome desktop. Regards,

---

### Post by SZF2001 on 2007-06-27
Hmm... I'm not sure exactly whats up. I'm sure Zwack would know, but he doesn't have a good reason to come back to the thread...

Maybe you could PM him?

And just so everyone knows, my Sansa wasn't stolen, just hidden under my mattress.

---

### Post by encleadus on 2007-08-04
Hi,
Just wanted to say that the step of adding a blank text file named .is_audio_player to the root directory in order for Rhythmbox to recognize the player worked for me with a Sansa Express 1GB model on Fiesty 7.04. Thanks for the guide!

Cheers

---

### Post by Jeff Gavett on 2007-08-13
I'm looking at this to use for the voice recording in a big way, recording voice lessons and other music lessons. Is it high enough quality for this? Do you think any one of you could post a sample of what the recording quality is like with musical source? Thanks!

---

### Post by Jiiprah on 2007-08-22
**@ Jeff Gavett**
All i can say is that the mic is super sensitive. just don't shuffle around with the player. it picks up, just the press of the Sansa button and makes a loud noise.

**@ SZF2001**
Setting the music EQ on "rock" sounds like someone shoved a towel into the speaker. I prefer the normal setting.

**Photos:**
I followed the specs for a sample image and made an image in gimp. But it still could recognize it, i must have don't something wrong.

**Thank You So Much:**
I had a problem with my mp3s. They wouldn't organize into artist and album categories. I use Rythmbox to edit the tags but it didn't work. Then i found this post. I installed Easytag through Automatix and edited the tags in that. And it worked. Thank You!!!

---

### Post by jollemeyer on 2007-08-26
Just my 2 cents on how I got my tags working:

[http://ubuntuforums.org/showthread.php?t=527725]("http://ubuntuforums.org/showthread.php?t=527725")

I basically used eyed3 to convert id3v1 to id3v2.3.
I could do a mass conversion with this tool.

---

### Post by SZF2001 on 2007-10-08
[center][img]http://www.rockbox.org/rockbox400.png[/img]

[SIZE="4"]RockBox for your Sansa e200[/SIZE][/center]

I did not create these instructions. I give full credit to the [Anything But iPod](http://www.anythingbutipod.com/forum/showthread.php?t=18258) forums, and their Rockbox FAQ. I am just posting in this topic to make sure we have RockBox details down.

This post is as of Monday, October 08, 2007 - details could change drasticaly if you are reading this two years from now, or something.

**[SIZE="3"]Installation[/SIZE]**

We will be discussing the *Manual* way of installing Rockbox - there is a GUI version to use, but the manual install is usually a better bet and you can watch your progress for any mistakes.

 - You will need to be able to have your e200 connected with a USB cable into your computer to read and write information.
 - You will need to be able to archive and extract .zip files from the Zip archiving scheme.

Here are the following steps with the *Manual* procedure:

 1: Grab the [Current Rockbox Build](http://build.rockbox.org/) for the e200 player.
 2: In the root directory of *your e200* (NOT the root folder), extract the build. Make sure it isn't in any MUSIC folders or any other folder beside the main directory of your Sansa. (Make sure your USB mode is on MSC) - if done correctly, your root Sansa folder will have a /.rockbox folder. If you receive a &#8220;-1&#8221; error when you start Rockbox, you have not extracted the contents of the .zip file to the proper location.
 3: Grab the Bootloader ([Right click and save as this file if you are running a 32-bit system,](http://download.rockbox.org/bootloader/sandisk-sansa/sansapatcher/linux32x86/sansapatcher) OR [right click and save as this file if you are running a 64-bit system](http://download.rockbox.org/bootloader/sandisk-sansa/sansapatcher/linux64amd64/sansapatcher)).
 4: Again, make sure the e200 player is connected to the computer.
 5: In a root terminal (or with root permission, such as *sudo*), point your directory to the Bootloader (using the *cd* command). Then, type this out:
```
chmod +x sansapatcher
./sansapatcher
```
 If it is able to catch your Sansa player (and it will let you know), follow the script commands (press *i* to install, then *ENTER*, etc, it's pretty easy).
 6: If you have recieved no errors, congradulations - you have succesfully installed Rockbox on your Sansa e200! You should be able to unplug your Sansa (make sure to unmount!) and see the Rockbox splash screen, then do as you please.

To uninstall, follow the steps backwards (you will need that script again to uninstall the Bootloader, after which just delete the /.rockbox folder).

If these steps are not clear to you, or you want to try the GUI, [go here](http://download.rockbox.org/manual/rockbox-sansae200/rockbox-buildch2.html#x4-60002). There is various information on running your new Rockbox and the automated method of installation. Good luck!

**[SIZE="3"]Transfering Files with Rockbox on the Sansa e200[/SIZE]**

[Thanks for the post!](http://ubuntuforums.org/showpost.php?p=2631149&postcount=1)

If you don't understand what that post means, it's really simple - before you connect the Sansa to your computer through the USB line (with MSC), you need to hold down the left button of the four direction buttons by the navigation wheel. It will, at first, show Rockbox booting up, and it realizes it's on a USB line so it switches back to the default firmware of the Sansa. At this point, you can either NOT hold down the button and simply charge the Sansa, or if you hold down the left button, will connect with the computer for file transfering.

---

### Post by MONODA on 2007-11-15
when i plug my sansa e260 in i cant view it on my computer and on the sansa screen it says disconected.

---

### Post by barry_vancouver on 2007-11-19
my Sansa e280 had no problems being instantly recognized and mounted on my laptop with Feisty Fawn. 

My Desktop PC with Gutsy 7.10, however, refused to mount the device...unitl I typed the following command into Terminal:
 sudo modprobe -r ehci_hcd


I found this command trolling Google and ubuntu forums on and off the last few days for any advice relating to Sansa usb drives and mp3 players...

Give it a go!  Worked beautifuuly for me on Gutsy!! :d

Now I can sleep!!

---

### Post by la3875 on 2007-11-23
Tried the script in the terminal on Xubuntu 7.10, and no joy for my Sansa e250... I'll have to give it a go on Gnome next. 

Well still no luck connecting in Gnome either. Might have to go back to Feisty next... Stay tuned

---

### Post by samurai_dave on 2007-11-28
My Sansa was working with Feisty, then I had to do a clean install to Gutsy which screwed things up, and I was getting an error message saying that I didn't have sufficient privileges to mount the device.

This error crept over to my external USB drive which contains all my music (which had been working) making a solution more urgent.

Turns out the problem for me was having an entry in my fstab for an sdc device, the mount point for my USB devices.  Commenting this out fixed the problem for my Sansa and external drive.

I presume the problem was that having a manual definition for a USB device worked when I was only using one, but when I tried the Sansa it freaked out on me.  Gutsy is recognising both of these drives now, so it's worth a go if you're having the same problem.

---

### Post by la3875 on 2007-11-30
Hey samurai_dave you're gonna have to elaborate a little more for a plug 'n play guy like me. When I look into the fstab file i have no scd devices listed. Can you show what your fstab file looks like?

Thanks. This sounds like you've found the fix...

---

### Post by 99bluefoxx on 2007-12-14
> **Zwack said:**
> Converting video is tricky as the codecs have to be just right.  The exact codecs are not supported fully in Linux yet (although it is possible that someone is working on it.  Doing some things (such as resizing and rotating) is relatively easy.  Converting to the exact format is much harder.  

Somebody suggested a command which works for him but I can't get it to produce a valid output file.  The closest I've managed so far is this...

```
mencoder -ofps 15 -vf rotate=1,scale=160:208 \
-ovc lavc -lavcopts vcodec=mjpeg:vbitrate=150:mbd=1:gray \
-oac pcm -srate 11025 \
-of lavf -lavfopts format=mov:i_certify_that_my_video_stream_does_not_use_b_frames \
<input file> -o <output file>
```But it doesn't work on my e250r...

I'm also poking around with bitmap formats at the moment as that is a more interesting issue to me...  

Z.
i tried that one just now, didnt work
heres output
```
bluefoxx@azurE-prIDE:~$ mencoder -ofps 15 -vf rotate=1,scale=160:208 -ovc lavc -lavcopts vcodec=mjpeg:vbitrate=150:mbd=1:gray -oac pcm -srate 11025 -of lavf -lavfopts format=mov:i_certify_that_my_video_stream_does_not_use_b_frames /home/bluefoxx/Desktop/inuyasha_ep_1.ogg -o /media/Sansa e260/VIDEO
MEncoder 2:1.0~rc2-0ubuntu1~feisty1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.93GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option lavfopts: Unknown suboption i_certify_that_my_video_stream_does_not_use_b_frames
Error parsing option on the command line: -lavfopts

Exiting... (error parsing command line)
bluefoxx@azurE-prIDE:~$ 


```
so what did i do wrong?

---

### Post by McNee on 2007-12-18
I bought an e280 a few months back (was on sale at Best Buy for $120). I am not a hardcore user, but it's been nice. 

I'm glad I found this thread... the info here looks very well organized and presented... and it's slick that you are going back and updating the original posting as you get new info.

 I'm looking forward to getting it working well with Ubuntu (I just made the full time switch a bit over a month ago), and just found the info on setting up playlists... which I generally don't use, but really want to get set up this week so I can bring it to my mom's with some powered speakers for Christmas music next week. I have about a dozen Christmas music albums, so will be nice to just put them in a playlist and let it go.

---

### Post by marcordenis on 2007-12-19
As I am an Ubuntu newbie, and I just recently got a Sansa, I wanted to ask if somebody could solve my problem:
When I try to connect to my PC (in Ubuntu) it tells me that it is connected for about one second, then it becomes disconnected again. I my "media" directory I see a folder name "Sansa e280" but when I click on it, it shows it as if it were an empty folder.......Couldn't transfer anything from Ubuntu to my Sansa yet, had to do it using Windows :(
Hope someone can help me........

---

### Post by 99bluefoxx on 2007-12-20
> **marcordenis said:**
> As I am an Ubuntu newbie, and I just recently got a Sansa, I wanted to ask if somebody could solve my problem:
When I try to connect to my PC (in Ubuntu) it tells me that it is connected for about one second, then it becomes disconnected again. I my "media" directory I see a folder name "Sansa e280" but when I click on it, it shows it as if it were an empty folder.......Couldn't transfer anything from Ubuntu to my Sansa yet, had to do it using Windows :(
Hope someone can help me........
try changing the "USB mode" under "settings" to "MSC" instead of "MTP", thats all i can offer
mine crapped out on me today, claims its read only now, i can put around 10 MB of content on it then it becomes read only
 after that or 10 minutes of being pluged in then i have to reboot to do it all over

---

### Post by marcordenis on 2007-12-20
> **99bluefoxx said:**
> try changing the "USB mode" under "settings" to "MSC" instead of "MTP", thats all i can offer
mr
nope..... didn't work for me..... I formatted (under Windows) and tried again, still doesn't work: it show connected with the arrows , then it shows disconnected, the it shows connected without arrows, then disconnected, and stays that way....
wasn't it supposed to stop at "Connected" with the arrows???

---

### Post by 99bluefoxx on 2007-12-20
hmm, you formatted it you say?i dont know but usually doing that to a DAP is a bad idea in my expirence, i lost my first mp3 player doing that
maybe take it to the store and say it stoped connecting?thats what i would do
if your using 7.10 i have heard some issues with people using this player
search google for "anythingbutipod.com" and try checking theyr sansa forums

---

### Post by marcordenis on 2007-12-21
> **barry_vancouver said:**
> my Sansa e280 had no problems being instantly recognized and mounted on my laptop with Feisty Fawn. 

My Desktop PC with Gutsy 7.10, however, refused to mount the device...unitl I typed the following command into Terminal:
 sudo modprobe -r ehci_hcd


I found this command trolling Google and ubuntu forums on and off the last few days for any advice relating to Sansa usb drives and mp3 players...

Give it a go!  Worked beautifuuly for me on Gutsy!! :d

Now I can sleep!!
thank you for this.......... solved my problem........... I know it's an old post, but I was too lazy to look through 10+ pages of forum and the anythingbutipod forums, but at least I found it
THANKS AGAIN!!!!!!!

---

### Post by SZF2001 on 2007-12-22
Oh my God, I've become so lazy I can't even go back a few pages to look at questions and stuff.

If you really feel like something needs to be added to the guide or have specific questions for me, feel free to PM me, I occasionally log on to the Ubuntu Forums once in a while. I've tried to make the guide as guide-able as possible but I'm not sure what to do anymore. I've switched back to Windows (sorry, extreme problems with wireless on Linux, I don't manufacture the cards and am not made of money, I do like Linux though), so I'm not sure how much help I can be anymore, especially when it comes to the latest versions of Ubuntu.

---

### Post by la3875 on 2007-12-23
Well I tried the sudo modprobe -r ehci_hcd but still no love with my e250. Might have to go back to Feisty because I'm not going to wait for it in Hardy.

---

### Post by marcordenis on 2007-12-23
I suppose you are in MSC mode...... I had to give myself the permission to access my Sansa by going into root......

---

### Post by la3875 on 2007-12-26
Silly me... Put it in MTP mode and it shows up in Rhythym Box and I can drag and drop. Not as seamless that other unnamed companies players or software but it works. One day I'm going to get brave and give Rock Box a try!

Happy Holidays!

---

### Post by MusicMastaMike on 2007-12-27
I just put Rockbox on my Sansa e260, and I'm loving it.  I've created a shell script to convert any ffmpeg compatible video to Rockbox compatible format.  

Download the attached file and extract it.  Put the script wherever you like and make sure it's executable (sudo chmod a+x sansa-convert).  Make sure that you have ffmpeg installed (sudo apt-get install ffmpeg).  Execute the script in a terminal (./sansa-convert) for usage instructions.

Hopefully someone else finds this to be useful.  If you have any questions, feel free to message me!

--Edited script now attached, includes more error checking.

---

### Post by DasCrushinator on 2007-12-27
> **MusicMastaMike said:**
> I just put Rockbox on my Sansa e260, and I'm loving it.  I've created a shell script to convert any ffmpeg compatible video to Rockbox compatible format.  

Download the attached file and extract it.  Put the script wherever you like and make sure it's executable (sudo chmod a+x sansa-convert).  Make sure that you have ffmpeg installed (sudo apt-get install ffmpeg).  Execute the script in a terminal (./sansa-convert) for usage instructions.

Hopefully someone else finds this to be useful.  If you have any questions, feel free to message me!

About to give this ago, but I have a few questions as I set it up:

Does this allow color on the video?
Does the audio work properly?
Do the video and audio stay in sync?

I ask because this has been quite an issue with scripts to convert videos for the sansa with and without rockbox installed on them.

---

### Post by MusicMastaMike on 2007-12-27
> **DasCrushinator said:**
> About to give this ago, but I have a few questions as I set it up:

Does this allow color on the video?
Does the audio work properly?
Do the video and audio stay in sync?

I ask because this has been quite an issue with scripts to convert videos for the sansa with and without rockbox installed on them.

From my tests (I've used some music videos and some other clips), the color and audio work great, and the audio and video have stayed in sync.  Again, the video will only work with Rockbox installed since it is an mpg video.  Let me know if you have any problems with it, I'd be happy to try and help you out!

p.s. I would recommend having the latest version of Rockbox installed if you don't already.

---

### Post by DasCrushinator on 2007-12-27
> **MusicMastaMike said:**
> From my tests (I've used some music videos and some other clips), the color and audio work great, and the audio and video have stayed in sync.  Again, the video will only work with Rockbox installed since it is an mpg video.  Let me know if you have any problems with it, I'd be happy to try and help you out!

p.s. I would recommend having the latest version of Rockbox installed if you don't already.

Awesome!  Never had any luck with video on the Sansa until now.

---

### Post by MusicMastaMike on 2007-12-27
> **DasCrushinator said:**
> Awesome!  Never had any luck with video on the Sansa until now.

Glad it worked out for you!

---

### Post by spamking2000 on 2007-12-29
@MusicMastaMike - 

OK... I'm REALLY hoping this is a stupid question, but I'm going to ask before I give it a try. I'm not familiar with RockBox at all, so I want to make sure I have this straight before I go in an start messing around with anything related to my new Sansa... I'm a Sansa-newb and so far what I've found regarding video on it hasn't been too promising.

OK... I think I'm hearing that if I use your script in RockBox that I can sync the video to my Sansa and it will play on the Sansa. The other way I read one of the posts was that it would just play in RockBox.

I just want to confirm, for myself and anyone else out there who may have possibly been confused:

Does this mean if I use RockBox that I can convert my video media to work on the Sansa?

Thanks a bunch!

---

### Post by MusicMastaMike on 2007-12-29
> **spamking2000 said:**
> @MusicMastaMike - 

OK... I'm REALLY hoping this is a stupid question, but I'm going to ask before I give it a try. I'm not familiar with RockBox at all, so I want to make sure I have this straight before I go in an start messing around with anything related to my new Sansa... I'm a Sansa-newb and so far what I've found regarding video on it hasn't been too promising.

OK... I think I'm hearing that if I use your script in RockBox that I can sync the video to my Sansa and it will play on the Sansa. The other way I read one of the posts was that it would just play in RockBox.

I just want to confirm, for myself and anyone else out there who may have possibly been confused:

Does this mean if I use RockBox that I can convert my video media to work on the Sansa?

Thanks a bunch!

The purpose of this script is to convert a video on your computer to a format compatible with a Sansa e200 series with RockBox already installed.  Many people previously had problems converting videos and keeping the audio and video in sync, but this script does not suffer from that problem.  Does this fully answer your question?

---

### Post by spamking2000 on 2007-12-30
@MusicMastaMike,

I think it does. I checked out Rockbox though and it looks like I would have to load that into the firmware rather than the retail "OS" thats came with the Sansa. Not sure I'm that brave as to tear up my Sansa to put another system on it. I checked out their emulator and it looks pretty basic... might be hard to read when using it hooked up to the stereo in my car while I'm driving.

I'm aware of the video and syncing problems that people have had... just not sure what the best work around is. Even if I installed RockBox, their site says to do it from a Windows machine and I notice the program is .exe... so I'd have to be faithful enough that it would work correctly under wine.

Any idea of a way to do the conversion while still keeping the retail firmware on the Sansa? Or do I really just need to set up a Windows virtual machine (which I've so far been able to avoid)?

To anyone reading - Also, I know people are all anti-ipod, but the Sansa e260 is my first personal media player. I'm curious, I've heard the Zune is made by Microsoft, so I'm guessing MSC mode isn't an option. What about other players? Does the iPod have this problem with video? Are there other players out there that might have been a better choice? I could have sworn I saw one at Office Depot or Office Max that played Divx, but I'd never heard of the brand, and don't remember what it was now. Most of my video is in Divx, so that would have certainly been convienent if it worked.

---

### Post by MusicMastaMike on 2007-12-31
> **spamking2000 said:**
> @MusicMastaMike,

I think it does. I checked out Rockbox though and it looks like I would have to load that into the firmware rather than the retail "OS" thats came with the Sansa. Not sure I'm that brave as to tear up my Sansa to put another system on it. I checked out their emulator and it looks pretty basic... might be hard to read when using it hooked up to the stereo in my car while I'm driving.

I'm aware of the video and syncing problems that people have had... just not sure what the best work around is. Even if I installed RockBox, their site says to do it from a Windows machine and I notice the program is .exe... so I'd have to be faithful enough that it would work correctly under wine.

Any idea of a way to do the conversion while still keeping the retail firmware on the Sansa? Or do I really just need to set up a Windows virtual machine (which I've so far been able to avoid)?

To anyone reading - Also, I know people are all anti-ipod, but the Sansa e260 is my first personal media player. I'm curious, I've heard the Zune is made by Microsoft, so I'm guessing MSC mode isn't an option. What about other players? Does the iPod have this problem with video? Are there other players out there that might have been a better choice? I could have sworn I saw one at Office Depot or Office Max that played Divx, but I'd never heard of the brand, and don't remember what it was now. Most of my video is in Divx, so that would have certainly been convienent if it worked.

Installing Rockbox does not in any way remove the original firmware.  It's basically like having a dual-boot mp3 player.  I found a great how-to on their website that worked perfectly, and it even gives Linux instructions!  I did the manual installation rather than the automated, but there's instructions for both.  Here's the link: _[COLOR="Blue"][http://download.rockbox.org/manual/rockbox-sansae200/rockbox-buildch2.html#x4-60002]("http://download.rockbox.org/manual/rockbox-sansae200/rockbox-buildch2.html#x4-60002")[/COLOR]_

The only weird thing about Rockbox that I've come across is that when I plug it in to my computer to charge it or add music, videos, etc., it boots into the original OS.  This isn't a problem for me, considering it doesn't actually operate while plugged in, just kind of strange.  Also, the MUSIC folder on the Sansa is for some reason hidden, so Rockbox cannot see it.  You can change the permissions, but every time the original OS is booted, permissions are reset.  The best way to get around this is to simply create another folder to put your music in.

Also, from my experience, Rockbox is very easy to configure when it comes to themes (inlcuding colors, fonts, icons, etc.), EQ, etc., and I personally think the sound quality is a tad better than the original OS.

---

### Post by marcordenis on 2007-12-31
imho, the manual install works better than the automated one. I used the method described on this post: [http://ubuntuforums.org/showpost.php?p=3496631&postcount=116](http://ubuntuforums.org/showpost.php?p=3496631&postcount=116)
and it worked very well. 
(By the way, this link is also given on the first page of this thread, under Installing Rockbox)

---

### Post by spamking2000 on 2008-01-01
@MusicMastaMike and marcordenis - 

OK! Thanks a bunch for the help. I wasn't aware of the dual boot, so that might be a better option than I was thinking.

One question though - where do I go for themes? I just want to make sure that whatever I do, its simple and easy to read for changing songs/folders/playlists while driving!!

Thanks!

---

### Post by marcordenis on 2008-01-02
You can get themes for rockbox on the e200 here:
[http://www.rockbox.org/twiki/bin/view/Main/WpsSansaE200](http://www.rockbox.org/twiki/bin/view/Main/WpsSansaE200)
or here:
[http://www.rockbox-themes.org/index.php?res=176x220x16](http://www.rockbox-themes.org/index.php?res=176x220x16)

There are a few other pages, but these are the main ones.
Hope that helps.

---

### Post by andymushu on 2008-01-02
For all who are still having trouble with mounting your sansa under gutsy, here is what worked for me:
```
sudo modprobe ehci_hcd
```
to make sure that the module is in the kernel, then
```
sudo apt-get install pmount
```
Modprobing ehci_hcd allowed me to transfer files to my sansa e250r if it was attached to the computer when the computer booted up, but if i plugged it in after it had booted, i got nothing. Installing pmount instantly fixed this. I hope this is helpful to someone.

edit: this fix was nullified once i did a cold boot. It was ultimately solved by removing rhythmbox by a simple ```
sudo apt-get remove rhythmbox
```

---

### Post by marcordenis on 2008-01-04
just wondering....
Has anybody found a way to get videos to play using the original firmware? The mpeg converter forRockbox works very well, but obviously doesn't work in the original firmware.
Another thing.... Did anyone get pictures to work (other than Album Art)?
Thanks.....

---

### Post by MusicMastaMike on 2008-01-04
> **marcordenis said:**
> just wondering....
Has anybody found a way to get videos to play using the original firmware? The mpeg converter forRockbox works very well, but obviously doesn't work in the original firmware.
Another thing.... Did anyone get pictures to work (other than Album Art)?
Thanks.....

I never could figure out the right video settings for the original firmware.  I used the software that came with it (installed through XP in VirtualBox), but I was very displeased with the video quality that it gave me.  And I'm not sure about pictures.  I know they work fine in RockBox, but I never got around to testing them out in the original firmware.  I know that the provided software converts pictures to the correct format, but I haven't fiddled around with it... I'll get back to you on it!

---

### Post by marcordenis on 2008-01-04
thanks.... but what pictures work with Rockbox? Do they need a specific format, size, etc.?

---

### Post by MusicMastaMike on 2008-01-04
> **marcordenis said:**
> thanks.... but what pictures work with Rockbox? Do they need a specific format, size, etc.?

The only requirement is that they have to be .jpg.  Rockbox will automatically resize it for you.

---

### Post by marcordenis on 2008-01-05
ok.... thanks for your help

---

### Post by la3875 on 2008-01-08
Finally got up the gumption to flash the Sansa with Rockbox, though I have to admit I wussed out and used the automatic installer from Windows...

And... Rockbox ROCKS! so many more features and settings are available, I'm glad I did and cant see myself going back to the original firmware. Great thread and program. Keep it going!:guitar:

---

### Post by Chetamonye on 2008-01-09
> **MusicMastaMike said:**
> I just put Rockbox on my Sansa e260, and I'm loving it.  I've created a shell script to convert any ffmpeg compatible video to Rockbox compatible format.  

Download the attached file and extract it.  Put the script wherever you like and make sure it's executable (sudo chmod a+x sansa-convert).  Make sure that you have ffmpeg installed (sudo apt-get install ffmpeg).  Execute the script in a terminal (./sansa-convert) for usage instructions.

Hopefully someone else finds this to be useful.  If you have any questions, feel free to message me!

--Edited script now attached, includes more error checking.

MusicMastaMike,

Thanks for making the script.  I've tried it and I am getting an error.  Maybe you can help.  

*"The message is MPEG1/2 does not support 5/1 fps.  Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height."*

Any ideas?  I'd really like to try getting video to work on my Sansa.

Oh, I'm running Feisty, yes, ffmpeg is installed.

Thanks, Chet

---

### Post by MusicMastaMike on 2008-01-09
> **Chetamonye said:**
> MusicMastaMike,

Thanks for making the script.  I've tried it and I am getting an error.  Maybe you can help.  

*"The message is MPEG1/2 does not support 5/1 fps.  Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height."*

Any ideas?  I'd really like to try getting video to work on my Sansa.

Oh, I'm running Feisty, yes, ffmpeg is installed.

Thanks, Chet

Chet,

What type of video are you trying to convert?  Please post the output of: ```
ffmpeg -i [path to input file]
```

I'm also assuming you haven't changed any ffmpeg parameters in the script, correct?  

-Mike

---

### Post by Chetamonye on 2008-01-09
> **MusicMastaMike said:**
> Chet,

What type of video are you trying to convert?  Please post the output of: ```
ffmpeg -i [path to input file]
```

I'm also assuming you haven't changed any ffmpeg parameters in the script, correct?  

-Mike

Thanks for the quick response.

NO, I have not changed any parms.  

The output is exactly the same as previously posted.

```
"The message is MPEG1/2 does not support 5/1 fps. Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height."
```

The file being converted is an mpg.

Thanks for the help.

Chet

---

### Post by MusicMastaMike on 2008-01-10
> **Chetamonye said:**
> Thanks for the quick response.

NO, I have not changed any parms.  

The output is exactly the same as previously posted.

```
"The message is MPEG1/2 does not support 5/1 fps. Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height."
```

The file being converted is an mpg.

Thanks for the help.

Chet

I'm at a loss here... Does it happen with all of your videos or just a specific one?

I Googled your error message and ended up with this thread: [http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-February/002222.html]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-February/002222.html")
I don't know if that will help you or not, but from that, I thought maybe you have a different version of libavcodec installed than I do.  I have libavcodec1d (the Medibuntu package) installed, so perhaps if you have a different version, that could maybe cause issues?

Anybody else got any ideas on this one?

Mike

---

### Post by 99bluefoxx on 2008-01-10
so i have gone through 3 e260s now and am on my fourth, so i have given up on the origional firmware
i put rockbox onto it and it is working well, i however would much like to be abel to watch my videos on it, so after some rooting around on the rockbox site i found i can use mencoder
i input the conversion code but this is what i got
```
bluefoxx@azurE-prIDE:~$ mencoder /home/bluefoxx/Desktop/anime\,\ movies/inuyasha/anime_eps/Inuyasha_EP_1.ogg -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=96:vmax_b_frames=16:vb_strategy=2 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=200k -vf scale=224:176,harddup -ofps 25 -o /home/bluefoxx/Desktop/Inuyasha_ep_1.mpg
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.93GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
The vbitrate option must be an integer: 200k
Error parsing option on the command line: -lavcopts

Exiting... (error parsing command line)
bluefoxx@azurE-prIDE:~$ 

```what did i do wrong?
also, is this the appropiat thread for this
anything to help is great, i love to learn more on linux

excuse any typos, my cordless is breaking down[too much use and celeron lags, need to upgrade to a 778 cpu]

---

### Post by DasCrushinator on 2008-01-10
> **99bluefoxx said:**
> so i have gone through 3 e260s now and am on my fourth, so i have given up on the origional firmware
i put rockbox onto it and it is working ell, i however would much like to be abel to watch my videos on it, so after some rooting around on the rockbox site i found i can use mencoder
i input the conversion code but this is what i got
```
bluefoxx@azurE-prIDE:~$ mencoder /home/bluefoxx/Desktop/anime\,\ movies/inuyasha/anime_eps/Inuyasha_EP_1.ogg -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=96:vmax_b_frames=16:vb_strategy=2 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=200k -vf scale=224:176,harddup -ofps 25 -o /home/bluefoxx/Desktop/Inuyasha_ep_1.mpg
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.93GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
The vbitrate option must be an integer: 200k
Error parsing option on the command line: -lavcopts

Exiting... (error parsing command line)
bluefoxx@azurE-prIDE:~$ 

```

what did i do wrong?
also, is this the appropiat thread for this
anything to help is great, i love to learn more on linux

excuse any typos, my cordless is breaking down[too much use and celeron lags, need to upgrade to a 778 cpu]

I've tried that in the past and got some error as well.  You're better off just using the script provided a few posts up.

---

### Post by 99bluefoxx on 2008-01-10
qctually, i just got it to work, i just had to remove the "k" from the end of the part of this ```
c -lavcopts vcodec=mpeg2video:vbitrate=200k
```
now almost done converting first episode, and watching first half[was too impatiant, lol]
only problem encountered so far has been the occasional frwwweeze up of the video stream resulting in a de-sync of the audio with the video, hitting menue, and then going back to the file has worked, just choose"resume from xx:xx" and your back wear you were
rockbox indeed rocks, now i have something to watch/do on the bus/skytrain, XD

---

### Post by DasCrushinator on 2008-01-10
> **99bluefoxx said:**
> qctually, i just got it to work, i just had to remove the "k" from the end of the part of this ```
c -lavcopts vcodec=mpeg2video:vbitrate=200k
```
now almost done converting first episode, and watching first half[was too impatiant, lol]
only problem encountered so far has been the occasional frwwweeze up of the video stream resulting in a de-sync of the audio with the video, hitting menue, and then going back to the file has worked, just choose"resume from xx:xx" and your back wear you were
rockbox indeed rocks, now i have something to watch/do on the bus/skytrain, XD

Cool, however I have never suffered the sync issues since trying Mike's script :)

---

### Post by 99bluefoxx on 2008-01-10
really?
then i think i shall try it out, maybe it can convert blade faster than mencoder =3

---

### Post by Chetamonye on 2008-01-10
> **MusicMastaMike said:**
> I'm at a loss here... Does it happen with all of your videos or just a specific one?

I Googled your error message and ended up with this thread: [http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-February/002222.html]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-February/002222.html")
I don't know if that will help you or not, but from that, I thought maybe you have a different version of libavcodec installed than I do.  I have libavcodec1d (the Medibuntu package) installed, so perhaps if you have a different version, that could maybe cause issues?

Anybody else got any ideas on this one?

Mike

Hmmm.  The scripts worked perfectly on an .asf file, and a wmf file.  I tried a different mpg and I got the same error.  I'll play with it some more and see if I just need to change some of the settings.  

Thanks for looking into this.  I appreciate it.  

Chet

---

### Post by dumpy on 2008-02-19
Has anyone used this:

[http://www.mazleg.com/sansa/](http://www.mazleg.com/sansa/)  

I searched and couldn't find anything on here, but I am curious about this application.  I like the idea of being able to edit a playlist based on what is already on my player.

I'm a definite newb (first post, a couple of months on xubuntu) so i am not quite sure how to make something executable.   Any info/help that could be provided would be great.  thanks!

---

### Post by 99bluefoxx on 2008-02-20
well, as great as this thread has been, its no longer helpful to me, as i no longer have a sansa e200 :(
got mugged a few weeks ago...and of course the 60+ other ppl standing right there did nothing...like cows...moo....

---

### Post by dumpy on 2008-02-20
> **dumpy said:**
> Has anyone used this:

[http://www.mazleg.com/sansa/](http://www.mazleg.com/sansa/)  

I searched and couldn't find anything on here, but I am curious about this application.  I like the idea of being able to edit a playlist based on what is already on my player.

I'm a definite newb (first post, a couple of months on xubuntu) so i am not quite sure how to make something executable.   Any info/help that could be provided would be great.  thanks!

I got this to work and it works well once some changes are made:guitar:.  I have to open it via a terminal with "perl sansa-editor".

At first it didn't find my Sansa, but once I created a directory called "PLAYLISTS" in the Sansa, it works quite well.  I'm a wicked newb, but I thought I'd pass this along as there doesn't seem to be any info on here about this program.


Edit:  It did transfer the playlists quite well, but when I try to open them  with the Sansa, it says they are blank.  I've opened them up with a text editor and everything appears ok,  does anyone have a functioning .pla file I could look at to see what is wrong with mine?

---

### Post by leetcharmer on 2008-02-27
> **barry_vancouver said:**
> my Sansa e280 had no problems being instantly recognized and mounted on my laptop with Feisty Fawn. 

My Desktop PC with Gutsy 7.10, however, refused to mount the device...unitl I typed the following command into Terminal:
 sudo modprobe -r ehci_hcd


I found this command trolling Google and ubuntu forums on and off the last few days for any advice relating to Sansa usb drives and mp3 players...

Give it a go!  Worked beautifuuly for me on Gutsy!! :d

Now I can sleep!!

That command doesn't work for the sansa connect 4gb.

---

### Post by SZF2001 on 2008-03-02
Something I think people should know, as of March 2nd 2008 I've backed up the guide on a .txt file in case something happens to the Ubuntu forums (Mark is a rich man, but money can't buy complete security)... I really, really, really don't plan on updating anything anymore. Seriously. I mean seriously this time. Super serious.

I'm not going through the trouble of saving other posts, like the rockbox and the easytag setup one, but if it ever need be I'll just write another.

I'm glad I could help people. Apparently this is the first hit you get when you google "ubuntu sansa" or vice versa. Thank you all for the help, all I really did was string information together.

---

### Post by elj4176 on 2008-03-04
Why is this player so picky? I have 60GB worth of music (all tagged) and I bought the e260 for my wife to use. I figured I could just drop some files on it like I do with my iaudio x5 - but no. I add tracks and the refresh database just hangs. 

So I remove all tracks, delete mtable.sys and retag using easytag and try again - same thing. I'm getting tired of this players inability to do what it is designed to do - play music.

If I can't get this thing working tonight it is going back and I'm buying another iaudio for her to use.

---

### Post by SZF2001 on 2008-03-04
You do realize that, in the e200 series, the highest it can go is around 10 gig, and that's if you buy a miniSD card too? You can't cram 60 gigs of music on it, that's impossible.

Or if that's not the problem (since you make it seem so), did you try getting the latest firmware? Sometimes there are problems with old firmware that causes problems with songs and tagging info.

---

### Post by elj4176 on 2008-03-04
Of course I know  that ;)

The 60GB is MY music on my laptop. I was just trying to give her something to listen to on her little 4GB Sansa player. I managed to get 2 GB of tracks properly tagged using easytag.
I just think it should be easier than it is. On my iaudio X5 I just drag and drop and it just works. It doesnt care if i use thee wrong version of id3 tags. The sansa seems to get confused if the wind blows while i'm transferring tracks to it.

---

### Post by DasCrushinator on 2008-03-04
> **elj4176 said:**
> Of course I know  that ;)

The 60GB is MY music on my laptop. I was just trying to give her something to listen to on her little 4GB Sansa player. I managed to get 2 GB of tracks properly tagged using easytag.
I just think it should be easier than it is. On my iaudio X5 I just drag and drop and it just works. It doesnt care if i use thee wrong version of id3 tags. The sansa seems to get confused if the wind blows while i'm transferring tracks to it.

I think it is because the currently installed firmware only understands certain versions of IDV3 tags.  If you update the firmware to the very latest, it should recognize the way you have the tags done currently.

In fact, I think this may be discussed earlier in this thread (about how earlier versions of the firmware only supported earlier (read; OLD) versions of IDV3).

I would look myself, but I am about to hop in the shower, and I am pretty sure this will solve the problem ;)

Good luck!

---

### Post by SZF2001 on 2008-03-07
Hey guys, something weird - I'm using Gutsy, and easyTAG updated... So will it make your tags the latest? I've got everything successfully tagged just like I've always done, but the sansa will now read everything as "Unkown"...

Is there a latest firmware to keep up?

EDIT: Wow, read up on this issue on page twelve, I just rockboxed my sansa so now everything is fine... Is this urgent enough for an update to the guide or what?

---

### Post by loos on 2008-03-16
just want to say thanks for great forum...had sansa 260e for about 4-5 months and had ripped some cd s at a friends faster computer on win exp... long and short was  I kept getting odd little temp files all over sansa that were protected...figure was drm from windows media player ,  last month decided to format and updated firmware to clear up missing disk space on sansa... all was good until tried to move files off sansa...came up as read only disk all of a sudden... tried all kinds of sudo/chown/chmod   from root user that could find...no help,,, then last resort...remembered to add the file from page 1 here   .is_audio_player
 all is now happy and free! thank you all!

---

### Post by PhilCash on 2008-03-20
> **andymushu said:**
> For all who are still having trouble with mounting your sansa under gutsy, here is what worked for me:
```
sudo modprobe ehci_hcd
```
to make sure that the module is in the kernel, then
```
sudo apt-get install pmount
```
Modprobing ehci_hcd allowed me to transfer files to my sansa e250r if it was attached to the computer when the computer booted up, but if i plugged it in after it had booted, i got nothing. Installing pmount instantly fixed this. I hope this is helpful to someone.

edit: this fix was nullified once i did a cold boot. It was ultimately solved by removing rhythmbox by a simple ```
sudo apt-get remove rhythmbox
```

G'day All,
I'm at day 3 on Ubuntu 7.10 and loving it so far, but I'm not having any luck with connecting my Sansa e280. It's set to MSC. It connects/disconnects repeatedly when plugged in. Rhythmbox starts then greys out. 
I tried the first two commands above with no change. 
Am I correct in thinking that Rhythmbox is the cause of the problem and they the third command above uninstalls rhythmbox? 
If so, what is the consensus on a music player to replace it with?
Cheers,
Phil

---

### Post by nick_h on 2008-03-20
> Am I correct in thinking that Rhythmbox is the cause of the problem and they the third command above uninstalls rhythmbox?
Yes.

> If so, what is the consensus on a music player to replace it with?
Try banshee and exaile.

---

### Post by PhilCash on 2008-03-21
These forums and the level and speed of support are one of the most outstanding benefits of the Ubuntu community. Thanks to both andymushu and nick_h for their information and rapid response. Sansa and its card mounted nicely thank you. Banshee; what an excellent name for a music player!
Cheers.
Phil

---

### Post by rotata on 2008-03-22
Thank you for the guide! 

I run xubuntu gutsy on an eeePC using RhythmBox. After following your instructions, I was able to connect my Sansa without any trouble.

---

### Post by lawhorne on 2008-04-08
in reference to the rhythmbox issue mentioned above... my mounting problem/rhythmbox problem was solved by disabling the mtp plugin.

---

### Post by Oreo Priest on 2008-04-13
> **Zwack said:**
> I don't know about the double-song problem (yet) but this is totally safe.  I have deleted the entire contents of the system folder on my e250R and it rebuilt the database.  It got rid of all of the Rhapsody channels that I don't use as well... :)

Z.

ACK! I followed this advice and deleted the contents of the data folder and my e280 semi-bricked on me. Now when it refreshes the database, it stops halfway through with a blue screen of death. Help me!

---

### Post by Neo40 on 2008-04-15
I'm thinking to buy a Sansa e280 but I found on this thread it seems to have problem playing movies? Is it because we are with Linux? If I have some video clips in avi, wmv or mpg format and I'm trying to play them on my eventually e280 player, I'll get problem?  What are the solutions?

Thanks

---

### Post by Oreo Priest on 2008-04-16
I've solved my own problem by the way. I like my e280; I struggled with the standard firmware for a while, but now that I've installed Rockbox everything is awesome. I have not, however, tried to play movies yet.

---

### Post by marcordenis on 2008-04-28
so......
I got Hardy recently, and wanted to put some songs onto my Sansa e280, and so I connect it, and it doesn't show anything. I decided to type in the Gutsy command, but still nothing. It just does nothing (well it does still manage to freeze up Rhythmbox). Then I followed the tip to turn off MTP support in Rhythmbox, so I did that. That made the device recognised by Rhythmbox, and it imported all the songs, except for the last one, and just froze on the last one. I then decided to also put off iPod support and plug in my Sansa. It still loaded the songs in Rhythmbox, but I just closed it before he had finished importing everything. In the file manager it showed Sansa E280 3 times. I still haven't fixed that. One of them shows the files, and has a yellow bar on top saying "These files are on a digital audio player" and has a button to open Rhythmbox. One of the others has only this bar, the third mention of Sansa E280 is empty. I have noticed that one is called SANSA E280, one is called SANSA E280_, and one is called SANSA E280__. The one with two underscores works. This is some progress, but I don't really like this appearing three times. How can I solve that / what is it for?
Thank you in advance.

EDIT: Just found out that I had an invalid track. Deleted that and now all the songs are displayed in Rhythmbox no problem.

---

### Post by 99bluefoxx on 2008-04-28
> **marcordenis said:**
> so......
I got Hardy recently, and wanted to put some songs onto my Sansa e280, and so I connect it, and it doesn't show anything. I decided to type in the Gutsy command, but still nothing. It just does nothing (well it does still manage to freeze up Rhythmbox). Then I followed the tip to turn off MTP support in Rhythmbox, so I did that. That made the device recognised by Rhythmbox, and it imported all the songs, except for the last one, and just froze on the last one. I then decided to also put off iPod support and plug in my Sansa. It still loaded the songs in Rhythmbox, but I just closed it before he had finished importing everything. In the file manager it showed Sansa E280 3 times. I still haven't fixed that. One of them shows the files, and has a yellow bar on top saying "These files are on a digital audio player" and has a button to open Rhythmbox. One of the others has only this bar, the third mention of Sansa E280 is empty. I have noticed that one is called SANSA E280, one is called SANSA E280_, and one is called SANSA E280__. The one with two underscores works. This is some progress, but I don't really like this appearing three times. How can I solve that / what is it for?
Thank you in advance.
just drop the files you want into the /MUSIC/ folder on the e200
as for multiple appearances, try the commands "sudo umount /media/SANSA\ R280_ && sudo umount /media/SANSA\ E280__", and when your finished with organizing the music player use the terminal command "sudo umount /media/SANSA\ E280" *then* procede to unplug it[as ubuntu syncs the data on unmount for files under a certain size - or so i remember from feisty, i use my e270 in hardy and its OK, other than rhythmbox opening on its own - but thats another problem i created :\ oh well]

---

### Post by jjremy on 2008-04-29
I've just switched to Ubuntu when Hardy was released and I'm having problems getting music onto my sansa e280. 
When I connect it, it mounts fine, everything shows up(even my microSD card). But I can't drop any music into the music folder. When I try to I get an error message saying "the destination is read-only". 

I've scanned through your main tutorial and didn't see anything regarding this issue. Didn't read the entire thread though. So I apologize if this has already been covered somewhere.

any help would be greatly appreciated. This is the LAST thing keeping my Ubuntu experience from being perfect.

---

### Post by DasCrushinator on 2008-04-29
> **jjremy said:**
> I've just switched to Ubuntu when Hardy was released and I'm having problems getting music onto my sansa e280. 
When I connect it, it mounts fine, everything shows up(even my microSD card). But I can't drop any music into the music folder. When I try to I get an error message saying "the destination is read-only". 

I've scanned through your main tutorial and didn't see anything regarding this issue. Didn't read the entire thread though. So I apologize if this has already been covered somewhere.

any help would be greatly appreciated. This is the LAST thing keeping my Ubuntu experience from being perfect.

What mode is your player in?  UMC or MTP?

---

### Post by jjremy on 2008-04-29
It's in MSC. I tried switching to MTP and it wouldn't mount at all. Switched back to MSC and it again mounts fine, but says its read-only.

---

### Post by darrenn on 2008-04-29
I have e280 and it works perfectly in Hardy with music. When it comes to movies and songs that arent tagged in idv3 you can have problems.

---

### Post by marcordenis on 2008-05-22
Just wanted to say that I've fixed it myself, as now Rhythmbox works very well for MTP. Just have to drag and drop songs in Rhythmbox and he does everything automatically, and as long as the music is tagged in Rhythmbox I think the e200 can read it (as I haven't had any problems using songs tagged directly in Rhythmbox). Thanks a lot all the same, great forum and great thread.

---

### Post by phannigan on 2008-06-05
I am new to Ubuntu and also have a Sansa e260 that will not mount when i plug it in. The error I receive is attached. Sansa shows "connected" on the unit and on the computer - but "unable to mount" Any simple recommendations? Thanks.

---

### Post by renstar on 2008-06-20
Does anyone have any experience getting files that were transfered in windows to show up in ubuntu?  I use both xp and ubuntu 8.04.

I'd like to be able to hook my e280v2 up to the ubuntu machine and just play directly off of the mp3 player if possible.  The player mounts in MSC mode but there is nothing in the MUSIC folder.

-r

---

### Post by ecca on 2008-07-01
So I have a sansa e280. I changed it's USB mode to MSC and now when I plug it in everything shows up just fine (on MTC I got nothing). The problem occurs when I go to put new music on. I started out using rhythm box and simply dragging and dropping but I got this error telling me it's a "Read-only file system". Okay. So the same happens if I try to move music in through a command line. After this I figured I would try and remount it as read write see if that helped at all, and got a new error:
" mount: can't find /media/Sansa e280/MUSIC/ in /etc/fstab or /etc/mtab "

Now I am just confused :( I read about others having similar sounding problems but being a complete n00b can't fathom how to fix it by myself. Any help would be appreciated!

---

### Post by grossaffe on 2008-07-06
> **ecca said:**
> So I have a sansa e280. I changed it's USB mode to MSC and now when I plug it in everything shows up just fine (on MTC I got nothing). The problem occurs when I go to put new music on. I started out using rhythm box and simply dragging and dropping but I got this error telling me it's a "Read-only file system". Okay. So the same happens if I try to move music in through a command line. After this I figured I would try and remount it as read write see if that helped at all, and got a new error:
" mount: can't find /media/Sansa e280/MUSIC/ in /etc/fstab or /etc/mtab "

Now I am just confused :( I read about others having similar sounding problems but being a complete n00b can't fathom how to fix it by myself. Any help would be appreciated!

I think i'm having the same problem.  I'm also a bit of a noob.

---

### Post by SZF2001 on 2008-07-08
So apparently there are new models out? Have Sandisk taken the e200 series off the shelves or did they just give them a face lift? They all look so different now wtf.

---

### Post by Mat/Mb on 2008-07-12
I can connect My Sansa E260 to Ubuntu(latest version) and open the folder but I cannot delete or add any songs to the player, all the files are locked. I tried to change the permissions but it says permissions cannot be found. Can anyone help me?

---

### Post by Jack-Frost on 2008-08-16
> **Mat/Mb said:**
> I can connect My Sansa E260 to Ubuntu(latest version) and open the folder but I cannot delete or add any songs to the player, all the files are locked. I tried to change the permissions but it says permissions cannot be found. Can anyone help me?


I have a similar problem. I get my music onto the sansa player, then when I unmount, or simply disconnect the player, it goes into refresh mode and FREEZES, right in the middle. It's been driving me nuts. Can anyone help?

---

### Post by lddm00 on 2008-09-23
Hi, I recently bought a sansa e260 and I can't get to work in Ubuntu 8.04. I configure MSC mode in the player and when I connect it says "connected" in the player but in the pc doesn't mount automatically. When I type lsusb in the console doesn't appear also the player as connected. Any help would be good.
Cheers.
Luis

---

### Post by stevek123 on 2008-09-24
I'd say give it up on the Sansa. I've busted on this issue for months. Its the firmware from Sansa. Linux wont get thru it. I wrote to Sandisk to gripe. They sent back a pansy letter that said 'sorry - but we did send this to our QC dept...'. They're tied in with M$ - and I wont buy or recommend one of these again. Best of luck.

They also wouldnt supply a link to an older firmware that still allowed Linux use, and seemed surprised that I would even consider such a thing. LOL.

---

### Post by CParticle on 2008-10-06
So I've seen surprisingly little on issue with the sd cards.  I've got a simple problem with my e260.  I can connect to my Hardy box and I can drag files from Rhythmbox to  a Nautilus windows for my e260.  What I can't see is how to get the miniSD to mount.  I've tried the modprobe command just in case but no joy.  If anyone has any ideas on how to mount the mini sd it would be much appreciated.  Thanks.

CParticle

---

### Post by Nico0020 on 2008-10-07
I have not tried my Mini SD card yet, I have a 2gig one I am gonna put it in.  I'll try it later this week and let you know what my results are.  Though I am using Banshee to transfer my files over.

---

### Post by Keith_Beef on 2008-10-19
Well, I recently got a Sansa e280 with a silvery R on the back case, just above the CE mark.

I never tried playing anything with the Sansa formware, I just went straight ahead and RockBoxed it.

If I boot into the original firmware by holding down the left key while powering up, I can find out:
[LIST]
[*]firmware version is 01.02.18A
[*]usb mode is MSC
[/LIST]

I've read around, and looked at the man page for mencoder, and found that the following commands work for converting my DVDs ripped for watching on the computer or on a Cowon D2.
```
mencoder inputfile.avi -o outputfile.mpg -oac mp3lame \
-lameopts cbr:br=64 -ovc lavc -lavcopts vcodec=mpeg2video -ffourcc mjpb -vf scale=220:176 -ofps 12 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
```

Rockbox seems to rotate the image through 90° so that the 220×176 image occupies the physical screen correctly... no need to ask mencoder to do the rotation.

To rip straight from a DVD to a file for the Sansa, I replace inputfile.avi with a string for the DVD title (and optionally chapter), device and for audio language, for example:
```
dvd://8 -dvd-device /dev/dvd1  -alang English
```

I noticed that the first time I watched a film, the sound and video were out of synch, but this was cured by going to Settings - Display Options and setting as follows:
```
Dithering: Yes
Display FPS: No
Limit FPS: Yes
Skip frames: No
```

I hope this helps anybody else still having trouble getting video to work on these Sansa players.

---

### Post by Tommy100 on 2008-10-20
Thanks SZF great thread! :D i could not find the thanks icon, so this will have to do. ;)

---

### Post by Olasimbo on 2008-10-28
HI all! I have a Sansa M240 player and I'm having problems formatting it. I had a problem and had to reboot my machine with it connected and, when I did it, the space available suddenly diminished from 960 MB to 940 MB. Even if I delete everyhting in it it still doesn recover all the space available. So I tried formatting it to get it back to the original configurations, but here's the problem, I tried formatting it using the mkfs.vfat and nothing changes, I get this:

$ sudo mkfs.vfat /dev/sdb

mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/sdb contains a mounted file system.

Still the same space. Then, I got gparted and tried doing it through gparted, but, even though it recognizes the mp3 mounted, it does't allow the option to format it. When I click with the right button, it's greyed out.

Anyone can give me any help on this?? I'd appreciate it very much...

---

### Post by lips_are_sealed on 2008-11-03
Hello, 
My name is Ashley, I just want to start off by saying thankyou so much for all the helpful tips provided for the Sansa MP3 player. 

Unfortunately, I have not been able to recover my lost information on my MP3 player. :shock: I accidently hit the formatting button(stupid me), and lost all the music I downloaded on the Sansa music player... I have tried holding the off button for 15 seconds and then turning the lock as I turn on the MP3 player again and holding the record button, but I have only got a black light with white words saying "please unlock the HOLD switch, to turn power on." And then it turns itself off.... Instead of saying recover information... 

Can somebody help me? :confused:

---

### Post by darrenn on 2008-11-04
> Hello,
My name is Ashley, I just want to start off by saying thankyou so much for all the helpful tips provided for the Sansa MP3 player.

Unfortunately, I have not been able to recover my lost information on my MP3 player. I accidently hit the formatting button(stupid me), and lost all the music I downloaded on the Sansa music player... I have tried holding the off button for 15 seconds and then turning the lock as I turn on the MP3 player again and holding the record button, but I have only got a black light with white words saying "please unlock the HOLD switch, to turn power on." And then it turns itself off.... Instead of saying recover information...


Asyley,

This is easy to fix all you have to do is download the firmware from the sansa site and copy it to your mp3 player. 

[http://www.sandisk.com/Retail/Default.aspx?CatID=1376](http://www.sandisk.com/Retail/Default.aspx?CatID=1376)

---

### Post by stevek123 on 2008-11-06
> **CParticle said:**
> So I've seen surprisingly little on issue with the sd cards.  I've got a simple problem with my e260.  I can connect to my Hardy box and I can drag files from Rhythmbox to  a Nautilus windows for my e260.  What I can't see is how to get the miniSD to mount.  I've tried the modprobe command just in case but no joy.  If anyone has any ideas on how to mount the mini sd it would be much appreciated.  Thanks.

CParticle

I cant get anything from my e260-wont read anything past the menu list - not music, pics, or vids... but my e260 mounted 2G sd minicard automounts in 7.10 & 8.04 perfectly and is fully functional... go figure...

---

### Post by finch127 on 2008-11-16
Hey guys,

I have recently had a problem on my sansa, namely that it stopped on the database refresh screen and wouldnt go on anymore.

Thankfully, i had installed Rockbox on it, so anyone having these problems, heres how you can fix it without deleting everything:

1. You MUST have rockbox installed for this to work. I recommend it over stock firmware (its like ubuntu for mp3 players lol). theres excellent guides on how to do this on their website, and i highly recommend doing this just so you have a reliable backdoor in case the original firmware breaks like mine. Go here to get it/ learn about it:

[http://www.rockbox.org/](http://www.rockbox.org/)

2. Once you have rockbox or if you had it (you must have it, and it must be bootable), just go to the file browser on your player in rockbox, go to system, and then  scroll to the DATA folder.

3. Hold the center select button, and you will get a menu. Select delete directory. Dont worry, this is only the database of files where the player goes to find the references to the music. Your files WILL NOT be deleted from this.


 idk if this is optional, but i would do it anyway:
4. Once its deleted, go back to system folder. Hold center select and select create directory from the menu. Name the folder DATA in all caps (to replace the old one)

5. When thats done, shutdown the player. Wait a second or two and plug in the USB cable. It will boot in original firmware, rebuild the database from scratch, and you should be able to mount/ backup your files now and then do what you like. 

Idk if this is a one time fix, but i did it to save my years of music collecting all tied up on my one mp3 player. I got all 7 gb of music out onto my PC, backed it up, and worried no more.

---

### Post by finch127 on 2008-11-16
BTW the above post was for the green bar freezing on the database refresh screen. This should work for anyone

---

### Post by cart159 on 2008-12-02
**[Aiseesoft DVD Converter Suite](http://www.topsevenreviews.com/aiseesoft-dvd-converter-suite.html)** is a professional combination of [**Aiseesoft DVD Ripper** ](http://www.topsevenreviews.com/download/dvd-ripper/dvd-ripper-108068.exe)and [**Aiseesoft Total Video Converter**](http://www.topsevenreviews.com/download/video-covnverter/as-total-video-converter-108068.exe). 
 [img]http://www.topsevenreviews.com/image/dvd-video-suite/aiseesoft-dvd-converter-suite-icon.jpg[/img]

Download this best [DVD Converter Suite](http://www.topsevenreviews.com/download/dvd-video-suite/as-dvd-converter-suite-108068.exe) now.

Key functions and features of this perfect DVD Converter Suite:

(1)Convert DVD and any video/audio to the various video/audio formats
Converter Suite software could easily convert DVD and any video to the various video/audio formats such as MP4, H.264, AVI, MP3, WMV, WMA, FLV, MKV, MPEG-1, MPEG-2, 3GP, 3GPP, VOB, DivX, Mov, RM, RMVB, M4A, AAC, WAV, etc. 

(2) Support almost all popular portable players
Aiseesoft DVD Converter Suite software can convert DVD and video to all the popular devices: PSP, iPod Classic, iPod Touch, iPod Nano, iPhone (3G), iPhone, Zune, Zune 2, Blackberry, Nokia, Creative Zen, Sony Walkman, iRiver PMP, Archos, PS3, Apple TV, Xbox, iPAQ, Pocket PC, Mobile Phone, etc. 

(3) Easy and powerful editing function (Merge, Trim, Crop)
Aiseesoft DVD Converter Suite software offers powerful editing functions such as merging multiple DVD chapters, titles or different videos files into one file, trimming any clip of video or DVD, cropping video size and so forth. 
1:Merge multiple DVD chapters, titles or different videos files into one file.
2:Cut any clip of video.
3:Crop Video Size.

(4)Capture your favorite image
You can capture your favorite video image only by clicking the “SnapShot” function and the picture will be saved.

(5)Support Preview

(6)Fastest Conversion Speed
It has a >400% conversion speed and a short while your conversion will be finished.

(7)Easy to use
Aiseesoft DVD Converter Suite is very user-friendly and easy to use. Only a few clicks to complete the conversion with supervising the whole process on real time.

---

### Post by ailisaone on 2008-12-08
**Question one:** 
What formats does the SanDisk Sansa support?
**Answer:**
Audio Formats: MP3, WAV, WMA
Video Formats: AVI, MPEG4, WMV, QuickTime, MPEG2, ASF 
Photo formats: BMP, JPEG, TIFF, GIF 

**Question two:**
How can I put my DVD movies and other videos downloaded from online site on my Sandisk Sansa?

**Answer:**
As one of mobile devices fans, I was looking for a valuable all-in-one converter that can both rip DVD and convert video. Recently my friend recommend me the Best DVD Converter Suite — Aiseesoft DVD Converter Suite that can meet my needs. Now I will share with you. 

[img]http://www.aiseesoft.com/images/guide/sandisk-sansa.jpg[/img]

This [**Best DVD Converter Suite**](http://www.aiseesoft.com/dvd-converter-suite.html) actually includes two useful software: [**Best DVD Ripper**](http://www.aiseesoft.com/dvd-ripper.html) and [**Total Video Converter**](http://www.aiseesoft.com/total-video-converter.html).
Aiseesoft DVD Converter Suite supports almost all the portable devices, such as: Sansa,Google phone,PSP, iPod Classic, iPod Touch, iPod Nano, iPhone (3G), iPhone, Zune, Zune 2,Blackberry, Nokia, Creative Zen, Sony Walkman, iRiver PMP, Archos, PS3, Apple TV, Xbox, iPAQ, Pocket PC, Mobile Phone, etc. You can enjoy your favorite DVD and video files on them.

[img]http://www.aiseesoft.com/images/guide/f-dvd-converter-suite.jpg[/img]

---

### Post by Jose Catre-Vandis on 2008-12-28
> **Keith_Beef said:**
> Well, I recently got a Sansa e280 with a silvery R on the back case, just above the CE mark.

I never tried playing anything with the Sansa formware, I just went straight ahead and RockBoxed it.

If I boot into the original firmware by holding down the left key while powering up, I can find out:
[LIST]
[*]firmware version is 01.02.18A
[*]usb mode is MSC
[/LIST]

I've read around, and looked at the man page for mencoder, and found that the following commands work for converting my DVDs ripped for watching on the computer or on a Cowon D2.
```
mencoder inputfile.avi -o outputfile.mpg -oac mp3lame \
-lameopts cbr:br=64 -ovc lavc -lavcopts vcodec=mpeg2video -ffourcc mjpb -vf scale=220:176 -ofps 12 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
```

Rockbox seems to rotate the image through 90° so that the 220×176 image occupies the physical screen correctly... no need to ask mencoder to do the rotation.

To rip straight from a DVD to a file for the Sansa, I replace inputfile.avi with a string for the DVD title (and optionally chapter), device and for audio language, for example:
```
dvd://8 -dvd-device /dev/dvd1  -alang English
```

I noticed that the first time I watched a film, the sound and video were out of synch, but this was cured by going to Settings - Display Options and setting as follows:
```
Dithering: Yes
Display FPS: No
Limit FPS: Yes
Skip frames: No
```

I hope this helps anybody else still having trouble getting video to work on these Sansa players.

This is great, but mencoder refuses to parse the last part:
```
-of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames
```

any suggestions?

---

### Post by bsb on 2009-02-22
> **barry_vancouver said:**
> 
My Desktop PC with Gutsy 7.10, however, refused to mount the device...unitl I typed the following command into Terminal:
 sudo modprobe -r ehci_hcd


Thanks, worked for me.  
I had the same breakage going from Gutsy to Hardy
(along with a lot more...)

---

### Post by msohn88 on 2009-03-02
I have know idea how to uninstall it and Sansapathcher... I don't know what that is.

Could you explain this more clearly?

Rockbox Utility is not working for me either.

---

### Post by msohn88 on 2009-04-01
Hello, my name is Min and I am using EasyTAG.

When I went to Settings > Preference, ID3V2 and ID3V1 both are checked, so I have to uncheck the ID3V1 to make it to ID3V2?

I am afraid if I do something wrong, I would mess up my computer, so anybody help please?

---

### Post by morpheus.pv on 2009-05-13
hi,

patched libgphoto deb (i386) for jaunty 9.04:
[http://rapidshare.com/users/CDB8QP](http://rapidshare.com/users/CDB8QP)

bug described on launchpad... [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12)

---

### Post by casa202 on 2009-06-08
Hi I moved some songs to my sansa e260 and and edited the tags with EasyTAG but the player won't sort the songs the right way. The tags are filled correctly, what might be that I'm doing wrong?

---

### Post by mf205 on 2009-06-15
I can't mount my e200.  I'm running 64-bit Jaunty.  I plug it in, the computer ignores it completely, and the sansa says connected very briefly and then settles on disconnected.  When I do "sudo modprobe -r ehci_hcd", I get

FATAL: Module ehci_hcd not found.

When I go to Places-Computer, there's "USB Drive" there, but I get "Unable to mount location.  No media in the drive."

  Please tell me some things I should be typing, and I'll tell you what comes up.

(Btw, I'm a newb, and I know three-tenths of FA about Linux.  So words of one syllable, please.)

Please help.  I'm really frustrated.  I've been using Ubuntu for six weeks now, and I've come really close to cracking and going back.  I don't think I could explain to a non-expert why I'm using it instead of Windows.

Thanks.  Sorry to interrupt all your expert-talk about tags etc.

---

### Post by ForgivenByJC on 2009-06-16
mf205, taking from what morpheus.pv said in post #211
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12)
Instead of using dpkg -i libgphoto2-2_2.4.2-0ubuntu4_i386.deb, use dpkg -i libgphoto2-2_2.4.2-0ubuntu4_amd64.deb.  I too am using Jaunty on amd64 and just got Rockbox to work with my SanDisk Sanse E280.  Good luck with it.

---

### Post by mf205 on 2009-06-16
Fantastic.  Thanks.  Sorry I ignored #211 because it looked like it was about photos.  Job done.

---

### Post by inspired on 2009-06-26
> **morpheus.pv said:**
> hi,

patched libgphoto deb (i386) for jaunty 9.04:
[http://rapidshare.com/users/CDB8QP](http://rapidshare.com/users/CDB8QP)

bug described on launchpad... [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12)
Thanks Morpheus,
I am looking forward to getting this fixed.
(removed)

UPDATE: I think I figured out the files question/answer. So I have remove the text above.

---

### Post by mf205 on 2009-06-27
OK, I've been happily using my e200 for a week, installed RockBox and put lots of music on it.  But now it won't mount.  I'm back where I was in #213.  When I connect the device, it shows a picture of a USB cable, and Places-Computer shows a USB drive which it won't mount.  I tried repeating the fix from #214/#211, but it doesn't work.  Help.

---

### Post by BoredOutOfMyMind on 2009-06-29
> **mf205 said:**
> OK, I've been happily using my e200 for a week, installed RockBox and put lots of music on it.  But now it won't mount.  I'm back where I was in #213.  When I connect the device, it shows a picture of a USB cable, and Places-Computer shows a USB drive which it won't mount.  I tried repeating the fix from #214/#211, but it doesn't work.  Help.

Are you using MSC or MTP from Settings> USB Mode ?

Rockbox does not support USB, so you have to boot to the Sansa loader. Then plug and play.   I bought my Sansa when iPod was not fully supported.  Gave the iPod to my wife and have been very happy with my e260/Rockbox for 2 years on Linux. ):P

---

### Post by mf205 on 2009-06-29
Thanks for the reply.  I'm using MSC.

I'm afraid I'm a novice/idiot, so I don't understand "boot to the Sansa loader".  I also don't know what you mean by "Rockbox doesn't support USB" - it was quite happy with a USB connection until two days ago.

---

### Post by ForgivenByJC on 2009-06-30
mf205, try copying this in a terminal window when your Sansa is plugged in (use Ctrl+Shft+V to paste into terminal).
```
sudo fdisk -l | grep W95
```

It will say something like
```
/dev/sdc1   *           1        1019     7833300    b  W95 FAT32
```

This means your computer recognizes the Sansa and identifies it as /dev/sdc1 (or whatever).  Now, mount it as root by typing and changing /dev/sdc1 to whatever the "sudo fdisk -l | grep W95" step above told you:
```
sudo mkdir /media/sansa
sudo mount /dev/sdc1 /media/sansa -o user,rw,exec,umask=000
```

Can you now access your Sansa normally?

You will not be able to dismount (unmount) this easily, so again in the terminal type (remember to modify /dev/sdc1 appropriately):
```
sudo umount /dev/sdc1
```


The "mkdir" command means to make a directory, and with the steps provided this will leave /media/sansa after you remove your Sansa, to remove the directory:
```
sudo rmdir /media/sansa
```

---

### Post by SirWeazel on 2009-08-12
Morpheus.pv (#211), thank you.  Your patched worked. I was scared to install it, because i wasn't sure what file to download. I'm glad that i picked the correct one. For people confused like me, i just downloaded libgphoto2-2_2.4.2-0ubuntu4_i386.deb from the rapidshare link, clicked it, and it worked instantly. I've been trying all sorts of stuff to fix my sansa issue (compile, modify, delete reaname, all sorts of files and its a wonder my computer still works, i'm the FNG with linux). Thank you. I was wondering if maybe you could tell me what fixed the problem/or what the patched file fixes. Maybe a little description which patched file applies to what people. (could i have hosed my system by clicking on the wrong file?)  Thank you so much for peopel who are knowlegelable lending a helping hand. - also, should i hold on to the patched file, will an upgrade in the future break the patch?  Once again, thank you.

---

### Post by dennyhorner on 2009-08-13
Hello SZF2001,

Thanks for sharing such informative tutorial.

---

### Post by mf205 on 2009-09-09
@ForgivenByJC: thanks for your help.  In fact the fdisk command you suggested did nothing, but I was able to get it working again by repeating the instructions from before.

I may be wrong here, but I have a feeling it all went wrong because Update Manager decided to update libgphoto.  So I won't let it do that again.  (Thumbs up for an OS that lets you choose which updates you want to install.)

---

### Post by SirWeazel on 2009-09-09
Why does libgphoto try to update with the updates. This issue has been around for awhile now, how come there hasn't been an official fix added to the repositories, so i can stop unchecking it as an update?

---

### Post by danceswithcats on 2009-10-03
Huge thanks for this.  I've been looking for links to rockbox tutorials for ages.  Great work!  Thanks again.

---

### Post by Gibby13 on 2009-10-21
> **morpheus.pv said:**
> hi,

patched libgphoto deb (i386) for jaunty 9.04:
[http://rapidshare.com/users/CDB8QP](http://rapidshare.com/users/CDB8QP)

bug described on launchpad... [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998/comments/12)


Perfect, worked for me on Jaunty

---

### Post by Owwl on 2010-10-25
Ok, I go into settings and change it to MSC, I plug it in, it does not show up on my desk top, it does not show up in my computer. 
It works fine with xp. how can I get it to work? 
I should mention that I am very new to computers, so the simplest solution would be appreciated.
Thanks.

---

### Post by SirWeazel on 2010-11-02
What version of ubuntu are you using? Are you sure your USB ports are working correctly with ubuntu? (do the ports work with other devices?)

---

### Post by Alex Fuchs on 2011-01-14
@MusicGuruMike Thanks for the script. I use WinFF to encode video for my Sansa e260 with RockBox.The script needs some fixing though, change "mp3" to "libmp3lame" and the $OUTPUT option is not defined.
When I used the arguments as a preset in WinFF I got better results than with the original presets and that's what i was looking for in the first place. so cheers.

---

