---
title: "zsh: Execute string with command and params"
date: 2012-07-18
forum: Programming Talk
---

### Post by kkjaergaard on 2012-07-18
I want to do like this in zsh:

```
S=aacgain -r
$S audio.m4a
```

I get the error: *zsh: command not found: -r*

What I wanted to happen: *aacgain -r audio.m4a*

In human, I want to define the entire command including parameters. Later in the script, I just have to supply the filename.

Is this possible?

---

### Post by Barrucadu on 2012-07-18
Use an array:

```
S=(aacgain -r)
$S audio.m4a
```

Unlike bash, zsh doesn't split strings on spaces when used in a command.

---

