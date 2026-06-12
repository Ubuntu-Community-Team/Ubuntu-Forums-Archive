---
title: "SVN question, working on the same document simultaneously"
date: 2009-10-08
forum: Programming Talk
---

### Post by exutable on 2009-10-08
Hey guys,

I am trying to use SVN as a means of group collaboration for my university group.  My understanding was that if we all worked on a document that we somehow could merge it?  The only thing that I can get to work is overwriting each others files(commit).

If I edit line 24 and my group member edits line 46 on the same document, shouldn't we be able to merge those revisions into one document?

I've messed around with commit and merge and can't get them to work.


Thanks,


Dane

---

### Post by johnl on 2009-10-08
Assuming you are working with a plain text file, this might work.  Any 'word processor' formats like .odt, .doc, etc are not stored as plain text and subversion will not be able to merge them.


Here is how it would work if you are working with a plain text document:

user 1 checks out the document.
user 2 checks out the document.

user 1 makes changes.
user 2 makes changes.

user 1 commits changes.

user 2 tries to commit changes.  Since the document has changed in the repository he must 'update' first.

user 2 updates.  Here is where the magic happens.  Subversion will either automatically merge his existing changes into the new document ('G') or there will be a merge conflict 'C' and he must perform the merge manually.

Once any conflicts are resolved, user 2 can commit the file.

---

### Post by exutable on 2009-10-08
Ahh OK, now regarding LaTeX.  That's basically stored in plain text right?  So svn would merge those accordingly.  Similarly it would merge .c files right?

---

### Post by johnl on 2009-10-08
Yes, latex and C source code are both 'plain text'.  (Pretty much any source code files are plain text).  

the merge algorithm deals in 'lines' -- lines inserted, lines removed, and lines changed.  If you and your friend touch the same lines, you are likely to get a merge conflict, because it doesnt know how to deal with two separate changes to the same line.  This just means you have to merge the lines manually.  If you touch different lines, it will likely merge cleanly.

You can see what your local changes consist of by doing 'svn diff <filename>'.


Hope this helps.

---

