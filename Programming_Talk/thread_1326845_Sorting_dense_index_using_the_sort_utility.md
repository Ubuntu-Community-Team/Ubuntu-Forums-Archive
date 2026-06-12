---
title: "Sorting dense index using the sort utility"
date: 2009-11-14
forum: Programming Talk
---

### Post by band-aid on 2009-11-14
For my file processing class one of our projects is to generate a dense index off of a variable length master file and sort it using the unux sort command. The index is being generated fine but for the life of me I cannot straighten out these issues presented by the integer offset of the index file records being interpreted as characters by sort. The index looks like this

```

[ASCII KEY][INTEGER OFFSET][NEWLINE]

```

The records in the index are fixed length. I pad them all up to the same size to ensure this.

I am currently using 
```

system("sort -b --key0,<last character in key> index.ndx")

```

where <last character in key> is calculated and inserted into the command string and I build it. Unfortunately, some of the bytes in the integer are being interpreted as newline characters with disastrous effects. Any suggestions?

---

