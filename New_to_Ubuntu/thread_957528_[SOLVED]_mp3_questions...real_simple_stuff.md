---
title: "[SOLVED] mp3 questions...real simple stuff"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Tu1J4kXk8NUhMz on 2008-10-24
#1 I just ripped a CD to my hard drive. Is there some way to make sure that Sound Juicer has ACTUALLY encoded the files as mp3, and not as an ogg or something with a .mp3 extension?

#2 When I hover over my music files, I get a little talk bubble with a music note in it. What's that?

I feel like a 4 year old asking about why the sky's blue. All the same, I don't know...so I ask you! Thanks in advance!

---

### Post by Gone fishing on 2008-10-24
You need to install the mp3 codecs etc, you need to installed ubuntu-restricted-extras

---

### Post by Sarmacid on 2008-10-24
> **teamjh14 said:**
> #2 When I hover over my music files, I get a little talk bubble with a music note in it. What's that?

If you hover for long enough, you'll start listening to the mp3, kinda like a preview feature.

---

### Post by jerome1232 on 2008-10-24
As far as verifying the codec, if you pop open a terminal (Applications->Accessories->Terminal)

And type:
```
file /path/to/mp3/file
```

it should return something like this

```
file 04-metallica-the_day_that_never_comes.mp3 
04-metallica-the_day_that_never_comes.mp3: Audio file with ID3 version 2.3, **MP3 encoding**
```

---

### Post by Tu1J4kXk8NUhMz on 2008-10-24
> **Sarmacid said:**
> If you hover for long enough, you'll start listening to the mp3, kinda like a preview feature.

:-o Neat! I like Ubuntu more and more each time I use it.

> **jerome1232 said:**
> As far as verifying the codec, if you pop open a terminal (Applications->Accessories->Terminal)

And type:
```
file /path/to/mp3/file
```

it should return something like this

```
file 04-metallica-the_day_that_never_comes.mp3 
04-metallica-the_day_that_never_comes.mp3: Audio file with ID3 version 2.3, **MP3 encoding**
```

Very helpful. The readout was a bit different, but at the very least I know it's mp3. Thanks!

---

### Post by Ganonspike on 2008-10-24
Yeah the bubble will start the song as long as you hover, and depending on what ripping program you used you might have the option to specify what format to rip too.

---

### Post by sacauntos on 2008-10-26
True, as you have already verified you have the mp3 codecs, you just have to start your ripper program (in my case Sound Juicer) and look for the preferences tab (in SJ Edit-> Preferences -> Output format) and check that you have chosen mp3. You can also edit ripping profiles to encode in different formats or with different sound quality.

---

