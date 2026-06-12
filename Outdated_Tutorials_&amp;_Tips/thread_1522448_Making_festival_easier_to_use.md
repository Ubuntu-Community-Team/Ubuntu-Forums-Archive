---
title: "Making festival easier to use"
date: 2010-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by gbargoud on 2010-07-02
I have festival on my computer for text to speech. I have recently come to Linux from Mac and had gotten used to the easy to use text to speech command there:

```
say [what you want said]
```

I wanted that ease of use with festival so I decided to write a script that does that. here it is:

```

#! /bin/bash

echo "$*" > ~/.tmp
festival --tts ~/.tmp
rm ~/.tmp

```

and saved that as /usr/bin/say . Now for text to speech I can use that easy to use Mac command.


for those of you not versed in bash-fu here is a line by line explanation:

```
 #! /bin/bash 
```
tells which interpreter to use.

```
 echo "$*" > ~/.tmp 
```
take all arguments on the command line and save them as a file called ~/.tmp this file will be hidden due to the leading dot.

```
 festival --tts ~/.tmp 
```
read the file ~/.tmp using festival.

```
 rm ~/.tmp 
```
delete the hidden file created above.

---

