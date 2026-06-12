---
title: "Splitting a file based on hex header and footer"
date: 2009-10-02
forum: Programming Talk
---

### Post by Rathaeum on 2009-10-02
First of all, Thank you for your time.

I'm trying to split a big file into smaller files using a hex header and footer as the markers for the beginning and ending of the file.

000001BA440004000401  <------header
FFFFFFFF000001B9           <------footer 

I can also use the hex offsets for the small parts of the file I want to split from the big file (since I found them), but I'm not sure which of the two (hex offsets or searching for hex values) would be easiest to program in order to split the big file into the small files.

I'm currently programming in C++ so that is preferable.

---

### Post by MindSz on 2009-10-02
What's the file format? all hex? ASCII? binary? combination?

When you say 'hex offsets' what does it mean? Is it a hex-encoded integer value that points to the segment you want to split?

Are the header and footer part of the original file or do you add them to each piece of code you split?

---

### Post by Rathaeum on 2009-10-02
Well I'm saying you read the file as hex, just like every file can be represented by hex values (or binary).

So you read the file in hex and then search for the hex values (header and footer) and cut out the parts of the file you need. 

The hex offsets aren't pointers in a programming sense, but are offsets in memory that give the location of a specific byte in the file. So by knowing the offsets you know how many bytes come before, after and how many byte the section you want to take out is.

I know search algorithms and a basic understanding of programming, it's just all in binary, and I don't know if it's possible or how to do everything in hex.

---

### Post by ghostdog74 on 2009-10-02
> **Rathaeum said:**
> 
I'm currently programming in C++ so that is preferable.

you are currently taking a course in C++ programming ? if you are not, forget about using c++. For splitting files, try the csplit or split utility. check their man or info page to see their usage.

---

### Post by Rathaeum on 2009-10-03
> **ghostdog74 said:**
> you are currently taking a course in C++ programming ? if you are not, forget about using c++. For splitting files, try the csplit or split utility. check their man or info page to see their usage.

Well, I have before, and that's the only programming language I've learned so far so it's my default. I'll check out those two though, thanks for the help! :KS

---

