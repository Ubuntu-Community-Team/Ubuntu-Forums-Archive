---
title: "what is the best (least headaches to sync) MP3 player for linux?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Nante on 2008-05-11
I currently have a Creative Zen Vision M 30 GB MP3 player I use for audiobooks etc, my job keeps me travelling about 20 days a month and I would like to have all my audiobooks with me because its always the ones I didn't have room for that I end up wanting to listen to. I have been looking at the Archos 605 160 GB, the Zune 80 GB, and the Ipod classic 160 GB, of those 3 I like the Archos the best but the music forums are full of horror tales about their durability, anyone have any experience with them? and if they are as fragile as said which of the other two would give me less indigestion getting it to work with Ubuntu?

---

### Post by System Monitor on 2008-05-11
I would try Amarok

---

### Post by grannyw on 2008-05-11
VLC definitely is the one

---

### Post by inportb on 2008-05-11
Um... let's try to stick to the topic.

> **Nante said:**
> I currently have a Creative Zen Vision M 30 GB MP3 player I use for audiobooks etc, my job keeps me travelling about 20 days a month and I would like to have all my audiobooks with me because its always the ones I didn't have room for that I end up wanting to listen to. I have been looking at the Archos 605 160 GB, the Zune 80 GB, and the Ipod classic 160 GB, of those 3 I like the Archos the best but the music forums are full of horror tales about their durability, anyone have any experience with them? and if they are as fragile as said which of the other two would give me less indigestion getting it to work with Ubuntu?

I've been using my Palm T|X, and it's been awesome. Generally, you should have no trouble using devices with standard removable storage.

iPods work very well with Amarok and the like... except for iPod Touch and iPhone.

---

### Post by Nante on 2008-05-11
Thanks I currently use Aramok to load the creative Zen, but it is full so I need a new one, I have seen posts that said the new Ipods wouldn't work with linux has that been fixed?

---

### Post by HunterThomson on 2008-05-11
Ya, all player work grate with linux.... If it is a MPT formatted mp3 player you use Gnomad2 program to sinc

---

### Post by ubunter1 on 2008-05-11
> **Nante said:**
> I currently have a Creative Zen Vision M 30 GB MP3 player I use for audiobooks etc, my job keeps me travelling about 20 days a month and I would like to have all my audiobooks with me because its always the ones I didn't have room for that I end up wanting to listen to. I have been looking at the Archos 605 160 GB, the Zune 80 GB, and the Ipod classic 160 GB, of those 3 I like the Archos the best but the music forums are full of horror tales about their durability, anyone have any experience with them? and if they are as fragile as said which of the other two would give me less indigestion getting it to work with Ubuntu?

i have the same player you do and the program i use is gnomad, in hardy that is and i like it alot the interface isnt pretty but it gets the job done easily,i tried amarok before with the player and had some troubles. good luck though.

---

### Post by hahnson on 2008-05-12
I own a zen 16 gb player and before 8.04 it was a real pain in the b*** to get it working. i found a simple way to acces the whole player, not only the music by using mtpfs, this should work with most mtp devices.

what i did:

 

1. install mtpfs (make sure you have enabled the universe, restricted and multiverse sources under Software Sources)

 

:~§ sudo apt-get install mtpfs

 

this will install mtpfs and its dependencys  (fuse, glib, gthread, mad (libmad), id3tag (libid3tag), libmtp)

 

2. Create a directory to muont your device

 

 :~§ sudo mkdir /media/ZEN 

 

or whatever you like, the advantage by having it under /media is that it will show up as a removable drive.

 

3. Connect your player and 

 

  :~§ sudo mtpfs /media/ZEN -o allow_other

 

4. If everythin went well you shuld have a entry on the desktop and under Places -> Removable media named ZEN, open it and you shuld find several folders, your music files are loocated under /Music and so on

 

5. When you wisch to disconnect the player, execute

 

  :~§ sudo umount /media/ZEN

 

this work perfectly for me, any inputs? is this a bad idea to do? it feels to easy considering the amount of trubles with 7.10

(i wrote it in a form of a guide to make it more clear, hope i havent missed anything)

---

### Post by BenM on 2008-05-12
I'd cross the Zune off the list. It doesn't work well with linux. I wrote this on another thread.

> I have a Zune and would advise against getting one if you are running linux. From what I've read, the only way to rune the Zune software is by using VirtualBox (and here) It sounds like a linux alternative for Zune software unlikely to happen soon (if ever).

In addition, I think Zune only supports AAC, WMA and MP3 files. If you want to use FLAAC or Ogg, you are out of luck. While the player itself isn't to bad, its reliance on proprietary/DRM software has really made me regret my decision to buy one.

---

### Post by ubunter1 on 2008-05-18
i also tried running the disk that came with the zen player, the creative installer under wine, it installs but it cannot run the program and aborts after a couple screen setups.

---

### Post by cooltd825 on 2008-06-25
yeah, i have the Zen V Plus.  Amarok works perfect for me!

except the media buttons on my keyboard won't work.  but that's a pretty minor detail.  Amarok is the only good media player that has support for MP3 player syncing.

---

### Post by Canis familiaris on 2008-06-25
> **System Monitor said:**
> I would try Amarok

+1 for Amarok!

---

### Post by whitethorn on 2008-06-25
I bought myself a cowon d2.  I think the current ones have 16Gb internal memory which can be expanded using SD/SDHC cards. With the d2 you can either just copy the music folder style over onto it and you can play it no need to sync.  Or you can change it over to MTP connections and then use something like amarok to sync with it. I haven't tried that out yet.  The best part about the D2 is that it has a huge battery life. 

[http://www.cowonamerica.com/products/cowon/d2/](http://www.cowonamerica.com/products/cowon/d2/)

Here check it out

---

### Post by bryncoles on 2008-06-25
if you're using creative zens, then kzenexplorer is quite a good program. much prettier than gnomad, supports syncing and you can move files around by just dragging and dropping them where you want them. 

ive grown to like it a lot!

---

### Post by zapree on 2008-06-30
> **BenM said:**
> I'd cross the Zune off the list. It doesn't work well with linux. I wrote this on another thread.

i think that zune supports more formats, but as to zune compatibility with linux....  Zune software is a pain in the F***ING A** on windows, although i like the acutal layout of the media player along with the swipe pad.  So basically if you still have windows its great (although the software can be a pain in the *** sometimes), but as of now the only way through linux is what they said, and i agree that i dont think that a hack for zune is coming out any time soon... so stick to a player that already has compatibility with linux or at least has a hack available.

---

### Post by flytripper on 2008-06-30
install gnomad2 then use banshee.. :)

---

### Post by Francewhoa on 2009-10-16
Ubuntu media players overview at [http://www.ubuntugeek.com/ubuntu-media-players-overview.html](http://www.ubuntugeek.com/ubuntu-media-players-overview.html)

---

### Post by nothingspecial on 2009-10-16
cowon

They are treated as removable media, just drag `n` drop.

---

### Post by rgb1701 on 2009-10-16
> **System Monitor said:**
> I would try Amarok

The OP (original post) is asking about portable MP3 players that work well with Ubuntu, not media player software on Ubuntu.

To answer the OP's question- my pick would be the Sansa Fuze-

[http://www.overstock.com/Electronics/SanDisk-Sansa-Fuze-2-GB-Multimedia-MP3-Player-Refurbished/4136469/product.html#](http://www.overstock.com/Electronics/SanDisk-Sansa-Fuze-2-GB-Multimedia-MP3-Player-Refurbished/4136469/product.html#)

I picked one up a couple of weeks ago after reading that it played .flac and .ogg files.  While I don't use .ogg often, I do need/want .flac support.   You shouldn't buy a player that doesn't support .flac. 

Philosophically, I would purchase only players that supported open formats like flac and ogg, whether you use them or not, for the same reason you choose to use FOSS software like Ubuntu/Linux.

Also from the freedom functionality standpoint, you only want players that can be recognized like any USB stick on Ubuntu/Linux.  Technically, this capability is called MSC Mode, or Mass Storage Class.

[http://forums.sandisk.com/sansa/board/message?board.id=announcements&thread.id=96](http://forums.sandisk.com/sansa/board/message?board.id=announcements&thread.id=96)

This means the player will be mounted ("seen") as a standard USB storage device, just like any USB stick, memory card, or USB hard drive.

Avoid any non-MSC players like the plague.  There is ZERO excuse for not using MSC mode, other than anti-consumer DRM and artificial lock-in reasons.  Both Apple and MS Zune's use non-standard, restrictive methods to keep you from freely transferring files to/from their devices.  Microsoft came up with their own protocol "MTP" in order to restrict and control users and enable DRM schemes.

While the Sansa Fuze has only 2-8GB memory, it has an SD card slot that can take up to at least 32GB cards. The price of SD cards is always dropping, so every few months you can buy a 32 GB card and carry them with you.  Future firmware updates could support higher capacity cards.

The Fuze is well built to tier-1 standards, unlike the generic MP3 players like

[http://www.geeks.com/details.asp?invtid=SIL-S-818A-4GB&cat=MP3](http://www.geeks.com/details.asp?invtid=SIL-S-818A-4GB&cat=MP3)


The Fuze meets or exceeds the build quality of Apple or MS stuff, includes a good quality FM tuner with great reception (unlike generics), has a voice record and radio record function, plays video, can browse by directory/folder (too many big name media players cannot), and has a real illuminated mechanical wheel vs a touch wheel.  Battery life is outstanding.

You can easily update the Fuze firmware in Linux, which I have done to mine already, and Rockbox support is coming along nicely-

[http://www.rockbox.org/](http://www.rockbox.org/)

Rockbox is an open source firmware replacement for portable media players.  You should not buy a media player that doesn't support Rockbox.

---

### Post by coprolites on 2010-04-20
I use the Samsung P2 (released 2007). It comes as a MTP device in most area's but can be changed to UMS very easily, which essentially turns it into a flash drive allowing you to sync with virtually any program.

Samsung made a new version of the P2 - the P3. It seems better (I want it). I'm fairly certain you can change this to UMS as well.

There are great reviews at [anythingbutipod]("http://www.anythingbutipod.com/") and any other info is probably in their forums.

---

### Post by SmokeyMcpuff on 2010-04-20
So what do I use if I have an iPod touch? Is there some way I can sync/manage it?

I'm running Ubuntu 9.10.. Thanks!

---

### Post by tarahmarie on 2010-07-15
I too am tired of the headaches with proprietary crap. I'm done with pods and zens and zunes. 

Is the Sansa line the best way to go?

I want one that will work with Amarok.

---

### Post by weshallallbefree on 2010-07-31
Searched intensely for an ogg player back in 2008 before travelling

Couldn't find a replacement hd for an old, broken iPod to install Rockbox on.

Ended up with a Meizu Mini Player M6 8GB, used it almost every day since, brillant, decent battery time still. Not sure if they're still available. Guessing my next ogg player will be residing in an Android phone.

Extensive player list here:
[http://wiki.xiph.org/index.php/PortablePlayers](http://wiki.xiph.org/index.php/PortablePlayers)

Searching for a handy day-to-day Ubuntu sync. solution now, coming from os x itunes and [iTuneMyWalkman]("http://ilari.scheinin.fidisk.fi/itunemywalkman/"). Do need that sort of 1-click feature, don't want to do drap'n'drop folder-by-folder for every sync.

Anybody know if that's doable on any Linux media player? Simply to mark which playlists and podcast you want synced to your player or drive.

---

