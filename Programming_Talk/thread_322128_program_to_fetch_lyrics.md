---
title: "program to fetch lyrics?"
date: 2006-12-20
forum: Programming Talk
---

### Post by earobinson on 2006-12-20
Anyone know of a python program that I can call with a song title and artist that will return the lyrics? The only program I know of is in /usr/lib/rhythmbox/plugins/lyrics/lyrics.py

But I'm unable to use that since I cant call it from the command line.

All I want is to call it from the command line so I can redirect the answer to a file.

eg
```
<program> tool "the pot" > tool-the-pot.txt
``` would sent the lyrics to the file tool-the-pot.txt

Thanks

---

### Post by po0f on 2006-12-20
earobinson,

Do you know of a web site that has a lyrics DB available for browsing?

---

### Post by earobinson on 2006-12-20
the program I linked seems to use [http://api.leoslyrics.com/api_search.php?auth=Rhythmbox&artist=%s&songtitle=%s](http://api.leoslyrics.com/api_search.php?auth=Rhythmbox&artist=%s&songtitle=%s) ... the program is installed with rhythmbox but I will post it for anyone who wants to see it ... it is under the gpl after all

edit: the program is found here [http://www.edwardandrewrobinson.com/lyrics.py]("http://www.edwardandrewrobinson.com/lyrics.py")
Can you guess my full name?

---

### Post by po0f on 2006-12-20
earobinson,

Look at the web site name (api.leoslyrics.com).  Looks like you have to sign on to be a dev to get access to their service through a third party program (normal searching through the site as a regular user works).

---

### Post by earobinson on 2006-12-20
well thats the site rhythmbox uses, and I have the source rhythmbox uses so it should be possible no?

---

### Post by po0f on 2006-12-20
earobinson,

Can you run it as a stand alone app?
```
[FONT="Courier New"]$ python lyrics.py[/FONT]
```

[EDIT]

I'm stupid, disregard that.  :rolleyes:

---

### Post by earobinson on 2006-12-20
no standalone app ... was hoping for a link to another prject , dont think Im gooing to be able to mod that code

---

### Post by po0f on 2006-12-20
earobinson,

It looks like the LyricGrabber class in that file doesn't rely on a GUI to work.  Maybe you could write a script that imports lyrics.LyricGrabber and start from there?

---

### Post by Tomosaur on 2006-12-20
May not be entirely what you're looking for, but Amarok can display lyrics to whatever song is playing, via the 'Context' menu. It doesn't save the lyrics though, and occasionally it gets confused when there are a few interpretations of the lyrics, and asks you to pick one. It's pretty cool though.

It wouldn't take very long to write a script/prog which would do this, provided you had access to a website which stores lyrics.

---

### Post by earobinson on 2006-12-21
I think im going to end up writing one, and if there is any intrest I will post the program here

---

### Post by UbuWu on 2006-12-21
Part of the script [here]("http://forums.xbox-scene.com/lofiversion/index.php/t428829.html") might be useful.

---

### Post by Get_Ya_Wicked_On on 2006-12-21
nice song example!

---

### Post by earobinson on 2006-12-21
> **Get_Ya_Wicked_On said:**
> nice song example!
Thanks!

---

### Post by earobinson on 2006-12-24
Anyone else now having problems with the plugin for rhythmbox to fetch lyrics? Or have I spamed that site so much they blocked me?

---

