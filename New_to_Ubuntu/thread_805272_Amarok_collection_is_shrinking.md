---
title: "Amarok collection is shrinking"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by thedaylights on 2008-05-23
Songs are disappearing from my Amarok music library. I store my music on an external hard drive, ntfs format, which I mount using ntfs-3g. Amarok was working fine with the external for a few months. Lately I noticed that when I searched for an artist I knew I had, it wasn't showing up. I can navigate to the folder on the "files" tab in Amarok and play the music that way. But it seems to be progressive - today I opened Amarok and my music collection is about a tenth of what it was.

Any clues as to what is causing this?

---

### Post by Monicker on 2008-05-23
Are you using sqlite or mysql for the amarok backend database?  Sqlite can have problems handling large collections of songs.  I had to switch to mysql because the sqlite database kept becoming corrupt.

---

### Post by Hobo Joe on 2008-05-23
Have you tried rescanning up updating your collection?

---

### Post by thedaylights on 2008-05-23
> **Monicker said:**
> Are you using sqlite or mysql for the amarok backend database?  Sqlite can have problems handling large collections of songs.  I had to switch to mysql because the sqlite database kept becoming corrupt.

I've been using MySQL from the beginning because I have a large collection of music. I love how quickly it loads up!

---

### Post by thedaylights on 2008-05-23
> **Hobo Joe said:**
> Have you tried rescanning up updating your collection?

I am currently re-scanning my collection. But it still shouldn't spontaneously drop files, should it? It's annoying if it continues to do so, and I search for a song, don't find it, and figure ah well, I guess I don't have that one.

---

