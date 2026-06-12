---
title: "Difference between /home and /home/ on linux?"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by Delco on 2015-03-05
When specifying a folder in a terminal command, is there any difference between having a trailing slash ( / ) or not? Is /home equivalent to /home/?

---

### Post by Raman_Butta on 2015-03-05
There's no difference. Both are same.

---

### Post by bapoumba on 2015-03-05
Hmm, no, not really. Most of the time it wont make a difference, sometimes it can create havoc.
[http://stackoverflow.com/questions/18158248/should-i-put-trailing-slash-after-source-and-destination-when-copy-folders](http://stackoverflow.com/questions/18158248/should-i-put-trailing-slash-after-source-and-destination-when-copy-folders)
[http://devblog.virtage.com/2013/01/to-trailing-slash-or-not-to-trailing-slash-to-rsync-path/](http://devblog.virtage.com/2013/01/to-trailing-slash-or-not-to-trailing-slash-to-rsync-path/)
[http://unix.stackexchange.com/questions/50499/when-should-i-use-a-trailing-slash-on-a-directory](http://unix.stackexchange.com/questions/50499/when-should-i-use-a-trailing-slash-on-a-directory)

---

### Post by bab1 on 2015-03-05
> **Delco said:**
> When specifying a folder in a terminal command, is there any difference between having a trailing slash ( / ) or not? Is /home equivalent to /home/?

There is a difference.  The trailing / denotes the object is a folder not a file.

See [here]("https://cdivilly.wordpress.com/2014/03/11/why-trailing-slashes-on-uris-are-important/") as to whether it is important in your context.

---

### Post by Delco on 2015-03-05
Thanks! I had trouble using cp and I thought it was the trailing slash and it worked once I changed it.

---

### Post by oldos2er on 2015-03-05
If you use tab completion when running a cp command in terminal, it should add the trailing slash for you.

---

