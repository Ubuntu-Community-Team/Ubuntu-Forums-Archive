---
title: "Searching/indexing a binary file"
date: 2008-08-04
forum: Programming Talk
---

### Post by YetAnotherNoob on 2008-08-04
I have a large file with variable length records.  The data was written sequentially with a field length prefixed to the start of the record.

I want to write an application which can seek/search this file for a specific tag/content.

I am having trouble developing an alogrithm to search the file. If the records were fixed length I could easily develop a binary-chop or something similar which calculates the position by offset and record length.

But how can I randomly seek within a variable length record collection?  I would have trouble identifying what was data and record length...

Perhaps I should try and read and encode the file into another format first?

:confused:

---

### Post by dwhitney67 on 2008-08-04
Seems to me that you have already answered your question.

Having fixed record sizes would help immensely, however if you are searching for a particular record and the records are not sorted by some "key", doing the binary search wouldn't be of much help.

In cases where the records are fixed-sized and contain a "key" (such as a time-stamp or unique ID), and the records are sorted in relation to this key, then you would definitely be able to perform a binary search.

---

### Post by era86 on 2008-08-04
You could go through the file and create an index of fixed length.  As you said, convert the file first.

Are you looking to do this quickly?  Because this solution would not do so.

---

### Post by cabalas on 2008-08-05
How much control do you have over the file format?  If you really need to have variable length entries what about including an index at the start/end of the file which contains where abouts in the file the record starts.  As you already know the size of each item and presumably the number of items in the file (at the time of writing) it shouldn't be too much of a problem to add the index.

---

### Post by YetAnotherNoob on 2008-08-05
I think I will initially write some code to build a seperate index file as suggested.  Re-encoding the data file to fixed widths may result in too much disk space usage.

Each field has a unique ID, so I will store that and a "seek position" into the file. 

thanks for your ideas.

---

### Post by drubin on 2008-08-05
Maybe it is time to get a Data Base involved? :)

---

### Post by era86 on 2008-08-05
> **rubinboy said:**
> Maybe it is time to get a Data Base involved? :)

+1

I am doing a similar project and just so ya know, if the file is huge (> 2gig) make sure you look out for the type of your offset.  I'm not sure what language you are using, but make sure you store offsets in the index as 64bit integers.

Just a heads up!:guitar:

Goodluck

---

### Post by KingTermite on 2008-08-05
You could also scan the entire file at startup, create an array or hash of the records and sizes. Each entry could contain the offset to where that record is within the file.

---

### Post by era86 on 2008-08-05
> **KingTermite said:**
> You could also scan the entire file at startup, create an array or hash of the records and sizes. Each entry could contain the offset to where that record is within the file.

That would take up a huge amount of memory if we are talking about large files.

---

### Post by drubin on 2008-08-05
> **era86 said:**
> That would take up a huge amount of memory if we are talking about large files.

HUGE, if the file was 2gigs, we are talking about alot more then 2gigs of ram just to start up.... I would recommend writeing a script that ports this data over to a mysqlDB

---

