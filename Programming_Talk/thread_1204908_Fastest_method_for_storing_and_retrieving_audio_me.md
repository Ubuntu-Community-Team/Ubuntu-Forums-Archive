---
title: "Fastest method for storing and retrieving audio metadata?"
date: 2009-07-05
forum: Programming Talk
---

### Post by monsterstack on 2009-07-05
I'm creating a light-weight music application similar to Minirok in Python+GTK (although I might switch to something more C-ish, possibly Vala, if I get any better at it!) specifically designed for people with *enormous* song collections. 20gb and up, that sort of thing. As this application is going to have a music library, I'm going to need a way of storing the metadata so it can be retrieved. But it needs to be fast. For instance, Amarok 1.4 uses sqlite which is meant to be fast, but it grinds to halt when I add a large number of tracks to the playlist, and so do most of the other players I've used. I don't really need any of the super cool features the popular players have, so I'm hoping I can speed things up a little. What would be the fastest way of retrieving the metadata for the player?

Any help appreciated. Apologies if the question is noobish, too!

---

### Post by txcrackers on 2009-07-05
For that amount of data, you almost will have to use a database. I do know that Amarok 2 is using "embedded MySQL", so take from that what you will...

---

