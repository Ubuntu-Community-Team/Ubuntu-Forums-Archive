---
title: "Please explain this command to me (batch lame mp3 encoding)"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by moltenicee on 2013-07-04
**Context:**
If I have a folder of .flac files and I decode them to .wav files which have spaces or other characters in the file name, the lame encoder throws a message saying excess arguments. However, files with no spaces are fine. Instead of renaming every single file, I want to simply pipe the names to the lame encoder and encode them in bulk.

For mp3gain, I have resolved this with:

```
find -name "*.mp3" -print0 | xargs -0 mp3gain -r
```

because mp3gain only takes one input, the mp3 file.


For lame, there are two inputs for the command, a target .wav and a resulting .mp3.


Another thread I found used a for loop:

```
for f in *.wav; do lame --preset fast extreme "$f" "${f%.wav}.mp3"; done
```




[B]Question:
[/B]
I have taken AP Computer Science A so I know the basic ideas behind for loops but I am intrigued by the second argument for lame:

```
"${f%.wav}.mp3"
```

What does the dollar sign do? What do the curly brackets mean? How does the percent sign work? (The resulting file is just the title name of the file minus the .wav extension so maybe it is excluding the .wav in the filename?)

Help would be appreciated

---

### Post by zero2xiii on 2013-07-04
Hay,

To understand commands (something like this for example) your best bet would be to echo the result:

Try:
```
for f in *.wav; do **echo** "$f" "${f%.wav}.mp3"; done
```

That should start giving you an idea of what the ${f%.wav} part does.. Play around with the content. Change the .wav to just av for example and so forth.

I can give you a more straight answer, but I feel it is better for one to learn by experience. You would not have asked if you do not wish to learn :) my opinion.

Cheers and good luck.

---

### Post by moltenicee on 2013-07-04
Thanks for teaching me about echo.

I looked up the dollar sign and I guess that is just how you refer back to variables in a for loop.

I think I figured out the rest:

```
${f%.wav}
**test1.wav** becomes [B]test1
[/B]
${f%av}
**test1.wav** becomes [B]test1.w


[/B]
```
So the % sign deletes all the characters starting from the right.

And so ```
${f%.wav}.mp3 
``` simply removes the trailing .wav and adds .mp3 instead.

Thanks!



Edit:
After some research, I think that using
```
"${f/wav/mp3}"
```  is much clearer.

---

