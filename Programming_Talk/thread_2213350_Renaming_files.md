---
title: "Renaming files"
date: 2014-03-26
forum: Programming Talk
---

### Post by freebird54 on 2014-03-26
I have a normal enough task to complete - renaming some files.  Unfortunately I seem to be unable to come up with a command string that will accomplish what LOOKS to be a simple operation.  I have multiple(!) files of the form **## - Song Name.mp3**  (eg: *01 - Season of the Witch*) where the number refers to the track number on the CD it came from.  When I create a 'set' for in-car use, I do not need, or want, any track numbering. 

It seems that **mv** tries to find a directory to move it to - and that **rename** requires Perl knowledge to even operate it - knowledge I don't have.  There are a least 3 ways I could do this in AmigaDOS - 2 of them requiring only a single command, and the other involves having the **list** command write a script for me to execute - and thus is 2 commands.  Anything I have puzzled out so far on my terminal - OR on Nautilus - seems to involve hundreds of actions.. so far!  Anything else will take a long time to puzzle out a script with sed and cut and awk and...?

Any experts out there - can you give something simple (preferably) or at least working and comprehensible (to allow changes where necessary) to get this done a little more effectively? :)

Thanks in advance to whichever guru meditates on this....


PS: If anyone is interested, here is what would work in AmigaDOS:

**move ?????#?.mp3 #?.mp3**    // first 5 characters, then match 'anything' - to 'anything' without the 5 (obviously you don't want any .mp3 files WITHOUT the 5 leading characters in the directory when you do this!)

One could also match the numbers **(0-9|)** and strip them, and match ' - ' and leave it off too...  OR
use list to find the files, and output them to a file including a rename command with both versions of the file name filled in - then execute the file (AmigaDOS doesn't require a chmod to make a file executable).  

Not as fancy, or in the end quite as capable as full regex and all the tools - but a lot less confusing too!

---

### Post by buzzingrobot on 2014-03-26
If the filename contains spaces, mv will see each word as a separate argument. Try escaping it -- put quotes around it.

---

### Post by steeldriver on 2014-03-26
You could do something similar to your Amiga examples with bash parameter substitution (although a loop is needed, afaik)

```

$ for file in *.mp3; do mv -v -- "$file" "${file#[0-9][0-9] - }"; done
`01 - Season of the Witch.mp3' -> `Season of the Witch.mp3'

```

(strips the leading 2-digits-plus-space-hyphen-space from any mp3 files that have it - mv will skip any that don't match)

The perl syntax in the rename command is not too bad

```

$ rename -v -- 's/^\d+\s-\s//' *.mp3
01 - Season of the Witch.mp3 renamed as Season of the Witch.mp3
1999 - The Music of Canada.mp3 renamed as The Music of Canada.mp3

```

(match 1 or more digits followed by whitespace-hyphen-whitespace at the start of the name, and replace it with nothing), and rename supports older non-perl specific regex syntax if you're more comfortable with that e.g.
```

rename -v -- 's/^.....//' *.mp3          # match and replace (cut) five leading characters

rename -v -- 's/^.{5}//' *.mp3           # match and replace (cut)five leading characters (alternative)

rename -v -- 's/^[0-9]+ - //' *.mp3      # uses older style [0-9] instead of Perl \d and literal space instead of more general \s

```

---

### Post by Vaphell on 2014-03-26
i'd add that if you are going to experiment with *rename* you can test the results without making changes with *-n* parameter, so you can get the hang of it without risking anything.

on a sidenote, spending few hours to learn basics of regular expressions is one of the best investments one could possibly make and they are really not that confusing.

---

### Post by steeldriver on 2014-03-26
Good point Vaphell - I actually REMOVED the* -n* switches before posting because I always seem to get people posting back "I ran your commands and nothing happened"...

Also PLEASE point out if I have made any obvious snafus on the bash side of things :)

---

### Post by Vaphell on 2014-03-26
heh :-) when i post snippets that can go really wrong, usually i default to dry runs but explicitly mention it, even marking with bold/color which parts of code act as a safeguard (echos in front of mv/rm, -n in rename, etc).

obvious snafus in bash? not seeing anything, though i thought about something like this
```
for file in [0-9][0-9]\ -\ *.mp3; do mv -v -- "$file" "${file#*- }"; done
```
filtering done on the glob level which cuts down the number of calls and allows for lazier substitution within the loop, though it's more academic than anything :-)

---

