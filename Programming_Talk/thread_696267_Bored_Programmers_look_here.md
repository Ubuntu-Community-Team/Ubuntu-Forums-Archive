---
title: "Bored Programmers look here"
date: 2008-02-13
forum: Programming Talk
---

### Post by t3hi3x on 2008-02-13
Hopefully this isn't a violation of ubuntuforums agreement, but here we go:

If you're a bored programmer wishing to help out a busy few of them then I'd like you to know we need  help!

We're working on a project called teraTunes that will essentially be a music management system. It is of course under GPL. The code is not too organized, but it honestly isn't too much.

here is the temporary website until we get teraTunes.org up:

[http://jbuflashradio.com/teraTunes.org](http://jbuflashradio.com/teraTunes.org)

if you have questions you can email me <snip>Send a PM or Email through the profile</snip>

if any one has any ideas for a music management then post it!

---

### Post by melopsittacus on 2008-02-15
404, the temporary site cannot be found -- has it been moved?

---

### Post by themusicwave on 2008-02-15
Yeah I also got a 404 error.

Could you provide some more background on the project until the site is back up?

For example what does it do, what exactly is a "music management" system.  Why is it needed, how does it stack up against other i.e. Amarok?

Technical:

What language(s) is it written in, what 3rd part apps(databases and such) does it use?

I'm a programmer and may be interested.  I just need to know more.

---

### Post by t3hi3x on 2008-02-15
I'm glad people are responding.

website fix: (somethings wrong with virtual servers in apache)

[http://www.jbuflashradio.com/teraTunes.org](http://www.jbuflashradio.com/teraTunes.org)

[http://www.teratunes.org](http://www.teratunes.org) will up very soon!

The site sux very bad, as I am VERY busy, but it should have some time to work on it this week end.

The site semi-explains what it is, but I will go into more detail. I am sorry for the lack of it. There honestly a TON of thought behind it, just not too much action.

> Could you provide some more background on the project until the site is back up?

For example what does it do, what exactly is a "music management" system. Why is it needed, how does it stack up against other i.e. Amarok


teraTunes is not a player. It will will consist of one, but it is an entire music system. It involves a server running on a single computer with music tags stored in a database (mysql of course :) )

The client, will have teraTunes client and plugins for supported players, connects to the server and plays, downloads, and adds music to the remote server.

This allows you to have all of your music in one spot. In my case I have 30k songs, and I don't want to store it on all on all the computers I have.

Anyway,..
> What language(s) is it written in, what 3rd part apps(databases and such) does it use?

All binarys are written in C++ only. All webif stuff is written in PHP, and we use MySQL as our database plan.

I will post more on the website as i have time.

Thanks again for all the intrest. I am very excited about this project, and having help and 3rd party input would make it even better.

---

### Post by shawnhcorey on 2008-02-15
> **t3hi3x said:**
> Hopefully this isn't a violation of ubuntuforums agreement, but here we go:

If you're a bored programmer wishing to help out a busy few of them then I'd like you to know we need  help!

No, I'm ***_NOT_*** a bored programmer wishing to help;  I'm just a bored programmer.

I looked here and you have not achieved to undo my boredom.  Shame on you!  Next time bring some dancing girls.  Or something for bored programmers.

---

### Post by t3hi3x on 2008-02-15
> No, I'm NOT a bored programmer wishing to help; I'm just a bored programmer.

I looked here and you have not achieved to undo my boredom. Shame on you! Next time bring some dancing girls. Or something for bored programmers.

I know there isn't anything too exciting visible. The project is in its infancy. It has a lot of features that current music programs lac, and I would love to be able to sit down and put together a wonderful presentation of such.

I'm rather busy, I work 45 hours a week and then have 14 credit hours worth of school. All my other free time goes to planning my up-coming wedding.

This is why I am asking for help. As any Open Source, community supported project, it is your choice to help. I would not make anyone, after all, the best work is done by those who volunteer to do it.

And, LOL, sorry, but I think scantily dressed girls dancing around, though appeasing, is not in alignment with Ubuntu Forums' policies. However, If I be wrong, I will consider such a task. After all it's all in the name of programming.


If anyone wants to DL the code and check it out be my guest. It's simple. I have two binaries that add the code to the database. (I need to make a blank .sql file for you to add). One of the binary adds a single song, and the other recursively adds a folder. I am in the process of creating a user tool and a daemon. Though it's slow, the project is coming along.

Have fun!

---

### Post by rbprogrammer on 2008-02-15
> **t3hi3x said:**
> 
...
This allows you to have all of your music in one spot. In my case I have 30k songs, and I don't want to store it on all on all the computers I have.
...

this seems like it would be great, i have about 10 gigs worth of music, even though i only listen to about 1 gigs worth.  but even still, if i have all my music on some server, where ever it may be, does that mean i will have to download each song every time i want to listen to it??  and if the client software saves the songs on the clients machine, what is to stop me from just lugging around an external hard drive??

and if i have to download a gigs worth of music, thats going to eat up quite a bit a bandwidth for me, being away at school, having a limited connection with limited bandwidth :( .....

but all in all, it sounds like a good endeavor...

---

### Post by t3hi3x on 2008-02-16
> does that mean i will have to download each song every time i want to listen to it?? and if the client software saves the songs on the clients machine, what is to stop me from just lugging around an external hard drive??

Actually, you will have the option to stream it or download to play. You will also have the option of downloading the songs directly to your mp3 player.

I also am thinking of having an iPhone client to download the songs into the iPod on the go.

Also, using an SQL database to store the songs makes it fast. When you have a large amount of music it won't really affect the speed of searching.

In reality having a central place to store the songs, and a standardized way of doing so allows for any feasible application.

---

### Post by Zwack on 2008-02-16
So, why is this better than (for example) GNUMp3d?  Sure it doesn't use a database (just a file system) but it streams music from a single repository for you.

I'm not knocking, I'm just curious what this would have that isn't already out there.   I'm strange like that, if I don't have an itch, I don't scratch.

Z.

---

### Post by t3hi3x on 2008-02-16
GNUMp3d is a good start, but we are wanting to take it a step further: create a binary client that will allow you to add your music via the computer, and connect across the internet via a login box. It will basically what you think of Rhythmbox, but with a server backend.

---

### Post by H264 on 2008-02-16
Have you guys checked out SongBird? [http://www.songbirdnest.com/](http://www.songbirdnest.com/) It seems fairly good, at least when its mostly done.

---

### Post by t3hi3x on 2008-02-16
Wow. That looks like a huge opportunity for my project. It looks like someone my put iTunes out. I just dl'ed the current version and looks pretty nice. It also supports plugins which would make a teraTunes integrate into the player.

---

### Post by H264 on 2008-02-16
As far as I know, it is a mozilla backend, so things should be fairly easy to change, just like any other firefox plugin. What are you trying to accomplish that is different from songbird?

---

### Post by t3hi3x on 2008-02-16
teraTunes is to have a server backend with a player on the front end. Correct me if I'm wrong, but Songbird's main point is to combine the the playing with web hosted music. It's amazing don't get me wrong. I already am in love with it haha.

---

### Post by H264 on 2008-02-16
not really... but thats part of it... its main goal is to be an open source iTunes. I have not tried organizing music yet, so I don't know; it also works with online streams, but is fairly buggy last I checked.

---

### Post by t3hi3x on 2008-02-17
From what I'm seeing it's not too bad. The organizing of musics seems great. I only put about 100 songs on there, but it did well with that.

I really like the idea of it all. The support for plugins to the extent that it has is amazing. And the fact that is based off of Mozilla is awesome.

Thanks a lot for showing me that. It is greatly appreciated.

---

### Post by Zwack on 2008-02-17
Forgive me, but I still don't see the advantage to Teratunes...

Are the sound files going to be stored in the database, or just the metadata?

It's an internet frontend... so is gnump3d...

It has authentication... so does gnump3d...

It can stream music...  so can gnump3d...

It can have playlists... so can gnump3d...

It can upload new music... gnump3d can't do this, but numerous other programs can... 

It requires mysql (rather than SQLite say)... gnump3d doesn't require this ...

I'm really not trying to put you down, or off... I just don't see why a new solution is needed or what advantage it offers.  If you can't point to something and say "Look it has this benefit" then people are going to wonder why they should use it.

Search speed is not an issue for me as I store my tunes under an /Artist/Album/Tune file structure.  The largest single level is the top level and it's not that large.  If that grows to be a problem then I can either split them up alphabetically, or by Genre...

Z.

---

### Post by t3hi3x on 2008-02-17
> Are the sound files going to be stored in the database, or just the metadata?

The songs are stored in a common location, and the tag information is stored in MySQL.

> It's an internet frontend... so is gnump3d...

When I said "Internet" I meant a WAN. A web interface is nice, but that is exactly what teraTunes will not be. The web if is there, but it far from its main focus.

> It can stream music... so can gnump3d...

TeraTunes does not only stream music, it downloads.

> 
It can have playlists... so can gnump3d...

I didn't mention this, but it will not only have serverside play lists, it will have client said ones as well.

> It can upload new music... gnump3d can't do this, but numerous other programs can... 

Others may be able to do this, but that requires another piece of software, and teraTunes eases the process by making it apart of its client.

> ...I store my tunes under an /Artist/Album/Tune file structure. The largest single level is the top level and it's not that large. If that grows to be a problem then I can either split them up alphabetically, or by Genre...

In teraTunes, you don't need to worry about how its laid out becasue the SQL server will take care of it.

TeraTunes is not to be one piece of software. It is to have two main piece: a server and a client. The server is to be have a set standard that it will be easy to make any number of clients for it. From cell phones to computers, all using the SAME database of music.

---

### Post by Caduceus on 2008-02-17
I'm not able to contribute anything - my skillset is weak to say the least, but this has really inspired me to learn a language properly and start contiributing to the open source community. Thanks t3hi3x!

---

### Post by Zwack on 2008-02-17
> **t3hi3x said:**
> The songs are stored in a common location, and the tag information is stored in MySQL.

...

TeraTunes is not to be one piece of software. It is to have two main piece: a server and a client. The server is to be have a set standard that it will be easy to make any number of clients for it. From cell phones to computers, all using the SAME database of music.

Thanks, this makes it clearer where this is going and why this is useful...

Selling points, standard for clients, standard for servers.  Will there be an open standard for communication between the two?

Putting all of the files in one common location is a bad idea if this grows beyond a certain size...  It will get to the point where just trying to query the contents of that directory will slow down everything.  Can I suggest you use multiple directories and some kind of hashing algorithm to decide which directory a given file goes into?  It doesn't need to be anything complicated, just something that will spread the files out over multiple directories.

Z.

---

### Post by t3hi3x on 2008-02-17
> Selling points, standard for clients, standard for servers. Will there be an open standard for communication between the two?

I guess the best way to think of it would be:

Take a player like iTunes and take all the features it has (besides iTunes store), and let have a server backend. I guess that would be the best way to describe it. And making plugins for all of the other clients that accept them will allow for a completely universal client system.

> Putting all of the files in one common location is a bad idea if this grows beyond a certain size...

I disagree with this. Only becasue of way the databases are engineered:

there are two table that deal with music:

1 is the files table:

there are two columns: id and file

id is obvious and file points to locations of the file.

2 is the file_id table

that one has four columns: id, file_id, tag_type, value

file_id points to what song it is, tag_type uses ID3s stands for tag names and value is the value of the tag.

I disagree with your statment because there is not searching except within the SQL database. That is the entire reason behind having a database.

---

### Post by t3hi3x on 2008-02-17
Oh..I meant to thank you for challenging my ideas. It helps me understand what I am doing and better explain myself.

---

### Post by Zwack on 2008-02-18
> **t3hi3x said:**
> Oh..I meant to thank you for challenging my ideas. It helps me understand what I am doing and better explain myself.

Any time...  I really wasn't trying to put you, or your ideas down, I just wanted to know what was different about this...  If there's nothing different then why bother... As there is then it is an interesting concept, and I wish you all the best.

The issue with the size of a single directory could still be an issue...  The problem isn't with the filesystem so much as the directory structure itself.  The metadata that describes the files needs to be updated when the file is accessed.  The filesystem has to find the appropriate directory entry and update it... Which means that the filesystem has to look through the directory... Have you ever done an ls on a directory with thousands of entries in it?  It's like that.  It will start off fast but slow down as it gets big...  Obviously different filesystems handle it differently...

I'm almost tempted to run some benchmarks showing the difference for 100, 1,000, 10,000 files in a directory.

Z.

---

### Post by t3hi3x on 2008-02-18
1 TB of music come out to about 300k songs. :-D

Actually, I do plan to organize in the same fashion as mentioned above, but I guess I do not completely understand what goes on the meta data end.

---

### Post by Zwack on 2008-02-18
Metadata varies depending on the file system, but consists of things like owner, group, permissions, creation, modification and access times, and so on...

Here is a quick test of how long it takes to read different numbers of entries in directories... I can't guess at the state of the filesystem cache to guess at exactly how much of this was raw disk reads, but it should show you how much longer just 10,000 files takes to read than 1,000.

```

arm10@rogue:~/fstest$ time ls dummy100 > /dev/null

real    0m0.154s
user    0m0.000s
sys     0m0.004s
arm10@rogue:~/fstest$ time ls dummy1000 > /dev/null

real    0m0.029s
user    0m0.004s
sys     0m0.004s
arm10@rogue:~/fstest$ time ls dummy10000 > /dev/null

real    0m0.176s
user    0m0.076s
sys     0m0.000s
arm10@rogue:~/fstest$ 

```

Z.

---

### Post by t3hi3x on 2008-02-18
what fs were you using? I assume ext3. I wonder how different it would be on ntfs or fat.

Isn't the metadata stored in the allocating table?

I guess that it would be good to do a whole bunch of tests and see what the distribution is, but the differences don't seem significant.

I may do a test later.

---

### Post by Zwack on 2008-02-18
The wikipedia entry on the inode [http://en.wikipedia.org/wiki/Inode]("http://en.wikipedia.org/wiki/Inode") can probably explain it better than I can... 

But yes, this was ext3.

Z.

---

