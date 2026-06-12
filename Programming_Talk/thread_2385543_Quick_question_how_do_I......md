---
title: "Quick question how do I....."
date: 2018-02-21
forum: Programming Talk
---

### Post by Herbon on 2018-02-21
append the following "variable" items found in a txt file.

```

Blood Feud - Edward Klein
Carl Sagan   Contact
Carl Sagan   Pale Blue Dot
Carl Sagan   The Demon Haunted World
Christopher Lee's Fireside Tales
Confessions Of A Video Vixen-Karrine Steffans
DAN BROWN - Inferno  [Langdon 04]
Dan Kennedy - Renegade Millionaire

```

adding 

```

find ./ -name "* 

```

to the beginning of the line 

and

```

" -exec mv -t /media/Music/"1Audio Book"/ {} +

```

to the end of the line to complete following statements in a new txt file with python3

```

find ./ -name "*Blood Feud - Edward Klein" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   Contact" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   Pale Blue Dot" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   The Demon Haunted World" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Christopher Lee's Fireside Tales" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Confessions Of A Video Vixen-Karrine Steffans" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*DAN BROWN - Inferno  [Langdon 04]" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Dan Kennedy - Renegade Millionaire" -exec mv -t /media/Music/"1Audio Book"/ {} +

```

---

### Post by steeldriver on 2018-02-21
```

>>> with open("file.txt", "r") as f:
...     for line in f.read().splitlines():
...             print('find ./ -name "*{}" -exec mv -t /media/Music/"1Audio Book"/ {{}} +'.format(line))
...
find ./ -name "*Blood Feud - Edward Klein" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   Contact" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   Pale Blue Dot" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Carl Sagan   The Demon Haunted World" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Christopher Lee's Fireside Tales" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Confessions Of A Video Vixen-Karrine Steffans" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*DAN BROWN - Inferno  [Langdon 04]" -exec mv -t /media/Music/"1Audio Book"/ {} +
find ./ -name "*Dan Kennedy - Renegade Millionaire" -exec mv -t /media/Music/"1Audio Book"/ {} +
>>>

```

Not sure why you'd want to do that in python3 specifically those - these shell alternatives should work as well:

```

xargs -a file.txt -d '\n' printf 'find ./ -name "*%s" -exec mv -t /media/Music/"1Audio Book"/ {} +\n'

```

```

while IFS= read -r line; do printf 'find ./ -name "*%s" -exec mv -t /media/Music/"1Audio Book"/ {} +\n' "$line"; done < file.txt

```

```

mapfile -t lines < file.txt
printf 'find ./ -name "*%s" -exec mv -t /media/Music/"1Audio Book"/ {} +\n' "${lines[@]}"

```

---

### Post by The Cog on 2018-02-21
Yes, but I bet using xargs wasn't part of the homework assignment.

---

### Post by Herbon on 2018-02-22
@[**[COLOR=#DD4814][B]steeldriver**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1627500")

1st thanks, never thought about "xargs" or using "IFS" variable.  


xargs
[https://www.howtoforge.com/tutorial/linux-xargs-command/](https://www.howtoforge.com/tutorial/linux-xargs-command/)

IFS
https://bash.cyberciti.biz/guide/$IFS

---

