---
title: "rsync update only when time and filename stamp mismatch"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Hasen_A on 2008-04-23
Hello I am running a script to update several files on my server using **rsync** once I have made changes to the crucial files on my laptop. One code line in this script is responsible for keeping my website folder up-to-date:
```
rsync -rvLz --ignore-times ~/Sites myuser@myurl.com:~/
```
My script keeps uploading ~/Sites every time I run it although the option '--ignore-times' is set. '-u' didn't do the trick either. What is wrong here?

Sincerely,
Andreas

---

### Post by gsmanners on 2008-04-23
Isn't it because of "--ignore-times" (don&#8217;t skip files that match size and time) that it does that?

---

