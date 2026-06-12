---
title: "Read pdf in c"
date: 2009-07-17
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-17
i need to create a program which can read information form variety of file formats like pdf,doc etc and then use this data which i read in further applications.How shall i go abut it.

---

### Post by nvteighen on 2009-07-17
What you need is to make your program understand those formats so it can manipulate them... Ok, but that will take you years, specially because .doc is proprietary and those are very complex specifications... not just a trivial comma-separated-values text file :D

So... Try looking for some library that allows you to do that... For the .doc format, I guess you'll have issues in getting an open source library due to MS's software patents and copyright policies. 

For PDF, I see there's something called GNUpdf (install libgnupdf-dev package). [http://www.gnupdf.org/](http://www.gnupdf.org/) though it doesn't seem to be the library used by popular GNU/Linux PDF readers like Evince. No idea how it performs and it looks (from the API docs) to be a fairly complex library to use.

So now, what are you trying to accomplish?

---

### Post by c0mput3r_n3rD on 2009-07-17
> **nvteighen said:**
> 
So... Try looking for some library that allows you to do that... For the .doc format, I guess you'll have issues in getting an open source library due to MS's software patents and copyright policies. 


You would probably have to find a library that uses open offices .odt format instead .doc or .docx which like he said, is in a copyrighted and encrypted format.

---

