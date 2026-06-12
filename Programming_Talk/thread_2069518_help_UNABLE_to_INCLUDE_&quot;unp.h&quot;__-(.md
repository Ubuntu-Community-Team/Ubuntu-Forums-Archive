---
title: "help: UNABLE to INCLUDE &quot;unp.h&quot;  :-("
date: 2012-10-11
forum: Programming Talk
---

### Post by areYess platter on 2012-10-11
hi, i m starting new with UNIX NETWORK PROGRAMMING vol-1 by Richard Stevens.
almost 90% of the programs have a header file "unp.h".
I hv done all the steps mentioned in readme file. All builds are successfull.
I hv done all recommendations done at:-
_** [http://ubuntuforums.org/showthread.php?t=1559694](http://ubuntuforums.org/showthread.php?t=1559694)**_

Still my terminal returns with unable to locate unp.h.
PLEASE HELP.

---

### Post by lisati on 2012-10-11
*Thread moved to **Programming Talk**.*

---

### Post by dwhitney67 on 2012-10-11
> **areYess platter said:**
> 
Still my terminal returns with unable to locate unp.h.
PLEASE HELP.

"unp" is an acronym conjured by Stevens; it stands for Unix Network Programming.  It is not a real system header file, but a file that contains include statements for socket development related header files.

My suggestion is to refrain from relying on unp.h, and instead track down the header files that your application requires.  Perform the search for the appropriate header file(s) using the man-pages.  For example:
```

man socket

```
This will indicate that for the socket() function, you need to include <sys/types.h> and <sys/socket.h>.

---

### Post by lisati on 2012-10-13
You might also want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1559694](http://ubuntuforums.org/showthread.php?t=1559694)

---

