---
title: "Python - Help choosing an appropriate data structure"
date: 2006-08-26
forum: Programming Talk
---

### Post by neilp85 on 2006-08-26
I'm working on a Python app that will populate the comment tags of mp3s using the last.fm webservice api. At the moment it's pretty limited and only grabs the tags for that specific artist. I would like to add the ability to grab album and track tags as well. 

I'm having trouble deciding on a good way to store all this data internally. The best I've come up with so far is using three seperate dictionaries: artist, album and song. The latter two would use a tuple of artist, album and artist, song as keys. I'm not sold on this solution though. I've also considered using a tree-like structure but I foresee problems with that too.

This isn't necassarily limited to Python, that's just my language of choice.

---

### Post by Van_Gogh on 2006-08-26
Having them in seperate dictionaries is a terrible idea, IMO: Is is in general always best to related data collected.

So, my approach would be lists of dictionaries, with the track list being a list too, eg.
```

music = [{"artist":"Metallica", "Album":"The Black Album", "year":1991, "tracks":["Enter Sandman", "Sad but True", ....]}]

```
The "tracks" part could of course be done using tuples if there are multiple artists on an album e.g. 

```
"tracks":[("song_name", "album", "Artist"), ....]
```

---

### Post by neilp85 on 2006-08-26
I think you misunderstood what I'm trying to accomplish. Each artist has a set of tags that describes it's music, each album by an artist has a different set of tags that describe that album, and each song by an artist has a yet another different set of tags to describe that song. I then want to take some combination of those three sets of tags to get an accurate description of the music to store in the mp3.

The scenario I described would be something like this:
```
artisttags = {'Metallica': ['metal', 'rock', 'heavy metal', ...], ...}
albumtags = {('Metallica', 'The Black Album'): ['heavy metal', 'thrash metal', ...], ...}
songtags = {('Metallica', 'Enter Sandman'): ['metal', 'hard rock', ...], ...}
```
The method you described woudln't really work to store all these different tags.

My only other idea would be to nest the dictionaries. So you would have something like this:
```
alltags['Metallica'].tags = ['metal', 'rock', 'heavy metal', ...]
alltags['Metallica'].albums = {'The Black Album': ['heavy metal', 'thrash metal', ...], ...}
alltags['Metallica'].songs = {'Enter Sandman': ['metal', 'hard rock', ...], ...}
```
Neither of these solutions is ideal in my mind. The only real difference being the method for indexing into them to grab the tags. Also, the reason I'm disregarding the relationship between song and album is that in my eyes it would cause too many problems when the album is unknown. If you know the album great, if not you can still store song tags very simply.

If anyone can offer an argument for the merits of one over the other, or better yet a more elegent solution, I'm all ears.

---

### Post by peabody on 2006-08-27
> **neilp85 said:**
> I'm working on a Python app that will populate the comment tags of mp3s using the last.fm webservice api. At the moment it's pretty limited and only grabs the tags for that specific artist. I would like to add the ability to grab album and track tags as well. 

I'm having trouble deciding on a good way to store all this data internally. The best I've come up with so far is using three seperate dictionaries: artist, album and song. The latter two would use a tuple of artist, album and artist, song as keys. I'm not sold on this solution though. I've also considered using a tree-like structure but I foresee problems with that too.

This isn't necassarily limited to Python, that's just my language of choice.

So, are you just trying to consolidate the tags from artist, album and song and put them in the comment field?  Do you care about the relationship of the tags to the artist, album or song, or can you forget about that relationship once the tags have been retrieved?  It seems like you could just generate a list of all the combined tags and distill that to all unique entries.

---

### Post by neilp85 on 2006-08-27
> **peabody said:**
> So, are you just trying to consolidate the tags from artist, album and song and put them in the comment field?  Do you care about the relationship of the tags to the artist, album or song, or can you forget about that relationship once the tags have been retrieved?  It seems like you could just generate a list of all the combined tags and distill that to all unique entries.

I had initially considered this type of approach and even started implementing it. However, the main problem with this is that the last.fm webservice only allows one request per second since they have limited resources. Assume you want to update a large batch of mp3s at once. For each file you would need to make three queries to their server. For even just one album with 15 songs that would take 45 sec as opposed to 17 if you cached the artist and album tags.

Another smaller problem with this approach is you lose the value of the tags. Each tag is weighted based on the number of users who have used it to describe an artist, album or track from 0 to 100. If you save these values with the tag you can create your own interesting functions for tagging your music. For example, use artist tags weighted 25+, album tags 50+, track tags 75+, or whatever way you saw fit.

---

### Post by peabody on 2006-08-27
> **neilp85 said:**
> I had initially considered this type of approach and even started implementing it. However, the main problem with this is that the last.fm webservice only allows one request per second since they have limited resources. Assume you want to update a large batch of mp3s at once. For each file you would need to make three queries to their server. For even just one album with 15 songs that would take 45 sec as opposed to 17 if you cached the artist and album tags.

Another smaller problem with this approach is you lose the value of the tags. Each tag is weighted based on the number of users who have used it to describe an artist, album or track from 0 to 100. If you save these values with the tag you can create your own interesting functions for tagging your music. For example, use artist tags weighted 25+, album tags 50+, track tags 75+, or whatever way you saw fit.

I confess to having zero experience with last.fm.  So you're saying that you would lookup the artist and album tags once, but frequently update the song tags?  In other words, the artist and album tags don't change much but the song tags do so you cache the artist and album tags and then only focus on updating the song tags?

Hmm, do you still plan to store the data within the comment field, or instead store that data externally and then perform something like a hash, storing the hash in the comment field and looking up the data that corresponds to that song?  I guess I'm still a little confused as to the big picture of what you're trying to accomplish.

Edit:

I think I'm beginning to see your dilema.  You're trying to decide on the the best relationship:

The most fundamental unit to your data is a song.  A song is unique and it's tied to a music file.  There's only unique songs (maybe many versions, but each is unique).  Maybe you can have several copies of the same song, but there only needs to be one set of metadata for those copies.

You also have artists.  Artists can contain many songs.  They also have many albums.

You also have Albums.  Albums can contain one artist (maybe more, depends on how last.fm does it) and many songs.

Perhaps it's best to break out the UML.

```

[FONT="Courier New"]
______                   -------
|Album|    |--------->|->|Song |
-------    |          |  ------
|songs|----|________  |  |artst|
|artst|---->|Artist|  |  |album|--> to album
-------     --------  |  -------
    ^       |songs |--|
    |-------|albums|
            --------
[/font]

```

I would think of it using objects.  A Song has a reference to an Artist and an Album, as well as a title.  An album has a list of song references, a reference to an Artist and a title.  An Artist has a list of references to albums and a list of references to songs and a name.

The tricky part of an object scheme like this is writing it to disk.  It may be too inconvenient.  But it's what I came up with.

Edit 2:

I was just looking at the pickle module documentation.  I think this could be made to work if you created one more class that contained references to every Song, Album, and Artist object you wish to write.  Then you would simply write that class, and in the process all references would be written as well.  Nice that.

Edit 3:

Well, that could be made to work, but it requires all the objects be in memory.  If you're creating something that needs to cope with thousands of songs, this could seriously gobble up RAM (hmm, this might explain amarok and banshee's memory consumption...).  Still, doing it this way makes it work, without having to resort to an RDBMS back end.

Edit 4:

Just another thing, if you're implementing the above, you would probably want to create three utility hashes, one of the artists by name, one of the song by name and one of the album by name.  That way you could quickly lookup information given just a song, album or artist name.

I was also thinking about the way you thought of this:

> 
My only other idea would be to nest the dictionaries. So you would have something like this:
Code:
```

alltags['Metallica'].tags = ['metal', 'rock', 'heavy metal', ...]
alltags['Metallica'].albums = {'The Black Album': ['heavy metal', 'thrash metal', ...], ...}
alltags['Metallica'].songs = {'Enter Sandman': ['metal', 'hard rock', ...], ...}

```



This is much cleaner than my way, but it has disadvantages.  Namely, the artist's name is used to hash.  It would be nice to use the song name, or even better, a hash of the song file, since that's more likely to be your most common lookup.  However, hashing by the song name means storing redundant album and artist information.  It also means that you must always know the artist to have access to the information.  In other words, the artist's name must always be right to get the benefit of cached information. If it's off, you basically create a new artist with redundant song information.  Since you're syncing information with last.fm however, this probably isn't as big of a problem, because the user interface could tell the user that there's no artist by that name on last.fm, maybe it needs fixing?

I dunno, this is a surprisingly tricky problem, it may be worth source diving Rhythmbox, Amarok or Banshee source code to get an idea of how they deal with the problem.

Edit 5:

I don't quit do I?  I came across this on google and it seemed right up your alley.  Maybe a bit heavy, but right your alley.  Nothing but in depth discussion on the ways to store the meta data specifically related to a media player application:

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t45220.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t45220.html)

---

### Post by dwblas on 2006-08-28
Check out Metakit for python, [www.equi4.com/metakit/python.html](www.equi4.com/metakit/python.html) - It is an SQL type database but without the overhead.  You can store different types of recs in the same database and lookup whatever you want.  Something like where rec_type="artist", band="Metallica" would give you rock, heavy metal, etc.  Unless you just want to do this for the experience, there are packages out there that are fully tested and do what you want.  Also, you can then list it through an existing app like MultiListBox.py [http://aspn.activestate.com/ASPN/Python/Cookbook/Recipe/52266](http://aspn.activestate.com/ASPN/Python/Cookbook/Recipe/52266)

---

### Post by LordHunter317 on 2006-08-28
I don't see why (ignoring some annoying data issues like cds with various artists) a tree of data starting at artist, then album, then songs is insufficent.

What you query for (song info, album info, artist info) is irrelevant to *how* you store the data.  And you have enough info to create the tree structure regardless.

---

### Post by neilp85 on 2006-08-29
> **dwblas said:**
> Check out Metakit for python, [www.equi4.com/metakit/python.html](www.equi4.com/metakit/python.html) - It is an SQL type database but without the overhead.  You can store different types of recs in the same database and lookup whatever you want.  Something like where rec_type="artist", band="Metallica" would give you rock, heavy metal, etc.  Unless you just want to do this for the experience, there are packages out there that are fully tested and do what you want.  Also, you can then list it through an existing app like MultiListBox.py [http://aspn.activestate.com/ASPN/Python/Cookbook/Recipe/52266](http://aspn.activestate.com/ASPN/Python/Cookbook/Recipe/52266)

Thanks for the info, but this looks to be a little more powerful than what I need. I would also like to keep things as simple as possible so adding extra modules is a bit of a negative for me. Like you said, this started out as a neat idea I had and thought it would give me a good opportunity to practice with using Python. Anyway, I'll keep this package in mind for another project I've got brewing (not thought out enough to begin describing it yet).

---

### Post by neilp85 on 2006-08-29
> **peabody said:**
> 
I don't quit do I?  I came across this on google and it seemed right up your alley.  Maybe a bit heavy, but right your alley.  Nothing but in depth discussion on the ways to store the meta data specifically related to a media player application:

[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t45220.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t45220.html)

Thanks for all the thought and effort you put into this problem. That thread was a good read. Some of the methods discussed were a little over my head but interesting nonetheless.

---

### Post by dwblas on 2006-08-29
In that case, I see nothing wrong with your 3 dictionary idea.  It is a good way to start at least.  You could also have a dictionay of dictionaries, but I see no real advantage to that.  Also you can use a class as a structure, but again no real advantage.  Good luck.

---

