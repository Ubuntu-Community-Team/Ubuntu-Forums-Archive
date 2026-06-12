---
title: "quick text edit using bash"
date: 2009-05-08
forum: Programming Talk
---

### Post by Kingsley on 2009-05-08
I want to use bash to remove a certain portion of words in my playlist file. I know cut is probably one of the best tools for this, but I can't figure out how to use it to my needs.

Here's a portion of the text file I want to edit.
```

#EXTM3U
/media/shared/Muzik/Jimi Hendrix - Discography/Rainbow Bridge Vinyl Rip/03 - Pali Gap.mp3
/media/shared/Muzik/Nine Inch Nails - The Fragile/Nine Inch Nails - The Fragile (Left)/07 - Nine Inch Nails - Just Like You Imagined.mp3
/media/shared/Muzik/Megadeth - United Abominations/08 - A Tout Le Monde.mp3
/media/shared/Muzik/Pink Floyd - Echoes/04 - Time.mp3
/media/shared/Muzik/Lupe Fiasco - The Cool/04 - The Coolest.mp3
/media/shared/Muzik/Fela Kuti - 22 albums/Fela Kuti - 1972 - roforo fight/04 - Trouble Sleep Yanga Wake Am.mp3
/media/shared/Muzik/Fela Kuti - 22 albums/Fela Kuti - 1975 - Expensive ****/02 - Water No Get Enemy.mp3

```From each line, I need everything before the last slash (/) removed and the resulting text concatenated to another text file.

Thanks.

---

### Post by Kingsley on 2009-05-08
Whoops. I meant to type 'bash' in the title, not 'back.'

---

### Post by ibuclaw on 2009-05-08
Looks like sed is what you need.

```
sed 's/\/.*\///' **playlist.txt** > **newplaylist.txt**
```

Also, I can rename the thread title at your request.

Regards
Iain

---

### Post by Kingsley on 2009-05-08
That works just as I needed. Thank you very much.

And it'd be great if you changed the title for me.

---

### Post by ibuclaw on 2009-05-08
> **Kingsley said:**
> That works just as I needed. Thank you very much.

And it'd be great if you changed the title for me.

Your welcome, and the title has been change ;)

Regards
Iain

---

### Post by ghostdog74 on 2009-05-08
```

awk -F"/" '{print $NF}' file

```

---

### Post by MadCow108 on 2009-05-08
misread something ._.

---

### Post by Arndt on 2009-05-09
> **tinivole said:**
> Looks like sed is what you need.

```
sed 's/\/.*\///' **playlist.txt** > **newplaylist.txt**
```

Also, I can rename the thread title at your request.

Regards
Iain

Slightly easier to read, but functionally equivalent:

```
sed 's|.*/||'
```

---

