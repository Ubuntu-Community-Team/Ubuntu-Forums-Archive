---
title: "perl one liner"
date: 2011-07-07
forum: Programming Talk
---

### Post by PGScooter on 2011-07-07
Hi, I would like to write a one-line perl command that spits out everything that was put in except the last character, if that character is an end of line character.

I first tried the following:
```

perl -pe 's/\n$//'

```

but that strips *all* of the end of lines; I just want to strip the last one.

I think I am expecting too much from perl -pe because it processes each line separately and thus there is no way for it to treat the last line differently. Is this correct?

---

### Post by erind on 2011-07-07
I think you're looking for something like this:

 ```
perl -pe 's/\n$// [COLOR=Blue]if eof[/COLOR]' file
```

---

### Post by slavik on 2011-07-08
```
perl -e '$a = join "", <>; $a =~ s/\n$//; print $a;'
```

tests:

```

slavik@home-main:~$ echo -e 'hello\nworld'
hello
world
slavik@home-main:~$

slavik@home-main:~$ echo -e 'hello\nworld'| perl -e '$a = join "", <>; $a =~ s/\n$//; print $a;'
hello
worldslavik@home-main:~$

```

---

### Post by PGScooter on 2011-07-08
interesting, thanks for the replies. I'm trying to get it to work as an action using parcellite. Oftentimes I copy something with an end of line (like a command) but I don't want to past it into my shell because it will execute the command and I want to edit it before.
Both of your commands work I think, but for some reason in the action they don't:
```
echo "%s" | perl -e '$a = join "", <>; $a =~ s/\n$//; print $a;' | parcellite
```
I will post back if I figure it out.

Thank you for the help

---

