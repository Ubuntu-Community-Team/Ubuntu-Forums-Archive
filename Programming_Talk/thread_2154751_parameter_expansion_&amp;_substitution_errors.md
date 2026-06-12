---
title: "parameter expansion &amp; substitution errors"
date: 2013-06-15
forum: Programming Talk
---

### Post by VMC on 2013-06-15
I have this error that uses parameter expansion and parameter substitution, but I get errors. Can you spot the reason for the error?

```
#!/bin/sh

echo "AQ wE rTy  Ui  Op"

selection="AQ wE rTy  Ui  Op"

choice=${selection// } #remove spaces

choice2=${selection,,} #lower case

echo $choice

echo $choice2 
```

Here's the error: *./x: 5: ./x: Bad substitution*

This is just a simple snippet showing the error from a much larger script.

I found the simple error, I just wasn't expecting it.

The original script was showing most of the functions of zenity, found **[here]("http://www.mainstreetanswers.org/zenity.txt")**.

---

### Post by steeldriver on 2013-06-15
well the obvious thing would seem to be that those are bash substitutions, and on most (Ubuntu) systems, sh is not bash

---

### Post by VMC on 2013-06-15
> **steeldriver said:**
> well the obvious thing would seem to be that those are bash substitutions, and on **most (Ubuntu) systems**, sh is not bash

On the sh(dash) man page, was my clue. Then it hit me. First time I needed to change from sh to bash. In the past it was on another system. And in looking at code from usr/bin I found my answer. No parameter usage on using /bin/sh.

What threw me off was the length of code from the fist 'sh' assignment in the original zenity.sh script, and the parameters in question. I'll have to check my other OS's and see if their is perhaps a link from 'sh' to 'bash' or an updated 'sh'. I'm unsure of the difference of dash 'sh' and any others.

---

### Post by Vaphell on 2013-06-15
sh is used mostly for system stuff that is supposed to be light on resources and distros apparently symlink all kinds of stardards compatible shells there, according to their needs and vision. When you write a userspace, script declare it as a bash one right off the bat with proper hashbang line to remove any ambiguosity and enjoy convenient features bash has to offer.

---

