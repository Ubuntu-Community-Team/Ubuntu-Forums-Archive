---
title: "lurking in the shadows"
date: 2011-01-29
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-29
I'm having great fun creating high resolution image formats that use floating point pixel components. And the fun thing is you can expand out the dark levels to see all sorts of detail that you never thought were there. Sadly I just have a cheap camera and I  knowing nothing about photography :(

Anyway apparently there are cameras that produce "raw" format images with 12 and even 14 bits per color component!
So I copied some off the web to play with. See here is picture with not that much contrast but taken with an awesome camera.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182227&stc=1&d=1296293355[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=182228&stc=1&d=1296293479[/IMG]

Adjusting levels I manage to see the man's face but the problem isn't in the levels that the camera is recording... it seems to be the amount of noise that is limiting... so IDK... anyone have a view on what use high resolution color space actually might be in practice?

---

### Post by talonmies on 2011-01-29
> **worksofcraft said:**
> 
Anyway apparently there are cameras that produce "raw" format images with 12 and even 14 bits per color component!
Not per colour component. Just 12-14 bits of luminosity. An interpolation algorithm is required to convert the luminosity data back into RGB using knowledge of the spectral filtration characteristics of the image sensor. The result has much less than 12 or 14 bits of data per colour channel.

---

### Post by CptPicard on 2011-01-29
The point is, as far as I understand it, storing all the data that comes off the sensor, so that various kinds of post-processing can then be applied when necessary. When you save something like a JPEG, then that's it, you've already lost a lot of the original...

---

### Post by nvteighen on 2011-01-29
Er... JPEG is a lossy compressed format, so you have to expect this kind of behaivor. It works well with natural photography because in photos you don't need keep record of every single particle in order to get high quality; you just need a decent resolution and that makes it work.

PNG in the other hand is a lossless compressed format. That's why it's used a lot for digital painting, e.g. There you need to keep track of every single pixel and can't afford any kind of noise.

Read this, of interested: [http://en.wikipedia.org/wiki/Portable_Network_Graphics#Comparison_to_other_file_formats](http://en.wikipedia.org/wiki/Portable_Network_Graphics#Comparison_to_other_file_formats)

---

### Post by Zugzwang on 2011-01-29
> **worksofcraft said:**
> 
Adjusting levels I manage to see the man's face but the problem isn't in the levels that the camera is recording... it seems to be the amount of noise that is limiting... so IDK... anyone have a view on what use high resolution color space actually might be in practice?

If combine have a high shutter time with low sensivity of the sensor and a bright motive, the amount of noise will be significantly lower. For your example photography, the setting didn't seem to be sunny. So you can expect that in some situations, the amount of noise is lower and thus "high resolution color space" is more useful.

Then, when taking a photograph, you typically have to decide on the brightness of the motive in advance. If you have 12-14 bits of luminosity and in the end only need 8 bit per colour component, you can delay part of the settings you would normally apply to the camera before taking the picture to the later step of extracting the JPG/PNG/whatever picture from the RAW data on your PC. This gives you some flexibility as, for example, you might sometimes only need a small version of the picture, but you want to have it brighter. Then, the amount of noise you have in your example might be well acceptable. Sometimes, however, the amount of noise must be low but details in the darker parts of the picture might be ok. You do not always know in advance what you will use the picture for!

---

### Post by worksofcraft on 2011-01-29
Thanks for all of those replies :)

I have been reading more about the technology behind digital photography and about the [raw image data formats]("http://en.wikipedia.org/wiki/Raw_image_format"), evidently affected by different technologies of competing manufacturers.

It does seem to me now that the native YCrCb format of jpeg is the right way to encode these images and I can't fault the concept of discrete Cosine Transforms for data compression.

However when we go to extract the picture into 8 bit RGB components that can have further quantization restrictions due to gamma corrections etc... I feel the original potential is being lost.

This is especially bad for 8 bit monochrome when the original Y component in the jpeg might have had 12 or even 14 bit accuracy. I think images will rapidly deteriorate due to cumulative rounding errors when manipulating them with integer arithmetic especially of the 8 bit variety :shock:

---

### Post by worksofcraft on 2011-01-30
I was also reading about the new JPEG2000 standard and tried to fathom how to get normal RGB images in and out with a library known as [JasPer]("http://www.ece.uvic.ca/~mdadams/jasper/")... but so far I failed :(

It seems to me what we really want to store will have a logarithmic scale on the Y (luminance) component so that the relevant precision of changes will be proportional to the pixel brightness. OTOH we need linear scales on the Chroma signals so that they simply identify what proportion of that brightness must go to each component.

The older JPEG standard is nearly spot on with this. It encodes a Y'CrCb space which is using gamma corrected luminance instead of a logarithmic one... but both of those have kind of similar curvature.

The reason noise is so dominant on that dude's face is because I expanded a very narrow range of brightness levels to fill the full spectrum. Thus tiny variations in brightness show up as large jumps and presumably there would be no pixels at colors levels in between. Advanced cameras today are recording the same image with multiple exposures so that there will be one that was captured with a more appropriate sensitivity and then noise won't be such a problem!

p.s. Meanwhile I also got a file full of true random noise from [www.random.org](www.random.org) and put it in a picture as the rgb values. When I plotted the curves with  GIMP I was not expecting to get the curve shown :shock:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182386&stc=1&d=1296467094[/IMG]
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Gamma06_600.png/220px-Gamma06_600.png[/IMG]
 It looks mysteriously suggestive of a gamma distortion curve of old fashioned CRT devices :confused: I would love to understand why that should be, so any explanations will be welcome :)

---

### Post by worksofcraft on 2011-01-31
The problem with other people's software is that there is no telling what it might be doing... in this case those curves in gimp:

I made my own brightness histogram from the same random noise image and it actually looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182393&stc=1&d=1296473729[/IMG]

Evidently the gamma thing was a complete red herring as gimp was simply truncating my overall pixel brightness levels and showing just the first part of the curve.

---

### Post by worksofcraft on 2011-02-13
I'm still playing with graphics and experimenting with full floating point logarithmic luminance component while turning chroma into a very simple proportional distribution signal...

I'm making a modified jpeg decoder/encoder and it does do standard jpeg too but it really is incredible how much of that luminance signal is being lost in the standard :shock: I know jpeg decoders are 10 a penny these days but you do learn a fair bit actually implementing one ;) IDK what happened to posted images on the forum cuz even my generated png files don't display this end :(

Anyway, I digress... the question is about free software vs patents: Some realy good algorithms have been patented and I don't want to pay royalties on my free software, so one way round it... I think... is to build a brute force lookup table...

What would you do:
[LIST=1]
[*]simple sequential binary tree algorithm as per Huffman's design
[*]efficient patented algorithm
[*]brute force 1/2 Megabyte lookup table
[/LIST]

---

### Post by t1497f35 on 2011-02-14
Afaik Gimp 2.8 is supposed to fix (at least partially) the issue about losing image quality while editing or so. It was planned to be released about 2 months ago, sadly still waiting.
Can you attach the raw/original image of that guy walking down the road in first post?

---

### Post by worksofcraft on 2011-02-14
> **t1497f35 said:**
> Afaik Gimp 2.8 is supposed to fix (at least partially) the issue about losing image quality while editing or so. It was planned to be released about 2 months ago, sadly still waiting.
Can you attach the raw/original image of that guy walking down the road in first post?

That would be good... but the way I see it is that jpeg is only storing and quantizing linear 8 bit luminance, so all the DCT errors both in the luminance and chroma signals end up just looking like noise :(

That image was one from  URL="http://imaging.nikon.com/products/imaging/lineup/digitalcamera/slr/d7000/sample.htm"]Nikon Sample Images web site[/URL]

---

