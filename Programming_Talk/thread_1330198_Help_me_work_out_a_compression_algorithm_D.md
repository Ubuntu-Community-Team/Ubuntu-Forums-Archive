---
title: "Help me work out a compression algorithm :D"
date: 2009-11-18
forum: Programming Talk
---

### Post by Kazade on 2009-11-18
Hi,

Recently I started [this thread]("http://ubuntuforums.org/showthread.php?t=1327128") about an old game that I've started playing again. If you follow that thread you'll see I asked the developer to open source it, but they were unable to because they no longer own the rights to the code.

So, I thought I might just write a clone of the game. Writing a clone would be much easier if I could load the original assets during development. The only problem is that these original assets are compressed with some kind of algorithm, each compressed file has an added ".fla" extension.

I've started deciphering the compression, but I could do with some help from anyone that fancies a challenge. You can download the WarGames demo [here]("http://www.kazade.co.uk/downloads/wargames.zip"). If you install it through Wine (or on Windows) you can find the compressed files in C:\WarGamesDemo\qData. The key to working out the compression algorithm is that one single file is duplicated in both compressed and uncompressed versions (wgsLogo.bmp and wgsLogo.bmp.fla). By opening both in Ghex I've determined the following:

Header
First 4 bytes are always "FLA2"
The second 4 bytes are the length of the original file in bytes
The next byte is unknown, in the wgsLogo.bmp.fla it's 5, in other compressed files it's 2. This might be a key to the decompression process.

Data
Data seems to be read until there is some kind of repetition.  For example:
42 4D 06 B7 00 00 00 00 00 00
becomes
42 4D 06 B7 00 03 01

The next set of data is:
36 00 00 00 28 00 00 00

This becomes when compressed
36 01 04 41 28 01 04

Next chunk is:
2C 01 00 00 34 00 00 00
This becomes
2C 01 00 00 34 01 08 13

There is also a large chunk of the uncompressed file that repeats FF 00 FF FF 00 FF FF 00 FF etc., this becomes FF 00 FF 0F 03 0F 03 0F 03 0F etc. That section is probably a pretty good place to work out the pattern.

When the algorithm is understood I can write a C library to extract it, any help you guys can give me would be great :D

---

### Post by CptPicard on 2009-11-18
It's probably pigzip:

[IMG]http://www.hackles.org/strips/cartoon310.png[/IMG]

:)

Anyway it doesn't seem to be a straightforward run-length encoding... does the file contain something that would look like a dictionary? Does the "file" command just say "data"?

---

### Post by Kazade on 2009-11-18
> **CptPicard said:**
> It's probably pigzip:

[IMG]http://www.hackles.org/strips/cartoon310.png[/IMG]

:)

Anyway it doesn't seem to be a straightforward run-length encoding... does the file contain something that would look like a dictionary?

After the 9 bytes that make up the header it goes straight into the compressed file data. It looks like some kind of RLE but I think some of the bytes (for example 0F 03 in the example I mentioned) refer back to previously found data I'm not entirely sure how yet. 0F is likely some index into the previously found "table". 

I guess I can attach both files here as they come with the demo which I linked, so I have done. You'll have to remove the .txt extension from the .fla file, that's just there so ubuntuforums.org will upload it.

> 
Does the "file" command just say "data"?

I'm not sure what you mean?

---

### Post by CptPicard on 2009-11-18
I meant this...

```

eneva@pikkuapuri:~/Desktop$ file wgsLogo.bmp.fla
wgsLogo.bmp.fla: data

```

No help there though.

---

### Post by Kazade on 2009-11-18
> **CptPicard said:**
> I meant this...

```

eneva@pikkuapuri:~/Desktop$ file wgsLogo.bmp.fla
wgsLogo.bmp.fla: data

```

No help there though.

Ah, I see what you mean :)

---

### Post by denago on 2009-11-18
Maybe try asking the developer you contacted about the compression method used.  He might not have the ability to open source the program, but he might be able to tell you how the assets are compressed :p

---

