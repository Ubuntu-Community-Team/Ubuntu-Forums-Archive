---
title: "Bash script &gt; file permission denied"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2013-02-20
Hi guys

I'm writing a bash script that in several places writes to the end of a file.

I was using echo "text" >> file

this works fine for files I own but for files that belong to root I got permission denied

I solved this by doing a chmod on the file before editing and then back again after.

I then hit the problem that in some cases the file may not exist in the fist place and I hit permission denied again.

I could of course change the permissions on the folder this time or I could copy in a file and change its permissions.

I'm thinking there has to be a much more elegant solution to this though. Does anyone have a better way of doing this?

---

### Post by The Cog on 2013-02-20
Your problem is that the shell sets up the redirection before calling sudo, so that you still don't have rights to the output file.
This should do the trick:
```
sudo sh -c "echo txt >> /foo"
```

---

### Post by bigmonmulgrew on 2013-02-20
yeah I managed to find a note saying thats why it did it while googling but not a solution, thanks for that I'll try it.

I knew there must be a better way.

---

