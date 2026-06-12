---
title: "[SOLVED] Rhythmbox won't say rude words  :("
date: 2008-08-03
forum: New to Ubuntu
---

### Post by t0p on 2008-08-03
Rhythmbox is censoring the titles of the foul-mouthed music I like!  For instance, on the Serj Tankian album *Elect the Dead*, there's a track called "Beethoven's <bleep>" (expletive removed for sake of sensitive forum users) - but Rhythmbox says it's called "Beethoven's C***"!  Now, this may be all fine and dandy for Ubuntu's younger users - but I'm over 21! Well over 21!! And I reckon the lil kids should be using Edubuntu, anyway! ;)  But seriously, can I turn off the censor?  How?

**EDIT:** Amarok, Totem and vlc are also curtailing my freedom of speech!!  Nautilus is brave enough to say it as it sees it... but Nautilus doesn't play the tunes! :(

---

### Post by billgoldberg on 2008-08-03
Really, that's the first I hear of it.

And frankly I have no idea why it's happening.

All I can say is it isn't happening here.

There are some other equally good music players you can try:

--

Exaile, bmpx, banshee, audacious, ...

But I'm thinking it are the settings in your pc that do it, not the players itself.

Either way, you could try those.

I going to ask in the irc rooms for you.

---

### Post by billgoldberg on 2008-08-03
From what the people in the irc room told me, you're metadata (Id3 tags, ...) has been censored by whatever program created them.

I suggest you install "tagtool" and change it.

```
sudo apt-get install tagtool
```

---

### Post by Sef on 2008-08-03
<snip>

---

### Post by t0p on 2008-08-03
> **billgoldberg said:**
> 
There are some other equally good music players you can try:

--

Exaile, bmpx, banshee, audacious

Thank you.  I shall try 'em out now.

> **billgoldberg said:**
> 
But I'm thinking it are the settings in your pc that do it, not the players itself.

But what kind of settings would do that?  Nautilus doesn't mess like that (thought I guess that would be pretty uncalled-for in a file manager, monkeying with file names) and neither do my web browsers.


> **billgoldberg said:**
> 
I going to ask in the irc rooms for you.

Yeah cheers.

---

### Post by t0p on 2008-08-03
> **billgoldberg said:**
> From what the people in the irc room told me, you're metadata (Id3 tags, ...) has been censored by whatever program created them.

I suggest you install "tagtool" and change it.

```
sudo apt-get install tagtool
```

Wow that was quick!! Thanks I shall try it.

---

### Post by t0p on 2008-08-03
**Thanks billgoldberg!!!**  You were right, it's all in the tags, darn 'em!!

Now I just gotta figure out how to edit the flamin' things... the tagtools manpage ain't too informative... :(

---

### Post by billgoldberg on 2008-08-03
> **t0p said:**
> **Thanks billgoldberg!!!**  You were right, it's all in the tags, darn 'em!!

Now I just gotta figure out how to edit the flamin' things... the tagtools manpage ain't too informative... :(

Tagtool comes with a gui.

(alt +f2 and enter tagtool)

It's pretty easy to use.

---

### Post by JillSwift on 2008-08-03
> **t0p said:**
> **Thanks billgoldberg!!!**  You were right, it's all in the tags, darn 'em!!

Now I just gotta figure out how to edit the flamin' things... the tagtools manpage ain't too informative... :(
Get "Audio Tag Tool", it's a GUI app and very nicely done. (In Add/Remove apps.)

---

### Post by t0p on 2008-08-03
> **billgoldberg said:**
> Tagtool comes with a gui.

(alt +f2 and enter tagtool)

It's pretty easy to use.

Yeah, sort of.  Except when I edit 1 tag, another gets corrupted...

Anyway, problem solved!  And I apologize to the creators of Rhythmbox, Amarok, Totem and vlc... I should've known it wasn't you messing with my expletives! ;)

---

