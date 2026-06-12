---
title: "Why can't you delete a file from /tmp despite all permissions being there?"
date: 2020-04-14
forum: Programming Talk
---

### Post by php4fan on 2020-04-14
I wanted to reply to this thread:

[https://ubuntuforums.org/showthread.php?t=1225745](https://ubuntuforums.org/showthread.php?t=1225745)

but besides being wrongly marked as "solved", it's closed (why one would even want to close threads in a forum is beyond my understanding).

A workaround was suggested, but does anyone know the actual answer?

That is, why can't one user call unlink('/tmp/somefile') if the file (belonging to another user) has 666 permissions and /tmp has drwxrwxrwt permissions?
Why can you do that with a file within a subdirectory of /tmp but not in /tmp?

---

### Post by TheFu on 2020-04-14
a) these forums for 1 person, 1 question.  That is different from many other forums.  The "me too" stuff added to an existing thread seldom actually means the 2nd or 5th person is actually having the same, exact, issue.
b) Closing threads limits the never-ending spam these forums fight minute by minute, hour by hour, day by day.

Onto the specific question about permissions.
```
drwxrwxrwt
```
see that 't' at the end?  it makes all the difference.  When you review your Unix permissions training, it clearly says that only the owning userid of a file inside a directory with the +t bit set can delete the file.  [https://en.wikipedia.org/wiki/Sticky_bit](https://en.wikipedia.org/wiki/Sticky_bit)
> When a directory's sticky bit is set, the filesystem treats the files in such directories in a special way so only the file's owner, the directory's owner, or root user can rename or delete the file. 

So, it is working as designed.

---

### Post by The Cog on 2020-04-14
Because if the 't' bit on the /tmp directory. It's called the sticky bit. See Usage in [https://en.wikipedia.org/wiki/Sticky_bit](https://en.wikipedia.org/wiki/Sticky_bit) . Only the file owner can delete files.

Edit: Ninjad by TheFu. Again.

---

### Post by Skaperen on 2020-04-17
that workaround is a viable solution, but i am concerned about security. why are these 2 different userids being used like this?  a correct design would have the exact same userid in effect for both operations and be the owner of the file.  whatever network facing service this is, it should have a web server and database engine dedicated to it with everything running under the userid designated for that service.  while multi-user internal services are possible, they have many limitations, such as dealing with this /tmp file.  the kernel is a player in things like this and it works with raw numbers for so many things.

also,

delete-then-write should not be used to replace a file in all cases i can think of.  instead, write-temporary-then-move should be used.  if you have a good reason to use the former method, teach me about it.

---

