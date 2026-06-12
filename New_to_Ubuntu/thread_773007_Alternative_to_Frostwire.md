---
title: "Alternative to Frostwire?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by WBL on 2008-04-28
I'm looking for a good P2P program.  I used to use Frostwire, which was pretty good, but it won't work on 8.04 (because of the new Java, I think).

Does anyone else know a good P2P program for Ubuntu?

-WBL

---

### Post by TeoBigusGeekus on 2008-04-28
Why don't you use torrents?

---

### Post by damis648 on 2008-04-28
it works on hardy you just have to install some additional packages, i have done it... i do not remember what they were i will get back to you if you need the specifics however they automatically if you install limewire, then you can just remove it and frostwire works fine. :KS

---

### Post by WBL on 2008-04-28
> **TeoBigusGeekus said:**
> Why don't you use torrents?

I can't figure out how to get the torrents that I want.  :(

For example, while searching for a song (LEGAL, of course!) on piratebay or whatever, I get a huge file containing like 100 songs, whereas I only want one.  Stuff like Frostwire allows me to search for just one (legal) song.

Maybe I'm just too inexperienced at torrents...

-WBL

---

### Post by barney385 on 2008-04-28
[http://deluge-torrent.org/](http://deluge-torrent.org/)
 
It's in the repositories...

---

### Post by WBL on 2008-04-28
> **damis648 said:**
> it works on hardy you just have to install some additional packages, i have done it... i do not remember what they were i will get back to you if you need the specifics however they automatically if you install limewire, then you can just remove it and frostwire works fine. :KS

I might try that...though I've always heard that installing  Limewire is a "generally bad idea."

-WBL

---

### Post by perlluver on 2008-04-28
Make sure all of the applications are marked in add/remove, then look for Sun Java, install that then type in a terminal sudo update-alternatives --config java and pick sun java instead of openjdk.

---

### Post by TeoBigusGeekus on 2008-04-28
In &#956;torrent that I use through wine, whenever I choose a torrent, say an album with 50 songs, I always have the option to select which of the songs I want to download.
The problem is when some wankers zip or rar their torrents and you don't have a choice.
But on all today's torrents' sites you have the option to see a list of the contents of the torrent you want to download, so this is not a serious one...

---

### Post by i_have_a_sempron on 2008-04-28
I use Ktorrent and it also give the option to select/deselect what parts of the torrent you want to download.

---

### Post by Anduu on 2008-04-28
> **perlluver said:**
> Make sure all of the applications are marked in add/remove, then look for Sun Java, install that then type in a terminal sudo update-alternatives --config java and pick sun java instead of openjdk.

+1

Thats how I got Frostwire up and running on Hardy.

---

