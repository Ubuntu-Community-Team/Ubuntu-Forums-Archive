---
title: "Advice on easiest way to hack together podcast feed"
date: 2009-12-18
forum: Programming Talk
---

### Post by jimmy the saint on 2009-12-18
I can't think of a better place to put this question, so bear with me and move it to a better sub-forum if necessary.  

I use Rhythmbox to manage the few podcasts I listen to (mostly NPR news)

I would like to get a podcast for a show (all things considered), but there isn't one.  They do, however, make the show available daily in mp3 format.  I would like to integrate that into a local podcast xml file, which updates daily.

The show is available via a link in this format

```
http://public.npr.org/anon.npr-mp3/npr/atc/2009/12/20091217_atc_01.mp3
```

As far as I can tell, the only thing that changes is the date and there are usually 8-12 stories, so it would be atc_01.mp3, atc_02.mp3 etc.  There is a one day delay.

If I understand correctly, I should be able to generate an xml file, which adds the current show daily, then add that file to rhythmbox as an rss podcast feed.  I think I understand the workflow, but I have absolutely no idea how to go about implementing it.  Can someone here give me a suggestion on how to get started?  I figure this will be a fairly simple first programming task.

Thanks Very Much!

JTS

---

### Post by dhillonv10 on 2009-12-26
At a logical level, this is what you are trying to accomplish:

if (new link available)
     write it to the xml file
else 
     nothing.

Now this can be best done under python. Also there's a program called specto that gives you update when something new is available on a website, and perform certain actions, check if writing to a new file is one of them :guitar:

---

### Post by tgalati4 on 2009-12-26
Send them an email and ask them to publish a proper RSS feed for the show.

---

