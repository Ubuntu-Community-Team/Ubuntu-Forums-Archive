---
title: "rename files to play in sequence mp3"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-05-16
I have 25 files in a folder that are a talking book. Each file is named:

incidentsoftravelincentralamericavol1_25_stephens_64kb.mp3

My mp3 player (a portable device) lists them in playing order, starting with 

1

then 

10

then

11

then

20

etc. What names can I give these files so that they will play in order as you would read them in a book, ex: chapter 1, chapter 2, etc.

---

### Post by llamabr on 2012-05-16
I don't quite see the problem.  Is your mp3 player showing them out of order?

Also, be more explicit about the naming convention, and the order that your mp3 player likes.  are you saying it goes 1, 10, 11 ... 2, 20, 

If so, put  a zero in from of the single digit ones.  

Go to the dir and do a:

```
ls incident*mp3
```

and post the output

---

### Post by Vaphell on 2012-05-16
i'd try padding single digit numbers with 0 (01, 10, 11)
lexical order is not the same as numerical
in case of text strings **1** < **1**1 < **1**111111 < **2**

---

### Post by Mark_in_Hollywood on 2012-05-18
The output is posted as a screenshot. It starts, at the top of the list, with the last chapter of the book:

25

and goes all the way down to the first chapter

1

HOWEVER, in my mp3 player the play order is:

20, 21, 17, 18, 06, 07, 16, 19. 22, 23, 14, 15, 13, 24, 03, 04, 12, 25, 05, 08, 11, 02, 09, 10, 01

Is that explicit enough?

---

### Post by Mark_in_Hollywood on 2012-05-18
> **Vaphell said:**
> i'd try padding single digit numbers with 0 (01, 10, 11)
lexical order is not the same as numerical
in case of text strings **1** < **1**1 < **1**111111 < **2**

My files are already in that "sort of" numbering system.

---

### Post by Vaphell on 2012-05-18
are you sure your player is not in some 'randomized playlist' mode?

---

### Post by cryptotheslow on 2012-05-18
Does the mp3 player understand ID3 tags? If so perhaps populating the Track Number tag fields of the files would sort things out.

---

### Post by Mark_in_Hollywood on 2012-05-18
> **Vaphell said:**
> are you sure your player is not in some 'randomized playlist' mode?

I have re-read the manual. It is not set to randomized play mode.

---

### Post by Lisiano on 2012-05-18
> **cryptotheslow said:**
> Does the mp3 player understand ID3 tags? If so perhaps populating the Track Number tag fields of the files would sort things out.

Agreed. Since your files are properly numbered, it comes down to ID3 tags. Or you have a weird player that won't stop shuffling.

---

### Post by Mark_in_Hollywood on 2012-05-18
Thanks for the tip about the ID3 tags, they were completely missing.

Using the "[Audio Tag Tool]("http://www.ubuntugeek.com/tagtool-tool-to-tag-and-rename-mp3-and-ogg-vorbis-files.html")", I see that there were no Track Number "tags". I added them. Now they play in proper order. The link I gave is to a recent (2011) How-To on installing and using the tool.

I have attached a screenshot of what Chapter 25 looks like, using the Audio Tag Tool.

Thanks, community.

---

### Post by David Andersson on 2012-05-18
> **Mark_in_Hollywood said:**
> I have 25 files in a folder that are a talking book. Each file is named:

incidentsoftravelincentralamericavol1_25_stephens_64kb.mp3


**No answer**

If it have been about a music player on the computer, started from the command line, I would have suggested using **ls -v** in some way. The -v makes ls list filenames with numbers in them in a more natural order.

**One answer**

```
prename 's/_(\d)_/_0$1_/' *.mp3
```

This command puts a zero before the digit in filenames where there is only one digit between the _'s. That is, _1_ and _2_ becomes _01_ and _02_ while _10_ and _11_ are unchanged. Install package *gprename*. (If there are 100 or more files, do it in two steps.)

---

