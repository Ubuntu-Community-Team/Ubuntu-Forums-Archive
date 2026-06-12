---
title: "&quot;ValueError: incomplete format&quot; in Python"
date: 2009-03-10
forum: Programming Talk
---

### Post by poguemahone on 2009-03-10
Perhaps someone can help me with an error I'm getting in the following Python code: 

```
rowstr = '%(artist) %(album) %(track)' % \
    {'artist': artists[55], \
    'album': albums[55],    \
    'track': tracks[55]}

print rowstr
```

Here is the error:

```
Traceback (most recent call last):
  File "./mp3library.py", line 40, in <module>
    'track': tracks[55]}
ValueError: incomplete format

```

artists, albums, and tracks are lists of strings.

---

### Post by imdano on 2009-03-10
> **poguemahone said:**
> Perhaps someone can help me with an error I'm getting in the following Python code: 

```
rowstr = '%(artist) %(album) %(track)' % \
```You


artists, albums, and tracks are **lists of strings**.You have to mark them as strings when you format them.  Just stick an 's' after the close paren for each. ```
rowstr = '%(artist)s %(album)s %(track)s'
```

---

### Post by poguemahone on 2009-03-10
Thanks! That was it.

---

### Post by JoeZ99 on 2010-09-22
Dude, you're the best

---

### Post by StephenF on 2010-09-23
OT: 
Using arrays like that can result in them getting out of step with one another if care is not taken.

Maybe consider using arrays of collections.namedtuple. They can be used like this.

Creation.
```

MusicEntry = namedtuple('MusicEntry', 'artist album track')
entry = []
entry.append(MusicEntry('the artist', 'the album', 'the track'))

```
Individual access.
```

artist55 = entry[55].artist
album55 = entry[55].album
track55 = entry[55].track

```
Printing as per your example.
```

print '%(artist)s %(album)s %(track)s' % entry[55]._asdict()

```
Modification in part.
```

entry[55] = entry[55]._replace(track="Yesterday")

```
OT2:
The original thread participants are long gone.

---

