---
title: "Bash: autocomplete from list"
date: 2010-07-31
forum: Programming Talk
---

### Post by silentrebel on 2010-07-31
Let us assume that I have a text file with expressions separated by line breaks.

I would like Bash to include the expressions of this text file in its search when I press double-tab (autocomplete).

Is this possible?  How would I do it?  Programming is no foe of mine.

Thanks,
Grasswistle

---

### Post by geirha on 2010-08-01
You'll want to read the «Programmable Completion» chapter of bash's man-page.

You can look in /etc/bash_completion and /etc/bash_completion.d/* for examples.

---

### Post by gmargo on 2010-08-01
There are a bunch of examples in the **/usr/share/doc/bash/examples/complete/** directory if you install the **bash-doc **package.

---

