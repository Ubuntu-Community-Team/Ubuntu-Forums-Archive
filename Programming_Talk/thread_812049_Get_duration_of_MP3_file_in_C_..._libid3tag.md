---
title: "Get duration of MP3 file in C ... libid3tag?"
date: 2008-05-29
forum: Programming Talk
---

### Post by MicahCarrick on 2008-05-29
I'm using libid3tag in my application. I have everything I need except I'm not sure how to calculate the length... (or if I can get it using libid3tag). Can anybody point me in the right direction?

---

### Post by Bichromat on 2008-05-29
Can libid3tag do anything else than reading id3 tags ? Because I don't think the duration of a file is encoded in these tags. Maybe libmpeg3 could do what you want ?

---

### Post by sq377 on 2008-05-29
read /usr/include/taglib/tag_c.h

```
/*!
 * Returns the lenght of the file in seconds.
 */
int taglib_audioproperties_length(const TagLib_AudioProperties *audioProperties);

/*!
 * Returns the bitrate of the file in kb/s.
 */
int taglib_audioproperties_bitrate(const TagLib_AudioProperties *audioProperties);

/*!
 * Returns the sample rate of the file in Hz.
 */
int taglib_audioproperties_samplerate(const TagLib_AudioProperties *audioProperties);

/*!
 * Returns the number of channels in the audio stream.
 */
int taglib_audioproperties_channels(const TagLib_AudioProperties *audioProperties);

```

Get the TagLib_AudioProperties context like this:
```
const TagLib_AudioProperties *taglib_file_audioproperties(const TagLib_File *file);

```

Though I've found this library to be very lacking in c support (it's mainly c++).  Check out libid3.

---

