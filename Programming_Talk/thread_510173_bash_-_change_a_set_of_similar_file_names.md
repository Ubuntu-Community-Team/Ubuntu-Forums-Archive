---
title: "bash - change a set of similar file names"
date: 2007-07-26
forum: Programming Talk
---

### Post by Xubus on 2007-07-26
Okay, this is a rather vague question that may be obvious to some (hopefully very obvious :P)

I've searched for working with strings with bash but all the bash guides I've found are about writing scripts with dedicated files. I don't want to do that. I want to do it on the fly ;)

I want to take a set of similarly named files and rename them with another set of similar names.

An example: the output of cdda2wav would be lots of audio_01.wav. Currently I just do
flac --best *_[012][0123456789].* and rename them individually *by hand*. Ouch, eh.

What I'd want to do is say ... make name01-20 the names of the songs, then rename the files to
Artist.yyyy-mm-dd.Album.##.Track.flac. The only thing I realise at this point is I'm going to be using some kind of loop. Will I need sed? Sed scripts look awfully confusing ...

In repetition, I want to take
audio_[0-2][0-9].flac
and turn it into
Artist.2000-01-01.Album.[0-2][0-9].$name1-20.flac
Preferably with a one liner.

... I'm clueless! :confused: Can anyone show me how to do it please?


(I'm not sure whether this is worthy of being in the programming section ... mods feel free to move it to general if it's not)


Secondary question:
How would I monitor a folder and make a copy of each revision of every file in said folder each time they change and append the date onto said revisions (i.e. former_name+date.ext).

---

### Post by jyba on 2007-07-26
Maybe I've misunderstood exactly what format you want to use, but if you mean something like this...

```
Radiohead.2000-10-02.Kid_A.04.Everything_in_Its_Right_Place-01.flac
Radiohead.2000-10-02.Kid_A.04.Kid_A-02.flac
Radiohead.2000-10-02.Kid_A.04.The_National_Anthem-03.flac
Radiohead.2000-10-02.Kid_A.04.How_to_Disappear_Completely-04.flac
...
```

...then you can't do it as a one-liner. The Artist, Date, Album, and Album Number will all be the same for each track, so that's okay, and the Track Numbers can be generated in a one-liner, but you still have to type in each of the Track Titles (unless you're going to extract them from a file or something). You're better off doing it as a script and using 'read -p' in a loop to gather the Track Titles.

---

### Post by Xubus on 2007-07-26
> **jyba said:**
> Maybe I've misunderstood exactly what format you want to use, but if you mean something like this...

```
Radiohead.2000-10-02.Kid_A.04.Everything_in_Its_Right_Place-01.flac
Radiohead.2000-10-02.Kid_A.04.Kid_A-02.flac
Radiohead.2000-10-02.Kid_A.04.The_National_Anthem-03.flac
Radiohead.2000-10-02.Kid_A.04.How_to_Disappear_Completely-04.flac
...
```

...then you can't do it as a one-liner. The Artist, Date, Album, and Album Number will all be the same for each track, so that's okay, and the Track Numbers can be generated in a one-liner, but you still have to type in each of the Track Titles (unless you're going to extract them from a file or something). You're better off doing it as a script and using 'read -p' in a loop to gather the Track Titles.
Yes that's what I meant ;)

bash remembers variables right (across manually entered commands, I mean)? I thought I could enter

name1="Airbag" name2="Paranoid Android" etc ...

Then grab all the tracks ($name0[123...]) and rename them with something involving

for (first track) to (last track)
mv audio_[0-2][0-9].flac to Fixed string (Radiohead.1997-06-16.OK Computer.) + track # + .$name(number)

But I have 0 scripting experience ... I only understand the basic concepts. I'm trying to learn as well as getting something done here, see ;)

---

### Post by stylishpants on 2007-07-26
WAV files don't have any embedded metadata tags that you could use to extract album / artist / title information.

FLAC files can have this metadata, so assuming yours have it, what you could really use here is a file conversion program that can convert from flac to wav and lets you specify an output format for the filename that includes that metadata.

Maybe you should try soundkonverter.

---

### Post by jyba on 2007-07-26
Yes, I think stylishpants has the solution. cdda2wav is just a symlink to icedax. icedax looks primitive compared to soundkonverter. If you rip your cd's directly into flac using soundkonverter then you will preserve any metadata and thus may be able to rename them with a simple one-liner.

---

