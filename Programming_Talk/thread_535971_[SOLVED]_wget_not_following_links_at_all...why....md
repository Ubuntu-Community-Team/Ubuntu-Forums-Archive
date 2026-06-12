---
title: "[SOLVED] wget not following links at all...why...?"
date: 2007-08-27
forum: Programming Talk
---

### Post by Hopeless on 2007-08-27
hi,
```

wget --accept topic.asp?TOPIC_ID=*,forum.asp?FORUM_ID=*,forum.asp --wait=20 --limit-rate=20K
 -U Mozilla --mirror --html-extension --load-cookies 
~/.mozilla/firefox/xjg5nmlx.default/cookies.txt -e robots=off 
[http://www.somewebsite.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1](http://www.somewebsite.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1) 
```

does not download any links at all !!!!

why is this so????????

---

### Post by syssyphus on 2007-08-27
> **Hopeless said:**
> hi,
```

wget --accept topic.asp?TOPIC_ID=*,forum.asp?FORUM_ID=*,forum.asp --wait=20 --limit-rate=20K
 -U Mozilla --mirror --html-extension --load-cookies 
~/.mozilla/firefox/xjg5nmlx.default/cookies.txt -e robots=off 
[http://www.somewebsite.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1](http://www.somewebsite.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1) 
```

does not download any links at all !!!!

why is this so????????

did you single quote the url? bash wont like those funny chars (such as the &)

---

### Post by Hopeless on 2007-08-27
Ahhhhhh..no i didn't will try ...

thanks..

---

