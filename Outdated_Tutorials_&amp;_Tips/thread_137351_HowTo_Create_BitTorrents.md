---
title: "HowTo Create BitTorrents"
date: 2006-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jpkotta on 2006-02-27
**Theory:**
If you don't know the basics of [BitTorrent]("http://www.bittorrent.com/"), look at the [Wikipedia article]("http://en.wikipedia.org/wiki/Bittorrent").  The parts that are relevant for us are three things: the tracker, the .torrent file, and the client.

The client is what most people are familiar with.  I use [BitTornado]("http://www.bittornado.com/") myself.  The client uses a .torrent file to talk to other clients and down/upload data from/to them.  The .torrent file is more or less a list of files to get and integrity checks for them to prevent data corruption.  The tracker is a server that acts as an intermediary for the clients.  You must have a tracker, or the clients won't find each other.  Fortunately, there are many free trackers out there.  If you have a stable internet connection (i.e. nearly always up and static ip), you can be a tracker too.

**Practice:**
For this HowTo, I will use the Demonoid tracker.  Unfortunately, it requires registration.  There are several GNU/Linux applications and distributions on this tracker (as there are on most large trackers), and someone from these forums recommended it.  Most of what follows will apply to any tracker.

*Note: Apparently, these forums don't allow links to tracker sites, so you will have to Google for it.*

***One***
[INDENT]Make a directory for the file you want to upload and put your files there.
```
mkdir descriptively_named_dir
mv file1 file2 ... fileN descriptively_named_dir
```[/INDENT]

***Two***
[INDENT]Demonoid requires an info file to be in your torrent.  You can get it from the Demonoid site, in the upload page.
```
mv Torrent_downloaded_from_Demonoid_com.txt descriptively_named_dir
```[/INDENT]

***Three***
[INDENT]Go to the Demonoid upload page.  The fields are self explanatory.  You will create the .torrent file in the next step.  Keep the page open, you will come back to it. Copy the tracker url, you will need it in the next step.  [/INDENT]

***Four***
[INDENT]You will need either the source from the official client, or the bittornado-gui package.  Other clients have similar utilities to make the torrent.  Another option is to run the command line version, btcompletedir.  See the man page on how to use it.  
Run the torrent maker.```
btmaketorrentgui
```
In the file field, clearly you should add descriptively_named_dir.  In the tracker field, add the tracker URL from the previous step.  Add a comment and hit make.  You should have a .torrent file now.[/INDENT]

***Five***
[INDENT]Upload the .torrent to Demonoid and submit the form.  It should either give an error, or more hopefully, send you to a download page for the torrent you just uploaded.[/INDENT]

***Six***
[INDENT]Download the torrent and open it with your favorite client.  For BitTornado or official client: ```
btdownloadcurses demonoid_torrent_name.torrent
```
Of course, you already have the files, so it should be done immediately.  The tracker will take a minute or two to find your client (a seeder), and update itself to say "there is a seeder for this file".  *Keep the client open for as long as possible.  At least 24 hours, but weeks is better.* Now anyone who finds the file on the tracker can download the .torrent and start downloading from you.  If your file is popular, many people will download it and seed themselves.  Congratulations, you have published on the internet.
[/INDENT]

I will be glad to modify this to accomodate other trackers.  I wanted to upload a torrent but had never done so.  I was surprised that there was no HowTo on these forums, so I figured it out with Demonoid and wrote this up.

---

### Post by bored2k on 2006-02-27
[list=1][*]I have edited out all the torrent links because we simply don't allow those.
[*]You don't creat BitTorrents, you create torrents.[/list]

---

### Post by daredevil on 2006-03-01
I dont understand the difeerence between a torrent and bit torrent

---

### Post by bored2k on 2006-03-01
[QUOTE=daredevil]I dont understand the difeerence between a torrent and bit torrent[/QUOTE]
BitTorrent is the name of the official client/network. Think of the difference between eMule and ed2klinks.

---

### Post by buildid on 2006-03-02
mldonkey in combination with sancho gui :

higlight file 
and select compute torrent 
upload torrent 
thats it ...

works fine as BT client for me..

---

### Post by Georges on 2006-03-18
[QUOTE=buildid]mldonkey in combination with sancho gui :

works fine as BT client for me..[/QUOTE]

could you also tell me with which sancho and mldonkey versions you do this?

Wehn I download a torrent, it stops seeding it as soon as the download is finished.
And I found no way to seed it again, your "compute torrent" menu I could not find.
The downloaded files are available to the edonkey network but not to bittorrent.

Georges

---

### Post by tenjin1 on 2008-04-19
This question is related to Demonoid torrent seeding....
(seems forums there are down atm)

Does anyone (or OP) know how to add another file to a directory that you have already been seeding? For example, you have been seeding a TV series and have another episode you want to add to the existing one you have been seeding. I tried adding the extra file to the directory->remove seeding torrent from client->create new .torrent file of same directory with new file in it-> edit upload page to say new file added->and add newly created .torrent to client to be seeded...only to keep getting error: "Torrent deleted or not in pool..." :confused:

---

### Post by jpkotta on 2008-04-19
> **tenjin1 said:**
> This question is related to Demonoid torrent seeding....
(seems forums there are down atm)

Does anyone (or OP) know how to add another file to a directory that you have already been seeding? For example, you have been seeding a TV series and have another episode you want to add to the existing one you have been seeding. I tried adding the extra file to the directory->remove seeding torrent from client->create new .torrent file of same directory with new file in it-> edit upload page to say new file added->and add newly created .torrent to client to be seeded...only to keep getting error: "Torrent deleted or not in pool..." :confused:

It sounds like you created the .torrent file correctly (I don't know for sure; I don't know what client you're using and I'm probably not familiar with it whatever it is).  The torrent will not automatically update on the peers' end though.  They have to grab the new .torrent file and join that new swarm.  If you made the new .torrent correctly, they won't have to download the old data again, just the new data.

---

### Post by tenjin1 on 2008-04-19
Ah Ok, thanks.

Sounds like I did everything correctly but for some reason it's not working; And I think it's because when you initially create a new torrent on Demonoid, it has a field that will ask you to browse for .torrent file and upload it....But when I go through the Edit option on my torrent posting page, there is no place to upload the newly created .torrent file (reflecting the newly added file to the directory I'm seeding), therefore it's still using the old .torrent file from the initial new torrent upload. So that probably explains why it errors out everytime I add the new .torrent file to my client to seed.

I see no other way around this in Demonoid except delete the torrent posting and start a new..because the edit has no field to upload new .torrent file.

---

### Post by Tressica on 2009-04-24
I have a question.  Is there anyway to get a tracker that won't set off a firewall like Baracuda?  I ask because I need to get stuff, and my college system is shutting me down.  It blocks peer-to-peer.  I need this stuff ASAP.  Let me know if anyone has an idea.

P.S. It blocks proxies too.  Please let me know if you have an idea for me to try.

---

