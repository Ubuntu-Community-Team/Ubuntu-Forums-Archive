---
title: "Vim How to increase a value in search replace command"
date: 2011-03-28
forum: Programming Talk
---

### Post by ivancp on 2011-03-28
Hello,

I have this text in a source file:

```
/* Script: A script
 * Author: xyz
 * Date-created: 28 mar 2011 18:47:07
 * Last-modified: 28 mar 2011 18:47:19
 * Revision: 12
*/
```I want to update the Revision line when I save the file, 
I have this search-replace command 

s/\(Revision:\) \(\.*\)/\1 **\2**/g

How to increment the value of \2 match?

From:  Revision: 12
To:  Revision: 13

Regards.

---

### Post by lloyd_b on 2011-03-30
Try this one:```
s/Revision: \zs\d\+/\=submatch(0) + 1/
```It will search for "Revision: " followed by an integer value, replacing it with "Revision: " and the integer value plus one.

Lloyd B.

---

### Post by ivancp on 2011-04-10
Thank you!

---

### Post by geirha on 2011-04-11
Why not use a VCS that can do that for you?

---

