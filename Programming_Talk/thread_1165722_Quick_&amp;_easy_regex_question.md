---
title: "Quick &amp; easy regex question"
date: 2009-05-20
forum: Programming Talk
---

### Post by SoCalChris on 2009-05-20
I'm using a regex in python to parse an rss feed. How could I match a list of possible file extensions, instead of just one? For example, instead of just mpg files, I'd like to match mpg, avi, wmv, etc.

Here's what I'm using now.
```
pat=re.compile('(http://downloads.bbc.co.uk/podcasts/radio1/mills/\S+?\.mpg)') 
```

Thanks

---

### Post by ghostdog74 on 2009-05-20
you can use the alternation
```

\.(mpg|wmv|mpeg|somemore)

```

---

### Post by monraaf on 2009-05-20
How about replacing mpg with (mpg|avi|wmv)

---

### Post by SoCalChris on 2009-05-21
Thanks for the tip, but now I'm getting a new error.

```
Traceback (most recent call last):
  File "/usr/local/bin/getshow_18kids.py", line 77, in <module>
    for mpg, in tuples:

```

Here's the actual code that I'm using. The content variable contains the rss feed.
```
contents=content.split()
**pat=re.compile('(http://downloads.members.easynews.com/news/\S+?\.(mpg|avi|mp4|wmv|mkv)/\S+?\.(mpg|avi|mp4|wmv|mkv))')**
groups=(pat.search(line) for line in content.split())
tuples=(g.groups() for g in groups if g)
for mpg, in tuples:
    mpgsavefile=mpg.split("/")[-1]
    mpgsavefile=shellquote(urllib2.unquote(mpgsavefile).decode('utf8'))
    savefile='%s%s' % (savedir, mpgsavefile)
    cmd='wget -c --user=%s --password=%s -O %s %s' % (username,password,savefile,mpg)
    os.system(cmd)  

```

This is the string within the rss that I'm trying to match.
```
http://downloads.members.easynews.com/news/b/a/9/ba91526a9e5ae3732514645621b5a26e07f87b67e.mpg/18%20Kids%20and%20Counting%20-%202x13%20-%20New%20Duggars%20on%20the%20Block%20%5B480i%20DD2.0%5D.mpg
```

Thanks again.

---

### Post by soltanis on 2009-05-21
Was there an actual error message on that or was that it?

Dunno much python but I don't think you're supposed to have that comma there after the mpg in the for statement? Might not be the error though.

---

