---
title: "[SOLVED] scripting help"
date: 2008-05-24
forum: Programming Talk
---

### Post by gbladeCL on 2008-05-24
Hello,
I'd like to write a script that will swap a field in a file with another, but I'm too new to scripting.
I want to do something like this:

```
# problem with grep | read
grep 'PlayResX:' ${FILENAME}.txt | read $RESX
grep 'PlayResY:' ${FILENAME}.txt | read $RESY

# extract attribute
RESX=${RESX#"PlayResX: "}
RESY=${RESY#"PlayResY: "}

# swap stuff
```

But grep | read gives me an empty string in RESX and RESY

---

### Post by randallecook on 2008-05-24
I don't understand what you ar trying to do. Can you post a short example with the two input files and the output file?

I suspect that sed or awk (or perl, of course) can do this, if you feel like reading about them.

Randall

---

### Post by geirha on 2008-05-24
Perhaps something like this?
```

RESX=$(grep 'PlayResX:' $filename | cut -d' ' -f2)
RESY=$(grep 'PlayResY:' $filename | cut -d' ' -f2)

```
or maybe
```

eval $(grep 'PlayRes[XY]:' $filename | sed 's/: /=/')
echo ${PlayResX}x${PlayResY}

```

---

### Post by gbladeCL on 2008-05-24
That worked for me. Thanks.

What I wanted was to turn this:
```
PlayResX: 1280
PlayResY: 720
```
into this
```
PlayResX: 720
PlayResY: 1280
```
Now that I can read the numbers I can do the replace.

---

