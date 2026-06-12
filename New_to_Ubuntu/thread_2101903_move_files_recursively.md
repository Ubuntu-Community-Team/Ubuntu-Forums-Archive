---
title: "move files recursively"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Wray on 2013-01-05
I used F-spot to sort my photos (works pretty good, by the way)  However, i now have about 12K photos organized by yy/mm/dd. I want them sorted by yy/mm only.
There must be a script out there that will move the /dd files into their /mm files and delete the /dd directories.
As a complete noob, writing scripts is presently beyond my pay grade so to speak, and i'm going blind trying to do this manually.  I'm not even sure i could run a script, but i would like to give it a shot - with the guidance of this most excellent collection of geeks here,  of course!

---

### Post by Wray on 2013-01-07
> **Wray said:**
> I used F-spot to sort my photos (works pretty good, by the way)  However, i now have about 12K photos organized by yy/mm/dd. I want them sorted by yy/mm only.
There must be a script out there that will move the /dd files into their /mm files and delete the /dd directories.
As a complete noob, writing scripts is presently beyond my pay grade so to speak, and i'm going blind trying to do this manually.  I'm not even sure i could run a script, but i would like to give it a shot - with the guidance of this most excellent collection of geeks here,  of course!

[COLOR=Blue]Did i post this to the wrong forum?  Asking too much?  Violated some forum protocol? Peed in somebody's cornflakes?
So many questions, so few answers...Any kind of help is greatly appreciated.[/COLOR]

---

### Post by dannyboy79 on 2013-01-07
someone will come along sooner or later and try to help I am sure. if you want faster help, you could log into IRC channel on freenode #ubuntu or #bash to ask for helping creating a bash script.

Good luck

PS don't bump your thread more then once every 24 hours IMO. i know there's something written in the COC about bumping

---

### Post by steeldriver on 2013-01-07
Can you post the EXACT format of the directory structure / filenames?

You might be able to do it with a simple rename, something along the lines of

```
$ shopt -s globstar
$ rename -nv 's|(201[0-9]/[0-1][0-9])/([0-3][0-9])/(img.*)|$1/$2-$3|' **/*
$ shopt -u globstar
``````

.
.
.
2012/12/31/img008 renamed as 2012/12/31-img008
2012/12/31/img009 renamed as 2012/12/31-img009
2012/12/31/img010 renamed as 2012/12/31-img010
2012/12/31/img011 renamed as 2012/12/31-img011
.
.
.

```

---

### Post by Wray on 2013-01-07
I posted the thread several days ago.   The indication that that it was posted 1 day ago is WRONG.  I bumped only this AM.  
thanks for the reply  ):P   Oh, and i knew about the bumping rule  ;)

PS don't bump your thread more then once every 24 hours IMO. i know there's something written in the COC about bumping[/QUOTE]

---

### Post by Wray on 2013-01-07
> **steeldriver said:**
> Can you post the EXACT format of the directory structure / filenames?

You might be able to do it with a simple rename, something along the lines of

```
$ shopt -s globstar
$ rename -nv 's|(201[0-9]/[0-1][0-9])/([0-3][0-9])/(img.*)|$1/$2-$3|' **/*
$ shopt -u globstar
``````

.
.
.
2012/12/31/img008 renamed as 2012/12/31-img008
2012/12/31/img009 renamed as 2012/12/31-img009
2012/12/31/img010 renamed as 2012/12/31-img010
2012/12/31/img011 renamed as 2012/12/31-img011
.
.
.

```

F-spot created the directory structure        /Year
                                                                                / Month
                                                                                        /Day
and sorted the files into the appropriate directory
The date range is 2001 to 2013.
Thanks for the reply

---

### Post by Wray on 2013-01-08
[QUOTE=steeldriver;12443194]Can you post the EXACT format of the directory structure / filenames?

You might be able to do it with a simple rename, something along the lines of

```
$ shopt -s globstar
$ rename -nv 's|(201[0-9]/[0-1][0-9])/([0-3][0-9])/(img.*)|$1/$2-$3|' **/*
$ shopt -u globstar
```[CODE]
.
.
.
2012/12/31/img008 renamed as 2012/12/31-img008
2012/12/31/img009 renamed as 2012/12/31-img009
2012/12/31/img010 renamed as 2012/12/31-img010
2012/12/31/img011 renamed as 2012/12/31-img011

Thanks for the responses folks, but i discovered I had another problem: i started getting complaints that the /root was running out of space.  Looking around i found that i had stored about 25GB of photos under /root but i still had more than 200 GB of free space (Old Laptop!). Probably caused by too much messing around in "sudo"

Since this is a machine i use for playing around with only, I just blew it away and did a clean install.

Again thanks for the help all, i'm sure i will be back...

Now, to figure out how to mark this "solved" .

---

### Post by Impavidus on 2013-01-08
> **steeldriver said:**
> 
Now, to figure out how to mark this "solved" .
What about clicking "tread tools" near the top of this page and then clicking "mark this thread as solved"?

I agree it would be more straightforward to have a big orange "mark as solved" button next to the "new reply" button at the bottom.

---

