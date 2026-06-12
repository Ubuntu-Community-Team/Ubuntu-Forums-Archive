---
title: "bash script - how to make it recursive?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by eisam on 2008-09-05
Hi guys,

So I'm new to the forum here and pretty new to linux too, but I'm loving the ride. :popcorn:

Anyway, I have this quick script in bash to convert a batch of .ram files to .ogg format (it's something I modified from a friend's script):
```

#!/bin/bash

for i in *.ram ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && oggenc audiodump.wav -o $i; done

for i in *.ram; do mv "$i" "`basename "$i" .ram`.ogg"; done

rm audiodump.wav

```

It works fine, except it doesnt go into folders - it only works on the folder you happen to be in. Can anyone help me improve it?

Thanks,
E

---

### Post by Dedoimedo on 2008-09-05
Hello,

Try this:

In the parent directory, containing all the relevant subdirectories:

```
for i in $(ls -la)
do
if [ -d "$i" ]; then
 cd "$i"
 your script ...
fi
done
```

Cheers,
Dedoimedo

P.S. That's one way, you can also use ls -R to see everything, recursively ... there are several nuances, try which one suits you...

P.S.S. Do change the loop variable to make it more readable, use j, k etc.

---

### Post by finer recliner on 2008-09-05
> **Dedoimedo said:**
> Hello,

```
for i in $(ls -la)
do
if [ -d "$i" ]; then
 cd "$i"
 your script ...
fi
done
```


that isn't recursive. it will only go one level deep, and doesnt return to the parent directory to cd into subsequent subdirectories

---

### Post by eisam on 2008-09-05
thanks for replying so quickly, folks!

i think i need to do something along these lines:

```

for m in $(ls -R)
do
 if [i = *.ram] ; then
  mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i
  oggenc audiodump.wav -o $i
  mv "$i" "`basename "$i" .ram`.ogg"
  rm audiodump.wav
 fi
done

```

except that my if syntax seems to be wrong :( when i test a simplified version out on the command line (if [i = *c] ; then ls ~ ; done - having previously made i=abc) it fails with 
```
bash: [: too many arguments
```

whaa?:confused: does that mean the *.ram is being expanded before it gets compared to the i variable? any suggestions for what to do next?

---

### Post by HermanAB on 2008-09-05
You can do that in one line using the 'find' command.

Cheers,

Herman

---

### Post by Dedoimedo on 2008-09-05
> **finer recliner said:**
> that isn't recursive. it will only go one level deep, and doesnt return to the parent directory to cd into subsequent subdirectories

Read my entire post, include PS and PSS.
And I believe he knows how to cd back to parent ...
Dedoimedo

---

