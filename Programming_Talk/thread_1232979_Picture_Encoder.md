---
title: "Picture Encoder"
date: 2009-08-06
forum: Programming Talk
---

### Post by Godd on 2009-08-06
I'm trying to make a prog that will be able to encode digital information into the present colors in a photo in python.

However, I can't figure out a way to glean the actual palette from the photo to modify.

I tried the histogram function in PIL however it returns data that cannot be used as it return values greater than 256. And the palette functions are very poorly documented as far as I can tell.

So in leu of this I made a palette generator, however the photos look obviously doctored and remove part of the stealth of the idea.

How can a gather the actual palette from a black and white photo?

I have included a copy of the prog. If you have any other constructive criticism I'd be happy to take it from you.

I haven't made the decoder yet, but it is on the way eventually.

SYNTAX: ./pic_encoder.py [photo] [text to be encrypted]

The photos look really funky, but it works.

You'll need PIL obviously if you want to try.

I'm sure parts of the code are obfuscated. Ha.

---

