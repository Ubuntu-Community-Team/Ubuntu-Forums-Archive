---
title: "[SOLVED] E-Book &amp;amp; Palm Question"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by stuart264 on 2008-07-07
Hope this is the right place for this as I am fairly new to Ubuntu.

I have been using a Palm Tungsten to read e-books using the Mobipocket software in windows which will export directly to the pda or if I insert the sd memory card into the card reader slot.

Question is are there any apps in Ubuntu that will do this i.e. export an e-book to either an SD memory card or to a palm pda>

Stuart

---

### Post by ezekiel000 on 2008-07-07
Not as far as I know I use eReader:
[http://www.ereader.com/ereader/software/product/15003_pro_palm.htm](http://www.ereader.com/ereader/software/product/15003_pro_palm.htm)
for reading eBooks and MakeBook:
[http://www.ereader.com/ereader/software/product/15097_makebook.htm](http://www.ereader.com/ereader/software/product/15097_makebook.htm)
For creating eBooks.

This attached file includes MakeBook and help files to use it, and a sample eBook source file (remove txt extension).

eBooks go in \PALM\Books\

That's the best eBook system that is compatible with Linux and PalmOS as far as I know.
There is also Plucker but this is more of Browser than an eBook reader.

---

### Post by adewale on 2008-07-07
You can also take a look at this [http://www.mobileread.com/forums/showthread.php?t=12559](http://www.mobileread.com/forums/showthread.php?t=12559)

---

### Post by stuart264 on 2008-07-08
I tried e-reader initially when I first got my palm, its OK but the PC front end is a bit "twitchy" about what formats it accepts so I started using Mobipocket for Windows as that seems to accept a lot more imported formats.

I was looking at installing Mobipocket under Wine and seeing if it runs that way on Linux as that would solve a lot of my problems however I am still trying to work out how to get the exe installation files out of the .msi package.

---

### Post by stuart264 on 2008-07-08
Well that worked easily

For anyone that wants to know how you just download the Mobipocket file to your desktop after installing Wine and enter the following, seems to run pretty well but I still have to copy all my e-books across the network from my Windows machine


```
CD Desktop
wine start mobireadersetup.msi 
```

---

### Post by adam s on 2008-11-11
You can also install the "E-Book Reader" that is in Synaptic.

Adam

---

