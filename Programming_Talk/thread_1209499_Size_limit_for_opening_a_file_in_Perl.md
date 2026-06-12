---
title: "Size limit for opening a file in Perl?"
date: 2009-07-10
forum: Programming Talk
---

### Post by JasonEric on 2009-07-10
All,

   I am using Perl 5.8.8 on a Mac with OS  X.

  I have written a script that will open up a text file containing lines of html code, then write that code into another file for publishing on the web.

  The problem I am having is that not all of the file is being read into the array for processing.  I was wondering if there is a size limit to the file that Perl will load up for reading?  If so, how would I go about increasing this limit?  The largest file I am trying to load up is 11928 bytes.

   Thanks in advance.

Jason

---

### Post by ghostdog74 on 2009-07-10
it is only limited by the amount of system memory you have.

---

### Post by JasonEric on 2009-07-10
Hmmm...Ok.  Thanks.  I'll check on that.  Of course, knowing me, it's probably something simple I've messed up in the code!

Thanks for the help!

---

### Post by soltanis on 2009-07-10
If it's going to be publicly displayed HTML, Perl can handle it (Perl strings, for quick reference, can contain up to around 2 GB of data; arrays of strings can obviously hold much more, limited practically by system memory, or in this case, bandwidth).

---

