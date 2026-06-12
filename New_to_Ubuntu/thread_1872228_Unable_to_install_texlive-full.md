---
title: "Unable to install texlive-full"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by snl on 2011-10-30
I am trying to install texlive-full and get the following message

```
E: I wasn't able to locate file for the texlive-lang-greek package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```

Please advise.
Thank you in advance.

---

### Post by cavh on 2011-10-30
In a terminal type:

sudo apt-get update

and then

sudo apt-get install texlive-full

and post back with the result

NB: you need to enter your usual login password when entering any sudo command. Just type as usual, but note that you will not see any asterisks or other characters echoed in your terminal as you type.

---

