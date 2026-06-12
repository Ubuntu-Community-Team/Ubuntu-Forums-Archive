---
title: "Beginner python string replace question"
date: 2009-02-18
forum: Programming Talk
---

### Post by SaIva on 2009-02-18
Hi, probably not a hard task but I'm a big time beginner.

I have some documents that have US money values in them and I wanted to find all of these money values and replace them with the original values multiplied by 500. It's a little bit of a tedious task and I have to do it a lot so I thought I would write a script.

```

#Takes some long multi-line text and returns it with all of  the money values  multiplied by 500
#Money value starts with $, always ends with " " or "/" or "[" or "]" or "(" or ")" or "\n"

hh_in = raw_input("Paste here ;) ")
reading_money = False
i = 0

start = [] #start charcters' indices
end = [] #end characters' indices
for c in hh_in:
    if c == '$':
        reading_money = True
        start.append(i + 1)
    if reading_money == True:
        if c == " " or "/" or "[" or "]" or "(" or ")" or "\n":
            end.append(i - 1)
            reading_money = False
    i += 1

i = len(start) - 1 #I'm working backwards so that I don't mess up the character positions when I replace some text

while i >= 0:
    new_value = 500 * float(hh_in[int(start[i]),int(end[i])])
    del hh_in[int(start[i]),int(end[i])]
    #how can I insert the new value???
    i += 1
print hh_in

```

I get an error for this. line 23, in <module>
    new_value = 500 * float(hh_in[int(start[i]),int(end[i])])
TypeError: string indices must be integers, not tuple

And I have no idea how to insert back the new value. Can you guys give me some advice?

---

### Post by wmcbrine on 2009-02-18
First, Python strings are immutable. You can neither take a chunk out of the middle, nor insert one. You'll have to build a new string instead.

Second, the error message is easy to understand. You're trying to do:

string[start,end]

when what you need to do is:

string[start:end]

May I ask where you got the idea to do it the way you were trying to do it?

---

### Post by WW on 2009-02-18
I would consider using the re module, but if you haven't used regular expressions before, it might take longer to figure them out than it would take to get the code working without them.

One problem with your current approach is that strings are immutable.  You can't modify them in-place.  For example:
```

>>> s = "Hello, world!"
>>> s[7] = "W"  # This does not work.
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> del s[5]  # This does not work.
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object doesn't support item deletion
>>>

```
You'll have to create a new string from the old one, e.g.:
```

>>> t = s.replace(", w"," W")  # Create a *new* string.
>>> t
'Hello World!'
>>> 

```
You can assign the new string to the original, if you really want to "modify" the original.
```

>>> s = s.replace(", w"," W")
>>> s
'Hello World!'
>>> 

```

---

### Post by SaIva on 2009-02-18
Thanks a bunch, I think I've got it working after taking both of your advices and fixing a bunch of problems! If there's a better way to do something, please do let me know (the way I got the numbers all to two decimal points is probably pretty crude).

```

#Takes some long multi-line text and returns it with all of  the money values  multiplied by 300
#Money value starts with $, always ends with " " or "/" or "[" or "]" or "(" or ")" or "\n"

hh_in = raw_input("Paste here ;) ")
reading_money = False
i = 0

start = [] #start charcters' indices
end = [] #end characters' indices
for c in hh_in:
    if c == '$':
        reading_money = True
        start.append(i + 1)
    if reading_money == True:
        if c == " " or c == "/" or c == "[" or c == "]" or c == "(" or c == ")" or c == "\n":
            end.append(i)
            reading_money = False
    i += 1

i = len(start) - 1 #I'm working backwards so that I don't mess up the character positions when I replace some text

print i

while i >= 0:
    new_value = round(2 * float(hh_in[start[i]:end[i]]), 2)

    first_half = hh_in[0:start[i]]
    second_half = hh_in[end[i]:]

    hh_in = first_half + str(new_value) + second_half
    
    i -= 1

#This part is to make everything out to two decimal places since these are dollar amounts

hh_in = hh_in.replace(".0 ", ".00 ")
hh_in = hh_in.replace(".0/", ".00/")
hh_in = hh_in.replace(".0[", ".00[")
hh_in = hh_in.replace(".0]", ".00]")
hh_in = hh_in.replace(".0(", ".00(")
hh_in = hh_in.replace(".0)", ".00)")
hh_in = hh_in.replace(".0\n", ".00\n")

print hh_in

```

> **wmcbrine said:**
> Second, the error message is easy to understand. You're trying to do:

string[start,end]

when what you need to do is:

string[start:end]


Thanks, this made the error message more clear. I was scratching my head about where the tuple the error message was talking about was at but I see now I just confused the splice syntax.

> **wmcbrine said:**
> 
May I ask where you got the idea to do it the way you were trying to do it?


The idea for the program? I just figured I could delete the old text and insert new edited text so I googled and found out about del() (but I didn't know strings were immutable) and tried to find out how to insert new text.

> **WW said:**
> I would consider using the re module, but if you haven't used regular expressions before, it might take longer to figure them out than it would take to get the code working without them.

I'll check it out and try rewriting my script using this module - the documentation for it is kind of long :). Thanks for the tip.

---

### Post by wmcbrine on 2009-02-18
> **SaIva said:**
> The idea for the program?No, the idea to use a comma instead of a colon to take a slice of a string. I know that no Python reference would teach that...

> *If there's a better way to do something, please do let me know (the way I got the numbers all to two decimal points is probably pretty crude).*Yeah... what you want there is probably to use a format string. Specifically, '%.02f'.

```

hh_in = first_half + str(new_value) + second_half

```

could become:

```

hh_in = '%s%.02f%s' % (first_half, new_value, second_half)

```

(and then you could remove all the replaces).

Here's a place you could simplify:

```

if c == " " or c == "/" or c == "[" or c == "]" or c == "(" or c == ")" or c == "\n":

```

like so:

```

if c in (" ", "/", "[", "]", "(", ")", "\n"):

```

---

