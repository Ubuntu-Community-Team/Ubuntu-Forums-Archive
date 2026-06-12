---
title: "File format for streams of 3D data?"
date: 2011-03-04
forum: Programming Talk
---

### Post by Ultra Magnus on 2011-03-04
Hi,

I've been trying to think of a decent solution to a problem I've been having and I was wondering if anyone would be able to give any advice? 

I've been working on an optical measurement system - projecting a fringe pattern and analysing the fringe modulation to calculate a 3D surface of an object. It's used for measuring moving objects so I have around 25 3D surfaces per second. At the moment when I want to save the data I just save separate files containing height maps, masks and textures etc for each frame - if I capture > 1000 frames this can quickly become unwieldy - there must be a better way of doing this.

I've had a bit of a look and there are a number of 3D file formats but I couldn't find any that allowed you to save a stream of data, essentially like an AVI except for 3D mesh data. Is there a way to do this? Compression would be nice (although would have to be lossless since the data is for use in measurement) but just being able to save in a single file would suffice for the moment.

Thanks in advance,

James

---

### Post by PaulM1985 on 2011-03-04
I am not aware of anything like this that exists.

Have you looked into Huffman Trees?  It enables Huffman encoding, which is used to compress images for the PNG lossless image file format.

You could encode each frame and append it to the file, with some separator included so you can tell the difference between frames.

Paul

---

### Post by foxmuldr on 2011-03-04
> **Ultra Magnus said:**
> Hi,

I've been trying to think of a decent solution to a problem I've been having and I was wondering if anyone would be able to give any advice? 

I've been working on an optical measurement system - projecting a fringe pattern and analysing the fringe modulation to calculate a 3D surface of an object. It's used for measuring moving objects so I have around 25 3D surfaces per second. At the moment when I want to save the data I just save separate files containing height maps, masks and textures etc for each frame - if I capture > 1000 frames this can quickly become unwieldy - there must be a better way of doing this.

I've had a bit of a look and there are a number of 3D file formats but I couldn't find any that allowed you to save a stream of data, essentially like an AVI except for 3D mesh data. Is there a way to do this? Compression would be nice (although would have to be lossless since the data is for use in measurement) but just being able to save in a single file would suffice for the moment.

Thanks in advance,

James

Have you considered a straight-forward FOSS database like Mysql?  It handles binary large objects (blobs) and can store whatever you "dump" into them, and they'll be accessible with SQL statements, and querieable through standard forms.

Apart from that, your needs indicate a container form that's designed specifically for streaming media, and that relates to one of the forms already widely in use.

Since you're dealing with a unique set of data, it's likely you'll just need to write one.  But, depending on the scope of your long-term goals, the Mysql database would likely be the easiest to get setup and continue to use for files up to several hundred gigabytes.

- Rick C. Hodgin

---

