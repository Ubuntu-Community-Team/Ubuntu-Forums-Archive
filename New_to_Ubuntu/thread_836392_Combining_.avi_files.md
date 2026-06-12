---
title: "Combining .avi files?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by deejaypip on 2008-06-21
So I have some .avi files that I want to combine. On Windows, I used HJSplit, but I've been using Krusader ever since I switched to Ubuntu.

Here's my problem: When I try to combine the .avi files via Krusader, it says, "These files are not split." 
Well, my problem is that the movie does not play continuously: one movie is in two segments, another movie is in four segments, etc. So if I wanted to watch Movie A, which is in four pieces, I would watch piece one, then open piece two and watch it, and so on.

What do I do from here? :confused:


[For the curious, these are legal downloads of movies. I watch a lot of extremely dorky experimental films by underground artists who encourage movie downloading to spread their fan base.]

---

### Post by sdennie on 2008-06-21
I've used avimerge to do this in the past:

```

sudo apt-get install transcode

```

Then:

```

avimerge -o output_file.avi -i file1.avi file2.avi file3.avi file4.avi

```

---

### Post by roscal on 2008-06-21
If you install Java on your Linux machine,
you can run HjSplit for Java...

[http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)

It works great in my experiences.

Here's the direct download linK:
[http://www.freebyte.com/download/hjsplit/hjsplit_g.jar](http://www.freebyte.com/download/hjsplit/hjsplit_g.jar)

Once you've got the file, right click it , and choose, open with java.

---

### Post by deejaypip on 2008-06-21
Thanks. 

I used 'aptitude' instead of 'sudo-apt' (I know, I know, that was a bad decision) and I got this:

```
Package transcode is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package transcode has no installation candidate

```

---

### Post by sdennie on 2008-06-21
Have you disabled the multiverse repository or are you using an older version of Ubuntu?  Transcode is available via a new Hardy install without selecting anything.  Check System->Administration->Software Sources and make sure that the source that ends with (multiverse) is checked.

---

### Post by roscal on 2008-06-22
Um, maybe you didn't need the Mumbo,Jumbo eh?...
Like I said:
[http://www.freebyte.com/download/hjsplit/hjsplit_g.jar](http://www.freebyte.com/download/hjsplit/hjsplit_g.jar)
Download it/Right click it/ and open it with Java.
It is HjSplit.
Join /split away ....

---

### Post by deejaypip on 2008-06-22
Thanks; I'm trying both your tactic and vor's tactic. :)

---

### Post by deejaypip on 2008-06-22
Ah, yes, I did disable the multiverse respitory. It's enabled now. 

I joined together the movies with avimerge and it worked very well. The one problem is that I can't fast-forward... [shrug]

Thanks :)

---

