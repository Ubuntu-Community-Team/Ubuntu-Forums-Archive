---
title: "Bash script to rename files"
date: 2012-08-18
forum: Programming Talk
---

### Post by Odexios on 2012-08-18
Hello everyone!

I have a folder with a few files I want to rename; to speed things up a little I wrote a very little script to parse each file's name and create the new filename.

Here it is:

```
#! /bin/bash

for file in Sam*.mkv
do
  episode="${file#*-}"
  episode="${episode%%-*}"
  title="${file#*$episode-}"
  title="${title%(anime*}"
  title="$(echo $title | sed 's/\([Aabcdefghijklmnopqrstuvwxyz.,]\)\([ABCDEFGHIJKLMNOPQRSTUVWXYZ]\)/\1 \2/g')"
  echo "$file -> $prefix - $season""x""$episode - $title"".""$extension"
  mv "$file" "$prefix - $season""x""$episode - $title"".""$extension"
done

```

(By the way, I'd appreciate any suggestion for the sed part, which is *really* ugly)

season, extension and episode are variables I defined elsewhere.

Anyway, up to the echo part everything works fine (the new filename I want is right, and so on); but when we get to the line with mv, it raises an error saying that it can't move the file because there is no such file or directory.

I could have expected something went wrong in the parsing phase, but mv should work fine, considering I give it only two strings and the "file" variable remains untouched for all the script; can anyone help me find where's the mistake?

EDIT:
What sed does here:
> Whenever it finds a capital letter after a lowercase one (or a capital A, which was the only exception I needed) it puts a space between the capital letter and the previous one (somethingLikeThis -> something Like This).

Filename example:
```
SamuraiChamploo-12-TheDisorderDiaries(anime-mx)[18D45AB5].mkv
```

Echo output:
```
SamuraiChamploo-12-TheDisorderDiaries(anime-mx)[18D45AB5].mkv -> [DivX - ENG/JAP] Samurai Champloo - 01x12 - The Disorder Diaries.mkv
```

No judgement on the files, please xD

---

### Post by unevenflow on 2012-08-18
Hey,  try pyrenamer```
sudo apt-get install pyrenamer
```should do the job for you.

---

### Post by papibe on 2012-08-18
> **unevenflow said:**
> Hey,  try pyrenamer.
+1

Very easy to use GUI tool to rename files. It is specially good for renaming season/episode/name stuff.

Regards.

---

### Post by Vaphell on 2012-08-18
cli *rename* works with sed/perl-like expressions too.

i guess that sed is supposed to capitalize words and add nice spaces. What title formats should it support?
Obvious changes: [A..Z] -> [A-Z], [Aa..z,.] -> [Aa-z,.] and using -r to drop escaping of regex related symbols: -r 's/(..)(..)/\1 \2/' - much easier on the eyes. Group matching is more useful than literal () (they require \ here) so i prefer -r mode.

---

### Post by Odexios on 2012-08-18
Thanks for pyrenamer, I don't usually like this kind of tools, but it seems pretty neat.

Anyway, just as a learning experience, any clue on what's wrong with the script? I added a few details in the OP. I might not be always able to see how to make something work, but I'm usually able to understand why it's not working; it bugs me that I have no clue on what's wrong here.

> **Vaphell said:**
> cli *rename* works with sed/perl-like expressions too.

i guess that sed is supposed to capitalize words and add nice spaces. What title formats should it support?
Obvious changes: [A..Z] -> [A-Z], [Aa..z,.] -> [Aa-z,.] and using -r to drop escaping of regex related symbols: -r 's/(..)(..)/\1 \2/' - much easier on the eyes. Group matching is more useful than literal () (they require \ here) so i prefer -r mode.
Yeah, maybe explaining what sed does here might have been a good idea xD

Whenever it finds a capital letter after a lowercase one (or a capital A, which was the only exception I needed) it puts a space between the capital letter and the previous one (somethingLikeThis -> something Like This); so, yeah, you got it right.

Thanks for the advice! I didn't know of the - operator to specify a range, nor of the -r option; the result is a lot more clean now, thanks.

---

### Post by Vaphell on 2012-08-19
the problem lies here:
```
[DivX - ENG[COLOR="Blue"]/[/COLOR]JAP]
```
i'll let you figure out why ;-)

---

### Post by Odexios on 2012-08-19
> **Vaphell said:**
> the problem lies here:
```
[DivX - ENG[COLOR="Blue"]/[/COLOR]JAP]
```
i'll let you figure out why ;-)
Of course, there's no "[DivX - ENG" directory; using the slash was a poor choice. Solved it! Thank you, it was really bothering me [img]http://forum.gamesvillage.it/images/smilies/asd.gif[/img]

---

