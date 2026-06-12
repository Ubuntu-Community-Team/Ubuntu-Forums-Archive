---
title: "Python branching statement beginner question"
date: 2010-04-28
forum: Programming Talk
---

### Post by aloprot on 2010-04-28
Hey, I'm trying to learn python and I have trouble understanding some code. I hope you can help me understand.
So I have the following code:

```
def stripTags(html):
    inside = 0
    text = ''
    for char in html:
        if char == '<':
            inside = 1
            continue
        elif (inside == 1 and char == '>'):
            inside = 0
            continue
       [COLOR=Red] elif inside == 1:
            continue[/COLOR]
        else:
            text += char
    return text

```
I can't understand the lines in read. Why does the programmer puts them? I don't understand why does he checks again if he is in inside of the tag or not? and if let's say is it like in example,1 which is true...what happens? Continue what? Could someone help me understand this?Thanks.

---

### Post by CptPicard on 2010-04-28
Because the condition immediately before also has another additional condition, which may not be true (the char == '>' one). "Continue" just skips straight to the next item in the list and starts anew from top.

---

### Post by kostkon on 2010-04-28
```

elif inside == 1:
            continue
```
means that if it's already in the tag (and obviously the char isn't '<' or '>', since to reach this brand, the other two had to be false) then it is a character in the tag and it's not needed; the code just returns the text inside a tag and doesn't care about the tag per se.

---

### Post by aloprot on 2010-04-28
Thank you, I understood. It's a bit frustrating as a beginner. I get mentally kernel panic when seeing this code, and not knowing and understanding all the statements.

---

