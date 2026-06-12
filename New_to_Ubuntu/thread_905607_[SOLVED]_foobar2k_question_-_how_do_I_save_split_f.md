---
title: "[SOLVED] foobar2k question - how do I save split flac files?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by paker on 2008-08-30
I have a 1-cd-long FLAC and a CUE. I need to split the FLAC into individual tracks. I learned from this forum that Ubuntu doesn't have a program to split FLAC. As recommended by several members, I am now running foobar2000 under wine.

I have individual tracks in foobar2k window. How do I save these in hard disk? There is no SAVE option in FILE.

---

### Post by ajgreeny on 2008-08-30
If you can manage to put up with the degrading of the flac file conversion to an mp3, convert it with **soundconverter** or **soundkonverter**, and then use **mp3splt** to split that as you wish.  mp3splt (that's not a typo, there is no "i" in the name) does the job with no further decoding or encoding so there is no further degradation to the sound, just that first one, and I doubt you will be able to hear it.

---

### Post by lcg on 2008-08-30
> **paker said:**
> As recommended by several members, I am now running foobar2000 under wine.

I have individual tracks in foobar2k window. How do I save these in hard disk? There is no SAVE option in FILE.

You need to use Foobar's converter. Just select all the files, right click and select "Convert -> Convert to ...". In the following dialog, you can select FLAC as output format.
For the converter, you need a FLAC binary as well and I am not sure whether a Linux binary will work for that. Also, since you are actually converting from FLAC to FLAC, there is no quality loss; however, you will have to re-encode, which still takes some time.

There might be an alternative, which can split files from CUE sheets directly, without re-encoding: [Medieval CUE Splitter]("http://www.medieval.it/content/view/28/53/"). I don't know how well this works in wine, though (or if it works at all).

HTH,
Lars

---

### Post by paker on 2008-08-30
> **ajgreeny said:**
> If you can manage to put up with the degrading of the flac file conversion to an mp3, convert it with **soundconverter** or **soundkonverter**, and then use **mp3splt** to split that as you wish.  mp3splt (that's not a typo, there is no "i" in the name) does the job with no further decoding or encoding so there is no further degradation to the sound, just that first one, and I doubt you will be able to hear it.

I am eventually converting to mp3 for my portable player. I will look into it. Thanks.

> **lcg said:**
> You need to use Foobar's converter. Just select all the files, right click and select "Convert -> Convert to ...". In the following dialog, you can select FLAC as output format.
For the converter, you need a FLAC binary as well and I am not sure whether a Linux binary will work for that. Also, since you are actually converting from FLAC to FLAC, there is no quality loss; however, you will have to re-encode, which still takes some time.

There might be an alternative, which can split files from CUE sheets directly, without re-encoding: [Medieval CUE Splitter]("http://www.medieval.it/content/view/28/53/"). I don't know how well this works in wine, though (or if it works at all).

HTH,
Lars

I tried Right click > Convert to. One problem I encountered was that foobar2k needed location for FLAC or LAME. I went to usr>bin, but foobar2k didn't recognize these non-Windows programs.

I will check medival. Thanks.

---

