---
title: "python text to speech"
date: 2009-10-31
forum: Programming Talk
---

### Post by blairm on 2009-10-31
Hi,

I would like to have my incoming RSS feeds read by the computer using some form of text-to-speech eg Festival.
Is python a suitable language for something like that? And how big a project is it? 
I'm pretty much a beginner: have dabbled with the language in past but work commitments have prevented me spending as much time on it as I would have liked.
However, I'm not expecting to knock something like this out in a couple of days... or probably a couple of months. 
Any thoughts/advice?

Blair

---

### Post by matmatmat on 2009-10-31
Python should do it, all you will need to do is call festival with:
```

system("festival " + arg)

```
shouldn't take to long.
There's a tutorial [here]("http://www.tuxradar.com/content/make-talking-rss-feeds") (might spoil it though)

---

### Post by blairm on 2009-10-31
Thanks for that... the link to the tutorial is very useful, and given it suggests ways in which the script can be expanded I think there will still be a few challenges for me there.

Cheers,

Blair

---

