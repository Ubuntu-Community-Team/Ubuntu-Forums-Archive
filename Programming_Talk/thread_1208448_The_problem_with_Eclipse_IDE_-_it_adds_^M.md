---
title: "The problem with Eclipse IDE - it adds ^M"
date: 2009-07-09
forum: Programming Talk
---

### Post by Ascenti0n on 2009-07-09
I used to use Eclipse as my main IDE, but now I use Gedit mainly, as it's faster, lighter and is efficient for 90% of web development work I need to do on a day-to-day basis.

When using Gvim or Gedit to edit files I had created and edited using Eclipse, there is: ^M tags at the end of every line, almost like, and probably is, "CR" markers for the IDE's internal use.

Suffice to say, I'm not impressed by the unsightly additions, and I'd like to find a way of getting rid of these, with a script or something.

Any ideas?

---

### Post by dwhitney67 on 2009-07-09
dos2unix is your friend.  Use it to convert those files to use a newline in lieu of the CR.

As far as any IDE is concerned, I will refrain from commenting on those this early in the morning.

---

### Post by Ascenti0n on 2009-07-09
doeas anyone know of any gedit plugins / vim scripts that will help?

---

### Post by monraaf on 2009-07-09
You can use this in Vim to get rid of these ^M:

```

:%s/\r//g

```

---

### Post by master_kernel on 2009-07-09
I don't know why it saves in binary format instead of ASCII.

---

### Post by Ascenti0n on 2009-07-09
> **monraaf said:**
> You can use this in Vim to get rid of these ^M:

```

:%s/\r//g

```

awsome - what does this dark magic mean?

Seriously, it looks like regexp, but I don't understand it. Can anyone explain what this command means? It's serious power, and I feel I need a dose.

---

### Post by Mirge on 2009-07-09
search for \r, replace with nothing, globally.

At least I assume, it's been a while.

---

### Post by Ascenti0n on 2009-07-09
well, whatever it means, it's tasty. I really must set time aside to learn some regexp. :)

---

### Post by JordyD on 2009-07-09
> **Ascenti0n said:**
> well, whatever it means, it's tasty. I really must set time aside to learn some regexp. :)
It's not regexp. In vim, the syntax for the search and replace command is:

```
:<line number>s/<what you want to replace/<replaced with>/<options>
```

In this case, % = all lines; s = substitute; \r = what will be replaces (those ^M things); and we want to replace it with nothing, so we leave that spot empty; g = when you find one, don't stop, keep looking

Does that clear things up?

Examples:
```
:%s/hello/hi/i               replace hello with hi, case insensitive (i), and on all lines
:4s/guacamole/banana/gc      replace guacamole with banana, don't stop when you find one (g), confirm when you find one (c), on line 4
```

EDIT: I had a file where I needed to get rid of these. I didn't know that they were represented by \r, so I took a different approach:
```
:map <F2> nD
```
Then, I pressed "*" on one of the characters, this finds them all. Hold down F2, that executes nD over and over again. n goes to the next found, and D deletes everything to the end of the line, and since these were the only things at the end of the line, it deleted all of them. Mine was slower, but it was more fun to do. Plus, I didn't know about \r.

---

### Post by CptPicard on 2009-07-09
+1 to dwhitney67 ... I get the feeling that the actual issue has not been addressed clearly enough: the source probably comes from Windows, and therefore has the extra Windows newline characters which show up as ^M.

[http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

That is, it has nothing to do with Eclipse "tagging" anything. There may be a setting somewhere to properly read in Windows newline format sources though...

---

### Post by Mirge on 2009-07-09
> **JordyD said:**
> **It's not regexp**. In vim, the syntax for the search and replace command is:

```
:<line number>s/<what you want to replace/<replaced with>/<options>
```In this case, % = all lines; s = substitute; \r = what will be replaces (those ^M things); and we want to replace it with nothing, so we leave that spot empty; g = when you find one, don't stop, keep looking

Does that clear things up?

Examples:
```
:%s/hello/hi/i               replace hello with hi, case insensitive (i), and on all lines
:4s/guacamole/banana/gc      replace guacamole with banana, don't stop when you find one (g), confirm when you find one (c), on line 4
```EDIT: I had a file where I needed to get rid of these. I didn't know that they were represented by \r, so I took a different approach:
```
:map <F2> nD
```Then, I pressed "*" on one of the characters, this finds them all. Hold down F2, that executes nD over and over again. n goes to the next found, and D deletes everything to the end of the line, and since these were the only things at the end of the line, it deleted all of them. Mine was slower, but it was more fun to do. Plus, I didn't know about \r.

Looks like regular expressions to me... even s/find/replace/flag (or whatever) syntax looks like Perl to me.

---

### Post by TheStatsMan on 2009-07-09
Also agree with dwhitney67, dos2unix is the easiest way

---

### Post by myrtle1908 on 2009-07-09
> **Ascenti0n said:**
> well, whatever it means, it's tasty. I really must set time aside to learn some regexp. :)

Whilst not exactly the same as the Perl regexp implementation, VIM's is very similar.  See the following article:-

[http://www.geocities.com/volontir](http://www.geocities.com/volontir)

Also, here it describes the main differences between Perl regex and VIM ... [http://www.geocities.com/volontir/#compare](http://www.geocities.com/volontir/#compare)

---

### Post by JordyD on 2009-07-10
> **Mirge said:**
> Looks like regular expressions to me... even s/find/replace/flag (or whatever) syntax looks like Perl to me.

Cool. I guess I know regexp to some extent, and I didn't even know it.

---

