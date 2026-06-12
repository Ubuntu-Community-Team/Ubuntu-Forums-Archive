---
title: "C/C++ Program Utilizing 7-zip (LZMA) and CRC32?"
date: 2007-10-15
forum: Programming Talk
---

### Post by Githlar on 2007-10-15
I have a large collection of files, each of which has a known CRC32. Now, I want to make a program that will take these files, compress them in 7z format (the best format for this file type) and THEN be able to get the CRC32 of the file inside the 7z archive for double verification purposes before deleting the original (it's really sensitive data). I know this can be done with ZIP archives (though I'm not exactly sure how, I know the CRC32 info is stored in the ZIP archive).

So, really, I have two questions:
1. Is CRC32 info stored in 7z archives?
2. How can I get started developing an application that utilizes 7zip archives? I downloaded the LZMA SDK, but the lack of documentation and commenting is horrible. I can't seem to find a place that documents the functions, typedefs, etc.

---

### Post by Quikee on 2007-10-15
Why not make it simpler. Use p7zip to compress the files and for CRC32 checking use a procedure like this: 
[LIST]
[*] compress file(s) with crc32 files (sfv)
[*] decompress files(s) to temporary folder and check the crc32
[*] delete the original
[/LIST]

This way you are sure that the file is not corrupted in the 7z file.

Its trivial to create a script like this opposed to what you want to do. Also to make things even more secure you could recheck and store a md5 or sha-1 hash, which are far better than crc32.

---

### Post by Githlar on 2007-10-15
Well, I'm working with what I have.

---

### Post by mjwood0 on 2007-10-15
> **Githlar said:**
> Well, I'm working with what I have.

I think what he's suggesting is using a script instead of a full fledged program.

If you write a script to compress them --> uncompress them to a temp folder --> verify checksums --> delete master copies, you'll end up with the same result but with just a simple script.

---

### Post by Quikee on 2007-10-15
> **mjwood0 said:**
> I think what he's suggesting is using a script instead of a full fledged program.

If you write a script to compress them --> uncompress them to a temp folder --> verify checksums --> delete master copies, you'll end up with the same result but with just a simple script.

Exactly! Sorry if I have been unclear.

---

### Post by Githlar on 2007-10-16
Isn't that a little more time consuming then just verifying the CRC32 inside the 7zip file? (Assuming the 7zip format stores CRC32's like ZIP files. I have no reason to believe that it doesn't yet). I've heard of checking CRC32's of files inside archives by reading the CRC32 from the file and decompressing the file into memory to check the integrity. To my knowledge, this can't be done with a shell script? But then again, keep in mind that I'm still kind of a n00b =P

When looking at the LZMA source, I noted that one of the headers has CRC in it. This leads me to believe that CRC32 is used somewhere in the 7zip file format - as 7zip is derived (if not identical to) LZMA.

---

### Post by mjwood0 on 2007-10-16
You're very right. If the CRC is stored in the 7zip header somewhere, it would be faster.  However, I think it's critical to see how often this script will be used and whether or not it's time critical.  

Point is, you could have written the slow script and run it a few times by now in the same time it's taken you to research and post here.  So if it was something you'd use a couple times a month, perhaps it's not worth developing an entire program for it.  Then again, it you enjoy developing code, by all means!

Just my $0.02.

---

### Post by Githlar on 2007-10-17
I found out where CRCs come into the matter - kind of. If you use a command like:

7z l -slt [archive]

It will give you a verbose run-down of all the files in the archive. It includes a CRC (Not CRC32 =() in that run-down. But the speed at which it gives you that list leads me to believe that that information is stored in the archive somewhere...

It really irritates me that I can't find more information on 7zip. It's supposed to be an open format, correct? However, every time I try to find some technical info I hit a brick wall VERY hard. It's a good thing I have a thick skull and a high tolerance for pain or I'd have given up long ago =P.

So, here's the real deal without going into too much detail. I have a common collection of files in which an XML list resides on the internet with CRC32's of these files for verification purposes. So, CRC32's are all I really have to work with or I'd just go with the CRC's. I'm writing a kind of remake for Linux of a Windows program I enjoyed that would mass-rename these files to the correct names and validate them. They only problem is that the Windows program did not have 7zip support and this particular collection of files is rather large. I'm only about a third of the way done recompressing all of them, but I've already saved 2gigs by converting to 7z format. I would love to write a GTK application that is kind of a clone of that program that would be suitable to the whole audience of that file set that is interested in saving space. The problem I'm having though is that I can't find almost any information regarding LZMA/7zip format or example code to get me off the ground.

---

### Post by Quikee on 2007-10-18
Did you look into "/usr/share/doc/p7zip-full/DOCS/" directory (especially the file" 7zFormat.txt.gz"), which is part of p7zip-full package in the repository. There you have the description of 7z format and other things. 

The source is the best documentation... look at the source of p7zip which you can also get from repository. 

If I'm not mistaken you can also get the 7z source code or examples for many different programming languages like java, c#, c++ in the [7zip SDK]("http://www.7-zip.org/sdk.html").

---

