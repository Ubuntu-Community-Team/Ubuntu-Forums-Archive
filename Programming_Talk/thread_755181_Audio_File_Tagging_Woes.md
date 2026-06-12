---
title: "Audio File Tagging Woes"
date: 2008-04-14
forum: Programming Talk
---

### Post by GenuineXP on 2008-04-14
Does anyone else think that the ID3vX tagging specifications are awful? It's very, very unfortunate that the MP3 format ever became defacto, but it is, and to maintain compatibility with my other devices (and b/c most audio files I download are MP3s), my music collection uses the MP3 format exclusively.

I'm wondering if there's a way to embed another type of tag in MP3 files without interfering with most standard programs or devices. I was actually thinking of writing my own simple specification and creating a Mono based program to view and edit, but after reading about Vorbis tags, I don't see the need. My biggest complain is using a single string to store one to many relationships, such as one song with many artists. This is so error prone, doesn't display well, and makes it hard for audio programs to search files. I hate seeing items listed as "Artist B; Artist A",  "Artist A, Artist B", "Artist B & Artist A", and "Artist A and Artist B"!

I thought, "Why not just allow multiple entries for a given field/attribute?!" Vorbis seems to do just this, with key-value pairs. Much better! But can this tagging specification be used with MP3 files without breaking them?

To be honest, I'm surprised that ID3vX tagging hasn't seen any radical changes lately; it really isn't very well designed IMHO. Anyone agree?

**EDIT:**

Sorry, I realize this may be in the wrong forum. I orignally started posting here because I've been hashing out a custom tag specification for my personal use. Of course, this would be utterly useless, at least on any other devices, because programs/devices won't have any idea how to read the information! At best, I could create a conversion tool, but that somewhat defeats the purpose. Oh well...

---

