---
title: "[SOLVED] [Python] strip a line using delimiters."
date: 2008-11-11
forum: Programming Talk
---

### Post by buttertoad on 2008-11-11
I apologize if this is covered elsewhere but I did not find it.

My goal is a program that will take a chunk of data from a serial connection, remove the garbage, and print one line from it.

So far I can open the serial connection, get the data, remove the esc characters but I can't figure out how to strip the line I want. The line always starts with #! and ends with #n. The line is formated how I want it as far as whitespace goes, but the length of the line is subject to change.

I'm sure the answer is staring me in the face but I can't figure it out.
I'm very new to python so any help would be greatly appreciated.
Thanks.

---

### Post by Greyed on 2008-11-11
Does the line contain #?  If not,

```

>>> '#!Some random string.#n'
'#!Some random string.#n'
>>> spam = '#!Some random string.#n'
>>> spam.split('#')
['', '!Some random string.', 'n']
>>> ham = spam.split('#')[1]
>>> ham
'!Some random string.'
>>> ham[1:]
'Some random string.'

```

That's just to show how to extract one string from the middle.  However, if you already have it down to the level as shown by spam then it is just a slice:

```

>>> spam[2:-2]
'Some random string.'

```

---

### Post by buttertoad on 2008-11-12
That did it! :)
Thank you.

fwiw, this is the line I was trying to extract from:
```
                                                                  #!00:00:00  SAR   SRE2   1  DV1149 NORMAL END OF TAPE #n !        !#TIME !+APPL  PROC  TAPE  VOLUME !TMESSAGE "!                                                                              #!00:00:00  SAR   SRE2   1  DV1149 NORMAL END OF TAPE #n !        !#TIME !+APPL  PROC  TAPE  VOLUME !TMESSAGE "!
```

---

