---
title: "How to Upload &quot;recordMyDesktop&quot; files to youtube"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by metalaxesucks on 2012-01-28
I saw that you have to convert the file using this command:

mencoder out.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o out.avi

But what the hel1? My video is in my folder
"/home/(user name)"
Do I just run this command & it will automatically locate my video & convert it? :mad:

---

### Post by MG&amp;TL on 2012-01-28
Errr...no. As an 'ls' will tell you, bash(the shell) automatically opens in /home/username ($HOME), so you will already be in the right directory.

---

### Post by metalaxesucks on 2012-01-28
I ran the command as I mentioned & it converted my file, but the quality was really bad, here is a screenshot of the result of the conversion:
[https://sites.google.com/site/blahblahoinkoink/cow](https://sites.google.com/site/blahblahoinkoink/cow)

I'll just give up for now :(

---

