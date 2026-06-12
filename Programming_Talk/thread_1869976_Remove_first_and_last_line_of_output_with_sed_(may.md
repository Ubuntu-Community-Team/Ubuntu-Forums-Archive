---
title: "Remove first and last line of output with sed (maybe a better way)"
date: 2011-10-26
forum: Programming Talk
---

### Post by cj13579 on 2011-10-26
HI all,

I'm getting really frustrated with this so I was wondering whether someone can help me out? I am am trying to remove the first and last line of the following output:


```
ID     Done       Have  ETA           Up    Down  Ratio  Status       Name
   3     1%    10.1 MB  Unknown      0.0     0.0   0.57  Stopped      Horrible Bosses {2011} DVDRIP. Jaybob
Sum:           10.1 MB               0.0     0.0
```

The output is from transmission-remote. I am trying to dump this all into a variable in a script and it isn't going particularly well. I am trying to use sed but cannot get the command to work. This is what I have so far:

```
TORRENTLIST=$(transmission-remote --auth user:password --list | sed -e '1d;$d;s/^ *//' | cut –only-delimited –delimiter= ” ” –fields=1)
```

This is supposed to be dynamic so there could be 1 or 100 things in this list. The next step of my script feeds into a loop doing different stuff basded on their status and Completeness (if you wanted to know - lol).

My failing is that I copied this sed command from somewhere and I can't remember where. I have googled my life away trying to understand sed but I'm just there yet.

Many thanks in advance for any advice!

Thanks

Chris

---

### Post by Vaphell on 2011-10-26
it does exactly what you want
1d **d**eletes **1**st line, **$**d deletes the **last** line, s/^ *// removes spaces at the beginning (^) of each line (**s**ubstitutes any sequence of spaces with nothing).

test:
```
$ echo $'ID whatever\n      stuff\n more stuff\nSum: 666'
ID whatever
      stuff
 more stuff
Sum: 666

$ echo $'ID whatever\n      stuff\n more stuff\nSum: 666' | sed '1d; $d; s/^ *//'
stuff
more stuff



```

---

### Post by cj13579 on 2011-10-27
> **Vaphell said:**
> it does exactly what you want


You are completely right. I found what it was by sticking -x on my script but it was staring me in the face. Where I had copied it from the website it had copied in a load of additional random characters, changed some characters - all sorts of stuff was going on.

Many thanks for your quick response and help!

---

