---
title: "Adding a music store to RhythmBox..."
date: 2010-05-29
forum: Programming Talk
---

### Post by Baldrick_NZ on 2010-05-29
Hi all,

I know that RhythmBox now has three options of music store, the latest being UbuntuOne. Whilst these are probably very good alternatives to iTunes in some countries, for most other countries they are rendered practically to useless - particularly for commercial and local music.

So, what I was wanting to know is, is there a way of either replacing either one of the three existing stores with a local store of the users choice, OR, adding some form of GUI that the user can input the URL of a local store and select it from a list in RhythmBox (or other media player such as Banshee or Amarok) by rewriting the appropriate source code?

If so, what would be the process to change the URL inside RhythmBox?

For me, I would rather replace either Jamendo or Magnatune with our local 'Marbecks' digital music store ([www.marbecksdigital.co.nz](www.marbecksdigital.co.nz))

It'd be interesting to see what others think about offering a forth, local & customisable' music store option...

Cheers,
Baldrick

---

### Post by ssam on 2010-05-29
i think you would need to cooperate with the music provider.

it would probably be quite easy to modify the magnatune plugin. it seems to pull an XML file with all the song info, and then play the files from the address in the file

you can see the XML file in
.cache/rhythmbox/magnatune/song_info.xml

you would need the music provider to offer a similar XML file, and stream URLs for their music. the XMLfile also has a 'buy' tag with a link to the page to buy the song/album.

---

