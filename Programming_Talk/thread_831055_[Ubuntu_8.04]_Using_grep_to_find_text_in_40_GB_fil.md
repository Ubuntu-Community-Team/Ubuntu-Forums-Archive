---
title: "[Ubuntu 8.04] Using grep to find text in 40 GB file - weird error"
date: 2008-06-16
forum: Programming Talk
---

### Post by Redsandro on 2008-06-16
My drive *NTFS* **MFT** was broke so it wouldn't work. But there is this raw text file that I want back. Meanwhile, the drive is completely broken, but I still have an image of **sda** I created with **dd**. The image is, as was the drive, 40 GB. I cannot mount this image as the MFT is broken and it contains 4 partitions.

Since *multiboot* was mentioned in the article, I want to search for it in the image. If I could open the image as a huge textfile, I would be able to find the article back since it's stored as raw text, ascii I think. However, No text-editor in the world will open a 40 gigabyte file.

Then I tried tried:

$ **grep -U -b -B 10 -A 10 -m 100 multi ./sda.tst.img > ./sda_test.txt**
$ **cat sda_test.txt** 
Binary file ./sda.tst.img matches
$ **grep -U -b -B 10 -A 10 -m 100 'multi' ./sda.tst.img > ./sda_test.txt**
$ **cat sda_test.txt** 
Binary file ./sda.tst.img matches
[SIZE="1"](and I tried a whole lot more variations)[/SIZE]

*sda_test.txt* keeps showing no matches, [SIZE="4"]but the real problem is[/SIZE] that the command finishes immediately. That does not make sense as searching a 40 GB file would take at least 15 minutes.

[SIZE="4"]The weirdest thing[/SIZE] I found during trial and error: when I write it like this:
$ **grep -U -b -B 10 -A 10 -m 100 '[COLOR="DarkRed"]ultibot[/COLOR]' ./sda.tst.img > ./sda_test.txt**
[COLOR="#8b0000"]Note the typo! This will not give any results.[/COLOR]
*Then* **grep** suddenly searches for *20 minutes* before saying no matches were found!

What's going on here, and how can I find my article?

---

### Post by squaregoldfish on 2008-06-16
The -U option will force grep to treat the file as binary. In this mode, grep will look for a match, and simply print "Binary file matches", then stop. My guess is that your original search term 'multi' happens to be near the front of the file, which is why you get a near-instant result.

If you use -a instead of -U, it will make grep think the file is plain text, at which point it should go through the whole file looking for matches.

Hope this helps,
Steve.

---

### Post by Redsandro on 2008-06-16
That sounds very logical. Didn't even think of that immediate match.. thanks!

But I was trying to get 100 [SIZE="1"](**-m 100**)[/SIZE] [SIZE="1"](some random number)[/SIZE] occurances into the file with the first and last 10 lines of text appended [SIZE="1"](**-B 10 -A 10**)[/SIZE] so I could see what matched what I was looking for, and use the byte-offset [SIZE="1"](**-b**)[/SIZE] to slice off about a MegaByte of the area I need, which only works in conjunction with binary [SIZE="1"](**-b**)[/SIZE].

Do you know how to get something similar that actually does work?

The manpages do not mention output is skipped while using -U. When I read again I also saw> -U
(...)
This option has no effect on platforms other than MS-DOS and  MS-Windows.I should use -u instead.

Anyway, if there's a match to *'multi'* near the beginning, text-mode matching would have the same result, right?

When archiving on that disk is finished, I'll give it another shot.

---

### Post by Redsandro on 2008-06-16
This one works! (tried on another random image) - thanks for the suggestion!
$ **grep -a -b -B 10 -A 10 -m 100 multi ./s2008.img > ./test.txt**

Two problems: 20 lines of machine language (or even 2) are a lot, since machine language doesn't do newlines. And it still finishes in 3 seconds. I think the keyword *multi* is used a million times on my drives.

**-edit-**

Anyway, figuring out a better searchword will be my puzzle for today. But do you know how I can get a good megabyte slice from the image with these weird offset numbers I get? (imagine the matched example is what I was looking for :P)

$ **cat test.txt**
2311616-R6017
2311627:- unexpected multithread lock error
2311664-R6016
--

---

### Post by squaregoldfish on 2008-06-16
I don't know for certain, but it may be that you can do something with dd.

You can use to to do a plain byte-for-byte copy, and the man page suggests you can skip chunks and specify how much to copy. It's done in blocks rather than bytes, but a bit of maths should get you there.

As I say, I've no idea whether it will work, but it's worth a shot.

---

### Post by geirha on 2008-06-17
As squaregoldfish mentions, dd is the perfect tool for this job. Something like this should skip the number of bytes ($byteoffset) you get from grep, and copy out 1MiB (1048576).
```
dd bs=1 skip=$byteoffset count=1048576 if=the_image  >result_file
```

BTW, you're not guaranteed that it will be all in one place, it could be fragmented, but you probably allready know that. 

Also, there's a tool called [foremost]("apt:foremost") in the ubuntu-repositories. It can detect certain filetypes, including html and doc, on broken filesystems, and may be able to extract some files. Install it and read «man foremost», it has examples on how to use it.

---

### Post by Redsandro on 2008-06-17
I tried finding keywords on the image today, and I really find a lot of raw text pieces, but not what I am looking for. I am affraid the file was EFS encrypted, although I was 98% sure it was not.

Too bad! :(

Thanks for helping! :)

---

### Post by Redsandro on 2008-06-17
Geirha, didn't see your reply yet. Thanks for the info. I might be able to get some other stuff back I had given up on.

---

