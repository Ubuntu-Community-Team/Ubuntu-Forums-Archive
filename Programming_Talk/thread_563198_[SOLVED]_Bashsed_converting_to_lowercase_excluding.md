---
title: "[SOLVED] Bash/sed converting to lowercase excluding []"
date: 2007-09-29
forum: Programming Talk
---

### Post by arsenic23 on 2007-09-29
Ok, I download a LOT of files every week and so I've been working on a script that will rename them all to various standards based on all kinds of different things.

The part of the script I'm working on now converts all the characters in the filename to lowercase, capitalizes the first character in the filename, and then capitalizes the first letter of every word in the file that is over 3 letters long.

After testing it I realized that just switching every character in the file to lowercase at the beginning isn't going to work for me.  What I need to do is change every character that doesn't fall between [ and ] into lowercase so that things like [MonO] keep there odd case structure.

I messed around with sed for a while, and tried to read up a little more on y/ but to no availe.  I just can't figure out how to change the case of everything save for the insides of [].

Any help would be apriciated.

---

### Post by arsenic23 on 2007-09-29
Ok, I did figure out a way to add what I wanted into the portion of the script that moves [$stuff] to the end of filenames.  What I'm doing is this:

```

sed -e 's/\(^[^\[]*\)\(\[[^]]*\]\)\([^.]*\)/\1\3\2/' -e 's/\(^[^[]*\)/\L\1/g' -e 's/\([^]]*$\)/\L\1/g'

```

---

